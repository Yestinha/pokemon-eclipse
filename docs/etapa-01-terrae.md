# ETAPA 1 — Terrae

## Objetivo

A primeira etapa da versão Godot de Pokémon Eclipse é construir **o começo do jogo em Terrae**.

Nenhuma implementação fora deste escopo deve bloquear ou desviar o desenvolvimento.

A etapa só será considerada concluída quando todos os requisitos abaixo estiverem integrados e funcionando como uma única experiência jogável.

---

## 1. Mapa de Terrae funcional

### Requisitos mínimos

- [ ] terreno completo;
- [ ] caminhos e circulação definidos;
- [ ] limites do mapa;
- [ ] casas e construções externas;
- [ ] laboratório da Professora Star;
- [ ] praça e elementos centrais planejados;
- [ ] entrada/saída da cidade;
- [ ] colisões;
- [ ] portas e pontos de entrada;
- [ ] composição visual final do exterior;
- [ ] identidade visual própria para as construções.

### Incrementos permitidos nesta etapa

Podem ser implementados desde que sejam usados em Terrae e contribuam diretamente para o acabamento do mapa:

- sombras;
- água animada;
- elementos ambientais com pequenas animações;
- partículas discretas;
- iluminação;
- objetos com profundidade visual;
- movimentações ambientais simples.

Esses efeitos não devem bloquear a conclusão do mapa base.

### Critério de conclusão

Deve ser possível abrir Terrae, caminhar por todo o espaço permitido e validar visualmente terreno, construções, limites e colisões.

---

## 2. Interiores e NPCs

### Interiores

- [ ] criar todos os interiores acessíveis de Terrae;
- [ ] implementar entrada e saída;
- [ ] colisões internas;
- [ ] decoração coerente com cada morador ou função;
- [ ] posicionamento dos NPCs internos.

### NPCs comuns

Cada NPC de Terrae deve possuir:

- [ ] aparência definida;
- [ ] sprite;
- [ ] posição;
- [ ] direção;
- [ ] movimentação, quando aplicável;
- [ ] colisão;
- [ ] interação;
- [ ] diálogo;
- [ ] contexto coerente com Terrae.

NPCs comuns não devem existir apenas como decoração sem identidade.

### NPCs especiais — Lina e Professora Star

Lina e Professora Star são personagens especiais da história e exigem um nível adicional de apresentação.

Cada uma deve possuir:

- [ ] sprite overworld próprio e final;
- [ ] animações próprias;
- [ ] nome na caixa de diálogo;
- [ ] caixa de diálogo personalizada;
- [ ] retrato;
- [ ] suporte a expressões;
- [ ] troca de expressão durante falas;
- [ ] diálogos implementados;
- [ ] eventos necessários ao começo em Terrae.

---

## 3. Player

Sun/Moon deve estar funcional como personagem jogável.

### Requisitos

- [ ] sprite correto;
- [ ] idle;
- [ ] movimento para baixo;
- [ ] movimento para cima;
- [ ] movimento para esquerda;
- [ ] movimento para direita;
- [ ] colisão;
- [ ] interação com objetos e NPCs;
- [ ] entrada em portas;
- [ ] transição entre exterior e interior;
- [ ] câmera funcional.

Sistemas como corrida só entram nesta etapa caso sejam realmente necessários ao fluxo de Terrae.

---

## 4. Menus

O objetivo desta etapa é implementar a estrutura visual e a navegação dos menus.

### Requisitos

- [ ] abrir o menu;
- [ ] navegar entre abas;
- [ ] abrir uma aba;
- [ ] retornar;
- [ ] fechar o menu;
- [ ] voltar corretamente ao jogo;
- [ ] identidade visual própria do Pokémon Eclipse.

As abas podem existir sem conteúdo definitivo.

Exemplos:

- Pokémon;
- Mochila;
- Trainer;
- Mapa;
- Configurações;
- Salvar.

A estrutura exata poderá ser refinada durante a implementação.

---

## 5. Abertura do jogo

### Requisitos

- [ ] inicialização do jogo;
- [ ] logo Pokémon Eclipse;
- [ ] imagem/tela de abertura;
- [ ] comando de início;
- [ ] transição para o começo jogável;
- [ ] entrada em Terrae.

Animações e efeitos adicionais podem ser adicionados depois que a estrutura básica estiver funcionando.

---

# Critério final — ETAPA 1 CONCLUÍDA

A etapa é considerada concluída quando uma build executável permite:

1. abrir Pokémon Eclipse;
2. visualizar a abertura;
3. iniciar o jogo;
4. entrar em Terrae;
5. caminhar pela cidade;
6. respeitar corretamente colisões e limites;
7. entrar e sair das construções;
8. explorar os interiores;
9. conversar com todos os NPCs;
10. interagir com Lina com apresentação especial;
11. interagir com Professora Star com apresentação especial;
12. abrir e navegar pelos menus;
13. fechar o menu e continuar jogando normalmente.

Quando todos esses pontos estiverem aprovados:

> **ETAPA 1 — TERRAE CONCLUÍDA**

Somente então será formulada a Etapa 2.

---

## Regra absoluta de escopo

Enquanto a Etapa 1 estiver ativa:

> **Nenhum desenvolvimento deve sair de Terrae.**

É permitido criar sistemas genéricos apenas quando eles forem utilizados por algum requisito de Terrae.

Não implementar antecipadamente sistemas apenas porque poderão ser úteis no restante do jogo.


---

## Documentos técnicos da Etapa 1

O desenvolvimento de Terrae deve seguir também:

- [Especificação de Terrae](terrae-godot-spec.md)
- [Blueprint técnico de Terrae](terrae-technical-blueprint.md)
- [Pipeline de arte e assets](terrae-asset-pipeline.md)
- [Estrutura inicial do projeto Godot](godot-project-structure.md)

Esses documentos detalham apenas decisões necessárias à Etapa 1 e não autorizam expansão de escopo.
