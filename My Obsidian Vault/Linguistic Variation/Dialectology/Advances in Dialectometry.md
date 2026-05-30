From [*Advances in Dialectometry*][https://www.annualreviews.org/content/journals/10.1146/annurev-linguist-030514-124930].

# Introduction

Dialectometry is a field that studies dialects using mathematics and computer science. Instead of assuming that dialects have fixed borders, today's researchers know that language changes gradually from one region to another (like a slope) or spreads in small, isolated communities.

The researcher Séguy, one of the pioneers, passed away in a car accident, but his work was continued by Hans Goebl. Together, they are seen as the founders of this field. Goebl focused on Romance languages (like Portuguese and French) and introduced major innovations, such as Thiessen tiling, the use of inverse frequency weightings, descriptive statistics, and cluster analysis.

>  **Thiessen tiling** is just a geometric method used to draw areas on a map around the places where data was collected. A "tile" is drawn around each village so that any point inside that space is physically closer to that village than to any other. This helps draw automatic boundaries around speakers. On the other hand, **inverse frequency weighting** serves to balance words: if a word is very common and everyone uses it, the system reduces its importance in the analysis; if it is a rare word, it gains more weight because it helps show what makes a region unique. Finally, **cluster analysis** is a technique that groups similar data. The computer looks at thousands of words and automatically groups towns with similar accents into clusters, saving researchers from the work of analyzing word by word by hand. Goebl also advocated for the use of computers in this field from a very early stage (Goebl 1982b).

Another major innovation was **edit distance** (or Levenshtein distance), first used by Kessler (1995). This is a calculation that counts how many letters or sounds we need to change to turn one word into another (for example, turning "porta" into "puorta"). Shortly after, Embleton (1993) applied the **Multidimensional Scaling (MDS)** technique to dialectometry.

> MDS functions as a visual simplifier. It takes a massive, confusing table filled with the differences between every single town and turns those numbers into a simple 2D or 3D graph. This way, regions with similar dialects sit physically close to each other on the chart, making the results easy to understand at first glance.

# Related work

Many researchers try to understand the exact degree to which people speaking different dialects can actually understand one another. Wieling and his team (2014a) used edit distance to study foreign accents and compared the computer's results with ratings given by real people. They discovered a very strong correlation (_r_ = 0.8) using a logarithmically transformed version of the edit distance metric.

> This **r** is Pearson's Correlation Coefficient, which measures the strength of the connection between two variables on a scale from -1 to 1. A score of 0.8 is a giant positive connection, meaning the computer's calculations match human perception almost perfectly. The **logarithmic transformation** is just a mathematical adjustment used to flatten data when there are extreme variations, preventing a single highly unusual accent from ruining the study's overall average.

The same researcher (Wieling, 2014c) later compared this edit distance system with another model based on how humans learn. Both methods showed very similar performance. This proves that when we analyze many words together to create an average, the exact mathematical method we choose does not drastically change the final result.

In other studies, Sanders and Chin (2009) used edit distance to measure speech deviations in people with cochlear implants, and Kondrak (2013) used another method (longest common subsequence ratio) to find words with similar spellings in different languages, helping to identify automatic translations.

# Recent advances in dialectometry

Looking at the big picture, the breakthroughs of the last five years have focused on:
- discovering which specific words and sounds drive the most differences between dialects;
- realizing that social factors (like age or social class) and the type of vocabulary actively shape the geography of language;
- creating new ways to measure how dialects change over time;
- evolving the core theories of dialectology;
- paying closer attention to grammar and sentence structure within dialects;
- using new data sources from the internet instead of relying only on old printed linguistic atlases;
- creating apps and websites so that any researcher can use these statistical tools easily.

Dialectometry has been criticized in the past for looking too much at the general map while forgetting the individual words that cause those patterns (Schneider 1988, Woolhiser 2005). To solve this, new approaches emerged based on **Principal Component Analysis (PCA)** and **Factor Analysis**.

> Both PCA and Factor Analysis serve to reduce and simplify mountains of data. PCA takes hundreds of word variations and summarizes them into a few "principal components" that explain most of the differences. Factor Analysis goes a step further and tries to find a hidden force (a "factor") that causes several different words to change the same way across the map. In practice, they help researchers notice which sounds or words always go together in the same regions.

Pröll and his team (2014) used Factor Analysis to draw maps of variation. To display these factors on a single map, they gave each location a specific color (based on the strongest factor) and a specific intensity (based on the strength of that factor).

>**Factor strength** (or _factor loading_) works like a connection score between a specific town and the accent being studied. A high score means the town is the perfect example of that dialect. The map gets divided into colored zones, and the authors explain that we should look at the darkest, most intense centers of each color to understand the dialect, rather than at the border lines.

Another idea was proposed by Pröll (2013, 2014), based on dialectometric intensity estimation. This method takes a single word from an atlas and cleans up any random anomalies on an "area class map." Then, he applies **fuzzy clustering** to understand the underlying patterns.

>*Fuzzy clustering* is a flexible grouping algorithm where data points do not have to belong 100% to a single side. Instead of declaring that a town belongs entirely to Dialect A, this method calculates probabilities. A border town can be classified as 70% Dialect A and 30% Dialect B, which matches real-world language blending much better.

This intensity method fixes the issue where linguistic atlases suffer from small errors (sometimes the interviewed speaker had a personal quirk or accent that did not represent the whole town). The computer analyzes the villages within a certain radius around the central point and calculates the probability of a word being used there. If neighbors use the same word, the probability goes up; if they use a different one, the probability drops and the system corrects the map. Essentially, this acts as a data "smoother" to wipe away random errors. The final map uses colors and intensities to show these probabilities. Additionally, researchers can extract complexity and homogeneity (similarity) scores from these maps (Pickl, 2013).

Grieve (2011) and Lameli (2013) created **multivariate spatial analyses**, which do something similar. Grieve wanted a mathematical way to recreate old maps that were drawn by tracing separation lines (isoglosses) by hand. He proved that this computational analysis finds much more detailed patterns because it successfully cleans "noise" from the dataset.

> From a statistical perspective, **multivariate spatial analysis** simply means analyzing many geographic variables at the exact same time on the map. The **noise** refers to those random errors we mentioned earlier (like a single person using a very strange word that nobody else in the area uses). The computer model filters out these errors so they do not ruin the average.

Wieling and Nerbonne (2009) created a way to discover regional dialect groups and the exact words that cause them at the same time. They borrowed a computer science technique called **bipartite spectral graph partitioning**. Later, they adapted the method to allow for **hierarchical clustering** (2010) and created a formula to rank the most important sound correspondences in each group (2011a).

 > *Bipartite spectral graph partitioning* works like a network that connects two different types of data at the same time: places and words. The system cuts the network at the perfect points to split the map into regions and, in the exact same step, tells you which words define each region. **Hierarchical clustering** organizes these groups like a family tree, showing how large regions later split into smaller, local sub-dialects.

Kretzschmar (2012) argues that speech changes constantly and that the distribution of different words follows a non-linear curve (the Zipf-curve or A-curve). This means there are only one or two highly popular words that everyone uses, alongside a huge number of rare words that almost nobody uses. Recently, the **Gini coefficient** (borrowed from economics) was introduced to measure the shape of this curve.

> **Gini coefficient** is used in economics to measure income inequality between the rich and the poor, ranging from 0 (perfect equality) to 1 (perfect inequality). In linguistics, a high Gini score proves that word distribution is highly "unequal," meaning people heavily prefer using the exact same word and leave other options aside. This helps researchers see if their study categories are too restrictive or if they reflect reality.

Wieling (2012) also brought sociology and dialectometry closer together using large regression models. He used **generalized additive mixed-effects regression modeling (GAMM)**, which manages to combine real 2D geographic coordinates, people's social traits, and the way these elements influence each other into a single calculation.

> GAMMs are incredibly powerful prediction tools. While normal regressions can only draw straight lines on graphs, GAMMs can draw complex, flexible curves to follow the actual reality of the map. The "interaction" means the model calculates how geography and society multiply each other's effects. For example, it can show that a speaker's age changes their way of speaking differently if they live in a big city versus an isolated mountain village.

Researchers also calculate how much of an accent is caused purely by physical distance. Heeringa and Nerbonne (2001) compared clearly divided areas against areas that change gradually, and Shackleton (2007) used distance and borders inside a multiple regression setup.

For years, there were two standard computer programs in this field. VisualDialectoMetry (VDM), made at Salzburg University, and RUG/L04, made at the University of Groningen. Both perform general aggregate analyses and create maps. RUG/L04 focused on mapping differences in pronunciation using edit distance, while VDM focused on vocabulary and grammar differences.

Later, 'Gabmap' was created, which is an online and much more user-friendly version of the old RUG/L04. Gabmap runs on the web and accepts text data (words) or numerical data (sound frequencies), calculating pronunciation differences. It also has tools to catch typing errors and view maps for individual words. Large divisions on the map can be studied using cluster analysis and MDS, allowing researchers to compare both results on the screen. Another similar web application is DiaTech (Aurrekoetxea et al. 2013), which functions more like VDM and focuses on analyzing situations where a single resident or location uses several different words for the exact same thing.