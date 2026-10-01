# Terrae — Especificação inicial para Godot

## Papel de Terrae

Terrae é a cidade inicial de Pokémon Eclipse e o único local em desenvolvimento durante a **Etapa 1**.

Ela deve funcionar como o primeiro espaço jogável completo do projeto e apresentar imediatamente:

- a identidade visual do Eclipse;
- a relação entre Sun/Moon, Charlie e Lina;
- a presença da Professora Star;
- o contraste entre cidade pequena, natureza e tecnologia;
- a frase-símbolo **“Alcance os céus.”**

## Elementos criativos já definidos

Terrae deve conter:

- aproximadamente cinco casas;
- casa do protagonista;
- laboratório da Professora Star;
- praça central;
- estátua de Mega Rayquaza;
- a inscrição **“Alcance os céus.”**;
- caminho de saída da cidade;
- NPCs locais;
- tecnologia acima do esperado para uma cidade pequena.

A cidade permanece pequena e acolhedora, mas não deve parecer genérica.

## Direção visual

### Objetivo

Terrae precisa transmitir:

- começo de jornada;
- familiaridade;
- segurança;
- natureza;
- tecnologia discreta;
- identidade própria.

### Construções

As casas não devem ser cópias umas das outras.

Cada residência deve ter alguma identidade própria por meio de:

- fachada;
- telhado;
- proporção;
- jardim;
- objetos externos;
- detalhes arquitetônicos;
- elementos associados a seus moradores.

O laboratório da Professora Star deve se destacar das residências e comunicar imediatamente sua função científica.

### Praça central

A praça é o coração visual da cidade.

A estátua de Mega Rayquaza deve funcionar como um marco reconhecível e como elemento narrativo.

A frase:

> **“Alcance os céus.”**

deve permanecer ligada à estátua e ao começo da jornada de Sun/Moon.

## Requisitos técnicos do exterior

Para aprovação do mapa exterior, Terrae deve possuir:

- terreno finalizado;
- caminhos definidos;
- limites claros;
- colisões funcionais;
- construções posicionadas;
- portas posicionadas;
- praça funcional;
- estátua posicionada;
- saída da cidade posicionada;
- camadas visuais coerentes;
- profundidade correta para objetos que devem ficar na frente ou atrás do Player.

## Acabamento ambiental permitido

Como a nova plataforma é Godot, podem ser usados quando contribuírem para Terrae:

- sombras;
- iluminação;
- água animada;
- vegetação com movimento discreto;
- partículas;
- elementos ambientais animados;
- detalhes de profundidade.

Esses efeitos devem complementar o mapa, não impedir sua conclusão.

## Interiores previstos

A Etapa 1 exige todos os interiores acessíveis de Terrae.

Já existem como necessidades narrativas:

- casa de Sun/Moon;
- laboratório da Professora Star.

As demais residências devem ser definidas e construídas conforme o elenco local de Terrae for fechado.

## Personagens diretamente ligados ao começo

Terrae deve comportar desde o início:

- Sun/Moon;
- mãe de Sun/Moon;
- Charlie;
- Lina;
- Professora Star;
- Riolu;
- Chikorita;
- moradores locais necessários ao mapa.

Na Etapa 1, **Lina** e **Professora Star** são tratadas como NPCs especiais de apresentação, com retratos, expressões e caixas de diálogo próprias.

## Sequência narrativa já definida para Terrae

A documentação atual estabelece como base do começo:

1. programa científico da Professora Star na TV;
2. Sun/Moon em casa com a mãe;
3. objetivo de ir ao laboratório;
4. encontro com Riolu e Chikorita;
5. encontro com Charlie e Lina;
6. ida ao laboratório;
7. despedida da mãe;
8. passagem pela estátua de Mega Rayquaza;
9. frase **“Alcance os céus.”**

Alguns eventos posteriores dessa sequência dependem de sistemas que ainda não pertencem ao escopo técnico da Etapa 1. Eles permanecem documentados como narrativa, mas não devem forçar a implementação antecipada de batalha ou sistemas Pokémon.

## Pendências específicas de Terrae

Ainda precisam ser fechados durante a Etapa 1:

- quantidade exata e função das residências;
- NPCs moradores de cada casa;
- aparência final do exterior;
- layout final da praça;
- proporção final da estátua;
- desenho final do laboratório;
- interiores finais;
- falas ambientais;
- nome da mãe, caso seja necessário;
- detalhes finais da apresentação de Lina e Professora Star.

## Regra de escopo

Nenhum elemento de Astrid, Praia Lactia, Rota Celestial 1 ou outras áreas deve ser implementado durante esta etapa.

Terrae deve ser concluída como um espaço independente antes da expansão do projeto.
