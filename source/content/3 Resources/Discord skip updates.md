When you open discord it first tries to update automatically. Buuuut, if you're in Arch like me the packages take maybe a day to be updated and meanwhile Discord says "download update manually" or some sh\*t.
Soooo, do this:

```.config/discord/settings.json
{
    "SKIP_HOST_UPDATE": true
}
```
