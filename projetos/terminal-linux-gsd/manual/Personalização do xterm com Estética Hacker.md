# 🧾️ Relatório Técnico: Personalização do xterm com Estética Hacker

## 🎯 Objetivo

Aplicar tema clássico: fundo preto + texto verde, para melhorar legibilidade e imersão no terminal gráfico `xterm`.

---

## 🔧 Etapas Técnicas Executadas

### 1. Criação do Arquivo de Configuração do Xterm

**Arquivo:** `~/.Xresources`

```bash
nano ~/.Xresources
```

**Conteúdo aplicado:**

```bash
! Aparência do xterm - Estilo Hacker
XTerm*faceName: Monospace
XTerm*faceSize: 10
XTerm*background: black
XTerm*foreground: lime
XTerm*cursorColor: white
XTerm*scrollBar: false
XTerm*loginShell: true
```

> ✅ Correção aplicada: erro de digitação `faceSiza` foi corrigido para `faceSize`

### 2. Aplicação Manual da Configuração

```bash
xrdb -merge ~/.Xresources
```

> ⚠️ Este comando **só pode ser executado após iniciar o ambiente gráfico (`startx`)**, pois depende da variável `DISPLAY` estar definida.

### 3. Integração Automática via `.xinitrc`

**Arquivo:** `~/.xinitrc`

**Versão final usada:**

```bash
#!/bin/sh

pulseaudio --start
xrdb -merge ~/.Xresources
xterm &
exec /usr/bin/openbox-session
```

> 💡 Isso garante que o `xterm` será iniciado **já com o tema customizado** carregado, toda vez que você rodar `startx`.

---

## ✅ Resultado Final

| Elemento  | Valor          |
| --------- | -------------- |
| Fundo     | Preto          |
| Texto     | Verde (lime)   |
| Fonte     | Monospace 10pt |
| Cursor    | Branco         |
| Scrollbar | Oculto         |

---

## 🧠 Considerações Técnicas

* `xrdb` aplica configurações X11 em tempo real
* `xterm` lê da base `Xresources` ao iniciar
* O `.xinitrc` é a ponte entre o ambiente gráfico e o comportamento inicial do usuário
