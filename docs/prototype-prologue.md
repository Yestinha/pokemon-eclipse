# Protótipo jogável — Prólogo

## Objetivo

Criar a primeira versão jogável de **Pokémon Eclipse** cobrindo apenas o prólogo já planejado.

O foco desta etapa não é polimento final. O objetivo é construir um fluxo completo, testável e pequeno o suficiente para aprender o processo de desenvolvimento sem tentar implementar o jogo inteiro de uma vez.

## Escopo do protótipo

O protótipo começa na casa de Sun/Moon em Terrae e termina após o evento da Praia Lactia, com Charlie e Lina seguindo caminhos separados e o próximo objetivo apontando para a cidade do primeiro Ginásio.

### Fluxo incluído

1. Introdução na TV com a Professora Star
2. Terrae
3. Encontro com Charlie, Lina, Riolu e Chikorita
4. Laboratório da Professora Star
5. Escolha entre Gible, Impidimp e Shinx
6. Duas batalhas iniciais contra Charlie e Lina
7. Despedida da mãe e estátua de Mega Rayquaza
8. Rota Celestial 1
9. Tutorial de captura com Lina
10. Evento da pena gélida e Articuno
11. Astrid
12. Exploração livre da cidade
13. Missão **ENCONTRE PROFESSORA STAR**
14. Praia Lactia
15. Primeira batalha contra a Equipe Void
16. Vladimir e Aggron
17. Intervenção de Victini com V-create
18. Fuga da Void com o Blue Orb
19. Eevee entregue ao trio
20. Separação temporária de Sun/Moon, Charlie e Lina

## Estratégia de implementação

O desenvolvimento será feito em pequenas entregas jogáveis.

### Etapa 0 — Ambiente

- [x] Configurar ambiente de desenvolvimento
- [x] Compilar a base atual sem alterações
- [x] Abrir a ROM compilada em um emulador
- [ ] Instalar e abrir Porymap
- [ ] Fazer um commit de checkpoint após a build funcionar

### Etapa 1 — Terrae vazia

- [ ] Criar mapa de Terrae
- [ ] Criar casa de Sun/Moon
- [ ] Criar laboratório da Professora Star
- [ ] Criar praça e posição da estátua de Mega Rayquaza
- [ ] Configurar warps e colisões
- [ ] Conseguir caminhar da casa até o laboratório

### Etapa 2 — Primeiro evento

- [ ] Introdução da TV
- [ ] Objetivo para ir ao laboratório
- [ ] Cena de Riolu e Chikorita
- [ ] Charlie e Lina
- [ ] Entrada no laboratório

### Etapa 3 — Inicial e rivais

- [ ] Implementar escolha do inicial
- [ ] Inicial no nível 5
- [ ] Batalha contra Charlie
- [ ] Batalha contra Lina
- [ ] Permitir escolher quem enfrentar primeiro
- [ ] Despedida da mãe
- [ ] Cena da estátua

### Etapa 4 — Rota Celestial 1

- [ ] Criar mapa
- [ ] Encontros selvagens de dia e noite
- [ ] Assistente da Professora Star
- [ ] Tutorial de captura
- [ ] Dois treinadores
- [ ] Poção visível
- [ ] Cena de Articuno

### Etapa 5 — Astrid

- [ ] Criar mapa da cidade
- [ ] Centro Pokémon
- [ ] Loja
- [ ] Residências
- [ ] NPC da Vara de Pescar
- [ ] Evento de chegada da Professora Star
- [ ] Ativar missão **ENCONTRE PROFESSORA STAR**

### Etapa 6 — Praia Lactia

- [ ] Criar mapa da praia
- [ ] Posicionar Equipe Void
- [ ] Batalha Poochyena / Pawniard / Yamask
- [ ] Cena de Vladimir e Aggron
- [ ] Cena de Victini usando V-create
- [ ] Fuga com o Blue Orb
- [ ] Conversa pós-batalha
- [ ] Entrega dos três Eevee
- [ ] Separação do trio

## Fora do escopo desta versão

Para evitar aumentar demais a primeira implementação, ficam para depois:

- sidequests adicionais;
- primeiro Ginásio;
- cidade do primeiro Ginásio;
- sistemas especiais de revanche;
- gimmicks de batalha;
- conteúdo de pós-game;
- polimento visual definitivo;
- equipes finais dos personagens.

## Regra de desenvolvimento

Não avançar para a próxima etapa enquanto a atual não estiver compilando e jogável.

Sempre que possível, fazer commits pequenos e descritivos para facilitar a identificação de erros e a evolução do portfólio.
