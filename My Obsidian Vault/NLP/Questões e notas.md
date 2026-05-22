>[! Pergunta]
>Retirar a pontuação e as stop words não pode confundir o parser, por haver falta de informação estrutural e de delimitação de frases?

A resposta curta é: **sim, retirar a pontuação e certas stop words pode destruir a capacidade do parser funcionar corretamente.**
É preciso distinguir entre "limpeza de ruído" e "simplificação excessiva":
 
- **A importância da pontuação para o Parser**: O parser depende de "âncoras" para entender a hierarquia da frase. Os pontos finais definem os limites da sentença, e as vírgulas indicam orações subordinadas ou enumerações. Se removeres toda a pontuação antes do parsing, o algoritmo verá apenas um fluxo contínuo de palavras, resultando numa árvore de dependências completamente caótica e errada.

- **O dilema das Stop Words**: Embora as stop words (como "o", "de", "com") sejam ruído para tarefas como a **Modelação de Tópicos**, elas são fundamentais para a **Análise Sintática**. Elas funcionam como conectores que indicam a relação entre termos. Por exemplo, na frase "O livro do João", a palavra "do" é a pista que o parser usa para ligar a posse ao sujeito. Sem ela, o parser teria dificuldade em estabelecer essa relação.

- **A estratégia da "Limpeza Inteligente"**: Nas pipelines modernas, a ordem é ajustada da seguinte forma:

	1. Faz-se uma **limpeza de ruído não linguístico** (remover tags HTML, links, caracteres de controlo, emojis se não forem relevantes).

	2. Mantém-se a pontuação e as stop words para realizar o **Parsing** e o **POS Tagging**.

	3. Só **depois** de extraída a estrutura gramatical é que se filtram as stop words ou a pontuação para tarefas que não precisam delas, como a vetorização para classificação ou modelos estatísticos.

Diferença entre abordagens Clássicas e Modernas:

- **Abordagem Clássica (ex: Bag of Words)**: Prioriza a remoção de tudo o que não seja "conteúdo" (substantivos e verbos) o mais cedo possível para reduzir a dimensionalidade.

- **Abordagem de Deep Learning (ex: Transformers/BERT)**: Quase não remove nada. Estes modelos aprendem que a posição de uma vírgula ou a presença de uma preposição altera completamente o sentido da frase, por isso o texto entra quase "bruto" no modelo.
