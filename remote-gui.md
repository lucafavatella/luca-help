macOS has native VNC client.
E.g. for server on localhost:5900 then `open vnc://localhost:5900`.

[`novnc`, browser based VNC client](https://kanaka.github.io/noVNC/noVNC/vnc.html).

Exposing Xvfb, X server for remote access, via VNC:
* https://en.wikipedia.org/wiki/Xvfb#Remote_control_over_SSH
* Example:
  ```
  apt-get update && apt-get install -y xvfb x11vnc
  Xvfb :1 -screen 0 2560x1600x24 -ac & x11vnc -forever -passwd p -rfbport 5900 -display :1 -noxrecord -noxfixes -noxdamage &
  ## Start a sample GUI app on display `:1`.
  apt-get update && apt-get install -y erlang-base
  epmd -debug &
  DISPLAY=:1 java -jar erlyberly-0.6.7-runnable.jar
  ```
* xvfb-run wrapper [example](https://github.com/SeleniumHQ/docker-selenium/blob/82632cb149d8312ae7250a807ead96c804f28453/NodeBase/entry_point.sh#L31)
* [Selenium in Docker container with VNC](https://github.com/RobCherry/docker-selenium)
* [Ubuntu in Docker accessible via VNC or web server `novnc`](https://github.com/fcwu/docker-ubuntu-vnc-desktop)
