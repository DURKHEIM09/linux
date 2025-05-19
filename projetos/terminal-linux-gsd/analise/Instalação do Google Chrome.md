# 🔄 Etapas Realizadas – Instalação do Google Chrome em Ambiente Linux Minimalista

## 1. Criação da Pasta e Acesso

```bash
mkdir -p ~/Downloads
cd ~/Downloads
```

## 2. Download do Pacote `.deb` do Google Chrome

```bash
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

### ⚠️ Problema:

Erro de DNS impediu o download.

### 🔧 Correção Aplicada:

Configuração ajustada no `systemd-resolved` para normalizar a resolução de nomes.

## 3. Instalação Manual do Pacote `.deb`

```bash
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

### ⚠️ Problema:

Apontou ausência das seguintes dependências:

* `fonts-liberation`
* `xdg-utils`

## 4. Correção de Dependências

```bash
sudo apt -f install -y
```

> Resolveu automaticamente os pacotes pendentes e finalizou a instalação.

## 5. Execução Correta no Ambiente Gráfico

Após iniciar o ambiente gráfico com:

```bash
startx
```

Executar o navegador:

```bash
google-chrome &
```

> 💡 Importante: esse comando só funciona **dentro do ambiente gráfico (xterm)**, pois o Chrome depende do servidor X.

---

## ✅ Resultado Final

| Item                        | Status          |
| --------------------------- | --------------- |
| Pacote `.deb` baixado       | ✅ Sim           |
| Chrome instalado via `dpkg` | ✅ Sucesso       |
| Dependências resolvidas     | ✅ Completas     |
| Chrome abriu no gráfico     | ✅ Funcionando   |
| Execução no terminal puro   | ❌ Não suportado |
