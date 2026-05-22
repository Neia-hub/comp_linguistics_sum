## ~={orange}Context-Free Grammars and Constituency Parsing=~
capítulo 18, Jurafsky & Martin (3º ed.)

### ~={yellow}1. O conceito de "Constuintes"=~
A ideia central é que os grupos de palavras se comportam como unidades lógicas (**~={purple}constituintes=~**) que podem ser manipuladas em conjunto.Há evidências linguísticas para a existência de constituintes, como a **~={purple}substituição=~** (substituir um sintagma nominal por um pronome) ou o **~={purple}movimento=~** (mudar a posição de um bloco inteiro na frase).
A estrutura de constituintes é habitualmente representada através de **~={purple}árvores sintáticas=~**, em que cada nó interno representa um constituinte (exs.: **NP**, **VP**, **S**).

### ~={yellow}2. Gramáticas Independentes de Contexto (Context-Free Grammars - CFG)=~
Uma CFG é um formalismo matemático que define um conjunto de regras para gerar todas as frases possíveis de uma língua.
Formalmente, uma CFG é composta por 4 elementos:
- um conjunto de **~={purple}símbolos não-terminais=~** (categorias sintáticas);
- um conjunto de **~={purple}símbolos terminais=~** (as palavras/o léxico);
- um conjunto de regras de produção (ex.: S → NP VP);
- um símbolo inicial (geralmente S).

**S** - Sentence (frase)
**NP** - Noun Phrase (Sintagma Nominal)
**VP** - Verb Phrase (Sintagma Verbal)

As regras de produção permitem a recursividade, o que possibilita à gramática gerar frases de comprimento potencialmente infinito (ex.: recursividade em sintagmas preposicionais ou orações relativas)

### ~={yellow}3. Treebanks e o PennTreebank=~
Um treebank é um ~={purple}**corpus**=~ (base de dados) de textos que foi anotado manualmente por linguistas com árvores sintáticas completas.
O PennTreebank é o recurso mais influente nesta área, utilizando um conjunto de etiquetas (**~={purple}tags=~**) específico para descrever a estrutura do Inglês do Wall Street Journal.
Estes recursos são vitais para treinar **~={purple}parsers=~** automáticos e para avaliar o seu desempenho estatístico.

### ~={yellow}4. Equivalência de Gramáticas e Forma Normal de Chomsky (CNF)=~
Duas gramáticas são equivalentes se gerarem exatamente a mesma linguagem (o mesmo conjunto de frases).
A Forma Normal de Chomsky (CNF) é uma versão simplificada de uma CFG, em que todas as regras têm apenas duas formas:
- A → B C (um não-terminal expande para um dois não terminais);
- A → w (um não-terminal expande para um(a) terminal/palavra).

Qualquer CFG pode ser convertida para CNF sem perder poder de expressão. Esta conversão é obrigatória para a aplicação de **~={purple}algoritmos de parsing=~** eficientes, como o CKY.

### ~={yellow}5. Algoritmo  CKY (Cocke-Kasami-Younger)=~
É um algoritmo de programação dinâmica que resolve o problema do "parsing" (análise sintática) de forma eficiente, evitando o reprocessamento de substruturas já analisadas.
O CKY trabalha de "baixo para cima" (bottom-up), preenchendo uma tabela (matriz) onde cada célula representa os constituintes possíveis para um intervalo específico de palavras na frase.
A complexidade do CKY é **O(n³)** (complexidade de tempo), onde **n** é o número de palavras na frase, o que o torna viável para processar frases longas.

### ~={yellow}6. Ambiguidade Sintática=~
Um dos maiores desafios na Linguística Computacional é a ambiguidade: uma única frase pode ter múltiplas árvores sintáticas válidas de acordo com a gramática.
> **Ex.:** *I saw the man with the telescope*

O algoritmo CKY lida com isto permitindo que cada célula da tabela contenha múltiplos símbolos não-terminais se diferentes regras puderem cobrir o mesmo intervalo de palavras. Para resolver qual a árvore "correta", o capítulo introduz a necessidade de **~={purple}gramáticas probabilísticas=~** (PCFG), que atribuem pesos às regras para encontrar a estrutura mais provável.

### ~={yellow}7. Avaliação de Parsers=~
A métrica padrão para avaliar a qualidade de um parser é o PARSEVAL, que mede a precisão e a revocação (recall) dos contituintes encontrados em comparação com uma árvore de referência (gold standard). Foca-se em verificar se os limites (boundaries) e a etiqueta do constituinte (ex.: NP de 0 a 3) coincidem com o esperado.

----
## ~={orange}Vector Semantics and Embeddings=~
Capítulo 5, Jurasky & Martin (3ºed.)
### ~={yellow}1. Semântica Lexical e o significado das palavras=~
- **Lexical Semantics**: o estudo linguísticso do significado das palavras. No processamento de linguagem natural (PLN), o desafio é representar o que uma palavra "significa" de forma computacional.

- **Lemmas e Senses**: uma palavra como "banco" pode ter múltiplos word senses (significados) um banco financeiro ou um banco de jardim. O lemma é a forma-base da palavra (ex: "correr" para "correndo").

- **Sinonímia e Antonímia**: Relações onde palavras têm significados quase idênticos (ex.: big e large) ou opostos (ex.: long e short).

- **Conotação**: o sentimento ou "vibe" que uma palavra carrega (ex.: "happy" carrega uma conotação positiva, enquanto "sad" carrega uma conotação negativa).

### ~={yellow}2. A Hipótese Distribucional (Distributional Hypothesis)=~
- **Distributional Hypothesis**: "conhecerás uma palavra pelas companhias que ela mantém" (tradução de Firth, 1957). O coneito central é que palavras que aparecem em contexto semelhantes tendem a ter significados semelhantes.

- **Vector Semantics**: em vez de definir palavras com dicionários, definimo-las como vetores (pontos num espaço multidimensional). Se "café" e "chá" aparecem perto de "beber" e "chávena", os seus vetores estarão próximos no espaço.

### ~={yellow}3. Vetores Esparsos: TF-IDF e PPMI=~
- **Term-Document Matrix**: uma matriz inde as linhas são palavras e as colunas são documentos. O valor em cada célula indica a frequência da palavra naquele documento.

- **TF-IDF (Term Frequency-Inverse Document Frequency**: uma métrica de peso que dá importância a palavras que são frequentes num documento mas raras no resto do corpus. Serve para ignorar palavras como "o" e "e".

- **PPMI (Positive Pointwise Mutual Information)**: uma alternativa à simples contagem de palavras. Mede o quanto a ocorrência de duas palavras juntas é mais provável do que se fosse por puro acaso.