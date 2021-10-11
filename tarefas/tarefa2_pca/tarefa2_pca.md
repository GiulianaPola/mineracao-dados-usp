# Tarefa 2 — Análise de Componentes Principais (PCA)

## 💡 Introdução

Em problemas de Ciência de Dados, frequentemente lidamos com conjuntos de dados com muitas variáveis (alta dimensionalidade). Embora esses atributos possam carregar informações importantes, muitos deles também podem ser redundantes ou pouco informativos. Técnicas de **redução de dimensionalidade**, como a **Análise de Componentes Principais (PCA)**, são ferramentas fundamentais para lidar com esses cenários.

A **PCA (Principal Component Analysis)** é uma técnica estatística que transforma os dados originais em um novo sistema de coordenadas, onde as direções (componentes principais) são ordenadas de acordo com a variância dos dados — ou seja, sua capacidade de explicar a informação presente no conjunto. Assim, as primeiras componentes principais carregam a maior parte da variabilidade dos dados, permitindo projetá-los em espaços de menor dimensão com perdas mínimas de informação.

Nesta tarefa, você aplicará a PCA ao conjunto de dados sobre câncer de mama disponível na biblioteca `scikit-learn`. O objetivo é praticar o pré-processamento, entender a transformação dos dados via PCA, interpretar os resultados e visualizá-los de forma clara e informativa.

---

## 🎯 Objetivos

* Compreender e aplicar a técnica de PCA para redução de dimensionalidade;
* Explorar, padronizar e visualizar dados reais;
* Analisar a variância explicada por diferentes números de componentes;
* Interpretar os resultados da transformação dos dados e promover uma análise crítica do modelo.

---

## 🛠️ Bibliotecas Recomendadas

* `pandas`
* `numpy`
* `scikit-learn`
* `matplotlib`
* `seaborn`

Certifique-se de ter essas bibliotecas instaladas antes de começar. Você pode instalá-las usando `pip install` se necessário.

---

## 🧪 Etapas do Exercício

### 1. Carregamento dos Dados

Utilize a função `load_breast_cancer()` do módulo `sklearn.datasets` para carregar o conjunto de dados.

```python
from sklearn.datasets import load_breast_cancer
breast = load_breast_cancer()
```

A função retorna um *bunch* de dados, semelhante a um dicionário, que inclui:

* `breast.data`: matriz de atributos com 569 amostras e 30 características numéricas.
* `breast.target`: vetor com os rótulos (0 para maligno, 1 para benigno).
* `breast.feature_names`: nomes das características.
* `breast.target_names`: nomes das classes.

---

### 2. Exploração Inicial dos Dados

Utilize a biblioteca `pandas` para transformar os dados em um `DataFrame` e realizar uma exploração inicial:

* Visualize as primeiras e últimas amostras (`head()` e `tail()`).
* Adicione uma coluna chamada `label` com os rótulos categorizados como `'Malignant'` e `'Benign'`.
* Use `.describe()` para obter estatísticas básicas sobre as variáveis.

```python
import pandas as pd

df = pd.DataFrame(breast.data, columns=breast.feature_names)
df['label'] = pd.Series(breast.target)
df['label'].replace(1, 'Malignant', inplace=True)
df['label'].replace(0, 'Benign', inplace=True)

print(df.head())
print(df.tail())
```

---

### 3. Pré-processamento: Padronização dos Atributos

A PCA é sensível à escala dos dados. Por isso, é fundamental padronizar os atributos antes de aplicá-la. Utilize o `StandardScaler` do `sklearn.preprocessing`.

Após a transformação, verifique se as médias dos atributos padronizados estão próximas de 0 e o desvio padrão próximo de 1.

---

### 4. Aplicação da PCA com 2 Componentes Principais

Utilize o módulo `sklearn.decomposition` para aplicar a PCA e reduzir os dados a 2 dimensões:

```python
from sklearn.decomposition import PCA

pca = PCA(n_components=2)
Xpca = pca.fit_transform(Xnorm)
```

Em seguida:

* Mostre a quantidade de variância explicada por cada uma das componentes principais usando `pca.explained_variance_ratio_`.
* Calcule a porcentagem total da variância explicada pelas duas componentes.
* Reflita: o quanto de informação foi preservado nessa transformação?

---

### 5. Visualização em 2D

Crie um gráfico de dispersão (scatter plot) das amostras no espaço das duas primeiras componentes principais. Use cores distintas para as classes `'Benign'` e `'Malignant'`.

Sugestão: utilize `seaborn` ou `matplotlib.pyplot`.

---

### 6. Análise com 3 Componentes Principais

Repita a análise usando 3 componentes principais.

* Verifique o valor de `pca3.explained_variance_ratio_`.
* Calcule a variância total explicada pelas três componentes.
* Compare com o caso de 2 componentes: houve um ganho relevante de variância explicada?

---

## 🔍 Perguntas Reflexivas

1. Qual a principal vantagem de usar PCA neste conjunto de dados?
2. Você considera que a visualização em 2D é suficiente para distinguir as classes? Por quê?
3. A terceira componente principal agrega informação relevante ou apresenta retorno marginal?
4. Que cuidados devem ser tomados ao aplicar PCA em conjuntos de dados de outras naturezas (por exemplo, com atributos categóricos ou não padronizados)?

---

## 📎 Entrega

* O código-fonte completo (`.ipynb` ou `.py`) com as etapas documentadas.
* Gráficos gerados com legendas e títulos apropriados.
* Respostas às perguntas reflexivas em um bloco final (markdown ou comentários).
* Certifique-se de que seu código está bem organizado, com comentários explicativos.

---

Se tiver dúvidas sobre o funcionamento da PCA ou das bibliotecas utilizadas, consulte a [documentação oficial do scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html) ou os tutoriais nas referências abaixo.

---

## 📚 Referências

1. [Scikit-learn - PCA](https://scikit-learn.org/stable/modules/decomposition.html#pca)
2. [DataCamp Tutorial - Principal Component Analysis in Python](https://www.datacamp.com/community/tutorials/principal-component-analysis-in-python)
3. [Exemplo prático com Iris Dataset (GitHub)](https://github.com/mGalarnyk/Python_Tutorials/blob/master/Sklearn/PCA/PCA_Data_Visualization_Iris_Dataset_Blog.ipynb)

---

Boa análise!