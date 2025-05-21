# Manual Técnico – Terminal Linux GSD 2.0

## ✨ Visão Geral
Sistema Linux construído com foco em minimalismo, desempenho e controle absoluto via terminal (CLI-first), com interface gráfica ativável sob demanda (GUI-on-demand). Baseado em Ubuntu Server 24.04 LTS, instalado em bare metal, sem ambientes de desktop completos.

---

## 🧱 Base do Sistema
- **Distribuição:** Ubuntu Server 24.04 LTS (instalação limpa)
- **Modo de uso:** Terminal puro (TTY) com interface gráfica acionável via `startx`
- **Foco:** Produtividade e aprendizado com ambiente 100% controlado e configurado pelo usuário


## 🧩 Estrutura de Particionamento com LVM

| Ponto de Montagem | Tamanho     | Tipo   | Local                       |
|-------------------|-------------|--------|-----------------------------|
| `/`               | 100 GB      | ext4   | Volume Lógico LVM `root`   |
| `/boot`           | 2 GB        | ext4   | Partição dedicada           |
| `/boot/efi`       | 1 GB        | FAT32  | Partição ESP UEFI           |
| `/mnt/dados`      | ~850 GB     | ext4   | Volume Lógico LVM `data`   |


## 👤 Perfil de Usuário
- Nome: `lucas`
- Hostname: `gsd`
- Acesso `sudo` habilitado
- SSH ativado com OpenSSH (autenticação por senha inicialmente)


## 🔧 Pós-instalação: Pacotes Essenciais

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y \
    curl git wget vim unzip htop net-tools \
    software-properties-common bash-completion
```


## ⚙️ Aliases Pessoais (Adicionados ao `.bashrc`)
```bash
alias ll='ls -lah --color=auto'
alias update='sudo apt update && sudo apt upgrade -y'
alias cls='clear'
alias gs='git status'
alias google='google-chrome &'
alias firefox='firefox &'
```


## 🖥️ Interface Gráfica sob Demanda
Instalação leve baseada em Xorg, ativável com `startx`:

```bash
sudo apt install -y xorg openbox xterm tint2 pcmanfm
```

### `.xinitrc`
```bash
#!/bin/sh
xrdb -merge ~/.Xresources
pulseaudio --start
xterm &
tint2 &
pcmanfm &
exec openbox-session
```

### `.Xresources`
```text
xterm*faceName: Monospace
xterm*faceSize: 10
xterm*background: black
xterm*foreground: lime
xterm*cursorColor: white
xterm*scrollbar: false
xterm*loginShell: true
```


## 🔊 Som e Microfone
```bash
sudo apt install -y pulseaudio pavucontrol
pulseaudio --start
pavucontrol &
aplay /usr/share/sounds/alsa/Front_Center.wav
```


## 🌐 Navegadores
### Firefox (Snap)
```bash
sudo snap install firefox
```

### Google Chrome
```bash
cd ~/Downloads
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
sudo apt -f install -y
```


## 🗂️ Scripts Criados

- `01-postinstall.sh`: Instala pacotes essenciais e define aliases
- `02-gui.sh`: Instala e configura Xorg, Openbox, `~/.xinitrc` e `~/.Xresources`
- `03-som.sh`: Instala e testa PulseAudio + Pavucontrol
- `04-navegadores.sh`: Instala Firefox + Chrome com aliases


## ✅ Status Final
- Sistema leve, responsivo e funcional
- Toda interface gráfica opcional, ativada por comando
- Som e navegadores operacionais
- Totalmente utilizável por terminal e acessível via SSH


## 📌 Observação Final
Este manual documenta não apenas o sistema em si, mas também o aprendizado real por trás de cada escolha. O GSD 2.0 é uma jornada de liberdade digital e construção manual de um ambiente Linux pessoal, documentado como engenharia de verdade.
