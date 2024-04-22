# librewolf

```
// ==UserScript==
// @name        github
// @namespace   Violentmonkey Scripts
// @match       https://github.com/*
// @match       https://docs.github.com/en/*
// @grant       GM_addStyle
// @version     1.0
// @author      -
// @description 10/28/2022, 5:04:47 AM
// ==/UserScript==

if (location.href.indexOf('https://github.com') == 0) {
  GM_addStyle(`
    :root:root {
      --base-size-16: 8px;
      --base-size-32: 16px;
      --fontStack-monospace: monospace;
    }
    body .container-xl { max-width: none }
    body .react-repos-overview-margin { margin-right: 0 }
    div[data-selector="repos-split-pane-content"] { max-width: none }
    body .container-lg { max-width: none }
    body .comment-body { font-size: 1rem }
    nav[role="navigation"] ul { font-size: calc(1.1 * var(--body-font-size, 14px)) }
    body .AppHeader .AppHeader-globalBar .AppHeader-context .AppHeader-context-item { padding-block: 0 }
    body .react-directory-filename-column h3, body .react-directory-row { font-size: 1rem }
    nav[aria-label="File Tree Navigation"] ul li div.PRIVATE_TreeView-item-container { font-size: 1rem }
    body .react-code-text { font-size: 15px; line-height: 21px }
  `);
  setInterval(function() {
    document.querySelectorAll('div[data-selector="repos-split-pane-content"]').forEach(div => {
      const parent = div.parentElement;
      if (parent && parent.localName == 'div') parent.style.maxWidth = 'none';
    });
  }, 1904);
}

if (location.href.indexOf('https://docs.github.com/en') == 0) {
  GM_addStyle([
    'body h1 { background: linear-gradient(45deg, #f29913, #75dd13, #186fe0, #e018cf, #14e0c1);',
    '  background-clip: text; -webkit-text-fill-color: transparent; margin-top: 0 }'
  ].join('\n'));
}
```

-----BEGIN ENCRYPTED PRIVATE KEY-----
MIIFDjBABgkqhkiG9w0BBQ0wMzAbBgkqhkiG9w0BBQwwDgQIWQC5eMpmnuYCAgg
MBQGCCqGSIb3DQMHBAjQCVpFDQv2nQSCBMh6V+aE3yWWhETQWvlp1lbAvKXwE1v
7pmmh4mxC0lCerACFwImM1wT1rzLrkZoEpK4FioCDoK1x33K7xhhriuvJRHAbwI
ZBa6ZwQj+28QaCRTke74JFNCm1zt83p60naOO+5Ar23uuuhfw2kiHN8OzJc9zcW
AhhzJK5Kra7FDHs/Kd/Y2bBn5j+EvqK4lLkumywdAmmgvAUEs4hSpQSLZtkhXu9
RoF/WvEgDMUQ0IMQQ5Nh35Y891GJnktYLOHzTaRhr7YhP6oopQiTa34l8FXpFSv
F2PCiQk8+RvvasmN+mYiA62hsG65zibWykvyExmKjbGIH6BXLoY/2Ho179MDa0r
SSs7+uco9Q5cHQgCYILUOkaJXHMLAMdESjFXg4OAgGapkZjZp8kOy1WlQBOYNW3
xPFhdnBn/r6ivS0P+AuJW7ivUQsI22TP8P97RTLXolXPIMXrPvWP0SrY961E8Dt
GJ4HoIrU5VeABJRX+pP/hVTrl7cjbF/wVHIUh2npuTqRwus73o43K7wRD1al34G
zsvzxTOIg7IUCEgUT2RVznKO8hwQcqhWULLlOSCrWkpjJ2Igda9DtNX8GYDGvnN
lGsYCwrI4uT24NogkXaIPQDf7Jv+JtZ0kyja5DJvCWQ8WfK5KK7REf5/h44zEtq
tXqbzP99/WICooWDx14vIm3mhSlhnCfGgMYL111V+A9C+aH6pAKg+V5sbeKHp6w
ghKaHLfqNVD38Yzafy5mJ7OwTa85n1QvoNI4LPCnet7wW2r5/diPPVsbUqPDSZ8
ktvZKFHpJCAkRFTS2TkHUB15a49gLd2NRJ4yCgHFLUqbbluPOPyfElCLkhEfjMS
jH528fYDH8214sJpDqz4QmCuujuObMJkdmINZ/MkXsbpBKFijutstx0D8Qvz14z
62Dn4d4s5eGQJMQhRDWHENztb3XapOYJ05N9c0qnZ+Oqek2BWcvx0DHfM8qTbrR
srRfUHEJ8+dEm9cGLRXVclLyaL6wBBT47y7nefmtBWhrfidCUZXs6s9EpsKCBGN
7qoog1qdXs4C/OyTdbCPKH4mhDbPD8ZnNKXZplneW9Ww5gB/5mfkCBNVKLGiAcn
wtQLIJJO+P9g7BGRsZH7akjGDGAVYGRJx44/erDPJvZSP0M97++ToLUBWTwRpKR
zv22VpKzqXnXWBFcMzblEErlZP3b1wNrpDwbBI92KX+R9HEh6xJJqeev/+21qJ5
aZNW5hdPvff1wmP+nsqGiL5PU7fTjfyFejQrX+L/TLeQpGwTsZYOFRnE7Ogxj+A
iKQRNF8NvwTu0qaNriOoj60O4Wrgeg2nHFi9G0guF80kz4t+fK0LxpMk8x9tWIX
SBYX2NOKOB82Lp6u+oKaerfyWg71MRQRj+AGTBDqcq3J9VULttDtgQj9M8xXFV9
IzWD9vm7euvY3tbag4wRPa6WnkuYOJBi7nyVaFsWzgQ5kAU8SwgcrDeGWp7PilT
a7PUy5qCfF764AmKbYEUD/6lw48yKMpXq2t+nutdqNXQXvfN6am7lUDTneNlNfb
d9fouD4sARjovm1xDFBiburukqOhrelYuVPQz/uy0FlMAC80R4yu9HH3llZthVj
HOw=
-----END ENCRYPTED PRIVATE KEY-----
