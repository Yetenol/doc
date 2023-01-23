---
dg-publish: true
storeId: XPFFTQ037JWMHS
wingetId: Microsoft.Edge
githubUser: 
githubRepo: 
githubBinary: 
website: 
priority: 1
---

# Add custom search engines

```
about:settings/searchEngines
```

- `Google` ← Search engine used in the address bar

| Search engine             | Keyword                 | URL with %s in place of query                                                                    |
| ------------------------- | ----------------------- | ------------------------------------------------------------------------------------------------ |
| DeepL                     | deepl.com               | `https://www.deepl.com/translator#../../%s`                                                      |
| Duden                     | duden.de                | `https://www.duden.de/suchen/dudenonline/%s`                                                     |
| JustWatch                 | justwatch.com           | `https://www.justwatch.com/de/Suche?q=%s`                                                        |
| Unicode Character Table   | unicode-table.com       | `https://unicode-table.com/en/search/?q=%s&p`                                                    |
| MOSES Modul Kurzübersicht | moseskonto.tu-berlin.de | `https://moseskonto.tu-berlin.de/moses/modultransfersystem/bolognamodule/ansehen.html?number=%s` |
| LaTeX Documentation       | texdoc.org              | `http://texdoc.org/serve/%s/0`                                                                   |
| LaTeX Documentation       | ctan.org                | `https://ctan.org/pkg/%s`                                                                        |

# Toggle experimental features

| Status   | Flag                                             | Description                       |
| -------- | ------------------------------------------------ | --------------------------------- |
| Disabled | `about:flags/#overscroll-history-navigation`     | Two-finger overscroll navigations |
| Disabled | `about:flags/#edge-show-feature-recommendations` | Recommends Bing as search engine  |

# Configure extensions

```dataview
TABLE WITHOUT ID
    "[" +
    choice(
        thumbnail,
        "<img src=\"" + thumbnail + "\" width=\"80\">",
        null
    ) + "](" +
    choice(
        modrinthId,
        "https://modrinth.com/mod/" + modrinthId,
        choice(
            curseForgeId,
            "https://www.curseforge.com/minecraft/mc-mods/" + curseForgeId,
            choice(
                edgeId,
                "https://microsoftedge.microsoft.com/addons/detail/" + edgeId,
                choice(
                    chromeId,
                    "https://chrome.google.com/webstore/detail/" + chromeId,
                    ""   
                )
            )
        )
    ) + ")"
    as "Website",
    file.link + " <br> " +
    choice(
        curseForgeId,
        "[![](https://img.shields.io/badge/CurseForge-install-blue)](" + 
        "https://www.curseforge.com/minecraft/mc-mods/" + curseForgeId + "/download?client=y" + ")",
        ""
    )
    as "Extension",
    Synopsis as "Synopsis"
FROM
    "apps" and [[]] and [[See extension]]
SORT
    choice(priority,priority,99)
FLATTEN
    "This is a Map of Extensions"
```



- Hide extensions from toolbar
    - Click on `Extensions button` in the toolbar
    - Disable `Show in toolbar` (eye icon) for all extensions

## Add keyboard shortcuts

```
about:extensions/shortcuts
```

- `Alt + Shift + D` ← Toggle current site _# Dark Reader_
- `Ctrl + Shift + 2` ← Choose another field in KeeWeb _# KeeWeb Connect_
- `Ctrl + Shift + 1` ← One-time codes _# KeeWeb Connect_
- `Ctrl + Shift + V` ← Submit the form automatically _# KeeWeb Connect_

# Modify settings manually

## Sync 

```
about:settings/profiles/sync
```

- Sign in to turn on sync
- [x] Favorites
- [x] Settings
- [ ] Basis info
- [ ] Passwords
- [ ] History
- [ ] Open tabs
- [x] Extensions
- [x] Collections
- [ ] Payments using Microsoft account

## Appearance

```
about:settings/appearance
```

- `System default` ← Overall apperance
- Scroll to `Customize toolbar`
- [x] Show tab actions menu
- [x] Hide title bar while in vertical tabs
- `Turn on` ← Show vertical tabs for all current browser windows
- `Only on new tabs` ← Show favorites bar
- Scroll to `Select which buttons to show on the toolbar:`
- [ ] Home button `[Alt+Home]`
- `Show automatically` ← Extensions button 
- [x] Favorites buttons `[Ctrl+Shift+O]`
- [ ] Collections button `[Ctrl+Shift+Y]`
- [ ] History button `[Ctrl+H]`
- [ ] Downloads button
- [ ] Web capture button `[Ctrl+Shift+S]`
- [ ] Share button
- [ ] Feedback button

## When Edge starts

```
about:settings/onStartup
```

- `Open the new tab page` ← When Edge starts

## Setup content handling


Block the following permission requests
```
about:settings/content/location
```
```
about:settings/content/notifications
```


---


Sources:

Related:

Tags:
[[../Install office apps]]