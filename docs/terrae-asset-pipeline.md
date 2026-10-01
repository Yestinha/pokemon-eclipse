# Terrae — Pipeline de arte e assets

## Objetivo

Definir como os assets visuais de Terrae serão produzidos e importados na versão Godot de Pokémon Eclipse.

O objetivo principal desta migração é preservar liberdade criativa sem perder organização técnica.

---

## 1. Regra principal

Nenhum asset precisa mais obedecer às limitações gráficas do GBA.

Não existem como requisitos do projeto Godot:

- limite de 15 cores;
- 4bpp;
- paletas `.pal`;
- sprites obrigatoriamente 16x32 ou 32x32;
- metatiles;
- limite de 512 tiles;
- chroma key verde;
- conversão para formatos gráficos do Emerald.

Assets 2D podem utilizar transparência alfa real.

---

## 2. Estilos diferentes podem coexistir

O projeto pode utilizar pipelines diferentes conforme o tipo de arte.

### Mundo / overworld

Preferência inicial:

- pixel art moderna;
- contornos legíveis;
- escala coerente;
- transparência;
- sem anti-aliasing acidental quando a intenção for pixel art.

### Retratos

Podem possuir:

- resolução superior;
- pintura digital;
- maior quantidade de cores;
- transparência;
- expressões diferentes.

### UI

Pode misturar:

- elementos pixel art;
- tipografia limpa;
- ilustrações;
- animações;
- efeitos vetoriais ou rasterizados.

A UI não precisa herdar as limitações visuais do overworld.

---

## 3. Escala inicial dos personagens

Para o primeiro teste de Terrae, usar como referência visual:

```text
Canvas comum de personagem: aproximadamente 64 x 64 px
```

Isso não é um limite.

Um personagem pode ultrapassar esse canvas quando:

- cabelo;
- acessórios;
- roupas;
- animações;
- pose;

exigirem mais espaço.

A dimensão definitiva será validada junto ao mockup de Terrae.

---

## 4. Formato recomendado

Para sprites e elementos 2D rasterizados:

```text
PNG
RGBA
transparência alfa
```

Evitar:

- JPG para pixel art;
- chroma key;
- fundo verde;
- recortes destrutivos;
- conversão precoce para paletas reduzidas.

---

## 5. Filtro de textura

Para pixel art do mundo:

- utilizar filtro nearest;
- evitar suavização automática;
- preferir escalas inteiras sempre que possível.

Para ilustrações e retratos que não sejam pixel art, o filtro pode ser configurado separadamente conforme a necessidade visual.

---

## 6. Organização sugerida

```text
assets/
├── characters/
│   ├── player/
│   ├── lina/
│   ├── charlie/
│   ├── star/
│   └── terrae_npcs/
│
├── environments/
│   └── terrae/
│       ├── terrain/
│       ├── paths/
│       ├── water/
│       ├── vegetation/
│       ├── buildings/
│       ├── props/
│       ├── statue/
│       └── effects/
│
├── portraits/
│   ├── lina/
│   └── star/
│
└── ui/
```

Não criar pastas de áreas futuras durante a Etapa 1.

---

## 7. Assets de terreno

Criar como módulos reutilizáveis:

- grama base;
- variações de grama;
- terra;
- caminho;
- transições de caminho;
- margens;
- água;
- bordas de água;
- flores;
- pequenas pedras;
- pequenos detalhes naturais.

### Regra

Variações devem existir para quebrar repetição, mas sem transformar o terreno em ruído visual.

---

## 8. Vegetação

Terrae deve evitar aparência de mapa retangular cercado por uma parede uniforme de árvores.

Preparar um pequeno conjunto modular:

- árvore principal;
- árvore secundária;
- arbusto;
- flor;
- grama alta decorativa;
- pequenos detalhes de chão.

Árvores podem ser maiores que um tile e preferencialmente existir como cenas/sprites quando isso facilitar profundidade e animação.

---

## 9. Construções

Construções importantes devem ser produzidas como assets independentes.

### Casa de Sun/Moon

Direção:

- acolhedora;
- doméstica;
- reconhecível como casa do protagonista.

### Casa de Charlie

Direção já estabelecida:

- energética;
- detalhes azulados;
- menos floral;
- identidade própria.

### Casa de Lina

Direção:

- delicada;
- mais charmosa;
- elementos florais ou visuais compatíveis com sua identidade;
- não reutilizar simplesmente a casa de Charlie com outra cor.

### Laboratório da Professora Star

Direção já aprovada conceitualmente:

- cinza/branco;
- azul;
- moderno;
- científico;
- fachada reconhecível;
- detalhes tecnológicos;
- leitura imediata de laboratório.

A arte conceitual anterior pode ser reutilizada como referência, não como limitação de resolução.

---

## 10. Estátua de Mega Rayquaza

A estátua é um asset narrativo e visual importante.

Ela não deve ser reduzida para caber em uma grade arbitrária.

Preparar como elemento independente:

```text
MegaRayquazaStatue
├── base
├── corpo/escultura
├── placa/inscrição
├── sombra
└── efeitos opcionais
```

A inscrição associada permanece:

> **“Alcance os céus.”**

---

## 11. Sombras

Evitar incorporar todas as sombras permanentemente ao sprite quando houver benefício em mantê-las separadas.

Separar sombra pode permitir:

- ajuste de opacidade;
- animação;
- reposicionamento;
- variação por horário;
- substituição posterior.

Entretanto, sombras desenhadas diretamente no asset continuam aceitáveis quando forem mais simples e visualmente melhores.

---

## 12. Animação ambiental

A produção de arte pode prever:

- água;
- folhas;
- grama;
- luzes do laboratório;
- pequenos brilhos;
- bandeiras/tecidos, se existirem;
- partículas.

Não produzir animação apenas porque o Godot permite.

Cada animação deve melhorar a identidade ou leitura de Terrae.

---

## 13. Nomenclatura

Sugestão:

```text
ter_ground_grass_01.png
ter_ground_path_01.png
ter_tree_01.png
ter_tree_02.png
ter_house_player.png
ter_house_charlie.png
ter_house_lina.png
ter_lab_star.png
ter_statue_rayquaza.png

lina_idle_front.png
lina_walk_front.png
lina_walk_back.png
lina_walk_left.png
lina_walk_right.png
```

Usar nomes em inglês nos arquivos técnicos para manter consistência com código e engine.

Lore e documentação podem continuar em português.

---

## 14. Arquivos-fonte de arte

Quando uma arte possuir arquivo-fonte editável, manter separação entre:

- fonte;
- export final utilizado pelo jogo.

Exemplo conceitual:

```text
art_source/
└── terrae/
    └── star_lab_source.*

assets/
└── environments/
    └── terrae/
        └── buildings/
            └── ter_lab_star.png
```

A política de versionamento de arquivos-fonte grandes será decidida depois de vermos os formatos e tamanhos reais.

Não configurar Git LFS antecipadamente sem necessidade.

---

## 15. Checklist de qualidade de um asset

Antes de um asset entrar como definitivo em Terrae:

- [ ] combina com a escala do mapa;
- [ ] possui transparência correta;
- [ ] não possui halo de chroma key;
- [ ] não fica borrado no filtro pretendido;
- [ ] possui contraste suficiente;
- [ ] respeita a identidade do personagem/local;
- [ ] funciona com profundidade;
- [ ] possui colisão planejável;
- [ ] não depende de limitação gráfica herdada do GBA;
- [ ] é coerente com os outros assets de Terrae.

---

## 16. Primeiro kit de arte necessário

Antes de produzir Terrae inteira, precisamos apenas de um kit mínimo para validar a linguagem visual:

- [ ] grama;
- [ ] caminho;
- [ ] árvore;
- [ ] arbusto;
- [ ] água;
- [ ] uma casa;
- [ ] laboratório em versão de teste;
- [ ] Player temporário;
- [ ] sombra básica.

Com esse kit será possível decidir escala e resolução antes de produzir o restante.
