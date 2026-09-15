# Elite Luau Architect

Skill para criar, refatorar e revisar sistemas Luau/Roblox com padrão de produção.

## O que ela cobre

- Tipagem estrita com `--!strict`
- Arquitetura modular e APIs explícitas
- Autoridade do servidor e validação de RemoteEvents
- Economia, inventário, combate e progressão
- DataStore, MemoryStore e concorrência entre servidores
- Gerenciamento de conexões e ciclo de vida
- Performance, Parallel Luau e otimização baseada em profiling
- Revisões técnicas com problemas ordenados por gravidade

## Instalação

1. Baixe ou clone este repositório.
2. No Codex/ChatGPT Work, abra **Plugins → Skills**.
3. Importe a pasta `elite-luau-architect`, que contém o arquivo `SKILL.md`.

## Como usar

Chame a skill no início do pedido:

```
Use $elite-luau-architect para criar um sistema de combate com RemoteEvents seguros.
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
2. Desempenho medido
3. Código simples, legível e sustentável

O cliente é tratado como entrada e camada visual; o servidor mantém o estado autoritativo.
