# librewolf

@Message(pairSeparator = "\\u0001", keyValuePairSeparator = "=", type = "FIX", version = "5.1")
class UptmResponseError {
@field:KeyValuePairField(tag = 10251) var tradeErrorCode: String? = null
@field:KeyValuePairField(tag = 10252) var tradeErrorDesc: String? = null
}

@Section(number =1)

@Message(pairSeparator = "\\u0001", keyValuePairSeparator = "=", type = "FIX", version = "5.1")

class UptmResponseHeader {
@field:KeyValuePairField(tag = 8, position = 0) var beginString: String? = null
@field:KeyValuePairField(tag = 9, position = 1) var bodyLength: String? = null
@field:KeyValuePairField(tag = 35, position = 2) var msgType: String? = null
@field:KeyValuePairField(tag = 49, position = 3) var senderComplD: String? = null
@field:KeyValuePairField(tag = 56, position = 4) var targetComplID: String? = null
@field:KeyValuePairField(tag = 115, position = 5) var onBehalfOfComplD: String? = null
@field:KeyValuePairField(tag = 128, position = 6) var deliverToComplD: String? = null
@field:KeyValuePairField(tag = 50, position = 7) var senderSublD: String? = null
@field:KeyValuePairField(tag = 142, position = 8) var senderLocationID: String? = null
@field:KeyValuePairField(tag = 57, position = 9) var targetSubID: String? = null
@field:KeyValuePairField(tag = 143, position = 10) var targetLocationID: String? = null
@field:KeyValuePairField(tag = 116, position = 11) var onBehalfOfSubID: String? = null
@field:KeyValuePairField(tag = 144, position = 12) var onBehalfOfLocationID: String? = null
@field:KeyValuePairField(tag = 129, position = 13) var deliverToSublD: String? = null
@field:KeyValuePairField(tag = 145, position = 14) var deliverToLocationID: String? = null
@field:KeyValuePairField(tag = 43, position = 15) var possDupFlag: String? = null
@field:KeyValuePairField(tag = 97, position = 16) var possResend: String? = null
@field:KeyValuePairField(tag = 52, position = 17) var sendingTime: String? = null
@field:KeyValuePairField(tag = 122, position = 18) var origSendingTime: String? = null
@field:KeyValuePairField(tag = 347, position = 19) var messageEncoding: String? = null
@field:KeyValuePairField(tag = -6, position = 20) var clientSendTime: String? = null
@field:KeyValuePairField(tag = -7, position = 21) var clientReceiveTime: String? = null
@field:KeyValuePairField(tag = -8, position = 22) var qOrderSendTime: String? = null
@field:KeyValuePairField(tag = -9, position = 23) var qOrderReceiveTime: String? = null
@field:KeyValuePairField(tag = -10, position = 24) var qExecSendTime: String? = null
@field:KeyValuePairField(tag = -11, position = 25) var qExecReceiveTime: String? = null
@field:KeyValuePairField(tag = -12, position = 26) var exchangeReceiveTime: String? = null

}

@Message(pairSeparator = "\\u0001", keyValuePairSeparator = "=", type = "FIX", version = "5.1")
class UptmResponseHop {
@field:KeyValuePairField(tag = 628) var hopComplID: String? = null
@field:KeyValuePairField(tag = 629) var hopSendingTime: String? = null
@field:KeyValuePairField(tag = 630) var hopRefID: String? = null
@field:KeyValuePairField(tag = 10100) var hopContext: String? = null
}

@Message(pairSeparator = "\\u0001", keyValuePairSeparator = "=", type = "FIX", version = "5.1")
class UptmResponseNumberOfErrors {

@field:KeyValuePairField(tag = 10250) var numberOfErrors: String? = null
}

@Message(pairSeparator = "\\u0001", keyValuePairSeparator = "=", type = "FIX", version = "5.1")
class UptmResponseNumberOfHops {

@field:KeyValuePairField(tag = 627) var numberOfHops: String? = null
}
@Section(number = 2)
@Message(pairSeparator = "\\u0001", keyValuePairSeparator = "=", type = "FIX", version = "5.1")
class UptmResponseObject {

@field:Link var header: UptmResponseHeader = UptmResponseHeader()

@field:Link var numberOfHops: UptmResponseNumberOfHops = UptmResponseNumberOfHops()

@field:OneToMany(mappedTo = "citi.uptm.UptmResponseHop")
var hoplList = mutableListOf<UptmResponseHop>()

@field:KeyValuePairField(tag = 10018) var zExecID: String? = null

@field:KeyValuePairField(tag = -14) var syncNum: String? = null

@field:KeyValuePairField(tag = 10238) var tradeOptionalField: String? = null
@field:KeyValuePairField(tag = 17) var execlD: String? = null

@field:KeyValuePairField(tag = 10249) var tradeStatus: String? = null

@field:Link var numOfErrors: UptmResponseNumberOfErrors = UptmResponseNumberOfErrors()

@field:OneToMany(mappedTo = "citi.uptm.UptmResponseError")
var errors = mutableListOf<UptmResponseError>()

@field:KeyValuePairField(tag = 10253) var tmsReportID: String? = null
@field:KeyValuePairField(tag = 10254) var sysTID: String? = null
@field:KeyValuePairField(tag = 55) var symbol: String? = null
@field:KeyValuePairField(tag = 10293) var tmlIReportID: String? = null
@field:KeyValuePairField(tag = 10074) var customInfo: String? = null
@field:KeyValuePairField(tag = 10617) var blotterCode: String? = null
@field:KeyValuePairField(tag = 20090) var rejectCode: String? = null

@field:Link var trailer: UptmResponseTrailer = UptmResponseTrailer()

class UptmResponseObjectSerde : Serde<UptmResponseObject> {
override fun fromBytes(bytes: ByteArray): Either<Throwable, UptmResponseObject> {
TODO("Not yet implemented")
}

override fun toBytes(body: UptmResponseObject): Either<Throwable, ByteArray> =
Either.catch {
val bindyKVPDataFormat = BindyKeyValuePairDataFormat(UptmResponseObject::class.java)
val baos = ByteArrayOutputStream()
bindyKVPDataFormat.marshal(

DummyCamelExchange(DummyCamelMessage(), DummyCamelContext(DummyCamelTypeConverter())),

mutableListOf(
mapOf(UptmResponseHeader::class.java.canonicalName to body.header),
mapOf(UptmResponseObject::class.java.canonicalName to body),
mapOf(UptmResponseNumberOfHops::class.java.canonicalName to body.numberOfHops),
)
.also { mutableList ->
body.hoplList.forEach { uptmResponseHop ->
mutableList.add(mapOf(UptmResponseHop::class.java.canonicalName to uptmResponseHop))
}
mutableList.add(
mapOf(UptmResponseNumberOfErrors::class.java.canonicalName to body.numOfErrors)
)
body.errors.forEach { uptmResponseError ->
mutableList.add(
mapOf(UptmResponseError::class.java.canonicalName to uptmResponseError)

)
}
mutableList.add(mapOf(UptmResponseTrailer::class.java.canonicalName to body.trailer))
b
baos
)
baos.toString(StandardCharsets.UTF_8).replace(Serde.crlfRegex, "").toByteArray()
}
}

@Section(number = 3)
@Message(pairSeparator = "\\u0001", keyValuePairSeparator = "=", type = "FIX", version = "5.1")
class UptmResponseTrailer {
@field:KeyValuePairField(tag = 10) var checkSum: String? = null
}

@Message(pairSeparator = "\\u0001", keyValuePairSeparator = "=", type = "FIX", version = "5.1")
class UptmTradeObject {
@field:KeyValuePairField(tag = 31) var lastPx: String? = null
@field:KeyValuePairField(tag = 32) var lastQty: String? = null
@field:KeyValuePairField(tag = 54) var side: String? = null
@field:KeyValuePairField(tag = 64, pattern = "yyyyMMdd") var settIDate: LocalDate? = null
@field:KeyValuePairField(tag = 75, pattern = "yyyyMMdd") var tradeDate: LocalDate? = null
@field:KeyValuePairField(tag = 150) var execType: String? = null
@field:KeyValuePairField(tag = 10018) var zExeclD: String? = null
@field:KeyValuePairField(tag = -14) var syncNum: String? = null
@field:KeyValuePairField(tag = 1) var account: String? = null
@field:KeyValuePairField(tag = 375) var contraBroker: String? = null
@field:KeyValuePairField(tag = 456) var securitylDSource: String? = null
@field:KeyValuePairField(tag = 455) var securitylID: String? = null
@field:KeyValuePairField(tag = 10031) var legalEntity: String? = null
