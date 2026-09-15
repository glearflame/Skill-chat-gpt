# Elite Luau Architect

Skill para criar, refatorar e revisar sistemas Luau/Roblox avançados, com padrão de produção.

## O que ela cobre

- Tipagem estrita com `--!strict`
- Arquitetura modular, contratos tipados e APIs explícitas
- Autoridade do servidor e validação rigorosa de RemoteEvents
- Economia, inventário, combate, replicação e progressão
- DataStore, MemoryStore, session locking e concorrência entre servidores
- Gerenciamento de conexões, tarefas e ciclo de vida
- Performance, Parallel Luau e otimização baseada em profiling
- Revisões técnicas com problemas ordenados por severidade

## Instalação

1. Baixe ou clone este repositório.
2. No Codex/ChatGPT Work, abra **Plugins → Skills**.
3. Importe a pasta `elite-luau-architect`, que contém o arquivo `SKILL.md`.

## Como usar

Chame a skill no início do pedido:

```
Use $elite-luau-architect para criar um sistema de combate escalável com RemoteEvents seguros.
```

Também pode pedir diretamente, por exemplo:

```
Use $elite-luau-architect para revisar este módulo de DataStore.
```

## Estrutura

```
elite-luau-architect/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── assets/
    └── icon.svg
```

## Princípios

A skill prioriza:

1. Correção
2. Desempenho comprovado por medição
3. Arquitetura avançada, tipada, segura e sustentável para sistemas que evoluem por anos

Ela evita soluções superficiais, código de tutorial e abstrações frágeis. O cliente é tratado como entrada e camada visual; o servidor mantém todo estado autoritativo.

## UI Specialist integrado

A skill principal inclui o [módulo UI Specialist](elite-luau-architect/references/ui-specialist.md), aplicado a pedidos de interfaces Roblox.

- Visual vibrante e lúdico para jogos familiares.
- Arte gerada para ícones, retratos e fundos; estrutura e texto em Luau.
- UITheme tipado, componentes avançados e animações controladas.
- Estados idle, hover/focus, pressed, disabled e selected quando relevante.
- Contraste calculado, safe areas e layouts para celular e desktop.
- Descarte de conexões e tweens, com autoridade do servidor em compras.

Exemplo: `Use $elite-luau-architect para criar uma loja de pets com UI vibrante, ícones gerados e suporte a celular.`

O módulo faz parte da pasta da skill; mantenha também `references/ui-specialist.md` ao copiá-la.
