ELKE - uma maravilha de ambiente criptografado usando FreeBSD

> Encrypted & Lovely Kage Environment

  * https://cpa.cryptorave.org/cryptorave-2026/talk/NGVZED
    - https://2026.cryptorave.org
    - http://femqcuwjelcd3lwdb2n47ylx6bsvbf3tqbb5sqrv7tbfvtetyyfsifqd.onion

<div align="center">
    <img src="ELKE.png" alt="Elke Maravilha">
    <br>https://duckduckgo.com/?q=elke+maravilha
</div>

# Resumo

Esse trabalho é focado na instalação de um ambiente FreeBSD em um servidor físico (ou virtual) em caráter de prova de conceito; a idéia principal é oferecer um sistema com criptografia de disco que possibilite desbloqueio remoto via SSH (combinado com Tor onion services, ou não). O disco pode oferecer partições ou datasets ZFS criptografados (onde instalamos o sistema operacional, e/ou armazenamos dados sensíveis).

# Descrição

As principais motivações para este trabalho e o compartilhamento dos detalhes de instalação do ambiente vem de duas apresentações feitas na EuroBSDCon (conferência européia sobre sistemas de linhagem BSD) com materiais, infelizmente, somente em língua inglesa:

* https://slideshare.net/slideshow/eurobsdcon-2021-autoinstalling-bsd-systems/250243872
  - https://youtube.com/watch?v=7F3UwfNB2JA
* https://slideshare.net/slideshow/eurobsdcon-2023-autoinstalling-bsd-systems-cases-using-pfsense-truenas-and-more/261357863
  - https://youtube.com/watch?v=ByvSwhCl8k8

Um ambiente similar, rodando em cima de sistemas com kernel Linux, é amplamente utilizado por empresas ou organizações que lidam com armazenamentos de dados sensiveis/sigilosos:

* https://duckduckgo.com/?q=dropbear+initramfs+luks

A ideia é, então, apresentar, em primeiríssima mão (e com um conteúdo em português brasileiro), um estado da arte mais avançado que os atualmente conhecidos utilizando FreeBSD. Toda a prova de conceito é feita usando snapshots das versões mais recentes; nenhuma release estável específica.

Além de armazenamento dos dados sensiveis, casos de uso mais específicos podem envolver, mas não se limitar à: sistemas de análise forense de malwares, ou base para instalação de instâncias do securedrop (ou globaleak).

Caso busque projetos similares que já entregem algum tipo de código pronto (funcional, ou não) para ser usado na instalação de um ambiente similarmente proposto, comece por aqui:

  * https://github.com/clinta/geliUnlocker
  * https://github.com/emtiu/freebsd-outerbase
  * https://github.com/oxfox22/freebsd-remote-crypto-single-drive
  * https://github.com/Sec42/freebsd-remote-crypto

# Aviso/Nota

Percebam pequenas discrepâncias em segmentos pontuais nas capturas de telas e sintaxe de alguns comandos exibidos nas telas; sim, elas existem e muito provavelmente permanecerão aí. Fica, no entando, o encorajamento para pesquisa e leitura mais aprofundada de como a implementação plena deve ser desenvolvida no lado de quem está interessado no setup.

Além disso, sim, ficaram "faltando" menções sobre alguns pontos mais detalhados "aqui e ali" como alguns contatos já questionaram - apenas um, na minha opinião, merece um destaque em especial:

  * https://bsdday.com.br (evento focado em BSD que ocorre frequentemente em seropécida no rio de janeiro).

Os demais: um abraço, um beijo e um queijo ;)

---

# Sistema Operacional (FreeBSD)

Código fonte do instalador:

### https://cgit.freebsd.org/src/tree/release
  * release.sh
  * ${TARGET}/make-memstick.sh
  * ${TARGET}/mkisoimages.sh

### https://cgit.freebsd.org/src/tree/usr.sbin
  * bsdconfig/
  * bsdinstall/

Versões, arquiteturas e suas respectivas imagens ou artefatos de instalação:

### https://download.freebsd.org/snapshots
  * amd64/amd64/16.0-CURRENT/
  * arm64/aarch64/16.0-CURRENT/
  * i386/i386/14.4-STABLE/
  * ISO-IMAGES/16.0/

# Ambiente Básico de Prova

### Hardware (Físico ou Virtualizado)

> Considere que seja possível boot da imagem de instalação do FreeBSD usando uma ISO ou um pendrive USB.

  * Arquitetura: aarch64 (arm64), i386, ou x86_64 (amd64)
  * CPU: 1
  * Interface de Rede: 1 (com ou sem acesso a Internet)
  * RAM: 1GB
  * Disco: 8GB

### FreeBSD
  * FAT:/dev/gpt/uefi (bootloader)
    - loader.efi
  * UFS:/dev/gpt/base (kernel & set-minimal)
    - base.img.uzip
  * ZFS:/dev/gpt/elke (pkg & set-base), geli
    - elke/ROOT/main, encryption=on

# Virtualização/Hipervisores

> Nenhuma recomendação específica aqui; use o que você se sentir mais confortável. A idéia é montar uma prova de conceito, e nada muito sofisticado.

### bhyve
  * https://bhyve.org

### kvm (virt-manager)
  * https://virt-manager.org

### vmm
  * https://openbsd.org/faq/faq16.html

### QEMU
  * https://qemu.org

### Hyper-V
  * https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v

### UTM
  * https://mac.getutm.app

### VirtualBox
  * https://virtualbox.org
