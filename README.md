# RAIA 2026 - Classificação de Sentimentos em Comentários Curtos 

## Visão geral do projeto

Este projeto tem como objetivo classificar comentários curtos de usuários em três categorias:

- positivo  
- neutro  
- negativo  

Os comentários são textos curtos, sem necessidade de técnicas avançadas de pré-processamento.

---

## Representação de texto: TF-IDF

Para transformar os textos em uma forma numérica, foi utilizado o método **TF-IDF (Term Frequency – Inverse Document Frequency)**.

De forma resumida:

- **TF (Term Frequency)** mede a frequência de uma palavra dentro de um comentário.
- **IDF (Inverse Document Frequency)** reduz a importância de palavras muito comuns no conjunto de textos.

Julguei essa estrategia pertinente em razão da baixa quantidade de itens no dataset.

---

## Por que não utilizar heurísticas simples

Uma abordagem baseada apenas em regras ou palavras-chave (por exemplo, associar “bom” a positivo) apresenta diversas limitações:

- dificuldade em lidar com frases ambíguas ou mistas,
- pouca capacidade de generalização,

Por esse motivo, optou-se por utilizar modelos estatísticos supervisionados (SVM e Reg Logistica).

---

## Modelos utilizados

### Support Vector Machine (SVM)

O primeiro modelo empregado foi um **SVM com kernel linear**, uma escolha comum em problemas de classificação de texto, especialmente quando combinado com TF-IDF. 

### Regressão Logística

Em seguida, foi testado um modelo de **Regressão Logística**, também amplamente utilizado em tarefas de classificação de texto. O objetivo foi comparar seu desempenho com o SVM.

---

## Estratégia de avaliação

O conjunto de dados contém apenas **50 comentários**. O desempenho dos modelos pode variar significativamente dependendo da divisão entre treino e teste.

Para evidenciar essa variação:

- testei dois tamanhos de conjunto de teste:
  - `test_size = 0.2`
  - `test_size = 0.4`
- para cada configuração, o experimento foi repetido diversas vezes utilizando diferentes valores de `random_state`;
- para cada repetição, foi calculada a acurácia do modelo;
- ao final, foram reportadas a média e o desvio padrão das acurácias obtidas.

Essa abordagem permite observar a diferença natural dos resultados quando se trabalha com uma quantidade reduzida de dados.

---

## Rotulagem manual dos dados

Um ponto importante deste projeto é que **o conjunto de dados original não possuía rótulos de sentimento**. Para viabilizar o uso de modelos supervisionados, foi necessário realizar a **rotulagem manual dos comentários**.

Apesar disso, a rotulagem manual foi essencial para permitir a aplicação das técnicas q usei.

---

## Resultado final

Como resultado, o projeto gera uma tabela que relaciona:
- cada comentário original,
- o sentimento atribuído pelo modelo treinado.

---

## Limitações

As principais limitações do projeto são:

- tamanho reduzido do dataset;
- necessidade de rotulagem manual dos dados;
- alta sensibilidade dos resultados à divisão treino/teste.

Por esse motivo, os resultados devem ser interpretados com cautela. 

---

## Conclusão

Este projeto apresenta uma solução completa de classificação de sentimentos utilizando:

- vetorização de texto com TF-IDF;
- modelos lineares supervisionados (SVM e Regressão Logística);
- avaliação com múltiplas divisões do dataset.

Apesar das limitações impostas pelos dados, o estudo ilustra os desafios e as boas práticas ao trabalhar com NLP em cenários de poucas observacoes.
