# Modelo Probabilístico de Recuperação de Informação

> **Seminário de Recuperação de Informação (RI)**  
> **Apresentadores:** Rafael Lemos & Matheus Cândido  
> **Duração:** 40 Minutos  
> **Referência:** Ricardo Baeza-Yates & Berthier Ribeiro-Neto (*Modern Information Retrieval*, páginas 48 a 55)

---

## 🌐 Acesso Online Direto (Sem Instalação e Sem `git clone`)

Para visualizar a apresentação interativa e utilizar o simulador de busca em qualquer navegador (computador, tablet ou smartphone), clique no link abaixo:

👉 **[Acessar Apresentação Online (GitHub Pages)](https://rafadecarvalholemosm-alt.github.io/projetos/)**

*(Link alternativo via visualizador web: [Abrir via HTMLPreview](https://htmlpreview.github.io/?https://github.com/rafadecarvalholemosm-alt/projetos/blob/main/index.html))*

---

## 📖 Conteúdo da Apresentação (21 Slides)

1. **Abertura:** Fundamentos Bayesianos, Dedução Formal e a Equação Robertson-Sparck Jones.
2. **A Ideia Fundamental:** O Conceito do Conjunto Resposta Ideal $R$ (Robertson & Sparck Jones, 1976).
3. **Princípio de Ranqueamento Probabilístico (PRP):** Definição 2.4 de Stephen Robertson [1364] e a crítica sobre a falta do espaço amostral.
4. **Representação Binária dos Documentos:** Vetor de pesos booleanos sob a hipótese da independência binária.
5. **Razão de Chances (*Odds*) e Regra de Bayes:** Minimização de julgamentos errôneos e passagem intermediária da Equação 2.13 com $P(R, q)$.
6. **Corte de Constantes e Fatoração:** Equação 2.14 e independência condicional entre termos.
7. **Variáveis Centrais:** Definição formal das probabilidades $p_{iR}$ e $q_{iR}$.
8. **Logaritmos e o Truque Algébrico:** As duas equações intermediárias da dedução passo a passo (páginas 50 e 51).
9. **A Equação-Chave do Modelo:** Equação 2.15 com somatório restrito aos termos de coocorrência.
10. **Tabela de Contingência (Tabela 2.9):** Conexão das contagens reais ($N, n_i, R, r_i$) da coleção.
11. **Dedução da Equação 2.16:** Substituição algébrica dos termos da tabela de contingência na razão de chances.
12. **Equação Robertson-Sparck Jones:** Ajuste clássico de $+0,5$ para evitar indefinições e escores infinitos.
13. **Bootstrap Inicial (Equação 2.17):** Estimativa na ausência inicial de julgamentos de relevância ($R = 0, r_i = 0$).
14. **Anomalia dos Pesos Negativos e Correção (Equação 2.18):** Eliminação de penalidades quando $n_i > N/2$ e a propriedade de $n_i = N$.
15. **Exemplo Prático ("to do"):** Contas abertas das Tabelas 2.10 e 2.11 ($N = 4, n_1 = 2, n_2 = 3$).
16. **Ranking Residual com Intervenção Humana:** Procedimento de recalibração em 4 etapas e análise do empate entre $d_3$ e $d_4$.
17. **Estimativa Automática de Croft e Harper (Equação 2.19):** Hipóteses cegas dispensando intervenção manual.
18. **Refinamento Recursivo:** Estimativas com $D$ e $D_i$, fórmulas iniciais sem ajuste ($D_i/D$), falha para $D=1, D_i=0$, termos ruidosos e observação sobre a coleção exemplo.
19. **Balanço Crítico:** Vantagens teóricas, as 3 grandes deficiências e a evolução histórica para o modelo BM25.
20. **Conclusão:** Comparativo Booleano vs. Vetorial vs. Probabilístico e considerações finais.
21. **Laboratório Interativo:** Simulador de busca probabilística com passo a passo didático em tempo real.

---

## 🧪 Laboratório e Simulador Interativo

O slide 21 integra um motor real de recuperação de informação probabilística:
* **Entrada de Documentos e Consultas:** Insira ou edite textos livremente.
* **Presets Oficiais:** Carregamento em 1 clique da coleção do livro (Slide 15 / Tabelas 2.10 e 2.11).
* **Seleção de Modelos:** Alterne entre a Equação 2.18, Equação 2.17, Robertson-Sparck Jones completa (+0,5) e Croft & Harper (Eq. 2.19).
* **Dedução Aberta Passo a Passo:** Tabela de contingência dinâmica, substituição numérica detalhada com MathJax e ranking ordenado pelo PRP com feedback de relevância interativo.

---

## ⌨️ Atalhos de Navegação

* <kbd>→</kbd> ou <kbd>Espaço</kbd>: Próximo slide
* <kbd>←</kbd> ou <kbd>Backspace</kbd>: Slide anterior
* <kbd>O</kbd> ou <kbd>Esc</kbd>: Visão geral em grade (Índice de miniaturas)
* <kbd>F</kbd>: Alternar modo Tela Cheia
* <kbd>T</kbd>: Iniciar / Pausar cronômetro de 40 minutos
