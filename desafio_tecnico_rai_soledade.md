<a href="https://colab.research.google.com/github/raisantos/desafio-tecnico/blob/master/desafio_tecnico_rai_soledade.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

**Importação das Bibliotecas utilizadas**





```
import pandas as pd
import matplotlib.pyplot as plt

from google.colab import drive
drive.mount('/content/gdrive')
root_path = 'gdrive/My Drive/Colab Notebooks/'
```

    Drive already mounted at /content/gdrive; to attempt to forcibly remount, call drive.mount("/content/gdrive", force_remount=True).


**Leitura da primeira aba da planilha**


```
aba1 = pd.read_excel(root_path+'dados.xlsx', sheet_name=0)
aba1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>Mes_1</th>
      <th>Mes_2</th>
      <th>Mes_3</th>
      <th>Mes_4</th>
      <th>Mes_5</th>
      <th>Mes_6</th>
      <th>Mes_7</th>
      <th>Mes_8</th>
      <th>Mes_9</th>
      <th>Mes_10</th>
      <th>Mes_11</th>
      <th>Mes_12</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>NaN</td>
      <td>janeiro</td>
      <td>fevereiro</td>
      <td>março</td>
      <td>abril</td>
      <td>maio</td>
      <td>junho</td>
      <td>julho</td>
      <td>agosto</td>
      <td>setembro</td>
      <td>outubro</td>
      <td>novembro</td>
      <td>dezembro</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Realizado</td>
      <td>240</td>
      <td>280</td>
      <td>200</td>
      <td>310</td>
      <td>230</td>
      <td>213</td>
      <td>239</td>
      <td>210</td>
      <td>210</td>
      <td>210</td>
      <td>232</td>
      <td>213</td>
    </tr>
  </tbody>
</table>
</div>



**Leitura da segunda aba da planilha**


```
aba2 = pd.read_excel(root_path+'dados.xlsx', sheet_name=1)
aba2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mês</th>
      <th>orcado</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>janeiro</td>
      <td>330</td>
    </tr>
    <tr>
      <th>1</th>
      <td>fevereiro</td>
      <td>290</td>
    </tr>
    <tr>
      <th>2</th>
      <td>março</td>
      <td>230</td>
    </tr>
    <tr>
      <th>3</th>
      <td>abril</td>
      <td>321</td>
    </tr>
    <tr>
      <th>4</th>
      <td>maio</td>
      <td>283</td>
    </tr>
    <tr>
      <th>5</th>
      <td>junho</td>
      <td>291</td>
    </tr>
    <tr>
      <th>6</th>
      <td>julho</td>
      <td>193</td>
    </tr>
    <tr>
      <th>7</th>
      <td>agosto</td>
      <td>259</td>
    </tr>
    <tr>
      <th>8</th>
      <td>setembro</td>
      <td>289</td>
    </tr>
    <tr>
      <th>9</th>
      <td>outubro</td>
      <td>230</td>
    </tr>
    <tr>
      <th>10</th>
      <td>novembro</td>
      <td>434</td>
    </tr>
    <tr>
      <th>11</th>
      <td>dezembro</td>
      <td>421</td>
    </tr>
  </tbody>
</table>
</div>



**Obtendo lista dos valores de REALIZADO da primeira aba do arquivo**


```
realizado = aba1.iloc[1:].values[0][1:]
realizado
```




    array([240, 280, 200, 310, 230, 213, 239, 210, 210, 210, 232, 213],
          dtype=object)



**Fazendo merge das abas. Adicionando coluna REALIZADO com os valores obtidos anteriormente na aba1 no dataframe da aba2**


```
aba2['realizado'] = realizado
aba2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mês</th>
      <th>orcado</th>
      <th>realizado</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>janeiro</td>
      <td>330</td>
      <td>240</td>
    </tr>
    <tr>
      <th>1</th>
      <td>fevereiro</td>
      <td>290</td>
      <td>280</td>
    </tr>
    <tr>
      <th>2</th>
      <td>março</td>
      <td>230</td>
      <td>200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>abril</td>
      <td>321</td>
      <td>310</td>
    </tr>
    <tr>
      <th>4</th>
      <td>maio</td>
      <td>283</td>
      <td>230</td>
    </tr>
    <tr>
      <th>5</th>
      <td>junho</td>
      <td>291</td>
      <td>213</td>
    </tr>
    <tr>
      <th>6</th>
      <td>julho</td>
      <td>193</td>
      <td>239</td>
    </tr>
    <tr>
      <th>7</th>
      <td>agosto</td>
      <td>259</td>
      <td>210</td>
    </tr>
    <tr>
      <th>8</th>
      <td>setembro</td>
      <td>289</td>
      <td>210</td>
    </tr>
    <tr>
      <th>9</th>
      <td>outubro</td>
      <td>230</td>
      <td>210</td>
    </tr>
    <tr>
      <th>10</th>
      <td>novembro</td>
      <td>434</td>
      <td>232</td>
    </tr>
    <tr>
      <th>11</th>
      <td>dezembro</td>
      <td>421</td>
      <td>213</td>
    </tr>
  </tbody>
</table>
</div>



**Adicionando coluna DIFF, com o cálculo da diferença entre as colunas ORÇADO E REALIZADO**


```
aba2['diff'] = aba2['orcado'] - aba2['realizado']
aba2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mês</th>
      <th>orcado</th>
      <th>realizado</th>
      <th>diff</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>janeiro</td>
      <td>330</td>
      <td>240</td>
      <td>90</td>
    </tr>
    <tr>
      <th>1</th>
      <td>fevereiro</td>
      <td>290</td>
      <td>280</td>
      <td>10</td>
    </tr>
    <tr>
      <th>2</th>
      <td>março</td>
      <td>230</td>
      <td>200</td>
      <td>30</td>
    </tr>
    <tr>
      <th>3</th>
      <td>abril</td>
      <td>321</td>
      <td>310</td>
      <td>11</td>
    </tr>
    <tr>
      <th>4</th>
      <td>maio</td>
      <td>283</td>
      <td>230</td>
      <td>53</td>
    </tr>
    <tr>
      <th>5</th>
      <td>junho</td>
      <td>291</td>
      <td>213</td>
      <td>78</td>
    </tr>
    <tr>
      <th>6</th>
      <td>julho</td>
      <td>193</td>
      <td>239</td>
      <td>-46</td>
    </tr>
    <tr>
      <th>7</th>
      <td>agosto</td>
      <td>259</td>
      <td>210</td>
      <td>49</td>
    </tr>
    <tr>
      <th>8</th>
      <td>setembro</td>
      <td>289</td>
      <td>210</td>
      <td>79</td>
    </tr>
    <tr>
      <th>9</th>
      <td>outubro</td>
      <td>230</td>
      <td>210</td>
      <td>20</td>
    </tr>
    <tr>
      <th>10</th>
      <td>novembro</td>
      <td>434</td>
      <td>232</td>
      <td>202</td>
    </tr>
    <tr>
      <th>11</th>
      <td>dezembro</td>
      <td>421</td>
      <td>213</td>
      <td>208</td>
    </tr>
  </tbody>
</table>
</div>



**Salvando arquivo .CSV**


```
aba2.to_csv(root_path + 'desafio-saida.csv', index=False)
```

**Obtendo valores das colunas do dataframe aba2 para montagem do gráfico**


```
meses = aba2['mês'].values
meses
```




    array(['janeiro', 'fevereiro', 'março', 'abril', 'maio', 'junho', 'julho',
           'agosto', 'setembro', 'outubro', 'novembro', 'dezembro'],
          dtype=object)




```
realizados = aba2['realizado'].values
realizados
```




    array([240, 280, 200, 310, 230, 213, 239, 210, 210, 210, 232, 213],
          dtype=object)




```
diff = aba2['diff'].values
diff
```




    array([90, 10, 30, 11, 53, 78, -46, 49, 79, 20, 202, 208], dtype=object)



**Montagem do gráfico relacionando os meses com "orçado x realizado"**


```
plt.figure(figsize=(15,7))
plt.bar(meses, diff, color='blue', bottom = realizados)
plt.bar(meses, realizados, color='orange')

plt.xlabel('Mês')
plt.ylabel('$')
plt.title('Gráfico Orçamento')
plt.legend(('Orçado', 'Realizado'))
plt.savefig(root_path + 'desafio-grafico.png')
```


![png](desafio_tecnico_rai_soledade_files/desafio_tecnico_rai_soledade_20_0.png)

