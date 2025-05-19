# 🧾️ Falha na Inicialização Gráfica via .xinitrc

## 🗒️ Contexto

* **Data:** 18–19 de maio de 2025
* **Ambiente:** VM VirtualBox
* **SO Base:** Ubuntu Server 24.04 LTS (sem GUI)
* **Objetivo:** Criar sistema com foco em terminal (TTY) e subir GUI leve sob demanda com `startx`

---

## 🌟 Descrição do Problema

Durante a tentativa de iniciar o ambiente gráfico com `openbox` e `xterm` via `startx`, o sistema:

* Iniciava o X, mas fechava imediatamente
* Apresentava erro:

```plaintext
xinit: connection to X server lost
```

---

## 🧪 Histórico de Tentativas e Testes

| Etapa | Ação                                                         | Resultado                                  |
| ----- | ------------------------------------------------------------ | ------------------------------------------ |
| 1️⃣   | Criado `.xinitrc` com `xterm &` e `exec openbox-session`     | ❌ X encerrava imediatamente                |
| 2️⃣   | Testado `.xinitrc` com `exec xterm` isolado                  | ✅ X iniciou corretamente com terminal      |
| 3️⃣   | Rodado `openbox-session` manualmente dentro do xterm         | ✅ Openbox funcionou normalmente            |
| 4️⃣   | Restaurado `.xinitrc` com `xterm &` + `exec openbox-session` | ⚠️ Erro: Only console users can run X      |
| 5️⃣   | Saído do X, rodado `startx` novamente no TTY                 | ✅ Ambiente funcional com `xterm` e Openbox |

---

## ❌ Causa Raiz Identificada

**Ausência da linha `#!/bin/sh` no início do arquivo `.xinitrc`**

Essa linha (shebang) define qual shell interpretará o script. Sem ela:

* O script pode ser mal interpretado
* Comandos como `exec`, `xterm`, `openbox-session` podem falhar
* O X inicia, mas fecha porque nenhum processo está mantendo ele ativo

---

## ✅ Solução Final Aplicada

Arquivo `.xinitrc` corrigido:

```bash
#!/bin/sh
xterm &
exec openbox-session
```

Comando para iniciar a GUI:

```bash
startx
```

---

## 🧠 Reflexão Pessoal (por `vboxuser`)

> “A primeira vez que eu fui configurar esse arquivo eu não sabia direito o que eu tava fazendo. Eu achei que essa linha do começo (`#!/bin/sh`) era só um comentário, e por isso não coloquei. Provavelmente todos os erros, travamentos e dores de cabeça vieram disso.
>
> Ontem de madrugada eu estava cansado e fiz a configuração sem atenção. Hoje, depois que resetamos o arquivo e você me passou aquele comando com `#!/bin/sh`, eu percebi o que tinha acontecido. Na hora que vi o xterm branco subir, eu entendi que o problema era meu desde o começo.
>
> O mais importante é que agora eu entendi o erro, e aprendi com ele. Isso não vai mais se repetir.”

---

## 🧩️ Conclusão

* 🧠 Problema simples, mas de alto impacto funcional
* ✅ Solução foi garantir a estrutura mínima válida do script
* 💡 Aprendizado profundo: detalhes em shell definem o comportamento do sistema

---

## 🛡️ Plano de Prevenção

* Sempre incluir `#!/bin/sh` em scripts de inicialização (`.xinitrc`, `.bash_profile`, etc.)
* Validar comandos críticos com `which`, `echo $?`
* Manter versões temporárias de arquivos com timestamp
* Evitar configurar o sistema em estado de cansaço 😅
