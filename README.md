# PokeBattle Arena

Jogo interativo de batalhas Pokémon para 2 jogadores com interface moderna, responsiva e sistema de tipos com vantagens.

## Visão Geral

PokeBattle Arena é um jogo da web que permite que dois jogadores compitam selecionando dois Pokémon cada um. O sistema calcula automaticamente os stats totais, aplica bônus de tipo quando aplicável e determina o vencedor da batalha.

## Funcionalidades Principais

- Seleção de Pokémon por nome ou ID
- Geração de Pokémon aleatório (até 1025 espécies)
- Sistema completo de tipos com vantagens (bônus de 15% em stats)
- Visualização detalhada de stats individualmente (HP, ATK, DEF, SpA, SpD, VEL)
- Cálculo automático de batalhador
- Efeitos visuais e sonoros durante a batalha
- Interface totalmente responsiva
- Acessibilidade com atributos ARIA
- Modal de resultado com placar final

## Estrutura do Projeto

```
src/
├── script/
│   └── script.js              (385 linhas de código)
│
├── css/
│   ├── style.css              (arquivo principal com imports)
│   ├── base/
│   │   ├── reset.css
│   │   └── variables.css
│   ├── components/
│   │   ├── buttons.css
│   │   ├── cards.css
│   │   └── filters.css
│   ├── layout/
│   │   ├── header.css
│   │   ├── footer.css
│   │   ├── forms.css
│   │   └── modals.css
│   ├── main.css
│   ├── animations.css
│   └── responsive.css
│
└── assets/
    ├── images/
    │   ├── logo.jpg           (logo no header)
    │   └── arena.jpg          (background)
    └── sounds/
        ├── battle.mp3         (música de batalha em loop)
        ├── hit.mp3            (efeito de impacto - 4x)
        ├── victory.mp3        (música de vitória)
        └── click.mp3          (som de clique)
```

## Como Jogar

1. Abra index.html em um navegador moderno
2. Digite o nome (ex: "pikachu") ou ID (ex: "25") de um Pokémon
3. Clique em "Buscar" ou "Aleatório"
4. Repita para os 4 slots (2 Pokémon por jogador)
5. Após preencher todos os slots, clique em "INICIAR BATALHA"
6. Veja a animação de batalha com efeitos sonoros
7. Visualize o resultado no modal mostrando:
   - Vencedor da batalha
   - Total de stats de cada jogador
   - Multiplicador de vantagem de tipo (se houver)
8. Clique em "RESTART" para jogar novamente

## Sistema de Tipos

18 tipos de Pokémon com tabela de vantagens baseada nos games:

- Fire: vantagem contra Grass, Ice, Bug, Steel
- Water: vantagem contra Fire, Ground, Rock
- Grass: vantagem contra Water, Ground, Rock
- Electric: vantagem contra Water, Flying
- Ice: vantagem contra Grass, Ground, Flying, Dragon
- Fighting: vantagem contra Normal, Ice, Rock, Dark, Steel
- Poison: vantagem contra Grass, Fairy
- Ground: vantagem contra Fire, Electric, Poison, Rock, Steel
- Flying: vantagem contra Grass, Fighting, Bug
- Psychic: vantagem contra Fighting, Poison
- Bug: vantagem contra Grass, Psychic, Dark
- Rock: vantagem contra Fire, Ice, Flying, Bug
- Ghost: vantagem contra Psychic, Ghost
- Dragon: vantagem contra Dragon
- Dark: vantagem contra Psychic, Ghost
- Steel: vantagem contra Ice, Rock, Fairy
- Fairy: vantagem contra Fighting, Dragon, Dark
- Normal: sem vantagens

Quando um jogador tem vantagem de tipo, recebe bônus de 15% em seus stats totais.

## Componentes Principais do JavaScript

### Estado do Jogo
- Armazena dados dos 2 jogadores com 2 slots cada
- null = slot vazio
- Objeto com nome, tipos, stats e imagem = Pokémon selecionado

### Funções de Áudio
- unlockAudio(): Desbloqueia reprodução de áudio (necessário por políticas do navegador)
- playClick(): Som de clique
- playHit(): Som de impacto (reproduzido 4x durante a batalha)
- playVictory(): Som de vitória
- startBattleMusic(): Inicia música de batalha em loop
- stopBattleMusic(): Para música de batalha
- playCry(): Toca o grito do Pokémon (da PokeAPI)

### Funções de Busca
- buscarPokemon(player, slot): Busca Pokémon pelo nome ou ID
- pokemonAleatorio(player, slot): Seleciona Pokémon aleatório
- carregarPokemon(player, slot, nomeOuId): Busca na PokeAPI e renderiza

### Funções de UI
- renderizarStats(): Cria barras visuais de stats
- traduzirTipo(): Traduz nomes de tipos para português
- mostrarErro(): Exibe mensagens de erro
- atualizarTotalJogador(): Calcula e exibe total de stats
- verificarBotao(): Mostra botão "INICIAR BATALHA" quando completo

### Funções de Batalha
- batalhar(): Inicia animação de batalha
- calcularResultadoFinal(): Calcula o vencedor
- calcularMultiplicador(): Aplica bônus de vantagem de tipo
- mostrarResultado(): Exibe modal com resultado
- reiniciar(): Reseta o jogo

## Dados Obtidos da PokeAPI

Para cada Pokémon a aplicação obtém:
- Nome
- ID
- Tipos (até 2)
- Stats base (6 valores: HP, ATK, DEF, SpA, SpD, VEL)
- Imagem oficial (artwork)
- Som de cry

## Tecnologias Utilizadas

- HTML5 semântico com atributos ARIA
- CSS3 com variáveis, Grid, Flexbox, animações
- JavaScript Vanilla (sem frameworks/dependências)
- PokeAPI v2 (https://pokeapi.co/)
- Fonts: Press Start 2P (headers), Poppins (corpo)

## Requisitos do Navegador

- Suporte a Fetch API
- Suporte a CSS Grid e Flexbox
- Suporte a Audio API
- Suporte a ES6 JavaScript
- JavaScript ativado

## Navegadores Compatíveis

- Chrome 60+
- Firefox 55+
- Safari 12+
- Edge 79+
- Opera 47+
- Navegadores modernos em geral

## Responsividade

- Mobile: Layout em coluna, Pokémon aleatório padrão
- Tablet (600px+): Cards ajustados
- Desktop (960px+): Layout lado a lado com VS central
- Wide Desktop (1200px+): Otimizações de tamanho


