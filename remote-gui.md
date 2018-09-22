macOS has native VNC client.
E.g. for server on localhost:5900 then `open vnc://localhost:5900`.

Exposing Xvfb, X server for remote access:
* https://en.wikipedia.org/wiki/Xvfb#Remote_control_over_SSH
*
  ```
  apt-get update && apt-get install -y xvfb x11vnc
  Xvfb :1 -screen 0 2560x1600x24 -ac & x11vnc -forever -passwd p -rfbport 5900 -display :1 -noxrecord -noxfixes -noxdamage &
  ## Start a sample GUI app on display `:1`.
  apt-get update && apt-get install -y erlang-base
  epmd -debug &
  DISPLAY=:1 java -jar erlyberly-0.6.7-runnable.jar
  ```
  