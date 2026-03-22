# Protocolo de Sincronização — Claude Code + OpenClaw

## Comandos Rápidos (cola no WhatsApp/Telegram)

### Ao INICIAR sessão num projeto

```
Antes de começar: faz git pull em lauro-context e no repo do projeto.
Lê USER.md do lauro-context e PROJECT.md do projeto. Me diz em 2 linhas
onde paramos da última vez.
```

### Ao FINALIZAR sessão (ou quando contexto tá chegando no limite)

```
Sessão acabando. Faz o handoff:
1. Atualiza HANDOFF.md (ou STATE.md) com o que foi feito e próximos passos
2. Commit com mensagem descritiva
3. Push pro GitHub
4. Me mostra um resumo de 5 linhas do que mudou
```

### Quando TROCAR de IA (Claude Code → OpenClaw ou vice-versa)

```
Vou trocar pro [Claude Code / OpenClaw]. Antes:
1. Commit + push de tudo que tá pendente
2. Atualiza HANDOFF.md com status atual
3. Me manda o resumo do que fez pra eu colar na outra sessão
```

### Quando SUSPEITAR que contexto tá desatualizado

```
Faz sync antes de continuar:
1. git pull em todos os repos
2. Relê USER.md + PROJECT.md do repo ativo
3. Me diz se mudou algo desde a última vez que leu
```

---

## Regra Automática (para as IAs)

### Claude Code — adicionar ao ~/CLAUDE.md (já feito)
- Antes de editar qualquer arquivo: verificar se há commits recentes no GitHub que não estão locais
- Ao detectar janela de contexto > 80%: iniciar handoff automaticamente
- Ao final de qualquer tarefa significativa: commit + push sem perguntar

### OpenClaw — adicionar ao AGENTS.md dele
- Antes de responder sobre decisão estratégica: sync GitHub + ler USER.md
- Ao detectar contexto > 80%: avisar "Contexto chegando no limite. Vou fazer handoff."
- Ao final de qualquer tarefa com código: commit + push

---

## O que cada arquivo faz

| Arquivo | Onde | Atualizar quando |
|---------|------|-----------------|
| `USER.md` | lauro-context | Mudar algo fundamental sobre missões/princípios (raro) |
| `MISSOES.md` | lauro-context | Quase nunca (é a visão de longo prazo) |
| `CONSELHO.md` | lauro-context | Adicionar/remover advisor (raro) |
| `PROJECT.md` | cada repo | Stack, estado, decisões técnicas mudam |
| `STATE.md` | consulta-ai | **TODO FINAL DE SESSÃO** |
| `HANDOFF.md` | nova-plataforma | **TODO FINAL DE SESSÃO** |

---

## Checklist Anti-Dessincronização

- [ ] Nunca trabalhar sem `git pull` primeiro
- [ ] Nunca terminar sessão sem `commit + push`
- [ ] Nunca tomar decisão estratégica sem ler USER.md
- [ ] Se outra IA trabalhou desde a última sessão → `git pull` obrigatório
- [ ] Se conflito entre memória e GitHub → GitHub vence
