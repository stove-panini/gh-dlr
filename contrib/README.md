This systemd service & timer will run gh-dlr on a weekly basis.

It's meant to be run as your own user! Please don't run this as root.

Setup
-----
Run the following:
```sh
mkdir -p ~/.config/systemd/user
cp gh-dlr.{service,timer} ~/.config/systemd/user
systemctl --user daemon-reload
systemctl --user enable --now gh-dlr.timer
```

Logs
----
The output can be reviewed by running `journalctl --user -u gh-dlr`
