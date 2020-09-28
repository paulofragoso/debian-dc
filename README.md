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
