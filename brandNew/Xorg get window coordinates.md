---
tags:
  - flashcards
---

- Get Process Id
????
```bash
xprop
#click on the window
```
![[Pasted image 20240101174652.png]]
<!--SR:!2024-01-04,3,250-->

- Get Window Id given process id
????
```bash
xdotool search --pid $pid
```
![[Pasted image 20240101174900.png]]
<!--SR:!2024-01-03,1,210-->

- Get Window Coordinates
????
```bash
xwininfo -id $window_id
```
![[Pasted image 20240101175023.png]]
<!--SR:!2024-01-04,2,230-->