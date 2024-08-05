### Features

## 📊   Previsão de Preço de Ações na AWS com

<img src="https://hermes.dio.me/tracks/72f36aaa-f969-4063-97d3-a2ea61b4114a.png" jsaction="" class="sFlh5c pT0Scc iPVvYb" style="max-width: 200px; height: 200px; margin: 0px; width: 354px;" alt="Bootcamp Nexa - Machine Learning para Iniciantes na AWS" jsname="kn3ccd" data-ilt="1722889726755" aria-hidden="false"> ![](https://d1.awsstatic.com/product-marketing/IronMan/AWS-service-icon_sagemaker.5ccec16f16a04ed56cb1d7f02dcdada8de261923.png)


Neste projeto inicial, eu assumirei o papel de um analista financeiro trabalhando para uma instituição de investimentos em ações. Vou utilizar o histórico de preços das ações de uma empresa fictícia chamada XXYZ, com dados entre 2016 e 2020, para construir um modelo de previsão e usá-lo para prever o preço futuro das ações.


| Column Name | Data type  |
| ------------ | ------------ |
|  Item_Id | STRING  |
|  Date | TIMESTAMP  |
| Close  | DECIMAL  |

![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/search_s3.png?raw=true)
No console S3, clique no bucket sagemaker-studio.

![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/studio-bucket.png?raw=true)
Fazendo Upload do arquivo csv
![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/s3_upload.png?raw=true) 


##### Importando o dataset no Canvas
daily_close_price.csv
![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/import-data.png?raw=true)



![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/import-from-s3-studio.png?raw=true) ![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/canvas-select-preview.png?raw=true) 

visualizar 100 linhas do conjunto de dados 

![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/canvas-preview.png?raw=true?)




##### Construindo e treinando um modelo de ML


![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/create-new-model.png?raw=true)


![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/select-dataset.png?raw=true)

Na próxima tela, vou configurar o tipo de modelo para treinamento.O Canvas selecionará automaticamente a Previsão de séries temporais como o tipo de modelo. 




![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/target-and-problem.png?raw=true)

Na tela de configuração de previsão de séries temporais, vou fornecer algumas informações:
- O campo itens: como eu identifico meus itens nos conjuntos de dados. Para este caso de uso, selecionei "Item_Id", pois estou planejando prever o preço por símbolo de ações.
- A coluna de grupo: se eu tiver agrupamentos lógicos dos itens selecionados acima, posso escolher o recurso aqui. Não tenho um para este caso de uso, mas exemplos de grupo podem ser NYSE, Nasdaq ou outros agrupamentos de símbolos de ações conforme desejado para o meu caso de uso.
- O campo de marcação de tempo: selecione "Date", que é o recurso que contém as informações de marcação de tempo. O Canvas suporta data no formato AAAA-MM-DD (por exemplo: 2018-01-01). Eu posso consultar outros formatos de dados suportados aqui.
- Preenchi 30 no campo "Número de Dias", assumindo que quero prever o preço de fechamento das ações para 30 dias no futuro.
- Selecionei Estados Unidos como o país para o campo de feriados, como informação adicional para alimentar o treinamento do modelo.
Por fim



![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/time-series-configuration.png?raw=true)
![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/time-series-configuration-2.png?raw=true)

Agora que a configuração está concluída, estou pronto para treinar o modelo. Atualmente, o SageMaker Canvas não oferece suporte ao Quick Build para previsão de séries temporais. Vou selecionar a opção Standard Build. O modelo levará cerca de 2 a 4 horas para treinar.

![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/start-standard-build.png?raw=true)

![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/model-training.png?raw=true)

#### Usando o modelo para gerar previsões

Quando o treinamento do modelo terminar, serei direcionado para a guia Analisar. Lá, poderei ver a precisão média da previsão e o impacto da coluna no resultado da previsão. Vou clicar no botão Prever e me preparar para executar algumas previsões.
![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/model-accuracy.png?raw=true)

Para criar previsões, eu preciso primeiro fornecer o intervalo de datas para o qual a previsão pode ser feita. Em seguida, posso gerar previsões para todos os itens no conjunto de dados ou para um item específico.

No nosso workshop, escolho a opção "Single item" e seleciono XXYZ na lista suspensa. O Canvas gera uma previsão para o meu item, mostrando a previsão média, um limite superior e um limite inferior.

Para a previsão gerada, posso clicar no botão do menu suspenso "Download" para baixar o gráfico da previsão como imagem ou os valores da previsão como um arquivo CSV.

![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/forecasts.png?raw=true)
![](https://github.com/HalleyVeras/lab-aws-sagemaker-canvas-estoque/blob/main/images/forecasts-2.png?raw=true)


