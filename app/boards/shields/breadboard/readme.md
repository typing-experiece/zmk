clean profile

sudo rm /Library/Preferences/com.apple.Bluetooth.plist
rm ~/Library/Preferences/ByHost/com.apple.Bluetooth.6BD9A879-1146-596E-874C-C7C4630F8DD1.plist


export SIDE=right;export DISK=disk2;
export SIDE=left;export DISK=disk3;

west build -p -d build/$SIDE  -b itsybitsy_nrf52840  -- -DSHIELD=breadboard_$SIDE &&  cp build/$SIDE/zephyr/zmk.uf2 $(mount -t msdos | grep $DISK | awk '{ print $3 }')

enable 
west build -t menuconfig