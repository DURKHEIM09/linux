# 🧾️ Diário Técnico: Projeto Linux Terminal-First com GUI sob Demanda

## 🎯 Objetivo

Criar um sistema Linux com foco em terminal como ambiente principal, mas com capacidade gráfica sob demanda via `startx`, para rodar navegador e jogos como Albion Online, com mínima dependência de interface gráfica.

---

## 🛠️ Etapas Cronológicas Executadas

### 1. Instalação do Ambiente Base

| Ação                                        | Detalhes                                        |
| ------------------------------------------- | ----------------------------------------------- |
| 🔧 Instalou o Ubuntu Server 24.04 LTS na VM | Sem interface gráfica                           |
| 📀 Plataforma:                              | Oracle VirtualBox                               |
| 🧰 Configuração VM:                         | 2+ GB RAM, Placa de som ativada, Intel HD Audio |
| ✅ Primeira inicialização:                   | Login: `uboxuser`                               |

### 2. Preparação do Sistema

| Comando                                                 | Descrição                                    |
| ------------------------------------------------------- | -------------------------------------------- |
| `sudo apt update && sudo apt upgrade -y`                | Atualizou pacotes                            |
| `sudo apt install -y xorg openbox xterm firefox`        | Instalou servidor gráfico e ferramentas base |
| `sudo apt install -y alsa-utils pulseaudio pavucontrol` | Instalou subsistema de som                   |

### 3. Criação do Ambiente Gráfico Manual (startx + .xinitrc)

**Conteúdo final de `~/.xinitrc`:**

```bash
#!/bin/sh
pulseaudio --start
xterm &
exec /usr/bin/openbox-session
```

| Comando   | Descrição                          |
| --------- | ---------------------------------- |
| `startx`  | Inicia GUI sob demanda             |
| `xterm`   | Terminal gráfico leve              |
| `openbox` | Gerenciador de janelas minimalista |

### 4. Diagnóstico e Correção de Som

| Ação                                            | Resultado                                    |
| ----------------------------------------------- | -------------------------------------------- |
| `aplay /usr/share/sounds/alsa/Front_Center.wav` | ✅ Áudio ALSA funcional                       |
| `pulseaudio --start`                            | ✅ Daemon inicializado                        |
| `pavucontrol &`                                 | GUI para gerenciamento de áudio              |
| Firefox + YouTube                               | ✅ Som funcional após ajuste no `pavucontrol` |

### 5. Navegador Gráfico

| Ação                | Resultado                     |
| ------------------- | ----------------------------- |
| `firefox &`         | Abriu com GUI dentro do xterm |
| Suporte a vídeo/som | ✅ Validado com YouTube        |

### 6. Correção de Sessão e Janela Minimizada

| Problema                                    | Solução                           |
| ------------------------------------------- | --------------------------------- |
| Janela minimizada não retornava (sem barra) | `pkill -f firefox` + relançamento |
| Sugestão adicional                          | Instalar `tint2` (opcional)       |

---

## ✅ Estado Atual do Sistema

| Componente                 | Status                   |
| -------------------------- | ------------------------ |
| Terminal puro              | ✅ Padrão                 |
| GUI sob demanda (`startx`) | ✅ Funcional              |
| Mouse, janelas             | ✅ Operacionais           |
| Firefox                    | ✅ Rodando                |
| YouTube com som            | ✅ OK                     |
| PulseAudio                 | ✅ Ativo                  |
| Controle de áudio          | ✅ `pavucontrol` validado |

---

## 📦 Pronto para: Instalar e rodar Albion Online

O sistema está 100% funcional, leve, modular e pronto para rodar aplicações gráficas como jogos.

---

## 🧠 Extras Recomendados (opcional)

### 🔧 Adicionar `tint2` para barra de gerenciamento de janelas:

```bash
sudo apt install -y tint2
```

**Depois, adicione ao `.xinitrc`:**

```bash
tint2 &
```

### 📂 Criar snapshot da VM

Recomenda-se salvar o estado atual da VM para evitar retrabalho e preservar a configuração funcional.
