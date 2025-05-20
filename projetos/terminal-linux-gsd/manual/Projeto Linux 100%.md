# 📋 Documentação Oficial — Projeto Linux Terminal-First com GUI On-Demand + Suporte a Jogos

## 🗕️ Data de Finalização do Projeto

**19/05/2025**

---

## 💻 Visão Geral do Sistema

| Item                | Resultado                                 |
| ------------------- | ----------------------------------------- |
| Sistema Base        | Ubuntu Server 24.04 LTS                   |
| Interface principal | Terminal puro (TTY)                       |
| GUI sob demanda     | `startx` + `xterm` + `openbox`            |
| Navegadores         | ✅ Firefox (Snap) + Google Chrome (.deb)   |
| Som funcional       | ✅ PulseAudio + pavucontrol                |
| Jogos suportados    | ✅ Albion Online                           |
| Estilo visual       | Terminal com fundo preto e letras verdes  |
| Virtualização       | ✅ Oracle VirtualBox com rede bridge e som |

---

## 🛠️ Etapas do Projeto

### Fase 1 — Instalação da VM

* Oracle VirtualBox no Windows
* ISO Ubuntu Server 24.04 LTS
* Configuração: 2 GB RAM, 2 CPUs, 25 GB HD, rede em Bridge
* Sem interface gráfica, usuário: `vboxuser`

---

### Fase 2 — Configuração Pós-Instalação

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y xorg openbox xterm firefox pulseaudio pavucontrol unzip wget curl fonts-liberation
```

---

### Fase 3 — Inicialização Gráfica Sob Demanda (.xinitrc)

```bash
#!/bin/sh
xrdb -merge ~/.Xresources
pulseaudio --start
xterm &
tint2 &
exec /usr/bin/openbox-session
```

---

### Fase 4 — Estilo Visual do Terminal (.Xresources)

```bash
xterm*faceName: Monospace
xterm*faceSize: 10
xterm*background: black
xterm*foreground: lime
xterm*cursorColor: white
xterm*scrollbar: false
xterm*loginShell: true
```

---

### Fase 5 — Navegadores

**Firefox**

```bash
sudo snap install firefox
```

**Google Chrome**

```bash
cd ~/Downloads
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
sudo apt -f install -y
```

**Alias**

```bash
echo "alias google='google-chrome &'" >> ~/.bashrc
source ~/.bashrc
```

---

### Fase 6 — Áudio e Som

```bash
pulseaudio --start
pavucontrol &
aplay /usr/share/sounds/alsa/Front_Center.wav
```

---

### Fase 7 — Instalação do Albion Online

```bash
cd ~/Downloads
chmod +x albion-online-setup
./albion-online-setup
```

**Diretório de instalação sugerido:**
`~/albiononline`

**Execução do jogo:**

```bash
~/albiononline/Albion-Online &
```

**Script opcional:**

```bash
nano ~/start-albion.sh
```

```bash
#!/bin/bash
cd ~/albiononline
./Albion-Online
```

```bash
chmod +x ~/start-albion.sh
```

---

## 📂 Organização de Arquivos

| Diretório/Arquivo   | Descrição                     |
| ------------------- | ----------------------------- |
| `~/Downloads`       | Pacotes .deb, setup do Albion |
| `~/albiononline`    | Instalação do jogo            |
| `~/.xinitrc`        | Inicialização gráfica         |
| `~/.Xresources`     | Aparência do terminal gráfico |
| `~/start-albion.sh` | Script de execução do jogo    |

---

## ✅ Extras Recomendados

```bash
sudo apt install -y tint2 pcmanfm
```

**Adicione ao `.xinitrc`:**

```bash
tint2 &
pcmanfm &
```

---

## 📊 Conclusão Final

Sistema leve, funcional e terminal-first com GUI on-demand. Suporta:

* Navegador moderno
* Som e vídeo
* Jogos Linux nativos
* Personalização de aparência
* Controle completo via terminal
