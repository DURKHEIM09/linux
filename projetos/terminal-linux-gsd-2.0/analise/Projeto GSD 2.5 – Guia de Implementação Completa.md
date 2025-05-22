# Projeto GSD 2.5 – Guia de Implementação Completa

## 🌐 Visão Geral
Esta é a versão 2.5 do projeto **Terminal Linux GSD**, focada em aprimorar usabilidade, consistência visual e controle terminal para ambientes Linux otimizados.

O objetivo é manter uma arquitetura funcional, limpa, modular e tecnicamente realista para uso pessoal e profissional.

---

## 🚀 Funcionalidades Implementadas

### 1. Ajuste de Horário do Sistema
- **Timezone definido:** `America/Sao_Paulo`
- **Sincronização via NTP ativada**
- **Script:** `01-horario.sh`

```bash
sudo timedatectl set-timezone America/Sao_Paulo
sudo timedatectl set-ntp true
timedatectl
```

---

### 2. Reorganização dos Monitores
- **Script ARandR criado:** `telasdeus.sh`
- **Adicionado ao `.xinitrc`:**

```bash
sh ~/Lucas/ScreenLayout/telasdeus.sh &
```

---

### 3. Configuração da Barra de Tarefas
- **Gerenciador:** `lxpanel`
- **Plugins incluídos:** Relógio digital, controle de volume
- **Adicionado ao `.xinitrc`:**

```bash
lxpanel --profile LXDE &
volumeicon &
```

---

### 4. Comandos Personalizados
- **Script criado:** `comandos.sh`
- **Alias adicionado ao `.bashrc`:**

```bash
alias comandos='sh ~/comandos.sh'
```

---

### 5. Instalação de Utilitários Essenciais
- **Script:** `05-utils.sh`
- **Utilitários instalados:**
  - flameshot
  - htop
  - neofetch
  - ranger
  - xclip
  - gnome-disk-utility
  - vlc
  - evince

```bash
sudo apt install -y flameshot htop neofetch ranger xclip gnome-disk-utility vlc evince
```

---

### 6. Diagnóstico e Correção do Áudio HDMI (DisplayPort)
- **Placa de som:** NVIDIA TU106 (DisplayPort)
- **Verificação de drivers com:** `aplay -l`, `lsmod`, `pactl`
- **Redirecionamento manual via `pactl`**
- **Script de varredura criado:** `scan_hdmi_audio.sh`
  - Testa todas as saídas HDMI/DP ativas
  - Move o som automaticamente para a correta

---

## 🔹 Estrutura de Diretório Recomendada

```
Linux/
└── projetos/
    └── terminal-linux-gsd/
        └── 2.5/
            ├── .xinitrc
            ├── comandos.sh
            ├── 01-horario.sh
            ├── 05-utils.sh
            ├── telasdeus.sh
            ├── scan_hdmi_audio.sh
            ├── audio_hdmi_gsd25.md
            └── README.md
```

---

## 🌟 Status Atual do Projeto

- [x] Ambiente funcional com monitores ordenados
- [x] Barra de tarefas responsiva e integrada
- [x] Comandos personalizados prontos para uso
- [x] Sincronização de hora automática
- [x] Controle de som funcional via DisplayPort
- [x] Scripts documentados e modulares


---

🚀 Projeto GSD 2.5: Profissional, leve e sob controle.
