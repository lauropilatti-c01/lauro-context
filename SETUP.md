# SETUP.md — Como configurar tudo

## Estrutura de pastas no GitHub

```
github.com/lauropilatti-c01/
│
├── lauro-context/          ← NOVO REPO (compartilhado)
│   ├── USER.md             ← Quem você é, missões, princípios, regras
│   ├── MISSOES.md          ← Manifestos completos (estilo Jobs)
│   └── CONSELHO.md         ← Conselho de advisors + workflow
│
├── consulta-ai/            ← REPO EXISTENTE
│   ├── PROJECT.md          ← Contexto específico do projeto saúde
│   ├── src/
│   └── ...
│
└── nova-plataforma/        ← REPO EXISTENTE
    ├── PROJECT.md          ← Contexto específico do projeto e-learning
    ├── src/
    └── ...
```

## O que vai onde

| Arquivo | O que contém | Quem usa |
|---|---|---|
| `USER.md` | Perfil completo, missões (resumo), princípios, regras, tabela do conselho | Toda IA, todo projeto |
| `MISSOES.md` | Manifestos completos estilo Jobs, estratégia, moats, riscos, acquirers | Referência quando precisa relembrar a visão |
| `CONSELHO.md` | Perfis dos 7 advisors, filosofias, frameworks, workflow do Chairman | Quando precisa tomar decisão estratégica |
| `PROJECT.md` (em cada repo) | Stack técnica, estado atual, roadmap, decisões tomadas, TODO | IA trabalhando naquele projeto específico |

## Como configurar cada IA

### Claude (claude.ai)

1. Vá em **Settings > Profile**
2. Cole o conteúdo do arquivo `CLAUDE_PROFILE.md` (versão compacta, cabe no limite)
3. Pronto — toda conversa nova terá esse contexto

**Para projetos específicos:** Quando estiver trabalhando no ConsultaAI ou na plataforma, cole o PROJECT.md relevante no início da conversa ou use Projects do Claude.

### OpenClaw / ZiroBot

1. Crie o repo `lauro-context` no GitHub
2. Configure o `USER.md` como o arquivo que o bot lê no início de cada conversa
3. Para cada projeto, configure o `PROJECT.md` do repo correspondente

**No OpenClaw, a estrutura do bot deve ser:**
- `USER.md` do `lauro-context` → carregado sempre (contexto global)
- `PROJECT.md` do projeto ativo → carregado quando trabalhando naquele projeto
- `CONSELHO.md` → carregado sob demanda quando ativar o conselho

## Como usar no dia a dia

### Conversa geral / brainstorm
A IA já sabe quem você é pelo USER.md. Só conversa.

### Trabalhando num projeto específico
```
"Estou trabalhando no ConsultaAI. [sua pergunta]"
```
A IA puxa o contexto do PROJECT.md daquele repo.

### Decisão estratégica
```
"Chairman, preciso do conselho sobre: devo lançar B2C ou B2B primeiro?"
```
A IA ativa o workflow do CONSELHO.md.

### Perdeu o foco? Relembre a visão
```
"Me relembre a missão de saúde completa"
```
A IA puxa o MISSOES.md.

## Manutenção

- **USER.md** → Atualizar quando mudar algo fundamental sobre você ou as missões
- **MISSOES.md** → Raramente muda (é a visão de longo prazo)
- **CONSELHO.md** → Adicionar novos advisors conforme necessário
- **PROJECT.md** → Atualizar frequentemente conforme o projeto evolui
- **CLAUDE_PROFILE.md** → Atualizar quando USER.md mudar (é a versão compacta)
