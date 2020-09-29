# Debian Instalação:

Instalacao em modo texto:

Passo 1: Liguagem: English - English

Passo 2: Continente ou Região: South America -> Brasil

Passo 3: Configurações de localização local: Uninted States - en_US.UTF-8

Passo 4: Mapa de teclado: American English

Passo 5: Configuracoes de rede e usuário

	Pode ser criado um usuário: Paulo Fragoso - paulo

Passo 6: Timezone: Pernambuco

Passo 7: Particionamento:

	Guided - use entire disk and set up LVM
	com 
	Separete /home, /var, and /tmp partitions

Obs.: Escreve o particionamento e o LVM (yes + yes)

Passo 8: Outro CD/DVD: no

Passo 9: Arquivos do Debian: Brazil

Obs.: Confirma o resto, não participar da pesquisa e salvar o grub no disco.

Passo 10: Instalação dos softwares:

	[ * ] SSH server
	[ * ] stantard system utilities

Obs.: Desmarcar outras opções. 

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
