# BinaryTest

This little sample shows how to copy your binaries to some location and set 'executable' attributes on them.

This can be used on a non-rooted phone, e.g. https://android.stackexchange.com/questions/53389/can-i-update-the-adb-shells-environment-variables

===

To update the PATH variable inside a running adb shell you can use the expect command. This works on a non-rooted phone where you can't edit system files as suggested in the other answers.

Put the following script somewhere on the path of your development machine, for example in ~/bin/adb-shell-busybox:

#!/usr/bin/expect --
spawn adb shell
expect "$" {
    sleep 0.1
    send "export PATH=/data/data/burrows.apps.busybox/app_busybox/:\$PATH\n"
}
interact
You can also inject any other setup commands that you might need.
