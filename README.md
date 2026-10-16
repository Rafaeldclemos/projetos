# Recuperação de Informação — Modelo Probabilístico

> **Seminário de Recuperação de Informação (RI)**  
> **Apresentadores:** Matheus & Rafael  
> **Conteúdo Oficial:** 21 Slides baseados no Modelo Probabilístico clássico (Robertson & Sparck Jones, 1976) + Laboratório Interativo (Slide 22)

---

## 🌐 Acesso Online Direto (GitHub Pages)

Para visualizar os slides da apresentação e utilizar o simulador de busca probabilística diretamente em seu navegador (sem necessidade de instalação):

👉 **[Acessar Apresentação Online](https://rafaeldclemos.github.io/projetos/)**

*(Link direto para os slides: [https://rafaeldclemos.github.io/projetos/teste_slides.html](https://rafaeldclemos.github.io/projetos/teste_slides.html))*

---

## 📖 Estrutura dos Slides (22 Slides)

1. **Capa:** Recuperação de Informação — Modelo Probabilístico (Matheus & Rafael).
2. **O Modelo Probabilístico:** Proposta de 1976 por Robertson e Sparck Jones e ideia fundamental.
3. **Fundamentos:** Arcabouço probabilístico, conjunto resposta ideal e estimativa de probabilidade.
4. **Termos de indexação:** Distinção de documentos relevantes no corpus e formulação da consulta.
5. **Representação de um Documento:** Vetores de pesos binários $V = \{t_1, t_2, \dots, t_n\}$.
6. **Matriz de Documentos:** Documentos $d_1$ a $d_7$ indexados pelos termos $t_1$ (Brasil), $t_2$ (Olimpíada), $t_3$ (Londres).
7. **Representação da Consulta:** Consulta $q = \text{Brasil Londres}$ em vetor binário.
8. **Representação Unificada:** Tabela consolidada dos documentos $d_1 \dots d_7$ e consulta $q$.
9. **Função de Busca:** Similaridade via razão entre probabilidades $\frac{P(d_j \mid \text{Rel})}{P(d_j \mid \neg\text{Rel})}$.
10. **Probabilidades Condicionais:** Pesos dos termos em função de $P(t_i \mid \text{Rel})$ e $P(t_i \mid \neg\text{Rel})$.
11. **Exemplo Numérico de Busca:** Consulta *Recuperação da Informação* com 10 documentos em Rel e $\neg$Rel.
12. **Fórmulas e Tabela de Símbolos:** $N, n, R, r$, peso na 1ª iteração ($IDF = \log(N/n)$) e iterações com feedback.
13. **Função de Similaridade:** Fórmula $\text{sim}(q, d) = \sum_{i=1}^t (w_{ik} \times q_i \times d_i)$ e significados.
14. **Exemplo de Cálculo de Similaridade:** Cálculo passo a passo com soma de pesos resultando em $0,8$.
15. **Cálculo de Pesos (IDF):** Tabela completa com $N = 7$ e cálculo detalhado do $IDF_{t1} \approx 0,15$.
16. **1ª Iteração:** Pesos calculados ($t_1: 0,15$, $t_2: 0,24$, $t_3: 0,37$) e ordem de recuperação.
17. **Similaridade na 1ª Iteração:** Cálculo de $\text{sim}(q, d_1) = 0,52$ e ordenação $d_5 \to d_3 \to d_1 \to d_6 \to d_7 \to [d_2, d_4]$.
18. **Feedback de Relevância (2ª Iteração):** Marcação de $d_3$ e $d_5$ como relevantes, ajuste de $r - 0,1$ e $N + 1$, cálculo detalhado de $w_{t1} \approx -0,42$.
19. **Similaridade na 2ª Iteração:** Novo cálculo $\text{sim}(q, d_1) = 1,51$ e ranking final $d_3, d_5, d_7, d_1, d_6$.
20. **Vantagens:** Princípio da otimalidade e ordenação por probabilidade decrescente.
21. **Desvantagens:** Estimativa da separação inicial, ausência de frequência de termos (pesos puramente binários) e falta de normalização por tamanho.
22. **Laboratório Interativo:** Simulador em tempo real com gerador sintético de 100 documentos, recomendações de modelos teóricos e detalhamento aritmético da similaridade.

---

## ⌨️ Atalhos de Navegação nos Slides

* <kbd>→</kbd> ou <kbd>Espaço</kbd>: Avançar slide
* <kbd>←</kbd> ou <kbd>Backspace</kbd>: Voltar slide
* <kbd>O</kbd> ou <kbd>Esc</kbd>: Visão geral em grade (Índice completo de miniaturas)
* <kbd>F</kbd>: Alternar modo Tela Cheia
* <kbd>Home</kbd> / <kbd>End</kbd>: Primeiro / Último slide
