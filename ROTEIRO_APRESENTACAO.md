# 🎙️ Roteiro Oficial de Apresentação: Modelo Probabilístico de RI

> **Seminário de Recuperação de Informação (RI)**  
> **Tema:** O Modelo Probabilístico Clássico (Robertson & Sparck Jones, 1976)  
> **Apresentadores:** Matheus & Rafael  
> **Tempo Total Estimado:** 25 a 35 minutos + 5 a 10 minutos de perguntas / laboratório livre  
> **Interface de Apoio:** [Slides Online no GitHub Pages](https://rafaeldclemos.github.io/projetos/) ou `http://localhost:8080/teste_slides.html`

---

## 📋 Visão Geral e Estratégia de Apresentação

| Bloco | Slides | Apresentador | Foco Principal | Tempo Sugerido |
| :--- | :--- | :--- | :--- | :--- |
| **Bloco 1: Fundamentos** | 1 a 5 | **Rafael** | Introdução, Motivação, Conceito do Conjunto Ideal e Vetor Binário | ~4 min |
| **Bloco 2: Representação** | 6 a 8 | **Matheus** | Matriz de Documentos $d_1 \dots d_7$, Consulta $q$ e Termos | ~3 min |
| **Bloco 3: Função de Busca** | 9 a 11 | **Rafael** | Razão de Chances, Probabilidades Condicionais e Exemplo Intuitivo | ~5 min |
| **Bloco 4: Formalismo & Fórmulas** | 12 a 14 | **Matheus** | Tabela de Símbolos ($N, n, R, r$), Fórmulas RSJ, Somatório e Exemplo | ~5 min |
| **Bloco 5: 1ª Iteração (IDF)** | 15 a 17 | **Rafael** | Cálculo de IDFs ($N=7$), Cálculo de $\text{sim}(q, d_1)$ e 1º Ranking | ~4 min |
| **Bloco 6: 2ª Iteração (Feedback)**| 18 a 19 | **Matheus** | Feedback com $d_3$ e $d_5$, Ajuste de Amortecimento e Reordenação | ~5 min |
| **Bloco 7: Balanço Crítico** | 20 a 21 | **Rafael** | Vantagens (Otimalidade) e Desvantagens (TF, Separação, Tamanho) | ~3 min |
| **Bloco 8: Demonstração ao Vivo** | 22 | **Ambos** | Laboratório Interativo: Execução em tempo real, presets e simulação | ~6 min |

---

## 🎬 Roteiro Slide a Slide

---

### Slide 1: Capa
* **Apresentador:** **Rafael**
* **Tempo:** ~45 segundos
* **O que falar:**
  > *"Olá a todos, professor e colegas. Sejam muito bem-vindos ao nosso seminário de Recuperação de Informação.  
  > Meu nome é Rafael, e junto com o Matheus, vamos apresentar hoje o **Modelo Probabilístico de Recuperação de Informação**.  
  > Vamos entender como a teoria das probabilidades foi introduzida na RI para responder à pergunta clássica: dada uma consulta do usuário, qual é a chance real de determinado documento ser relevante?  
  > Ao longo da apresentação, passaremos pelos fundamentos teóricos, dedução matemática, exemplos passo a passo e, ao final, faremos uma demonstração prática em um laboratório interativo desenvolvido especialmente para o seminário."*
* **Dica de postura:** Fala calma, contato visual com a banca/sala. O slide é limpo e moderno.

---

### Slide 2: O Modelo Probabilístico
* **Apresentador:** **Rafael**
* **Tempo:** ~1 minuto
* **O que falar:**
  > *"Para contextualizar: o modelo probabilístico clássico foi formalizado em 1976 por Stephen Robertson e Karen Sparck Jones. Ele surgiu como uma alternativa elegante aos modelos vetoriais e booleanos.  
  > A premissa central é a seguinte:  
  > Primeiro: a partir da consulta formulada pelo usuário, existe no universo da coleção um subconjunto ideal de documentos que contém **exatamente** aqueles que atendem à sua necessidade, e nenhum outro.  
  > Segundo: o sistema não conhece esse conjunto perfeito de antemão. Por isso, a partir de interações sucessivas — o chamado feedback de relevância —, o modelo vai recalculando e redefinindo o ranqueamento, aprendendo quais termos têm maior peso para aquele usuário."*
* **Destaque visual:** Apontar para os dois tópicos da tela.

---

### Slide 3: Modelo Probabilístico (Conjunto Resposta Ideal)
* **Apresentador:** **Rafael**
* **Tempo:** ~1 minuto
* **O que falar:**
  > *"Reforçando esse conceito-chave: o modelo trata o problema de RI através de um arcabouço probabilístico rigoroso.  
  > O nosso alvo é o chamado **conjunto resposta ideal**.  
  > Como o sistema não tem bola de cristal para adivinhar a intenção humana na primeira tentativa, ele formula uma hipótese: estima a probabilidade de cada documento pertencer ao conjunto ideal medindo a sua similaridade probabilística com a consulta.  
  > É essa similaridade que vai ditar a posição de cada documento no resultado."*
* **Transição para o próximo:** *"Agora, como nós representamos esses documentos e termos dentro do computador? O Matheus vai nos mostrar a estrutura de indexação."*

---

### Slide 4: Termos de indexação
* **Apresentador:** **Matheus**
* **Tempo:** ~1 minuto
* **O que falar:**
  > *"Boa tarde a todos! A primeira pergunta que devemos responder é: quais termos de indexação conseguem de fato distinguir os documentos relevantes dos demais no corpus?  
  > Na primeira interação, as características do conjunto ideal são desconhecidas. Então, o usuário dá o pontapé inicial formulando uma consulta preliminar. Essa consulta gera a primeira descrição probabilística do conjunto resposta.  
  > A grande força do modelo probabilístico está na melhoria gradativa: conforme o usuário inspeciona os primeiros resultados e marca quais foram úteis, o sistema incrementa a probabilidade daqueles termos específicos, refinando a busca para a próxima iteração."*

---

### Slide 5: Representação de um Documento
* **Apresentador:** **Matheus**
* **Tempo:** ~1 minuto
* **O que falar:**
  > *"Como isso é modelado matematicamente?  
  > Imagine que temos um vocabulário $V$ com $n$ termos de indexação: $V = \{t_1, t_2, \dots, t_n\}$.  
  > No modelo probabilístico clássico, cada documento é representado no computador como um **vetor binário** de tamanho $n$.  
  > Cada posição corresponde a um termo do vocabulário, e o valor é puramente binário:  
  > - $1$, se o termo está presente no documento;  
  > - $0$, se o termo não está presente.  
  > Notem que, nesta versão clássica, não medimos a quantidade de vezes que a palavra repete (TF); apenas a presença ou ausência booleana."*

---

### Slide 6: Representação de um documento (Exemplo com 7 Documentos)
* **Apresentador:** **Matheus**
* **Tempo:** ~1 minuto
* **O que falar:**
  > *"Vamos ver isso na prática com o nosso exemplo didático.  
  > Definimos três termos em nosso vocabulário:  
  > - $t_1$: Brasil  
  > - $t_2$: Olimpíada  
  > - $t_3$: Londres  
  > Na tabela à direita, temos 7 documentos, de $d_1$ a $d_7$.  
  > Vejam, por exemplo, o documento $d_1$: ele contém $t_1$ e $t_3$, então seu vetor é $[1, 0, 1]$ — ou seja, fala de Brasil e Londres, mas não de Olimpíada.  
  > Já o documento $d_5$ contém os três termos: vetor $[1, 1, 1]$. O documento $d_2$ só fala de Brasil: vetor $[1, 0, 0]$."*
* **Destaque visual:** Mostrar as linhas da tabela e a legenda à esquerda.

---

### Slide 7: Representação da Consulta
* **Apresentador:** **Matheus**
* **Tempo:** ~1 minuto
* **O que falar:**
  > *"E a consulta do usuário?  
  > O usuário digita uma busca, por exemplo: `Brasil Londres`.  
  > O sistema quebra essa expressão nos termos individuais e constrói o mesmo vetor binário:  
  > Como a busca tem 'Brasil' ($t_1$) e 'Londres' ($t_3$), mas não contém 'Olimpíada' ($t_2$), o vetor da consulta $q$ é exatamente $[1, 0, 1]$."*

---

### Slide 8: Representação dos documentos e da consulta
* **Apresentador:** **Matheus**
* **Tempo:** ~45 segundos
* **O que falar:**
  > *"Aqui temos o panorama completo da nossa coleção inicial:  
  > Os 7 documentos de $d_1$ a $d_7$, e na última linha destacada em vermelho, a consulta $q = [1, 0, 1]$.  
  > Agora que temos tanto a coleção quanto a consulta representadas no mesmo espaço vetorial binário, surge a grande questão matemática: como calculamos a função de busca para ordenar esses documentos?  
  > O Rafael vai nos explicar a formulação probabilística."*

---

### Slide 9: Função de Busca (Razão entre Probabilidades)
* **Apresentador:** **Rafael**
* **Tempo:** ~1.5 minutos
* **O que falar:**
  > *"A base teórica de ordenação é o que chamamos de **razão de chances** (*odds*).  
  > A similaridade entre um documento $d_j$ e a consulta $q$ é dada por:  
  > $$\text{Similaridade}(d_j, q) = \frac{P(d_j \mid \text{Rel})}{P(d_j \mid \neg\text{Rel})}$$  
  > O que isso significa intuitivamente?  
  > É a razão entre a probabilidade de observar aquele documento entre os documentos que são **relevantes** para a consulta, dividida pela probabilidade de observá-lo entre os **não relevantes** ($\neg\text{Rel}$).  
  > Se essa razão for muito maior que 1, a probabilidade de ser relevante supera com folga a chance de irrelevância, e o documento sobe no ranking."*
* **Destaque visual:** Apontar para o numerador e o denominador da fórmula.

---

### Slide 10: Função de Busca (Probabilidade dos Termos)
* **Apresentador:** **Rafael**
* **Tempo:** ~1.5 minutos
* **O que falar:**
  > *"Mas como calculamos essa probabilidade em função das palavras que compõem a consulta?  
  > Nós quebramos o cálculo atribuindo um peso a cada termo de indexação, baseado em duas estimativas:  
  > - $P(t_i \mid \text{Rel})$: probabilidade de o termo $t_i$ ocorrer em um documento relevante. Quanto maior esse valor, mais a presença do termo favorece a relevância.  
  > - $P(t_i \mid \neg\text{Rel})$: probabilidade de o termo $t_i$ ocorrer em um documento irrelevante.  
  > A barra vertical significa 'dado que', indicando probabilidade condicional."*

---

### Slide 11: Exemplo de Função de Busca (Consulta com 10 Documentos)
* **Apresentador:** **Rafael**
* **Tempo:** ~2 minutos
* **O que falar:**
  > *"Vejam este exemplo numérico muito claro:  
  > Consulta $q$: 'Recuperação da Informação'.  
  > Suponham que o usuário avaliou 10 documentos relevantes e 10 irrelevantes.  
  > Nos relevantes: o termo 'Recuperação' apareceu em todos os 10 ($P = 10/10 = 1,0$). 'Informação' apareceu em 8 ($P = 8/10 = 0,8$).  
  > Já nos irrelevantes: 'Recuperação' apareceu em 5 ($P = 0,5$), e 'Informação' em 6 ($P = 0,6$).  
  > Quais conclusões tiramos disso?  
  > 1. Documentos que contêm ambos os termos são, com certeza, os mais prováveis de serem relevantes.  
  > 2. O termo 'Recuperação' é um discriminador mais forte do que 'Informação', porque ele é quase exclusivo dos relevantes (1,0 vs 0,5), enquanto 'Informação' aparece quase tanto nos irrelevantes quanto nos relevantes (0,8 vs 0,6).  
  > 3. Em resumo: se um documento possui termos frequentes em $\text{Rel}$ e raros em $\neg\text{Rel}$, sua pontuação explode positivamente."*
* **Transição para o próximo:** *"Agora o Matheus vai nos apresentar a tabela de símbolos formal e as equações de peso de Robertson-Sparck Jones."*

---

### Slide 12: Função de Busca (Tabela de Símbolos & Fórmulas de Peso)
* **Apresentador:** **Matheus**
* **Tempo:** ~2 minutos
* **O que falar:**
  > *"Para calcularmos esses pesos de forma exata a partir de contagens da coleção, usamos uma notação padrão de quatro variáveis:  
  > - $N$: total de documentos na coleção;  
  > - $n$: número de documentos que contêm o termo $t_i$;  
  > - $R$: número total de documentos marcados como relevantes pelo usuário;  
  > - $r$: número de documentos relevantes que contêm o termo $t_i$.  
  > 
  > Com essas quatro contagens, temos duas situações:  
  > **1ª Situação: Primeira iteração (Cold Start):** o usuário acabou de disparar a busca e ainda não marcou nenhum documento como relevante ($R=0, r=0$). Nessa hora, não temos feedback, e o peso recai exatamente sobre a fórmula do **IDF clássico**:  
  > $$w_{i0} = \text{IDF}_i = \log(N / n)$$  
  > **2ª Situação: Nas iterações com feedback de relevância:** o usuário já marcou quem é relevante. Aplicamos então a fórmula clássica de Robertson e Sparck Jones:  
  > $$w_{ik} = \log\left( \frac{r \times (N - R - n + r)}{(n - r) \times (R - r)} \right)$$  
  > Esta fórmula compara a proporção do termo dentro do conjunto relevante contra o não relevante."*
* **Destaque visual:** Percorrer a tabela de símbolos e apontar as duas fórmulas na lateral.

---

### Slide 13: Função de Busca (Fórmula do Somatório de Similaridade)
* **Apresentador:** **Matheus**
* **Tempo:** ~1.5 minutos
* **O que falar:**
  > *"Com os pesos calculados, como calculamos o escore final de um documento?  
  > Pelo somatório de similaridade:  
  > $$\text{sim}(q, d) = \sum_{i=1}^t (w_{ik} \times q_i \times d_i)$$  
  > Onde $q_i$ e $d_i$ são binários (1 ou 0).  
  > Portanto, a similaridade entre a consulta e o documento nada mais é do que **a soma dos pesos de todos os termos da consulta que também estão presentes no documento**.  
  > Se o termo estiver na consulta e no documento, multiplicamos por 1 e somamos seu peso. Se faltar em um dos dois, o produto zera."*

---

### Slide 14: Exemplo de Cálculo de Similaridade
* **Apresentador:** **Matheus**
* **Tempo:** ~1.5 minutos
* **O que falar:**
  > *"Vejam um exemplo direto:  
  > Consulta: `Brasil Olimpíada Londres`.  
  > Documento $d$: 'Brasil em Londres 2012: O Brasil não foi bem no quadro das medalhas da Olimpíada de Londres 2012...'.  
  > Suponham que os pesos dos termos calculados pelo sistema sejam:  
  > - Brasil: $0,5$  
  > - Olimpíada: $0,2$  
  > - Londres: $0,1$  
  > Como os três termos ocorrem tanto na consulta quanto no documento, fazemos:  
  > $$\text{sim}(q, d) = (0,5 \times 1 \times 1) + (0,2 \times 1 \times 1) + (0,1 \times 1 \times 1) = 0,8$$  
  > Os três termos contribuem positivamente para a pontuação final."*
* **Transição para o próximo:** *"Agora vamos ver como o sistema calcula isso na nossa base de 7 documentos na primeira iteração. O Rafael vai conduzir os cálculos."*

---

### Slide 15: Exemplo de Cálculo de Pesos (IDF com $N=7$)
* **Apresentador:** **Rafael**
* **Tempo:** ~1.5 minutos
* **O que falar:**
  > *"Voltando à nossa tabela com $N = 7$ documentos:  
  > Como estamos na 1ª iteração, aplicamos a fórmula do IDF na base 10:  
  > $$\text{IDF}_i = \log_{10}(N / n)$$  
  > Vamos contar as ocorrências de cada termo nas colunas:  
  > - Termo $t_1$ (Brasil): aparece nos documentos $d_1, d_2, d_4, d_5, d_6$. Logo, $n = 5$.  
  >   $$\text{IDF}_{t1} = \log_{10}(7 / 5) = \log_{10}(1,4) \approx 0,15$$  
  > Observem a última linha da tabela: o peso atribuído a $t_1$ é exatamente $0,15$."*

---

### Slide 16: Cálculo dos Pesos (1ª Iteração Completa)
* **Apresentador:** **Rafael**
* **Tempo:** ~1.5 minutos
* **O que falar:**
  > *"Repetindo o mesmo cálculo de IDF para os outros dois termos:  
  > - Para $t_2$ (Olimpíada): aparece em 4 documentos ($d_3, d_5, d_6, d_7$), logo $n=4$:  
  >   $$\text{IDF}_{t2} = \log_{10}(7 / 4) = \log_{10}(1,75) \approx 0,24$$  
  > - Para $t_3$ (Londres): aparece em 3 documentos ($d_1, d_3, d_5$), logo $n=3$:  
  >   $$\text{IDF}_{t3} = \log_{10}(7 / 3) = \log_{10}(2,33) \approx 0,37$$  
  > Notem a lógica do IDF: quanto mais raro o termo na coleção (Londres só aparece em 3), maior é o seu poder discriminatório e maior é o seu peso ($0,37$ contra $0,15$ de Brasil)."*

---

### Slide 17: Similaridade na 1ª Iteração (Ranking Inicial)
* **Apresentador:** **Rafael**
* **Tempo:** ~2 minutos
* **O que falar:**
  > *"Agora calculamos a similaridade de cada um dos 7 documentos com a consulta $q$:  
  > Para o documento $d_1$: ele contém $t_1$ e $t_3$.  
  > $$\text{sim}(q, d_1) = (0,15 \times 1 \times 1) + (0,24 \times 1 \times 0) + (0,37 \times 1 \times 1) = 0,52$$  
  > Repetindo para todos os documentos, chegamos aos escores da coluna azul à direita:  
  > - $d_5$ obteve $0,76$  
  > - $d_3$ obteve $0,61$  
  > - $d_1$ obteve $0,51$  
  > - $d_6$ obteve $0,39$  
  > - $d_7$ obteve $0,24$  
  > - $d_2$ e $d_4$ empataram com $0,15$.  
  > Logo, a ordem de recuperação inicial é:  
  > $$d_5 \to d_3 \to d_1 \to d_6 \to d_7 \to [d_2, d_4]$$  
  > Agora o usuário examina essa lista e fornece feedback. O Matheus vai mostrar o que acontece na 2ª iteração."*

---

### Slide 18: Feedback de Relevância (2ª Iteração)
* **Apresentador:** **Matheus**
* **Tempo:** ~2.5 minutos
* **O que falar:**
  > *"Aqui está o grande diferencial do modelo probabilístico:  
  > O usuário olhou os resultados e marcou dois documentos como relevantes: **$d_3$ e $d_5$**.  
  > Portanto, agora temos $R = 2$.  
  > 
  > **Atenção para o detalhe matemático:** se aplicarmos a fórmula original diretamente, podemos ter divisão por zero ou logaritmo de número negativo quando $r$ for zero ou igual a $R$.  
  > Para resolver isso, usamos o ajuste clássico da literatura de RI: **subtraímos $0,1$ de $r$ e somamos $1$ a $N$** (ficando $N = 8$).  
  > 
  > Vamos ver o cálculo do peso do termo $t_1$ (Brasil):  
  > Olhando os dois documentos relevantes ($d_3$ e $d_5$): apenas $d_5$ tem $t_1$. Logo, $r = 1$. Com o ajuste, $r = 1 - 0,1 = 0,9$.  
  > Substituindo na fórmula de Robertson-Sparck Jones:  
  > $$w_{t1} = \log_{10}\left( \frac{0,9 \times (8 - 2 - 5 + 0,9)}{(5 - 0,9) \times (2 - 0,9)} \right)$$  
  > Simplificando as contas:  
  > $$w_{t1} = \log_{10}\left( \frac{0,9 \times 1,9}{4,1 \times 1,1} \right) = \log_{10}\left( \frac{1,71}{4,51} \right) \approx \log_{10}(0,379) \approx -0,42$$  
  > **Vejam que interessante:** o peso de $t_1$ ficou **negativo** ($-0,42$)!  
  > Por quê? Porque o termo 'Brasil' aparece muito mais nos documentos que não foram marcados como relevantes do que nos relevantes. O modelo penaliza a presença de $t_1$ e valoriza enormemente $t_2$ ($1,55$) e $t_3$ ($1,93$)."*
* **Destaque visual:** Acompanhar cada linha da substituição numérica na tela.

---

### Slide 19: Similaridade na 2ª Iteração (Novo Ranking)
* **Apresentador:** **Matheus**
* **Tempo:** ~2 minutos
* **O que falar:**
  > *"Com esses novos pesos recalibrados, recalculamos a similaridade de todos os documentos.  
  > Para o documento $d_1$:  
  > $$\text{sim}(q, d_1) = (-0,42 \times 1 \times 1) + (1,55 \times 1 \times 0) + (1,93 \times 1 \times 1) = -0,42 + 1,93 = 1,51$$  
  > Olhem agora a coluna azul da direita com as novas pontuações:  
  > - $d_3$ pulou para o primeiro lugar com $3,48$!  
  > - $d_5$ ficou em segundo com $3,05$!  
  > - $d_7$ subiu para $1,55$ e ultrapassou $d_1$ ($1,51$) e $d_6$ ($1,13$).  
  > - $d_2$ e $d_4$, que só tinham a palavra Brasil, afundaram com escore negativo ($-0,42$).  
  > Ou seja: o modelo aprendeu exatamente a preferência do usuário e reorganizou completamente o ranking."*
* **Transição para o próximo:** *"Agora o Rafael vai sintetizar as vantagens e as limitações teóricas desse modelo clássico."*

---

### Slide 20: Vantagens do Modelo Probabilístico
* **Apresentador:** **Rafael**
* **Tempo:** ~1.5 minutos
* **O que falar:**
  > *"A principal vantagem teórica do modelo probabilístico é a sua **otimalidade formal**.  
  > Sob o Princípio de Ranqueamento Probabilístico (PRP), está provado matematicamente que, se as probabilidades forem calculadas com precisão e os termos forem independentes, este método garante a taxa mínima de erro possível na recuperação.  
  > Os documentos são colocados exatamente na ordem decrescente da sua probabilidade real de satisfazer a necessidade do usuário, aproveitando cada feedback fornecido."*

---

### Slide 21: Desvantagens e Limitações
* **Apresentador:** **Rafael**
* **Tempo:** ~2 minutos
* **O que falar:**
  > *"Por outro lado, o modelo clássico possui três grandes desvantagens históricas que vocês precisam conhecer:  
  > 1. **Separação inicial:** no início da busca, o sistema não sabe quem é relevante e precisa 'adivinhar' através do IDF ou heurísticas.  
  > 2. **Ausência da frequência do termo (TF):** os vetores são binários (0 ou 1). Se uma palavra-chave aparece 50 vezes em um artigo longo ou 1 vez em outro curto, o modelo trata os dois exatamente do mesmo jeito.  
  > 3. **Falta de normalização pelo tamanho do documento:** documentos gigantescos têm maior chance de conter os termos simplesmente por serem longos, e o modelo clássico não corrige essa distorção.  
  > É justamente para corrigir essas três falhas que mais tarde surgiu a famosa evolução deste modelo: o **BM25**, que incorporou saturação de TF e normalização por comprimento do texto.  
  > 
  > E agora, para fecharmos com chave de ouro, vamos convidar todos a verem essa teoria funcionando na prática no nosso Laboratório Interativo!"*

---

### Slide 22: Laboratório Interativo (Demonstração Prática ao Vivo)
* **Apresentador:** **Rafael e Matheus em Conjunto**
* **Tempo:** ~5 a 7 minutos
* **Roteiro da Demonstração ao Vivo:**
  1. **Matheus:** *"Aqui no Slide 22, temos o motor de RI probabilística rodando ao vivo no navegador."*
  2. **Rafael:** *"Notem os botões no topo: podemos clicar em 'Exemplo Slides (Tabelas 2.10/2.11)' ou carregar coleções personalizadas. Vejam a consulta preenchida: `Brasil Londres`."*
  3. **Matheus clica em 'Executar Busca':** *"Ao clicar em Executar Busca, o simulador calcula imediatamente os escores da 1ª iteração. Vejam que $d_5$, $d_3$ e $d_1$ assumem o topo da lista exatamente como deduzimos no Slide 17."*
  4. **Rafael aponta para os detalhes:** *"Se clicarmos em qualquer documento, o sistema abre a decomposição aritmética completa, mostrando a contribuição de cada termo e a fórmula de probabilidade."*
  5. **Matheus marca $d_3$ e $d_5$ como relevantes:** *"Agora, simulando o usuário: clicamos nas caixas de seleção de relevância do $d_3$ e do $d_5$."*
  6. **Rafael clica em 'Recalcular com Feedback':** *"Vejam em tempo real: o sistema recalibra os pesos $w_{ik}$, penaliza o termo $t_1$, e o ranking se reorganiza imediatamente: $d_3$ e $d_5$ disparam para o topo!"*
  7. **Demonstração do Gerador Sintético (se houver tempo):**  
     *"Além disso, incluímos um Gerador Sintético: podemos gerar 100 documentos instantaneamente (com 10% mono-termo e 5% multi-termo) para testar a escalabilidade do modelo com grandes coleções."*
  8. **Encerramento conjunto:**  
     *Rafael:* *"Com isso, encerramos nossa apresentação teórica e prática."*  
     *Matheus:* *"Ficamos à disposição para dúvidas e perguntas da banca e dos colegas. Muito obrigado!"*

---

## 🎯 Guia Rápido de Respostas para Possíveis Perguntas da Banca

1. **Pergunta:** *"Por que o peso do termo $t_1$ (Brasil) ficou negativo na 2ª iteração?"*  
   **Resposta do Matheus:** *"Porque na fórmula de Robertson-Sparck Jones, quando um termo é muito mais comum nos documentos não relevantes do que nos relevantes ($n - r > r$), a fração interna se torna menor do que 1. Como o logaritmo de um número entre 0 e 1 é negativo, o peso passa a atuar como uma penalidade, rebaixando documentos que insistem em conter termos irrelevantes."*

2. **Pergunta:** *"Para que serve a subtração de 0,1 em $r$ e a soma de 1 em $N$?"*  
   **Resposta do Rafael:** *"É um fator de suavização (smoothing). Sem ele, se um termo não aparecesse em nenhum documento relevante ($r = 0$), teríamos logaritmo de zero (que tende a $-\infty$), ou divisão por zero caso todos os relevantes contivessem o termo ($r = R$). O amortecimento estabiliza as estimativas numéricas."*

3. **Pergunta:** *"Qual a principal diferença entre o Modelo Probabilístico clássico e o Modelo Vetorial (TF-IDF)?"*  
   **Resposta do Matheus:** *"O Modelo Vetorial calcula ângulos geométricos (cosseno) baseando-se puramente na frequência estatística dos termos. Já o Modelo Probabilístico tem fundamentação bayesiana: ele busca estimar a probabilidade formal de pertinência ao conjunto ideal de respostas e se apoia fortemente no ciclo de feedback interativo com o usuário."*
