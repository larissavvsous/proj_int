> Repositório destinado ao desenvolvimento de trabalhos relacionados a disciplina de Projeto Integrador I, II e III da Universidade Federal do Ceará.


<h1 align="center">
        <br>
        <br>
        Projeto Integrador I
        <br>
    </h1>

Esse projeto, com o tema "Análise de sentimentos em comentários de supermercados de Itapajé: entendendo a opinião dos consumidores" consiste na realização uma análise de sentimento (NLP - processamento de linguagem natural) em avaliações e comentários referentes a três principais supermercados da cidade local, são eles: Deirton, Para Ty e Menor Preço. Para saber mais, [clique aqui](https://github.com/larissavvsous/proj_int/blob/main/Projeto%20Integrador%20I%20PDF.pdf).


<p align="center">
  <a href="#dataset">Dataset</a> •
  <a href="#ferramentas-utilizadas">Ferramentas utilizadas</a> •
  <a href="#projeto">Projeto</a> •
  <a href="#consultas">Consultas</a> 
</p>


## Dataset

O dataset contém as seguintes colunas:

* nome: nome do cliente
* comentário: comentário do cliente
* quant_like_coment: quantidade de curtida naquele comentário
* nota (estrela): nota do cliente ao supermercado
* periodo: há quanto tempo foi comentado aquele comentário
* guia_local: pessoas que costumam comentar, dar nota, recebem do google um selo de 'guia local', como se o comentário dele(a) tivesse maior peso
* quant_fotos: quantidade de foto da pessoa no geral em todos os seus comentários
* quant_comentarios: quantidade de comentários da pessoa nas avaliações do google 
* supermercado: nome do supermercado
* rua_supermercado: endereço do supermercado
* feedback_super: retorno do supermercado diante da crítica/elogio

Onde:
* Cada instância é um comentário de um cliente referente à um determinado supermercado
* Possui valores ausentes

Colunas criadas ao longo da exploração e análise:
  
* cliente_id: nova coluna criada a partir da 'nome'
* comentario_sem_stopwords: comentário sem stopwords
* comentario_sem_pontuacao: comentário sem pontuação
* comentario_tokens: comentários tokenizados

## Ferramentas utilizadas

Durante a disciplina de Projeto Integrador I, utilizamos as seguintes ferramentas:

* Google Colabory
  - é um ambiente de notebooks Jupyter que não requer configuração e é executado na nuvem do Google. Com ele foi feito o código (python).
* Canva
  - é uma plataforma de design gráfico que permite aos usuários criar gráficos de mídia social, apresentações, infográficos, pôsteres e outros conteúdos visuais. Com ele foi feita a apresentação.
* JavaScript
  - é uma linguagem de programação (juntamente com HTML e CSS) de script em alto nível com tipagem dinâmica fraca e multiparadigma. Com ele, coletamos alguns dados da WEB.
* Instant Data Scraper
  - é uma ferramenta automatizada de extração de dados para qualquer site. Com ele, foi extraído a maioria dos dados.

## Projeto
O projeto final feito ao longo do semestre foi primeiramente criar um banco de dados completo e tratado, juntando os três supermercados e uma análise descritiva/exploratória. Daremos continuidade em Projeto Integrador II e III.

## Consultas

Um breve código com consultas: 

```python
  import pandas as pd

  # Carregando os conjuntos de dados
  deirton = pd.read_csv('deirton_tratado.csv')
  paraty = pd.read_csv('paraty_tratado.csv')
  menorpreco = pd.read_csv('menorpreco_tratado.csv')
  supermercados = pd.read_csv('3supermercados.csv')

  # Visualizando as primeiras linhas do dataset 'supermercados'
  print("\nPrimeiras linhas do dataset:\n", supermercados.head())

  # Uma breve análise descritiva
  estatisticas_descritivas = supermercados.describe()

  # Contagem de valores únicos em uma coluna específica
  valores_unicos = supermercados['supermercado'].value_counts()

  # Visualizar as estatísticas descritivas
  print("\nEstatísticas descritivas:\n", estatisticas_descritivas)
  print("\nContagem de valores únicos nos supermercados:\n", valores_unicos)

 # Gráfico interativo para analisar a distribuição da variável 'nota'
 import plotly
 fig = px.histogram(supermercados['nota'], nbins=10, title='Histograma das Notas', labels={'value': 'Notas', 'count': 
 'Frequência'})
 fig.show()
