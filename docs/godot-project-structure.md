# Estrutura técnica inicial — Godot

## Objetivo

Definir apenas a estrutura necessária para iniciar a Etapa 1 — Terrae.

Esta arquitetura é deliberadamente pequena. Novas áreas e sistemas só devem ser adicionados quando Terrae exigir.

## Estrutura sugerida

```text
pokemon-eclipse/
├── assets/
│   ├── characters/
│   ├── environments/
│   │   └── terrae/
│   ├── portraits/
│   ├── ui/
│   ├── audio/
│   └── effects/
│
├── scenes/
│   ├── world/
│   │   └── terrae/
│   ├── characters/
│   ├── interiors/
│   └── ui/
│
├── scripts/
│   ├── world/
│   ├── characters/
│   ├── dialogue/
│   └── ui/
│
├── data/
│   └── terrae/
│
└── docs/
```

## Primeiro marco técnico

O primeiro marco não é batalha, Pokédex ou captura.

É:

> abrir o projeto Godot e executar uma cena de Terrae na qual um controlador de teste consiga caminhar pelo mapa e validar escala, câmera, profundidade e colisões.

## Ordem inicial

1. criar o projeto Godot;
2. definir resolução e escala visual;
3. criar a cena principal de Terrae;
4. criar as primeiras camadas do terreno;
5. criar câmera;
6. adicionar um controlador temporário de teste;
7. adicionar colisões;
8. construir o exterior até aprovação.

O controlador temporário não representa o Player final. Ele existe apenas para permitir testar o requisito 1 antes da etapa dedicada a Sun/Moon.

## Princípios técnicos

- usar recursos reutilizáveis quando houver ganho real;
- evitar abstrações sem uso imediato;
- separar arte, cenas, scripts e dados;
- manter Terrae isolada como primeiro vertical slice;
- preferir sistemas data-driven quando isso reduzir repetição;
- preservar liberdade visual como requisito do projeto;
- não reintroduzir artificialmente limitações do GBA.
