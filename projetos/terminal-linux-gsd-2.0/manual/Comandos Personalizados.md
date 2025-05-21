# 📂 Guia de Comandos Personalizados – Projeto GSD 2.5

Este repositório contém scripts e atalhos personalizados criados no terminal Linux do Projeto GSD 2.5. Eles foram projetados para auxiliar no uso diário, consulta técnica rápida e padronização de boas práticas DevOps.

---

## 🧠 Comandos disponíveis

| Comando | Descrição                                                             |
|--------:|----------------------------------------------------------------------|
| `cc`    | Lista comandos comuns (`cd`, `ls`, `cp`, `mv`) com explicações claras |
| `tp`    | Mostra atalhos de teclado do terminal puro (Bash/TTY)                |
| `tx`    | Mostra comandos úteis do terminal gráfico (XTerm/startx)             |
| `helpme`| Exibe este menu com explicação de todos os comandos                  |

---

## 🛠️ Instalação Manual

1. Clonar o repositório:

   ```bash
   git clone https://github.com/seu-usuario/guias.git ~/guias
Tornar os scripts executáveis:

bash
Copiar
Editar
chmod +x ~/guias/*.sh
Adicionar os aliases no ~/.bashrc:

bash
Copiar
Editar
echo "alias cc='bash ~/guias/cc.sh'" >> ~/.bashrc
echo "alias tp='bash ~/guias/tp.sh'" >> ~/.bashrc
echo "alias tx='bash ~/guias/tx.sh'" >> ~/.bashrc
echo "alias helpme='bash ~/guias/help.sh'" >> ~/.bashrc
source ~/.bashrc
📎 Observações
Scripts escritos em Bash puro, sem dependências externas.

Compatíveis com ambientes minimalistas (Ubuntu Server 24.04).

Estrutura modular para fácil expansão (ex: man.sh, fzf.sh, etc.).

🧩 Próximos passos (ideias de evolução)
Criar função cc [comando] para explicar comandos individualmente

Integrar com fzf para navegação interativa

Gerar PDF com todos os comandos como manual técnico

yaml
Copiar
Editar

---

### ✅ Agora execute:

```bash
nano ~/guias/README.md
