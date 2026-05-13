ELKE - uma maravilha de ambiente criptografado usando FreeBSD

> encrypted & lovely kage environment

  * https://cpa.cryptorave.org/cryptorave-2026/talk/NGVZED
    - https://2026.cryptorave.org
    - http://femqcuwjelcd3lwdb2n47ylx6bsvbf3tqbb5sqrv7tbfvtetyyfsifqd.onion

* **Resumo**
Esse trabalho é focado na instalação de um ambiente FreeBSD em um servidor físico (ou virtual) em caráter de prova de conceito; a idéia principal é oferecer um sistema com criptografia de disco que possibilite desbloqueio remoto via SSH (combinado com Tor onion services, ou não). O disco pode oferecer partições ou datasets ZFS criptografados (onde instalamos o sistema operacional, e/ou armazenamos dados sensíveis).

* **Descrição**
As principais motivações para este trabalho e o compartilhamento dos detalhes de instalação do ambiente vem de duas apresentações feitas na EuroBSDCon (conferência européia sobre sistemas de linhagem BSD) -- com materiais, infelizmente, somente em língua inglesa:

* https://slideshare.net/slideshow/eurobsdcon-2021-autoinstalling-bsd-systems/250243872
  - https://youtube.com/watch?v=7F3UwfNB2JA
* https://slideshare.net/slideshow/eurobsdcon-2023-autoinstalling-bsd-systems-cases-using-pfsense-truenas-and-more/261357863
  - https://youtube.com/watch?v=ByvSwhCl8k8

Um ambiente similar, rodando em cima de sistemas com kernel Linux, é amplamente utilizado por empresas ou organizações que lidam com armazenamentos de dados sensiveis/sigilosos:

* https://duckduckgo.com/?q=dropbear+initramfs+luks

A ideia é, então, apresentar, em primeiríssima mão (e com um conteúdo em português brasileiro), um estado da arte mais avançado que os atualmente conhecidos utilizando FreeBSD.

Além de armazenamento dos dados sensiveis, casos de uso mais específicos podem envolver, mas não se limitar à: sistemas de análise forense de malwares, ou base para instalação de instâncias do securedrop (ou globaleak).

---

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
