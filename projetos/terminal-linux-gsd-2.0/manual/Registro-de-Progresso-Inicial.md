# Registro de Progresso Inicial – Terminal Linux GSD 2.0

## 📅 Etapa Técnica Concluída (com o analista)

### 1. ⚙️ Instalação do Sistema
- Ubuntu Server 24.04 instalado via modo texto
- Disco SSD de 1TB formatado integralmente
- Particionamento via LVM:
  - `/` → 100 GB
  - `/boot` → 2 GB
  - `/boot/efi` → 1 GB
  - `/mnt/dados` → ~850 GB

### 2. 🔑 Conta de Usuário
- Username: `lucas`
- Senha definida
- Usuário com acesso via terminal (CLI puro)

### 3. 🚪 Acesso Remoto
- OpenSSH Server instalado
- SSH funcional com:
```bash
ssh lucas@<IP>
```

### 4. 🔄 Atualização Inicial
```bash
sudo apt update && sudo apt upgrade -y
```
- Nenhum pacote de driver adicional instalado
- Nenhuma GUI instalada ainda
- Sistema ainda cru e preparado para personalização

---

## ⏰ Próximos Passos (sob coordenação atual)

1. Instalar pacotes essenciais:
   - `curl`, `git`, `vim`, `htop`, `unzip`, etc

2. Instalar interface gráfica leve:
   - `xfce4` (ou manter `openbox`/`xterm` com `startx`)

3. Configurar som:
   - `pulseaudio`, `pavucontrol`

4. Verificar montagem de `/mnt/dados`
   - `lsblk`, `mount`, `fstab`

5. Otimizar produtividade:
   - Aliases personalizados
   - Scripts automatizados
   - Navegadores e apps (Firefox, Chrome)
   - Jogo Albion Online

---

## ✅ Observação
Este documento marca o fim da primeira etapa assistida e o início da execução sob gestão direta com suporte técnico. A partir daqui, cada etapa será registrada com scripts, instruções e justificativas técnicas.

Sistema pronto para configuração definitiva e ativação das camadas produtivas.
