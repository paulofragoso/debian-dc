# Debian Instalação:

Instalacao em modo texto:

Passo 1: Liguagem English

Passo 2: Região other -> South America -> Brasil

Passo 3: Localizaco en_i18n

Passo 3: Particionamento:

	Guided for entire disk with LVM

# Modificações após instalação

Nome das interfaces:

	sed -i'.orig' 's|^\(GRUB_CMDLINE_LINUX.*\)"|\1 net.ifnames=0 biosdevname=0"|' /etc/default/grub
	grub-mkconfig -o /boot/grub/grub.cfg

Um exemplo de configuração de rede:

	cat << __EOF__ > /etc/network/interfaces
	# This file describes the network interfaces available on your system
	# and how to activate them. For more information, see interfaces(5).
	
	source /etc/network/interfaces.d/*
	
	# The loopback network interface
	auto lo
	iface lo inet loopback
	
	# The primary network interface
	auto eth0
	iface eth0 inet static
        	address 192.168.0.2/24
        	gateway 192.168.0.1
        	dns-nameservers 192.168.0.1 192.168.1.1
        	dns-search example.com
	__EOF__
