ELKE - uma maravilha de ambiente criptografado usando FreeBSD

> encrypted & lovely kage environment

  * https://cpa.cryptorave.org/cryptorave-2026/talk/NGVZED
    - https://2026.cryptorave.org
    - http://femqcuwjelcd3lwdb2n47ylx6bsvbf3tqbb5sqrv7tbfvtetyyfsifqd.onion

# Motivação

  ### Setups Semelhantes
    * https://cyberciti.biz/security/how-to-unlock-luks-using-dropbear-ssh-keys-remotely-in-linux
    * https://dwarmstrong.org/remote-unlock-dropbear
    * https://swissmade.host/en/blog/unlocking-a-luks-fully-encrypted-drive-and-booting-into-the-os-via-dropbear-ssh

  ### EuroBSDCon
    * https://slideshare.net/slideshow/eurobsdcon-2021-autoinstalling-bsd-systems/250243872
    * https://slideshare.net/slideshow/eurobsdcon-2023-autoinstalling-bsd-systems-cases-using-pfsense-truenas-and-more/261357863

# Sistema Operacional da Base (FreeBSD)

  ### https://cgit.freebsd.org/src/tree/release
    * release.sh
    * ${TARGET}/make-memstick.sh
    * ${TARGET}/mkisoimages.sh

  ### https://cgit.freebsd.org/src/tree/usr.sbin
    * bsdconfig/
    * bsdinstall/

  ### https://download.freebsd.org/snapshots
    * amd64/amd64/16.0-CURRENT/
    * arm64/aarch64/16.0-CURRENT/
    * i386/i386/14.4-STABLE/
    * ISO-IMAGES/16.0/

# Ambiente Básico de Prova

  ### Hardware (Físico ou Virtualizado)
    * Arquitetura: aarch64 (arm64), i386, ou x86_64 (amd64)
    * CPU: 1
    * Interface de Rede: 1
    * RAM: 1GB
    * Disco: 8GB

  ### FreeBSD
    * UFS:/dev/ufs/base (kernel)
    * ZFS:elke/ROOT/main

# Virtualização para Prova de Conceito

  ### Hyper-V
    * https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v

  ### QEMU
    * https://qemu.org

  ### UTM
    * https://mac.getutm.app

  ### VirtualBox
    * https://virtualbox.org

  ### bhyve
    * https://bhyve.org

  ### kvm (virt-manager)
    * https://virt-manager.org

  ### vmm
    * https://openbsd.org/faq/faq16.html
