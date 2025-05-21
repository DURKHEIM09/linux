# Projeto Terminal Linux GSD 2.0 – Manual Técnico Consolidado

## ✨ Visão Geral

Este projeto tem como objetivo criar um sistema operacional Linux **minimalista, funcional e sob total controle do usuário**, priorizando o uso via **terminal (CLI-first)** com ativação pontual de uma interface gráfica leve (**GUI-on-demand**). Ele representa uma transição deliberada de um ambiente dependente de interfaces gráficas (como Windows ou distros GNOME-heavy) para uma arquitetura centrada em eficiência, aprendizado e domínio técnico.

---

## 👨‍💻 Perfil do Projeto

- **Distribuição Base:** Ubuntu Server 24.04 LTS (instalação limpa e bare metal)
- **Interface principal:** Terminal puro (TTY + Bash)
- **Interface gráfica:** `startx` com ambiente leve composto por:
  - `xterm`: terminal gráfico
  - `openbox`: gerenciador de janelas
  - `tint2`: barra de tarefas
  - `pcmanfm`: gerenciador de arquivos
- **Acesso remoto:** OpenSSH (SSH com autenticação por senha inicialmente)
- **Público-alvo:** usuário em aprendizado técnico que busca documentar cada etapa
- **Foco:** produtividade via terminal, personalização consciente, documentação como prática de engenharia

---

## 🧱 Estrutura de Disco (LVM)

Instalação no SSD de 1TB com layout customizado via LVM para garantir flexibilidade e separação lógica:

| Ponto de Montagem | Tamanho | Tipo de Volume          |
|-------------------|---------|--------------------------|
| `/`               | 100 GB  | Volume lógico LVM (`root`) |
| `/boot`           | 2 GB    | Partição ext4 dedicada    |
| `/boot/efi`       | 1 GB    | Partição FAT32 (ESP UEFI) |
| `/mnt/dados`      | ~850 GB | Volume lógico LVM (`data`) |

---

## 👤 Configuração de Usuário

- Usuário: `lucas`
- Senha definida manualmente
- Permissão `sudo` configurada
- SSH habilitado para acesso remoto: `ssh lucas@<IP>`

---

## 🔧 Pós-Instalação

### Atualização inicial
```bash
sudo apt update && sudo apt upgrade -y
```

### Scripts personalizados criados

| Script                | Descrição |
|----------------------|-----------|
| `01-postinstall.sh`  | Instala pacotes essenciais (`curl`, `git`, `vim`, `htop`, etc.) e define aliases no `.bashrc` |
| `02-gui.sh`          | Instala ambiente gráfico (`xorg`, `openbox`, `xterm`, `tint2`, `pcmanfm`) e configura `~/.xinitrc` e `~/.Xresources` |
| `03-som.sh`          | Instala `pulseaudio`, `pavucontrol`, `alsa-utils`, e executa testes de áudio e microfone |
| `04-navegadores.sh`  | Instala Firefox (Snap) e Google Chrome (.deb), configurando aliases para execução via terminal gráfico |

---

## 🖥️ Interface Gráfica sob Demanda

Acionada com `startx`, a GUI utiliza:

- `xterm`: terminal gráfico padrão
- `openbox`: gerenciamento de janelas leve
- `tint2`: barra de tarefas básica
- `pcmanfm`: gerenciamento de arquivos visual

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

---

## 🔊 Áudio e Microfone

Instalado com:
```bash
apt install -y pulseaudio pavucontrol alsa-utils
```

Testes executados:
- Reproduzir áudio: `aplay /usr/share/sounds/alsa/Front_Center.wav`
- Verificar microfones disponíveis: `arecord -l`
- Interface de controle de som: `pavucontrol`

---

## 🌐 Navegadores

- **Firefox:** instalado via Snap
- **Google Chrome:** baixado manualmente e instalado via `.deb`
- Aliases configurados:
```bash
alias google='google-chrome &'
alias firefox='firefox &'
```

---

## ⚙️ Aliases Pessoais no `.bashrc`
```bash
alias ll='ls -lah --color=auto'
alias update='sudo apt update && sudo apt upgrade -y'
alias cls='clear'
alias gs='git status'
```

---

## ✅ Resultados Finais

- Sistema leve, responsivo e sob total controle do terminal
- Interface gráfica opcional e funcional
- Som, microfone e navegadores configurados
- Todos os scripts organizados, documentados e versionados

---

## 🚀 Status Atual

**Sistema 100% operacional.** Base estabelecida com terminal + GUI leve, pronta para expansões futuras.

### 🔜 Próximos objetivos:
- Adicionar apps gráficos pontuais (PDF, imagem, vídeo)
- Automatizar ações via shell (scripts de produtividade)
- Testar instalação de jogos Linux (Albion Online)
- Refinar segurança (chaves SSH, hardening)

---

## 🌐 Consideração Final

Este projeto não é um showcase de senioridade. É um documento vivo de aprendizado real, feito com intenção técnica e personalidade. Cada etapa foi pensada, executada, testada e documentada como parte de uma jornada para dominar o Linux como ambiente de trabalho e expressão digital.
