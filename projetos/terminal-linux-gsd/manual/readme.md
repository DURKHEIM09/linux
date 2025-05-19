# 📘 Manual Técnico – Terminal Linux com Gráficos Sob Demanda (GSD)

Este manual técnico documenta **todo o processo de instalação, configuração e uso** do projeto *Terminal Linux com Gráficos Sob Demanda*. O foco aqui é entregar um guia objetivo, funcional e 100% replicável para quem deseja montar um sistema Linux terminal-first, com ambiente gráfico ativado sob demanda.

> ⚠️ **Nota do autor:** Este projeto ainda está em desenvolvimento. Provavelmente receberá alterações, ajustes e revisões à medida que avanço nos testes e validação da ideia. Não tenho certeza de como ele funcionará 100% na prática. Para acompanhar minhas opiniões pessoais e percepções sobre o projeto, consulte a pasta [`analise/`](../analise/).

---

## 🛠️ Requisitos

* Hypervisor: VirtualBox, QEMU ou VMware
* Imagem: Ubuntu Server 22.04 LTS (ou similar)
* Acesso à internet
* Conhecimento básico em terminal Linux

---

## 🔧 Etapas Técnicas

### 1. Instalação do Sistema Base

* Baixe a ISO do Ubuntu Server 22.04
* Crie uma VM com pelo menos:

  * 2 vCPU
  * 2–4 GB de RAM
  * 20 GB de disco
* Instale o sistema no modo server (sem interface gráfica)
* Configure o usuário, hostname e acesso sudo

### 2. Atualização do Sistema

```bash
sudo apt update && sudo apt upgrade -y
sudo reboot
```

### 3. Instalação de Ferramentas Essenciais (CLI)

```bash
sudo apt install tmux htop ncdu neovim curl wget git net-tools nmap unzip -y
```

### 4. Navegação Web via Terminal

```bash
sudo apt install lynx elinks w3m ddgr -y
```

* `lynx`, `elinks`, `w3m`: navegadores de texto
* `ddgr`: buscador usando DuckDuckGo (substituto ao googler)

### 5. Configuração de Rede (se necessário)

```bash
sudo apt install isc-dhcp-client -y
sudo dhclient enp0s3
ip a
curl ifconfig.me
```

### 6. Instalação do Ambiente Gráfico sob Demanda

```bash
sudo apt install xorg openbox xinit x11-utils -y
```

### 7. Configurar o startx com Openbox

Crie ou edite o arquivo `~/.xinitrc`:

```bash
echo 'exec openbox-session' > ~/.xinitrc
```

Para iniciar:

```bash
startx
```

Para sair:

```bash
logout
```

### 8. Instalar Navegador Gráfico (quando em GUI)

```bash
sudo apt install firefox -y
```

Após `startx`, execute:

```bash
firefox
```

### 9. Instalar Steam ou Albion Online (modo gráfico)

**Albion:**

* Faça o download do launcher oficial via navegador gráfico
* Extraia e execute via script

### 10. Scripts Auxiliares (sugestão)

Crie um diretório `scripts/` com:

* `start_graphics.sh`
* `launch_albion.sh`
* `update_system.sh`

Exemplo:

```bash
#!/bin/bash
startx
```

---

## 🧠 Dicas de Produtividade

* Use `tmux` para sessões persistentes
* Utilize `neovim` como editor padrão
* Navegue com `ranger` (se instalado)
* Monitore com `htop` e `ncdu`

---

## 🔐 Segurança (opcional)

* Configure `ufw`:

```bash
sudo apt install ufw -y
sudo ufw enable
sudo ufw allow ssh
```

---

## ✅ Finalização

Este manual cobre o fluxo base para transformar um Ubuntu Server em um sistema Linux terminal-first com recursos gráficos sob demanda. Para problemas específicos, consulte a pasta `problemas/`.

Documentação sempre em progresso — acompanhe as atualizações.
