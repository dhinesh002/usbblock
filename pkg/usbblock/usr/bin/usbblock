#!/bin/bash

RULE_FILE="/etc/udev/rules.d/90-usb-block.rules"
RULE='SUBSYSTEM=="usb", ATTR{bInterfaceClass}=="08", ATTR{authorized}="0"'

case "$1" in
    enable)
        echo "$RULE" | sudo tee "$RULE_FILE" > /dev/null
        sudo udevadm control --reload-rules
        sudo udevadm trigger
        echo "USB storage blocking has been enabled."
        ;;

    disable)
        sudo truncate -s 0 "$RULE_FILE"
        sudo udevadm control --reload-rules
        sudo udevadm trigger
        echo "USB storage blocking has been disabled."
        ;;

    status)
        if grep -qF "$RULE" "$RULE_FILE"; then
            echo "USB blocking: ENABLED "
        else
            echo "USB blocking:: DISABLED"
        fi
        ;;

    *)
        echo "Usage: usbblock {enable|disable|status}"
        exit 1
        ;;
esac
