# kvm-on-gentoo
kvm on gentoo.

reference:
* [https://wiki.gentoo.org/wiki/QEMU#Networking](https://wiki.gentoo.org/wiki/QEMU#Networking)
* [http://www.agix.com.au/install-kvm-qemu-gentoo/](http://www.agix.com.au/install-kvm-qemu-gentoo/)

## kernel config(4.2.3-aufs)

    Virtualzation
      Host kernel accelerator for virtio net(CONFIG_VHOST_NET)
      
    Device Drivers
      Network device support
        Network core driver support(CONFIG_NET_CORE)
        Universal TUN/TAP device driver support(CONFIG_TUN)
        
    Networking support
      Networking options
        <*> 802.1d Ethernet Bridging (CONFIG_BRIDGE)

## USE flag

    app-emulation/qemu qemu_softmmu_targets_arm qemu_user_targets_arm qemu_user_targets_x86_64 sdl sdl2 usb smartcard gtk2 gtk
    media-libs/mesa gles2

## install

    $ emerge -av net-misc/bridge-utils app-emulation/qemu

## bridge setting

* set null to original interface
* use original interface setting on new bridge
* reference: [https://wiki.gentoo.org/wiki/Network_bridge#OpenRC](https://wiki.gentoo.org/wiki/Network_bridge#OpenRC)

### example(static ip)

    config_eth0="null"
    bridge_br0="eth0"
    config_br0="192.168.1.2/24"
    brctl_br0="setfd 0 stp off"

### example(dhcp)
    
    config_eth0="null"
    config_br0="dhcp"
    brctl_br0="setfd 0 sethello 10 stp off"
    bridge_br0="eth0"

### init script

    $ ln -s /etc/init.d/net.lo /etc/init.d/net.br0 ; /etc/init.d/net.br0 start ; rc-update add net.br0 default
