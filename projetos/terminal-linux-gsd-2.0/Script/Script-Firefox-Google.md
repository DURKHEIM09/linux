# Script: Instalação de Navegadores (Firefox e Google Chrome)

## Caminho: `scripts/04-navegadores.sh`

---

## 📃 Descrição
Este script instala o navegador Firefox via Snap, o Google Chrome via pacote `.deb` direto do site da Google, e adiciona aliases personalizados ao `.bashrc` do usuário `lucas` para facilitar a execução dos navegadores na interface gráfica.

---

## ⚙️ Comandos Executados
```bash
# Instala Firefox via Snap
snap install firefox

# Prepara diretório de downloads
mkdir -p /home/lucas/Downloads
cd /home/lucas/Downloads

# Baixa o Chrome diretamente do repositório oficial
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

# Instala o pacote e corrige dependências se necessário
dpkg -i google-chrome-stable_current_amd64.deb || apt -f install -y

# Adiciona aliases ao bashrc
cat << 'EOF' >> /home/lucas/.bashrc
alias google='google-chrome &'
alias firefox='firefox &'
EOF

# Corrige permissões do arquivo
chown lucas:lucas /home/lucas/.bashrc
```

---

## ▶️ Execução do Script
Execute como `root` ou via `sudo`:

```bash
sudo ./04-navegadores.sh
```

Ao final, é recomendado executar:
```bash
source ~/.bashrc
```
Para ativar os aliases sem reiniciar o terminal.

---

## ⚠️ Observações
- O Snap deve estar corretamente configurado.
- A instalação do Chrome exige conexão com a internet.
- Os aliases estão preparados para uso com `startx` e terminal X.

---

## 🌟 Resultado Esperado
- Firefox instalado via Snap
- Chrome instalado via `.deb`
- Aliases `google` e `firefox` funcionando no terminal gráfico
