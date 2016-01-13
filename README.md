# kvm-on-gentoo
kvm on gentoo

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

## use flag

    app-emulation/qemu qemu_softmmu_targets_arm qemu_user_targets_arm qemu_user_targets_x86_64 sdl sdl2 usb smartcard gtk2 gtk
    media-libs/mesa gles2
