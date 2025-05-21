# Script: Pós-Instalação Básica do Sistema (CLI Essentials)

## Caminho: `scripts/01-postinstall.sh`

---

## 📃 Descrição
Este script realiza a primeira etapa pós-instalação do sistema Terminal Linux GSD 2.0. Ele atualiza os pacotes do sistema e instala ferramentas básicas essenciais para produtividade no terminal. Também configura aliases personalizados no `.bashrc` do usuário `lucas`.

---

## ⚙️ Pacotes Instalados
```bash
apt install -y \
    curl \
    git \
    wget \
    vim \
    unzip \
    htop \
    net-tools \
    software-properties-common \
    bash-completion
```
Esses pacotes são considerados base para qualquer ambiente terminal de desenvolvimento ou administração Linux.

---

## 🗒️ Aliases Adicionados ao `.bashrc`
```bash
alias ll='ls -lah --color=auto'
alias update='sudo apt update && sudo apt upgrade -y'
alias cls='clear'
alias gs='git status'
```
Arquivo sobrescrito com `cat << EOF` e permissão atribuída ao usuário correto.

---

## ▶️ Execução do Script
Executar como root:
```bash
sudo ./01-postinstall.sh
```

---

## ⚠️ Observações
- O `.bashrc` é sobrescrito: se houver customizações anteriores, serão perdidas.
- Ideal executar esse script antes de configurar ambientes adicionais (como GUI ou som).

---

## 🌟 Resultado Esperado
- Sistema atualizado com utilitários básicos instalados
- Terminal com aliases personalizados ativos
- Base pronta para scripts subsequentes do projeto GSD
