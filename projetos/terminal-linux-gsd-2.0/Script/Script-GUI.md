# Script: Instalação da Interface Gráfica Leve (GUI-on-demand)

## Caminho: `scripts/02-gui.sh`

---

## 📃 Descrição
Este script instala uma interface gráfica leve e minimalista, composta por Xorg, Openbox, Xterm, Tint2 e PCManFM, totalmente acionada via `startx`. É ideal para um ambiente Linux terminal-first, com GUI apenas quando necessária.

---

## ⚙️ Componentes Instalados
```bash
apt install -y \
    xorg \
    xterm \
    openbox \
    tint2 \
    pcmanfm
```

Esses componentes permitem:
- `xterm`: terminal gráfico leve
- `openbox`: gerenciador de janelas
- `tint2`: barra de tarefas
- `pcmanfm`: gerenciador de arquivos

---

## ✍️ Configuração do `.xinitrc`
Arquivo criado para iniciar o ambiente com `startx`:
```bash
#!/bin/sh
xrdb -merge ~/.Xresources
pulseaudio --start
xterm &
tint2 &
pcmanfm &
exec openbox-session
```

Permissões ajustadas:
```bash
chmod +x /home/lucas/.xinitrc
chown lucas:lucas /home/lucas/.xinitrc
```

---

## 🌈 Tema Visual `.Xresources`
```text
xterm*faceName: Monospace
xterm*faceSize: 10
xterm*background: black
xterm*foreground: lime
xterm*cursorColor: white
xterm*scrollbar: false
xterm*loginShell: true
```
Arquivo salvo como `/home/lucas/.Xresources` e com permissão atribuída ao usuário.

---

## ▶️ Execução do Script
```bash
sudo ./02-gui.sh
```

Depois de executado:
```bash
startx
```

---

## ⚠️ Observações
- Requer servidor X ativo (não funciona via SSH sem tunelamento X)
- Os arquivos `.xinitrc` e `.Xresources` devem pertencer ao usuário final

---

## 🌟 Resultado Esperado
- Ambiente gráfico funcional e leve
- Interface minimalista com visual preto e verde (modo hacker)
- Controle total via terminal
