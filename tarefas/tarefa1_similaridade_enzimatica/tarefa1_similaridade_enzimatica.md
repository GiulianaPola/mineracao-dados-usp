# **Tarefa 1 - Similaridade de Enzimas entre Organismos**

**Disciplina:** Programação Aplicada à Bioinformática
**Nível:** Intermediário
**Linguagem:** Python
**Formato de entrada:** Arquivos FASTA
**Formato de saída:** Arquivos de texto `.txt` com os resultados

---

## 📘 **Objetivo**

Nesta tarefa, você irá implementar um programa em **Python** para analisar a similaridade entre sequências de DNA da enzima **topoisomerase** de três organismos diferentes: **rato**, **hamster chinês** e **cavalo**. As sequências são fornecidas em formato FASTA e devem ser comparadas tanto diretamente quanto por meio de vetores de contagem de aminoácidos. A tarefa envolve leitura de arquivos, manipulação de strings, cálculo de distâncias e geração de relatórios.

---

## 🧬 **Contexto Biológico**

A **topoisomerase** é uma enzima essencial em diversos organismos e está envolvida na modificação da estrutura do DNA. Comparar suas sequências pode revelar proximidade evolutiva entre espécies. Nesta atividade, você analisará as sequências de DNA desta enzima em três espécies:

* **Rato**: `rat.fasta`
* **Hamster chinês**: `hamster.fasta`
* **Cavalo**: `horse.fasta`

---

## 🖥️ **Tarefa**

Você deve desenvolver um script em **Python** que execute as seguintes etapas:

### 1. **Leitura das sequências FASTA**

Utilize a função fornecida abaixo para ler cada arquivo FASTA e obter a sequência de DNA como uma única string:

```python
def read_fasta(arq):
    seq = ''
    with open(arq) as f:
        f.readline()  # Ignora a primeira linha (descrição)
        for line in f:
            seq += line.strip()
    return seq
```

> **Dica**: Esta função deve ser chamada para os três arquivos: `rat.fasta`, `hamster.fasta`, `horse.fasta`.

---

### 2. **Comparação Simples entre Organismos**

Compare diretamente as sequências de DNA para os seguintes pares de organismos:

* Hamster × Cavalo
* Hamster × Rato
* Cavalo × Rato

Implemente uma **comparação simples de similaridade**, por exemplo, a **proporção de bases iguais na mesma posição** entre as duas sequências. Apresente os valores de similaridade percentual para cada par.

---

### 3. **Contagem de Aminoácidos**

Para cada sequência, conte as ocorrências de cada **aminoácido** representado pelas letras no alfabeto FASTA.

> 💡 **Observação**: Assuma que as sequências fornecidas já estão traduzidas para **sequências de aminoácidos** (isto é, não há necessidade de tradução do DNA para proteínas).

> 🔗 Consulte a lista de aminoácidos reconhecidos no formato FASTA:
> [https://pt.wikipedia.org/wiki/Formato\_FASTA](https://pt.wikipedia.org/wiki/Formato_FASTA)

Monte um vetor de contagem (frequência absoluta) com todas as letras válidas.

---

### 4. **Cálculo de Métricas de Similaridade**

Com os vetores gerados no passo anterior, calcule as seguintes métricas de distância/similaridade para os três pares de organismos:

* **Distância de Manhattan**
* **Distância Euclidiana**
* **Distância Supremum** (máxima diferença absoluta entre componentes)
* **Similaridade de Cosseno**

Apresente os resultados de cada métrica para cada par.

---

### 5. **Geração de Arquivos de Saída**

Crie **três arquivos de saída**, contendo:

1. `similaridade_dna.txt`: Resultados da comparação direta entre as sequências de DNA.
2. `vetores_aminoacidos.txt`: Tabelas com a contagem de aminoácidos para cada organismo.
3. `metricas_similaridade.txt`: Resultados das quatro métricas de distância para cada par de organismos.

---

## 📁 **Formato dos Arquivos**

### Arquivos de entrada:

* Texto no formato FASTA (ex: `hamster.fasta`)
* Primeira linha começa com `>descrição` (ignorada)
* As linhas seguintes contêm a sequência (em uma ou mais linhas)

### Arquivos de saída (exemplo de conteúdo):

#### `similaridade_dna.txt`

```
Hamster vs Cavalo: 85.3%
Hamster vs Rato: 92.1%
Cavalo vs Rato: 83.7%
```

#### `vetores_aminoacidos.txt`

```
Organismo: Hamster
A: 12
C: 9
D: 15
...

Organismo: Cavalo
A: 10
C: 11
...
```

#### `metricas_similaridade.txt`

```
Hamster vs Cavalo:
  Manhattan: 48
  Euclidiana: 8.60
  Supremum: 7
  Cosseno: 0.954

...
```

---

## 🧰 **Requisitos Técnicos**

* Linguagem: **Python 3.x**
* Bibliotecas padrão (`math`, `collections`, `numpy` se desejar usar)
* Código organizado, legível e comentado
* Os arquivos de saída devem ser gerados automaticamente

---

## 📦 **Entrega**

Você deve entregar um **arquivo `.zip`** contendo:

* O código-fonte Python (`similaridade_enzimas.py`)
* Os arquivos de saída (`similaridade_dna.txt`, `vetores_aminoacidos.txt`, `metricas_similaridade.txt`)
* Este `README.md` com instruções

---