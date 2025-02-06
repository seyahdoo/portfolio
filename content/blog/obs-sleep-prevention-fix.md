+++
title = "OBS display sleep prevention fix"
date = "2024-07-31"
type = "post"
+++


OBS normally would't allow the display to turn off. 
If you have a replay system running in the background and have an oled monitor, thats a very bad combo.

Run this command to disable that behaviour.

```
powercfg -requestsoverride process obs64.exe display system awaymode
```


