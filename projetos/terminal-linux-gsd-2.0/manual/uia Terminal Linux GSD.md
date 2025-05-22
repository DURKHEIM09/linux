# 📚 Guia Terminal Linux GSD

Este repositório reúne comandos personalizados, atalhos e instruções otimizadas para operação de sistemas Linux CLI-first com GUI sob demanda. Ideal para ambientes como o **Projeto Terminal Linux GSD**, onde o terminal é a principal interface de controle.

---

## 🧠 Comandos Personalizados Disponíveis

Digite no terminal os seguintes aliases:

- `cc` → Comandos Comuns com explicações
- `tp` → Atalhos de Teclado do Terminal Puro (TTY, Bash)
- `tx` → Comandos do Terminal com Interface Gráfica (XTerm)
- `gsdmenu` → Exibe o menu interativo com as três opções acima

> ⚙️ Esses comandos são implementados como scripts `.sh` em `~/gsd-scripts/` e integrados ao `.bashrc`.

---

## 📘 Comandos Comuns no Terminal – Explicados

| Comando         | Descrição                                    |
|-----------------|----------------------------------------------|
| `cd [dir]`      | Navega até o diretório `[dir]`               |
| `ls -lah`       | Lista arquivos (detalhado, ocultos, humano)  |
| `cp src dst`    | Copia arquivo de `src` para `dst`            |
| `mv src dst`    | Move ou renomeia arquivo                     |
| `rm -i arquivo` | Remove com confirmação                       |
| `mkdir nome`    | Cria diretório                               |
| `nano arquivo`  | Edita o arquivo no editor nano               |
| `cat arquivo`   | Mostra conteúdo de arquivo                   |
| `less arquivo`  | Visualiza texto com rolagem                  |
| `ping site`     | Testa conexão com site                       |
| `ip a`          | Mostra IPs e interfaces de rede              |

---

## 📜 Atalhos do Terminal Puro (Bash)

| Atalho          | Função                                       |
|-----------------|----------------------------------------------|
| `Ctrl + A`      | Início da linha                              |
| `Ctrl + E`      | Fim da linha                                 |
| `Ctrl + U`      | Apaga do cursor até o início                 |
| `Ctrl + K`      | Apaga do cursor até o fim                    |
| `Ctrl + W`      | Apaga palavra anterior                       |
| `Ctrl + L`      | Limpa a tela (`clear`)                       |
| `Ctrl + C`      | Interrompe o processo                        |
| `Ctrl + D`      | Fecha a sessão (`exit`)                      |
| `Ctrl + Z`      | Suspende o processo (`bg`)                   |
| `!!`            | Repete último comando                        |

---

## 🖥️ Terminal com Interface Gráfica (XTerm, startx)

### 🧷 Atalhos de Colagem:
- `Shift + Insert` → Colar texto copiado do navegador
- `xclip -o -sel clipboard` → Colar via X11 clipboard no terminal

### 📦 Comandos úteis:
| Comando            | Descrição                        |
|--------------------|----------------------------------|
| `vlc &`            | Abre reprodutor de mídia         |
| `evince &`         | Abre visualizador de PDF         |
| `pcmanfm &`        | Abre gerenciador de arquivos     |
| `flameshot gui`    | Abre ferramenta de captura       |
| `google-chrome &`  | Inicia o navegador               |

---

## 🛠️ Instalação dos Scripts

Crie o diretório:
```bash
mkdir -p ~/gsd-scripts
