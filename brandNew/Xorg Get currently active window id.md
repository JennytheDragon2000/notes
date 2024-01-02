

```bash
focused_window_id=$(xdotool getwindowfocus)
window_pid=$(xdotool getwindowpid "$focused_window_id")

```