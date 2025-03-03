---
created: 20240529-1045
tags:
  - Resources/firefox
---
El archivo userChrome puede no existir, hay que crearlo de ser necesario
`~/.mozilla/firefox/<default-folder>/chrome/userChrome.css`

``` css
#TabsToolbar {
    visibility: collapse;
}

#navigator-toolbox:hover #TabsToolbar {
    visibility: visible;
}
```


[Firefox config](about:config) cambiar `toolkit.legacyUserProfileCustomizations.stylesheets` a true
