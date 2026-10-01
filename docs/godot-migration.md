# Migração para Godot — Pokémon Eclipse

## Decisão de plataforma

Pokémon Eclipse deixa de ter o Game Boy Advance como plataforma-alvo principal e passa a ser planejado como um fangame 2D para PC desenvolvido em **Godot**.

A mudança é técnica, não criativa.

Continuam válidos os elementos já definidos para o projeto, incluindo:

- região de Solaria;
- Terrae como cidade inicial;
- Sun e Moon;
- Charlie e Lina;
- Professora Star;
- Equipe Void;
- história, personagens, ginásios e conceitos já documentados;
- identidade visual e direção artística planejadas.

O protótipo baseado em `pokeemerald-expansion` deve ser preservado como parte do histórico do projeto.

## Motivo da migração

A direção visual pretendida para Pokémon Eclipse passou a exigir uma liberdade maior do que a oferecida pela arquitetura gráfica do GBA.

A nova base deve permitir, quando útil ao projeto:

- sprites maiores;
- animações exclusivas;
- retratos e expressões em diálogos;
- interfaces próprias;
- iluminação;
- sombras;
- partículas;
- água e elementos ambientais animados;
- construções e cenários com identidade visual própria;
- maior liberdade de resolução, cor e composição.

A nova plataforma não deve transformar Eclipse em um RPG genérico. A intenção continua sendo preservar a estrutura e a sensação de uma aventura Pokémon, porém com apresentação autoral.

## Regra de desenvolvimento

Durante a primeira etapa da versão Godot, todo desenvolvimento deve responder à pergunta:

> Isto é necessário para algo que existe em Terrae?

Se a resposta for **não**, a implementação fica para uma etapa futura.

Sistemas reutilizáveis podem ser construídos desde que tenham uso real em Terrae.

Exemplos válidos:

- sistema de diálogo, porque os NPCs de Terrae precisam dele;
- sistema de retratos, porque Lina e Professora Star precisam dele;
- transição entre mapas, porque as casas de Terrae precisam dela.

Exemplos fora de escopo:

- batalha;
- captura;
- Pokédex completa;
- encontros selvagens;
- ginásios;
- evolução;
- rotas posteriores;
- Astrid;
- Praia Lactia.

## Princípio de implementação

O projeto será construído em pequenos blocos jogáveis.

Não será criado um grande motor Pokémon completo antes de existir o começo do jogo.

A primeira meta é produzir uma versão pequena, polida e funcional de Terrae que já represente a identidade de Pokémon Eclipse.
