# Script: Instalação e Teste de Som com Suporte a Microfone

## Caminho: `scripts/03-som.sh`

---

## 📃 Descrição
Este script instala o sistema de som PulseAudio, seu painel de controle (`pavucontrol`) e utilitários ALSA. Também executa um teste de áudio e verifica se o microfone é detectado corretamente.

---

## ⚙️ Comandos Executados
```bash
# Instala os pacotes essenciais para som e microfone
apt install -y pulseaudio pavucontrol alsa-utils

# Teste de áudio
aplay /usr/share/sounds/alsa/Front_Center.wav

# Verificação dos dispositivos de captura (microfone)
arecord -l
```

---

## ▶️ Execução do Script
Execute como `root` ou via `sudo`:
```bash
sudo ./03-som.sh
```

---

## ⚠️ Observações
- PulseAudio deve ser iniciado com `pulseaudio --start` (opcional adicionar no `.xinitrc`)
- `pavucontrol` é uma interface gráfica que requer ambiente X ativo (via `startx`)
- O comando `arecord -l` é ótimo para validar se o microfone está sendo reconhecido

---

## 🌟 Resultado Esperado
- Som funcional (teste de áudio bem-sucedido)
- Dispositivo de entrada de áudio identificado
- Interface `pavucontrol` disponível para configuração fina
