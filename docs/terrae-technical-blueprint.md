# Terrae — Blueprint técnico no Godot

## Status

Este documento define a arquitetura técnica **provisória** do mapa exterior de Terrae para a Etapa 1.

Nada aqui amplia o escopo do projeto para além de Terrae.

As decisões de escala visual serão validadas no editor antes de se tornarem definitivas.

---

## 1. Direção técnica

### Engine

- Godot 4.x;
- projeto 2D;
- câmera top-down;
- mundo construído com uma combinação de `TileMapLayer` e cenas 2D independentes;
- GDScript como linguagem padrão inicial.

### Princípio central

O mapa não deve ser tratado como uma grande imagem única.

Também não deve voltar a ser limitado pela filosofia de tiles do GBA.

A proposta é combinar:

- tiles para terreno repetitivo;
- cenas para construções;
- cenas para props;
- objetos livres para elementos únicos;
- camadas separadas para profundidade;
- efeitos independentes para acabamento.

---

## 2. Resolução e escala — proposta inicial

### Viewport de referência

Primeiro teste recomendado:

```text
Viewport interno: 640 x 360
Janela de teste: 1280 x 720
Aspect ratio: 16:9
Stretch: canvas_items
Aspect: keep
```

Essa resolução é uma **base de validação**, não uma limitação artística.

Antes de congelá-la, Terrae deve receber um mockup real contendo:

- Player temporário;
- uma casa;
- árvore;
- caminho;
- laboratório em escala aproximada;
- parte da praça.

Se a leitura visual ficar pequena demais, testar `960 x 540` antes de produzir o mapa definitivo.

### Regra

Não criar todos os assets antes de validar a escala.

---

## 3. Grade lógica

### Unidade base sugerida

```text
32 x 32 px
```

A grade serve para:

- terreno;
- alinhamento de caminhos;
- portas;
- colisões;
- organização de construções.

Ela **não** obriga todos os objetos a terem 32 x 32.

Exemplos:

- uma árvore pode ocupar 64 x 96;
- uma casa pode ocupar 192 x 160;
- a estátua pode possuir qualquer proporção;
- objetos decorativos podem ficar fora da grade quando necessário.

### Regra de liberdade

A grade organiza o mundo.

Ela não define o tamanho máximo da arte.

---

## 4. Estrutura da cena Terrae

Estrutura sugerida:

```text
Terrae (Node2D)
│
├── Ground
│   ├── GroundBase (TileMapLayer)
│   ├── Paths (TileMapLayer)
│   └── GroundDetails (TileMapLayer)
│
├── Water
│   └── WaterLayer (TileMapLayer / cenas animadas)
│
├── WorldObjects (Node2D - Y Sort)
│   ├── Buildings
│   ├── Trees
│   ├── Props
│   ├── Statue
│   └── TestCharacter
│
├── Foreground
│   ├── TreeCanopies
│   └── ForegroundDetails
│
├── Effects
│   ├── AmbientParticles
│   ├── Lights
│   └── AnimatedEnvironment
│
├── Boundaries
│   └── Collision objects
│
└── Camera
    └── Camera2D
```

Os nomes podem ser ajustados durante a implementação, mas a separação conceitual deve permanecer.

---

## 5. TileMapLayer — o que deve usar tiles

Usar tiles para elementos realmente repetitivos:

- grama;
- terra;
- caminhos;
- pedras de caminho;
- margens;
- água base;
- pequenas flores;
- detalhes repetitivos do chão;
- cercas modulares simples.

Evitar transformar em tiles:

- casas inteiras;
- laboratório;
- estátua;
- árvores muito grandes e únicas;
- placas importantes;
- objetos narrativos;
- elementos que precisem de animação complexa.

Esses elementos devem preferencialmente ser cenas independentes.

---

## 6. Construções como cenas

Cada construção importante deve poder existir como uma cena própria.

Exemplo:

```text
House_Player.tscn
├── Sprite2D
├── Shadow
├── Collision
└── DoorAnchor
```

Exemplo do laboratório:

```text
StarLab.tscn
├── Base
├── AnimatedDetails
├── Windows
├── Shadow
├── Collision
└── Entrance
```

### Benefícios

- posicionamento livre;
- sprites maiores;
- animações próprias;
- sombras próprias;
- colisões precisas;
- fácil substituição de arte;
- reutilização sem transformar tudo em atlas.

---

## 7. Profundidade e Y-sort

Terrae precisa permitir situações como:

- Player passar atrás de uma árvore;
- Player passar na frente de uma casa;
- NPC passar atrás de um objeto alto;
- copas cobrirem parcialmente personagens.

### Estratégia

O grupo principal de objetos dinâmicos deve usar ordenação por Y.

Elementos que não participam da ordenação devem ficar em camadas/Z-index separados.

Para árvores e estruturas grandes, preferir dividir visualmente quando necessário:

```text
Tree
├── Trunk/Base        ← participa do Y-sort
└── Canopy/Top        ← foreground
```

O mesmo princípio pode ser aplicado a:

- postes;
- arcos;
- placas grandes;
- estátua;
- estruturas com passagem por trás.

### Regra

Não resolver profundidade apenas alterando manualmente o Z-index de cada NPC.

O sistema deve funcionar naturalmente pelo posicionamento no mundo.

---

## 8. Colisões

### Terreno

Quando fizer sentido, colisões simples podem vir do próprio TileSet:

- água não atravessável;
- bordas;
- pequenos obstáculos modulares.

### Construções e props

Objetos grandes devem possuir colisão própria:

- `StaticBody2D`;
- `CollisionShape2D`;
- `CollisionPolygon2D` quando necessário.

### Filosofia

A colisão deve representar a área física útil do objeto, não necessariamente toda a área da imagem.

Exemplo:

Uma árvore de 96 px de altura pode bloquear apenas a região do tronco/base.

---

## 9. Limites de Terrae

A cidade deve ter limites naturais e técnicos.

### Limites visuais

Preferir:

- floresta;
- vegetação;
- relevo;
- cercas;
- água;
- estruturas;
- composição natural.

### Limite físico

Mesmo quando o limite visual já indicar o fim do mapa, deve existir uma barreira de colisão para impedir que o Player deixe a área jogável.

### Câmera

A `Camera2D` deve possuir limites coerentes para não revelar:

- vazio fora do mapa;
- áreas técnicas;
- partes inacabadas.

---

## 10. Água

A água de Terrae pode utilizar animação desde o requisito 1, porque existe no próprio mapa.

Pipeline recomendado:

```text
água base
+
animação discreta
+
reflexo/realce opcional
+
objetos de margem
```

Não criar agora:

- Surf;
- pesca;
- encounters aquáticos;
- física especial.

Nada disso é necessário para o mapa de Terrae neste estágio.

---

## 11. Sombras

Sombras são permitidas e recomendadas quando melhorarem a leitura da cena.

### Tipos

- sombra desenhada junto ao asset;
- Sprite2D separado;
- shader simples;
- iluminação 2D quando houver ganho visual real.

### Regra

Não escolher uma solução tecnicamente complexa antes de comparar visualmente com uma sombra simples.

O objetivo é qualidade visual, não complexidade.

---

## 12. Controlador temporário de teste

Durante o requisito 1, será usado um personagem temporário.

Esse personagem serve apenas para validar:

- escala;
- velocidade;
- câmera;
- colisão;
- profundidade;
- passagens;
- portas;
- sensação do mapa.

Ele não representa o sprite definitivo de Sun/Moon.

Quando chegar o requisito 3 — Player, ele será substituído pelo Player real.

---

## 13. Portas

Já durante o mapa exterior, cada entrada deve possuir um ponto claro de acesso.

Estrutura conceitual:

```text
Door
├── Area2D
├── CollisionShape2D
└── Destination
```

A transição completa para interiores será implementada no requisito 2, mas o mapa exterior já deve reservar posições e dimensões corretas.

---

## 14. Efeitos ambientais permitidos

Podem entrar no requisito 1 se forem usados em Terrae:

- folhas discretas;
- partículas de luz;
- água em movimento;
- pequenos movimentos de vegetação;
- brilhos tecnológicos no laboratório;
- iluminação ambiente;
- sombras.

Devem ser cenas independentes sempre que possível para poderem ser ativadas, removidas ou refinadas sem reconstruir o mapa.

---

## 15. Marcos internos do requisito 1

### M1-A — Escala aprovada

- [ ] viewport de teste;
- [ ] grade de 32 px;
- [ ] Player temporário;
- [ ] uma árvore;
- [ ] uma casa;
- [ ] trecho de caminho;
- [ ] mockup do laboratório;
- [ ] escala visual aprovada.

### M1-B — Mapa bruto

- [ ] terreno completo;
- [ ] caminhos;
- [ ] lago/água;
- [ ] praça;
- [ ] posição das construções;
- [ ] posição da saída;
- [ ] limites.

### M1-C — Navegação

- [ ] colisões;
- [ ] câmera;
- [ ] Y-sort;
- [ ] passagem correta por objetos;
- [ ] entradas posicionadas.

### M1-D — Identidade

- [ ] casas diferenciadas;
- [ ] laboratório final;
- [ ] praça final;
- [ ] estátua;
- [ ] vegetação e decoração;
- [ ] leitura visual coerente.

### M1-E — Polimento

- [ ] sombras;
- [ ] animações ambientais escolhidas;
- [ ] água;
- [ ] partículas/iluminação aprovadas;
- [ ] revisão final do exterior.

Ao terminar M1-E, o requisito **1 — Mapa de Terrae funcional** pode ser marcado como concluído.

---

## 16. O que explicitamente NÃO entra agora

Durante este requisito não desenvolver:

- sistema de batalha;
- sistema de Pokémon;
- captura;
- Party;
- Pokédex;
- inventário real;
- encontros selvagens;
- evolução;
- sistema de ginásios;
- Rota Celestial 1;
- Astrid;
- Praia Lactia.

A única pergunta válida continua sendo:

> Isto é necessário para construir ou testar Terrae?
