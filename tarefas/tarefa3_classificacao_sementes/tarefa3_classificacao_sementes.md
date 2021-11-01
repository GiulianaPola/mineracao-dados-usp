# Tarefa 3 - Classificação de Sementes de Trigo

## Descrição da Tarefa

Esta tarefa tem como objetivo aplicar métodos de classificação supervisionada utilizando a biblioteca `scikit-learn`, por meio de um exercício prático com dados morfológicos de sementes de trigo. A atividade inclui etapas de pré-processamento de dados, divisão em conjuntos de treino e teste, aplicação de três classificadores distintos e avaliação comparativa de seus desempenhos.

O exercício visa familiarizar os estudantes com a aplicação de algoritmos clássicos de aprendizado de máquina em problemas reais de classificação.

## Conjunto de Dados

O conjunto de dados utilizado está disponível no [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/seeds) e também no [OpenML](https://www.openml.org/d/1499). Ele contém **210 instâncias** de sementes de **três variedades de trigo**, com **sete atributos** numéricos extraídos a partir de imagens digitais:

- **Área (A)**
- **Perímetro (P)**
- **Compacidade (C = 4πA / P²)**
- **Comprimento do grão**
- **Largura do grão**
- **Coeficiente de assimetria**
- **Comprimento do sulco da semente**

O oitavo atributo é a **classe** (valores `1`, `2` ou `3`), representando a variedade da semente.

## Requisitos

Certifique-se de que as seguintes bibliotecas estejam instaladas no ambiente Python:

- `numpy`
- `pandas`
- `scikit-learn`
- `matplotlib` (opcional, para gráficos)
- `seaborn` (opcional)

Instalação via `pip`:

```bash
pip install numpy pandas scikit-learn matplotlib seaborn
````

## Pré-processamento de Dados

Antes de aplicar os modelos de classificação, é necessário:

* Verificar se existem valores ausentes (`NaN`) no dataset.
* Remover instâncias com valores faltantes, se existirem.
* Separar os atributos preditivos (`X`) da variável de classe (`y`).

## Divisão dos Dados

Os dados devem ser divididos aleatoriamente em:

* **200 instâncias para treino**
* **10 instâncias para teste**

Utilize `train_test_split` do módulo `sklearn.model_selection`, com estratificação para garantir proporções balanceadas entre as classes.

## Classificadores Utilizados

Três métodos de classificação devem ser aplicados:

1. **Árvore de Decisão** – `DecisionTreeClassifier` (módulo `sklearn.tree`)
2. **Naive Bayes Gaussiano** – `GaussianNB` (módulo `sklearn.naive_bayes`)
3. **Máquina de Vetores de Suporte (SVM)** – `SVC` (módulo `sklearn.svm`)

## Avaliação do Modelo

A acurácia será utilizada como métrica principal de desempenho. É calculada como:

> número de classificações corretas ÷ número total de instâncias de teste

Utilize `accuracy_score` do `sklearn.metrics`.

Além disso, imprima as **classes reais e preditas** para comparação direta.

## Execução do Programa

Para rodar o script:

1. Certifique-se de que o arquivo `seeds.csv` esteja no diretório do script.
2. Execute o programa Python que implementa todos os passos.

3. A saída esperada deverá conter:

* Resultado do pré-processamento
* Separação dos dados
* Classificação por cada método
* Acurácia individual
* Listagem das classes reais vs. preditas

Exemplo de saída:

```text
Decision Tree - Acurácia: 0.90
Reais:    [1 2 3 2 1 3 2 3 1 2]
Preditas: [1 2 3 2 1 3 1 3 1 2]

GaussianNB - Acurácia: 0.80
SVM - Acurácia: 0.90
```

## Autor e Informações Adicionais

* **Data da Tarefa**: 27 de setembro de 2021
* **Data de Entrega**: 1º de novembro de 2021

> Esta tarefa faz parte da disciplina de Introdução à Aprendizagem de Máquina e tem como objetivo aplicar conceitos fundamentais de classificação em um problema prático utilizando o `scikit-learn`.

---

*Em caso de dúvidas, consulte a documentação oficial do [scikit-learn](https://scikit-learn.org/stable/).*