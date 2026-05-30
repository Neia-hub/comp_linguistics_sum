## Context-Free Grammars and Constituency Parsing
capítulo 18, Jurafsky & Martin (3º ed.)

### 1. O conceito de "Constuintes"
A ideia central é que os grupos de palavras se comportam como unidades lógicas (**constituintes**) que podem ser manipuladas em conjunto.Há evidências linguísticas para a existência de constituintes, como a **substituição** (substituir um sintagma nominal por um pronome) ou o **movimento** (mudar a posição de um bloco inteiro na frase).
A estrutura de constituintes é habitualmente representada através de **árvores sintáticas**, em que cada nó interno representa um constituinte (exs.: **NP**, **VP**, **S**).

### 2. Gramáticas Independentes de Contexto (Context-Free Grammars - CFG)
Uma CFG é um formalismo matemático que define um conjunto de regras para gerar todas as frases possíveis de uma língua.
Formalmente, uma CFG é composta por 4 elementos:
- um conjunto de **símbolos não-terminais** (categorias sintáticas);
- um conjunto de **símbolos terminais** (as palavras/o léxico);
- um conjunto de regras de produção (ex.: S → NP VP);
- um símbolo inicial (geralmente S).

**S** - Sentence (frase)
**NP** - Noun Phrase (Sintagma Nominal)
**VP** - Verb Phrase (Sintagma Verbal)

As regras de produção permitem a recursividade, o que possibilita à gramática gerar frases de comprimento potencialmente infinito (ex.: recursividade em sintagmas preposicionais ou orações relativas)

### 3. Treebanks e o PennTreebank
Um treebank é um **corpus** (base de dados) de textos que foi anotado manualmente por linguistas com árvores sintáticas completas.
O PennTreebank é o recurso mais influente nesta área, utilizando um conjunto de etiquetas (**tags**) específico para descrever a estrutura do Inglês do Wall Street Journal.
Estes recursos são vitais para treinar **parsers** automáticos e para avaliar o seu desempenho estatístico.

### 4. Equivalência de Gramáticas e Forma Normal de Chomsky (CNF)
Duas gramáticas são equivalentes se gerarem exatamente a mesma linguagem (o mesmo conjunto de frases).
A Forma Normal de Chomsky (CNF) é uma versão simplificada de uma CFG, em que todas as regras têm apenas duas formas:
- A → B C (um não-terminal expande para um dois não terminais);
- A → w (um não-terminal expande para um(a) terminal/palavra).

Qualquer CFG pode ser convertida para CNF sem perder poder de expressão. Esta conversão é obrigatória para a aplicação de **algoritmos de parsing** eficientes, como o CKY.

### 5. Algoritmo  CKY (Cocke-Kasami-Younger)
É um algoritmo de programação dinâmica que resolve o problema do "parsing" (análise sintática) de forma eficiente, evitando o reprocessamento de substruturas já analisadas.
O CKY trabalha de "baixo para cima" (bottom-up), preenchendo uma tabela (matriz) onde cada célula representa os constituintes possíveis para um intervalo específico de palavras na frase.
A complexidade do CKY é **O(n³)** (complexidade de tempo), onde **n** é o número de palavras na frase, o que o torna viável para processar frases longas.

### 6. Ambiguidade Sintática
Um dos maiores desafios na Linguística Computacional é a ambiguidade: uma única frase pode ter múltiplas árvores sintáticas válidas de acordo com a gramática.
> **Ex.:** *I saw the man with the telescope*

O algoritmo CKY lida com isto permitindo que cada célula da tabela contenha múltiplos símbolos não-terminais se diferentes regras puderem cobrir o mesmo intervalo de palavras. Para resolver qual a árvore "correta", o capítulo introduz a necessidade de **gramáticas probabilísticas** (PCFG), que atribuem pesos às regras para encontrar a estrutura mais provável.

### 7. Avaliação de Parsers
A métrica padrão para avaliar a qualidade de um parser é o PARSEVAL, que mede a precisão e a revocação (recall) dos contituintes encontrados em comparação com uma árvore de referência (gold standard). Foca-se em verificar se os limites (boundaries) e a etiqueta do constituinte (ex.: NP de 0 a 3) coincidem com o esperado.

----
## Vector Semantics and Embeddings
Capítulo 5, Jurasky & Martin (3ºed.)
### 1. Semântica Lexical e o significado das palavras
- **Lexical Semantics**: o estudo linguísticso do significado das palavras. No processamento de linguagem natural (PLN), o desafio é representar o que uma palavra "significa" de forma computacional.

- **Lemmas e Senses**: uma palavra como "banco" pode ter múltiplos word senses (significados) um banco financeiro ou um banco de jardim. O lemma é a forma-base da palavra (ex: "correr" para "correndo").

- **Sinonímia e Antonímia**: Relações onde palavras têm significados quase idênticos (ex.: big e large) ou opostos (ex.: long e short).

- **Conotação**: o sentimento ou "vibe" que uma palavra carrega (ex.: "happy" carrega uma conotação positiva, enquanto "sad" carrega uma conotação negativa).

### 2. A Hipótese Distribucional (Distributional Hypothesis)
- **Distributional Hypothesis**: "conhecerás uma palavra pelas companhias que ela mantém" (tradução de Firth, 1957). O coneito central é que palavras que aparecem em contexto semelhantes tendem a ter significados semelhantes.

- **Vector Semantics**: em vez de definir palavras com dicionários, definimo-las como vetores (pontos num espaço multidimensional). Se "café" e "chá" aparecem perto de "beber" e "chávena", os seus vetores estarão próximos no espaço.

### 3. Vetores Esparsos: TF-IDF e PPMI
- **Term-Document Matrix**: uma matriz inde as linhas são palavras e as colunas são documentos. O valor em cada célula indica a frequência da palavra naquele documento.

- **TF-IDF (Term Frequency-Inverse Document Frequency**: uma métrica de peso que dá importância a palavras que são frequentes num documento mas raras no resto do corpus. Serve para ignorar palavras como "o" e "e".

- **PPMI (Positive Pointwise Mutual Information)**: uma alternativa à simples contagem de palavras. Mede o quanto a ocorrência de duas palavras juntas é mais provável do que se fosse por puro acaso.

- **Sparse Vectors:** estes vectores são "esparsos" porque a maioria das células é 0 (zero) (uma palavra não aparece na maioria dos documentos).
### 4. Vectores Densos: Word Embeddings
- **Embeddings**: Ao contrário dos vetores esparsos (que podem ter 50.000 dimensões), os embeddings são **dense vectors** curtos (geralmente de 50 a 300 dimensões) onde todos os valores são número reais (não apenas zeros).
- **word2vec**: um framework popular para aprender embeddings. O modelo baseia-se em prever o contexto de uma palavra.
- **Skip-Gram With Negative Sampling (SGNS)**: em vez de prever a palavra seguinte, o modelo aprende a distinguir se um par de palavras (ex.: "moeda" e "banco") é um par real de texto ou um par aleatório (**negative sampling**). A SGNS é um modelo mais refinado e a diferença entre este e o modelo anterior, **Bag of Words (BOW)**, é o facto de a SGNS estar desenhada para predizer o contexto a partir de uma palavra como input, e o BOW aprende a predizer uma palavra através do contexto.

> Ex.: um vetor para "rei" pode ser algo como [0.1, -0.5, 0.9,...].

#### A diferença entre as dimensões de vetores esparsos e vetores densos
No geral, uma dimensão é, essencialmente, um eixo no espaço (x,y,etc). Contudo, o seu signficado linguístico depende do tipo de vetor.
- **Vetores Esparsos (50.000 dimensões)**: no modelo de matriz termo-documento ( como o TF-IDF), cada dimensão corresponde a um **documento** ou a uma **palavra específica** do vocabulário. Se o corpus tem 50.000 palavras diferentes, cada palavra será representada por um vetor com 50.000 números. Há duas matrizes diferentes: a **matriz termo-termo**, cujas dimensões referem-se ao número de palavras totais diferentes num determinado corpus; a **matriz termo-documento**, cujas dimensões referem-se ao número total de documentos em comparação.
- **Vetores Densos (300 dimensões)**: aqui, as dimensões são abstratas. Não representam uma palavra específica, e sim "traços semânticos" que o computador aprendeu sozinho. Uma dimensão pode ser (invisivelmente) representar "realeza", outra "género", outra "pluralidade". O número 50.000 passa para 300 porque "comprimimos" a informação, forçando o modelo a encontrar as características mais importantes que definem o significado.
### 5. Semelhança de cosseno (cosine similarity)
O *cosine similarity* serve para medir quão parecidas são duas palavras, medindo o cosseno do ângulo entre os dois vetores.
Nos resultados dos cálculos, um valor de 1 entre dois vetores significa que as palavras são idênticas em contexto; 0 significa que não têm relação.
### 6. Analogias e Propriedades dos Vetores
- **Vector Analogies**: uma das propriedades mais famosas dos embeddings é a capacidade de resolver analogias através de aritmética vetorial.
> Ex.: *king - man + woman = queen*
> Isto mostra que o vetor captur a "essência" de género e realeza de forma matemática.
- **Bias (Viés)**: O capítulo alerta para o facto de que, como os modelos aprendem com textos humanos, podem herdar preconceitos sociais (ex.: associar "médico(a)" a homens e "enfermeiro(a)" a mulheres).
### 7. Avaliação de Embeddings
- **Intrinsic Evalutation**: testar os vetores em tarefas de semelhnça de palavras (comparar o score do computador com o de humanos) ou testes de analogia.
- **Extrinsic Evaluation**: usar os embeddings numa tarefa real (como análise de sentimentos ou tradução automática) e ver se o desempenho do sistema melhora.
---
## Dependency Parsing
Cap. 19, Jurasky & Martin (3ª ed.)

### 1. Dependecy Relations
**Dependensy grammar/dependency structure** descreve a sinteaxe como um conjunto de **relações binárias assimétricas** entre palavras:
- um **head** (também chamado "*governor*");
- um **dependent** (também chamadp "*modifier*").

Cada relação é representada por um **arco dirigido** do head para o dependent e normalmente vem **rotulada** com um tipo de relação gramatical (ex.: sujeito, objeto, modificador nominal, etc).

Muitas análises computacionais assumem a estrutura como uma **dependency tree** (árvore de dependências), frequentemente com um token artificial **ROOT** . A restrição mais usada no capítulo (motivada computacionalmente) é a de **àrvores enraizadas** (*rooted trees*), com estas condições (em termos de grafo dirigido):
- existe um único ROOT sem arcos de entrada;
- com exceção do root, cada palavra tem **exatamente um arco de entrada** (logo, **um único head**). Ou seja, cada palavra da frase só pode ser associada por um head e um só;
- existe um **caminho único** do root para cada nó (estrutura conectada).

Estas restrições garantem **single-headedness**, conectividade e um único ponto de ancoragem. A relação é **assimétrica** porque um head pode doar um arco a mais de 1 dependent, mas um dependent só pode receber um arco de um único head.

Outro conceito central é **projectivity**: uma árvore é **projective** se **não tiver arcos cruzados** quando as palavras estão na ordem linear (em português é da esquerda para a direita). Árvores **non-projective** permitem cruzamentos (úteis para certos fenómenos e línguas com ordem mais livre), mas tornam a inferência/os algoritmos mais exigente(s).

O capítulo usa como referência de rótulos gramaticais um conjunto de **dependency relations** ao estilo **Universal Dependencies** (ou muito próximo), ilustrando com exemplos típicos (head e dependent no exemplo):

A preto: head
A itálico: dependent
- Nominal Subject (NSUBJ): **United** *canceled* the flight.
- Object (OBJ): United **deviated** the *flight* to Reno. / We **booked** her the *flight* to Miami.
- Indirect Object (IOBJ): We **booked** *her* the flight to Miami.
- Compound (COMPOUND): We took the *morning* **flight**.
- Nominal Modifier (NMOD): (...) **flight** to *Houston*. 
- Adjectival Modifier (AMOD): Book the *cheapest* **flight**.
- Appositional Modifier (APPOS): **United**, a *unit* of UAL, matched the fares.
- Determiner (DET): *The* **flight** was canceled. / *Which* **flight** was delayed?
- Conjunction (CONJ): We **flew** to Denver and *drove* to steamboat.
- Coordinating Conjunction (CC): We flew to Denver *and* **drove** to steamboat.
- Case Marking (CASE): Book the flight *through* **Houston**.

>**Ideia-chave**:  ao contrário de **constituency parsing**, dependência **não codificam diretamente** constituintes grandes (NP, VP, etc); codificam primariamente quem depende de quem. Isto costuma ser muito útil a jusante (IE, semantic parsing, QA), porque  liga diretamente predicados e argumentos/modificadores.
### 2. Transition-Based Dependency Parsing
**Transition-based parsing** constrói uma árvore de dependências ao percorrer a frase e ao aplicar uma sequência de **ações (transições)** num estado incremental (de desenvolvimento). É tipicamente um método **greedy** (embora existam variantes como *beam search*), muito rápido.
Uma configuração (*state/configuration*) costuma ser um triplo:
- **stack** (pilha): palavras já parcialmente processadas;
- **buffer** (fila): palavras ainda por processar;
- **arc set** (A): arcos já construídos.

O estado inicial comum coloca o **ROOT** na pilha e todas as palavras no buffer; o estado inicial tem buffer vazio (e um conjunto de arcos que forma a árvore).

O capítulo descreve sistemas do tipo **shift-reduce**, muito usados, com ações como:
- **SHIFT**: move o primeiro item do buffer para o topo da stack;
- **LEFT-ARC(r)**: adiciona o arco do topo da stack (head) para o item abaixo (dependent), com rótulo (r), e remove o dependent da stack (na versão arc-standard típica);
- **RIGHT-ARC (r)**: adiciona um arco do item abaixo (head) para o topo (dependent), com o rótulo (r), e remove o dependent (ou head) conforme a variante.

(os detalhes exatos de "quem é removido" dependem do sistema: **arc-standard, arc-eager**, etc; a ideia constante é: SHIFT empilha palavras e ARC cria dependência e reduz elementos quando já tem o seu head decidido.)

O parser aprender um **classificador** que, a cada configuração, escolhe a melhor ação. Tradicionalmente, isto foi feito com **features** desenhadas à mão sobre palavras/POS e contexto na stack/buffer; depois, passou a ser feito com redes neuronais.

#### **Modelos e scoring**
O objetivo é escolher a sequência de transições que maximize a pontuação/probabilidade:
- pode ser vista como uma tarefa de classificação por passo (qual transição aplicar agora);
- pode usar aprendizagem supervisionada a partir de treebanks convertidas em sequências de transições (usando um oracle).

Pontos fortes: rapidez, boa precisão prática.
Pontos fracos: **erros propagam-se** (greedy), e algumas estruturas (ex.: não projetivas) exigem extensões (como transições adicionais, swap, ou sistemas específicos).
### 3. Graph-Based Dependency Parsing
Aqui, a frase é vista como um grafo completo (ou quase) de possíveis arcos i->j, e o parser escolhe a árvore global com maior score, em vez de construir incrementalmente.
#### Formulação como otimização
Define-se uma pontuação para cada arco candidato (ex.: somando scores locais) e procura-se a árvore (T) que maximize essa soma sujeita às restrições de uma **árvore enraizada** (um head por palavra, concectividade via root, sem ciclos).

Isto leva a um problema clássico: **Maximum Spanning Tree (MST)** em grafos dirigidos (cuborescência máxima, com algoritmos como o **Chuliu/Edmonds**) para o caso **projective**, há algoritmos de programação dinâmica (como Eisner) que exploram a restrição de não cruzamento.

#### Features vs. neural scoring
O capítulo contrasta:
- Abordagens clássicas: desenhar **features** para cada arco (palavras, POS, distâncias, direção, contexto) e aprender um modelo linear/CRF-like para scores;
- Abordagens modernas: **neural graph-based parsers**, onde, em vez de features manuais, se usa um **encoder** (ex.: biLSTM/Transformer) que produz representações contextualizadas de cada palavra, e um **scorer** (ex.: um MLP biaffine) que estima s (i->j) para cada par (i, j).
---
## Phonetics and Speech Extraction
### 1. Acoustic Phonetics and Signals
Conceitos-base:
- **waveform**: amplitude ao longo do tempo;
- **sampling rate**: (taxa de amostragem) e a ideia de discretização em amostras;
- **frequency** (Hz), **period**, e relações básicas para ondas;
- **amplitude**, **power** e **intensidade** (em dB), com fórmulas que aparecem no capítulo:
RM amplitude = $\sqrt {\frac{1}{N}}\times(X_1²+X_2²+...+X_n²)$
Power = $\frac{1}{N}\times(X_1²+X_2²+...+X_n²)$
Intensity = $10 \times log_{10}  ((\frac {1}{N\times P_o})\times(X_1²+X_2²+...+X_n²))$
$P_o$ (limiar auditivo de pressão): $2 \times 10^{-5}$ Pa
### 2. Feature Extraction for Speech Recognition: Log Mel Spectrum
Esta é a parte central do capítulo: transformar o áudio em vetores de features robustos e informativos para reconhecimento automático.

#### Pipeline base (visão geral)
1. **Pre-emphasis** (frequentemente usado): filtro simples para realçar altas frequências;
2. **Framing**: dividir o sinal em **frames** curtos (tipicamente ~25ms) com **hop** menor (ex.: 10ms), para capturar a dinâmica temporal;
3. **Windowing**: aplicar uma janela (ex.:**Hamming window**) a cada frame para reduzir descontinuidades nas bordas.
4. **Spectral Analysis**: calcular o espectro do frame com **DFT** (na prática, FFT).
5. **Mel filterbank**: agrupar energia em bandas na escala **Mel** (aproximando a perceção humana de frequência).
6. **log compression**: aplicar log à energia por banda -> **log Mel spectrum** (aproxima perceção da intensidade e ajuda a estabilizar variações multiplicativas).
#### Discrete Fourier Transform
O capítulo destaca a **Discrete Fourier Transform (DFT)** como ferramenta para extrair quanta energia existe em diferentes bandas de frequência num sinal discreto (digital). É o passo que converte cada frame (tempo) num vetor no domínio da frequência.
#### Mel Scale e filtros
A **Mel Scale** aproxima a sensibilidade auditiva: maior resolução em baixas frequências, menos em altas. O resultado do filtro é um vetor de energias por bandas **log** dá o **log Mel spectrum**, muito usado diretamente no ASR moderno (e também como base para MFCC).
### 3. MFCC: Mel Frequency Cepstral Coefficients
Os **MFCC** são uma compressão/transformação adicional sobre o log Mel spectrum.

Passos típicos:
1. Começa-se com o log Mel spectrum;
2. Aplica-se uma **Discrete Cosine Transform (DCT)** ao vetor log-Mel para obter coefficientes no domínio "cepstral": os **cepstral coefficients**.
3. Mantém-se apenas os primeiros coeficientes (baixas "frequências cepstrais", que capturam a envolvente espectral mais relevante e reduzem dimensionalidade e correlações).
O capítulo liga isto à ideia de **cepstrum** (representação útil para separar efeitos do trato vocal vs. excitação, em termos práticos: capturar a forma do espectro). Em pipelines clássicas, MFFCs costumam ser complementados com:
- **delta** e **delta-delta** (derivadas temporais) para a dinâmica;
- normalizações por locutor/canal (dependendo do setup).
---
# Reconhecimento Automático de Fala
Cap. 15, Jurafsky & Martin (3ª ed.)
## 1. O Modelo de Canal Ruidoso e a Regra de Bayes?
O ponto de partida fundamental para entender como um computador "ouve" é o conceito  de **Canal Ruidoso**. A fala é uma sequência de palavras pura que, ao passar pela garganta e pelo ar, se torna um sinal ruidoso. O objetivo do sistema é fazer o caminho inverso: descobrir a sequência de palavras $W$ mais provável de ter gerado o áudio observado $O$. Para isso, utilizamos a **Regra de Bayes**, que divide o problema em dois grandes vetores:
- **Modelo Acústico**: $P(O/W)$, foca-se nos sons;
- **Modelo de linguagem**: $P(W)$, foca-se na probabilidade de as palavras existirem naquela ordem na língua.
## 2. Do som à imagem: o especrograma
Um computador não consegue processar uma onda sonora diretamente como nós. O áudio precisa de ser fatiado em pequenos pedaços (**frames**) de cerca de 25ms. Cada pedaço é transformado num **espectrograma** - uma representação visual que mostra a energia em diferentes **frequências** ao longo do tempo. Na prática, o sistema de ASR "vê" o som antes de o traduzir.
A **attention** resolve o problema de o sistema se perder em áudios longos, permitindo-lhe "olhar" para a parte certa do sinal.
## 3. Alinhamento temporal e o Método CTC
Um grande obstáculo no ASR é que o ritmo da voz não é constante - podemos dizer "olá" em meio segundo ou em dois segundos.
Como é que o sistema sabe quando acaba uma letra e começa outra? Usamos o algoritmo **Connectionist Temporal Classification (CTC)**. Este método introduz um símbolo espectral chamado **blank**, que serve para preencher os espaços entre os sons detetados.
>Ex.: se o sistema ouvir "casa", ele pode gerar internamente `cccaaa---sss---aa`. O algoritmo CTC remove as letras repetidas e os símbolos `blank`, entregando a a palavra limpa: casa.

Sem o CTC, teríamos de marcar manualmente cada milissegundo de áudio com a letras correspondente, o que seria impossível de fazer em larga escala.
## 4. Medindo a eficácia com o Word Error Rate (WER)
Para saber se um sistema de reconhecimento de fala é realmente bom, comparamos a sua resposta com uma transcrição humana. A métrica padrão é p **Word Error Rate (WER)**. Esta fórmula contabiliza 3 tipos de falhas:
- **Substituição** (trocar "gato" por "rato");
- **Inserções** (adicionar palavras que não estão lá);
- **Eliminações** (eliminar palavras).

O cálculo é feito da seguinte forma:

$WER = \frac{subst.+inser.+elimin.}{\text{nº of words spoken}}$

Esta fórmula é baseada na métrica chamada **Lavenshtein distance** - a diferença entre duas "strings" (palavras, por exemplo). A WER varia de 0 a 1, onde:
**0** -> as *strings* comparadas são exatamente iguais.
**1** -> as *strings* comparadas são exatamente diferentes.
## 5. A evolução dos sistemas: Do HMM ao End-to-End
Antigamente, o reconhecimento de fala não era feito por uma única rede. Utilizava-se o chamado **pipeline clássico**, que dividia a tarefa em 3 componentes independentes: o modelo acústico, o modelo de pronúncia (um dicionário de fonemas) e o modelo da linguagem. O motor principal era o **Hidden Markov Models (HMM)**, que tentava adivinhar o estado "escondido" (neste caso, a palavra) e partir do som visível.
Atualmente, a tendência é o End-to-End Deep Learning, onde um único modelo neuronal aprender a converter o áudio em texto diretamente, sem precisar de um dicionário de pronúncia feito por humanos.
## 6. A ciência por trás do som: MFCC e Transformadas
Antes do áudio chegar à rede neuronal, ele sofre uma transformação matemática. O capítulo detalha o processo de extração de **Coeficientes Cepstrais em Frequência de Mel**.
1º. **Windowing**, em que o sinal é cortado em fatias minúsculas.
2º. Aplica-se a **Discrete Fourier Transform (DFT)**.
3º. As frequências resultantes da DFT são filtradas pela Escala de Mel, que dá mais importância aos sons que o ouvido humano realmente distingue.
## 7. Arquiteturas de Elite: Conformer e Whisper
O capítulo destaca o **Conformer**, que é atualmente uma das arquiteturas mais potentes. O Conformer combina o melhor de dois mundos: as **Redes Neuronais Convolucionais (CNNs)**, que são ótimas a captar padrões sonoros locais (como um som de uma consonante), e os **Transformers**, que são mestres em entender o contexto global da frase. Outro destaque é o modelo **Whisper**, treinado com um volume de dados massivo (680 mil horas), oque o torna incrivelmente resistente ao ruído de fundo e aos sotaques diferentes.
## 8. A procura pela melhor frase: Beam Search
Quando o modelo termina de processar o som, ele precisa de decidir qual é a frase final. Em vez de escolher apenas a palavra mais provável em cada passo (o que seria um erro se a primeira palavra estivesse errada), o sistema usa o **Beam Search**. Assim, o sistema mantém várias hipóteses em aberto simultaneamente - o **Beam Width** - e vai avaliando as menos prováveis à medida que avança.

> Ex.: se o sistema ouve algo que parece "casa" ou "caixa", ele mantém ambas as opções. Se as palavras a seguir forem "de cartão", e probabilidade de "caixa" sobre e o sistema descarta "casa".
---
# Text-to-Speech (TTS)
Cap. 16, Jurafsky & Martin (3ª ed.)
## 1. A estrutura de um sistema TTS
Um sistema de TTS moderno é geralmente dividido em duas grandes partes:
1. **front-end**, de análise de texto, que transforma o texto bruto em representações linguísticas (como fonemas e entoação).
2. **back-end**, de síntese de áudio, que pega nessa entoação e gera a onda sonora final que ouvimos.
## 2. O desafio da Normalização de Texto
O primeiro passo é a normalização de texto. O computador precisa de decidir como ler símbolos que não são palavras. Por exemplo, como ler "1997"? Pode ser um número cardinal ou um ano. O sistema usa regras e modelos para expandir abreviaturas e símbolos de forma correta.

>Exs.: "O Dr. vive na Av. Brasil" -> "O Doutor vive na Avenida Brasil"

## 3. De letras a sons: Grapheme-to-Phoneme (G2P)
Depois de normalizado, o texto precisa de ser convertido em fonemas. Este processo chama-se Grapheme-to-Phoneme. O maior problema aqui são as palavras homógrafas, palavras que se escrevem da mesma forma, mas têm pronúncias diferentes.
Para resolver isto, o sistema atribui uma probabilidade à pronúncia correta baseada na classe gramatical da palavra.
## 4. Prosódia: a melodia da fala
A fala humana não é plana; os modelos tentam prever o $F_0$ 
(frequência fundamental), que define o tom da voz. A duração de cada fonema (d) pode ser modelada matematicamente para que a fala soe natural:

$d_i = modelo(L_i, C_i)$, onde

$L_i$ representa o fonema
$C_i$ representa o contexto (se está no fim da frase ou se é uma sílaba tónica)
## 5. Vocoders e Redes Neuronais
No passado, usavamos a **síntese por concatenação**, que era basicamente "colar" pedaços de gravações humanas. Hoje, usamos **Vocoders Neuronais**, como o WaveNet ou Hi-Fi GAN. Estes modelos geram o áudio amostra por amostra, garantindo uma "textura vocal" muito realista. Os sistemas modernos são **End-to-End**, como o Tacotron 2 ou o FastSpeech. Eles recebem o texto e, através do mecanismo de attention, geram diretamente um espectrograma que o Vocoder transforma o som.
## 6. Avaliação: o teste do ouvido humano
Ao contrário do ASR, em que medimos erros de palavras, no TTS, a avaliação é subjetiva. A métrica principal é o **MOS (Mean Opinion Score)**. Pedimos a humanos para darem uma nota de 1 a 5 à fala sintetizada, avaliando 2 critérios:
- **Inteligibilidade**: conseguimos perceber o que foi dito?
- **Naturalidade**: soa como um ser humano ou como uma máquina?

$MOS = \frac{1}{N}\times\sum_{n=1}^N \times R_n$, em que

$R_n$ é a classificação dada por cada avaliador
$N$ é o número total de avaliadores

Um MOS acima de 40 é considerado excelente e muito próximo da fala real humana.

---
# Extração de Informação (IE)
Cap. 20, Jurafsky & Martin (3ª ed.)
## 1. Transformar texto em dados
O grande objetivo da Extração de Informação (IE) é identificar **quem** fez **o quê**, **a quem**, **onde** e **quando**. Enquanto um humano lê uma frase e percebe o contexto, o computador precisa de converter isso em triplos (entidade 1, relação, entidade 2). Uma **entidade** é um objeto do mundo real, como uma pessoa, empresa ou local. Uma **relação** é o que as une.

>Ex.: "A Samsung tem sede em Seul" -> sede_em(Samsung, Seul)

## 2. Extração de relações
Existem várias formas de ensinar um computador a encontrar relações entre entidades:
- **Padrões de Hearst**: são padrões linguísticos simples que indicam quase sempre uma relação de "tipo-de" (hiponímia).
>Ex.:"... frutos tais como **maçãs** e **peras**" indica que *maçã* é um tipo de fruto. O padrão é **X tal como (y,z)**

- **Supervisão Distante**: em vez de marcar milhare de frases à mão, usamos uma base de dados já existente (como a Wikipédia) para ensinar o modelo.
>Ex.: se sabemos que o **Steve Jobs** fundou a **Apple**, o computador procura todas as frases onde estes dois nomes aparecem e aprende os padrões de escrita que indicam **fundação**.
- **Extração de relações com redes neuronais**: hoje usamos modelos como o **BERT** para classificar a relação entre duas entidades numa frase, analisando o contexto que as rodeia.
## 3. Extração de eventos e tempo
O capítulo explica que não basta saber *quem*, é preciso saber *quando*. A **extração de eventos** identifica ações como *casamentos*, *eleições* ou *ataques informáticos*. Para isso, usamo o sisema **TimeML**, que serve para anotar o tempo de forma que o computador entenda.
As entidades temporais são chamadas de **TIMEX3**.

>Ex.: "No dia **12 de maio**" torna-se uma expressão normalizada que o computador guarda como **2026-05-12**.

Para relacionar eventos no tempo, usamos a lógica de que um evento pode ser:
- **antes** de outro;
- **simultâneo** a outro;
- **depois** de outro.

Sem a extração temporal, o computador não saberia se a **Nokia** *é* ou *foi* líder do mercado.
## 4. Template filling (Preenchimento de Moldes)
Esta é a aplicação mais prática da IE. Imaginemos que uma empresa quer monitorizar notícias sobre compras de empresas. O sistema tem um **template** (molde) vazio:
- comprador:
- adquirido:
- valor:
- data:

O computador lê a frase "A **Microsoft** comprou a **Activision** por **69 mil milhões** em **2022**" e preenche automaticamente os espaços. O **template filling** é essencial para o setor financeiro, em que a velocidade de extração de dados pode valer milhões.
## 5. Avaliação do sistema
Como medimos se a extração foi bem sucedida? Usamos 3 métricas principais: **precisão**, **recall** e o **F1-score**.
- Precisão (P): de todas as relações que o sistema extraiu, quantas estavam certas?
- Recall (R): de todas as relações que existiam no texto, quantas é que o sistema conseguiu encontrar?
- F1-score: uma medida que equilibra as duas anteriores.

$P=\frac{Acertos}{\text{Total Extraído}}$; $R=\frac{\text{Acertos}}{\text{Total existente no texto}}$; $F_1 = \frac{2\times P\times R}{P+P}$

>Ex.: se o texto tem 10 relações e o sistema encontra 8, mas apenas 4 questões certas, o recall é $0,8$ (80%) mas a precisão é apenas $0,5$ (50%).

---
# Semantic Role Labeling - SRL
Cap. 21, Jurafsky & Martin (3ª ed.)

## 1. A estrutura de argumentos do predicado
No centro da semântica de uma frase está o **predicado** (geralmente um verbo). Para compreender o significado, o computador precisa de identificar os seus **argumentos**. Por exemplo, no verbo "dar", é necessário haver alguém que dá, algo que é dado é alguém que recebe.
- **agente**: o iniciador consciente da ação. Ex.: *O **João** abriu a porta*.
- **paciente**: a entidade que sofre a ação ou muda de estado. Ex.: *O João abriu **a porta***.
- **instrumento**: a ferramenta usada para realizar a ação. Ex.: *Ele abriu a porta com **uma chave***.
Estes são chamados de **Papéis Temáticos**.
## 2. PropBank: papéis específicos por verbo
Como os papéis temáticos gerais (agente, paciente) podem ser ambíguos, o projeto **PropBank (Preposition Bank)** criou uma forma de rotular argumentos de forma numerada para cada verbo específico:
- **Arg0**: geralmente o agente ou experimentador;
- **Arg1**: geralmente o paciente ou tema;
- **Arg2**: frequentemente o beneficiário ou instrumento.

Exemplo para o verbo "vender":
"**A empresa** (Arg0) vendeu o **software** (Arg1) ao **governo** (Arg2)"

O **PropBank** evita discussões filosóficas sobre o que é um "agente", focando-se apenas em como os argumentos se comportam com aquele verbo específico.
## 3. FrameNet: a teoria dos enquadramentos
O FrameNet é outra base de dados fundamental que organiza o conhecimento em **frames** (enquadramentos). Um frame é uma situação esquemática (como "comércio" ou "julgamento") que envolve vários elementos.

No frame de **comércio**, temos elementos como *Comprador*, *Vendedor*, *Mercadoria* e *Preço*. Verbos diferentes podem ativar o mesmo frame (ex.: "comprar", "vender", "custar" ativam todos o mesmo contexto de comércio).

Enquanto o PropBank se foca no verbo individual, o FrameNet foca-se na situação global, permitindo que o computador relacione palavras diferentes que descrevem o mesmo cenário.
## 4. Sistemas Automáticos de SRL
Para um computador atribuir estes papéis automaticamente, ele utiliza hoje **Redes Neuronais Profundas** (como Bi-LSTMs ou Transformers). O sistema recebe a frase e, para cada verbo encontrado, atribui uma etiqueta de papel a cada **segmento** da frase.

A pontuação para um determinado papel *r* num argumento *a* dado um predicado *p* pode ser vista como uma finção de probabilidade.

O sistema analisa o caminho na árvore sintática entre o verbo e a palavra para decidir se ela é o sujeito (geralmente Arg0) ou o objeto (geralmente Arg1)

