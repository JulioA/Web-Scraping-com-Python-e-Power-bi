# Análise Exploratória de CEP's da região do Campo Limpo utilizando Python e Power Bi

*Raspagem de Dados utilizando a linguagem Python e integrando ela com a ferramenta Power Bi.*

Escolhi a região do Campo Limpo para essa análise pois é a região onde eu resido.

Dados a serem adquiridos.
![1](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/139e99ae-585d-4744-9496-82b087fcdd5f)


Vou utilizar o Insomnia para verificar se a nossa API está retornando os valores que a gente precisa e ao mesmo tempo gerar um código de aquisição dos dados.
![2](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/7929a30b-0d3d-49b2-9f67-102e46a9c870)
![3](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/ed2e5997-5e3c-4bf2-8e16-33b29fda8b4e)


Testamos o código no jupyter notebook acoplado ao anaconda e o retorno foi satisfatório. Criei um dataframe para tabelar esses dados e facilitar a leitura deles.
![4](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/7f9a5d58-de4b-4c56-9a29-aec5c0a10931)
![5](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/219ef1c7-8521-47fc-b96c-3b59bbb9d0c4)


Habilitei a extração de dados do Power Bi em Python através do anaconda, onde podemos extrair o dado diretamente da nossa aplicação apenas com o código.
![6](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/cc081e56-8772-461c-9563-68b076e9db54)
![7](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/1759122c-f6d9-416b-a369-8aa7cf4bba58)


Não há muitos dados a serem tratados por enquanto. Por isso apenas renomeei as colunas e exclui erros.
![8](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/dfcd56c9-714e-4082-8d74-87d26d84df23)
![9](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/9ec5d7ce-2d60-4175-bcca-b92524db20ff)
![10](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/9ae485c8-62bf-49df-b1f2-379a442478d0)


Aqui ocorre um erro muito comum do Power Bi em relação a localização. Podemos notar que mesmo utilizando CEP e Região, ele acaba colocando a localização em um local do qual não queremos.
![11](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/bf8e276a-5b8c-45c4-bc2d-7d9a024ab5a3)


Decidi voltar a nossa API e buscar a localização utilizando a biblioteca Geopandas, que nos permite buscar a latitude e longitude de determinada localização para uma precisão maior.
![12](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/c66b2b27-670f-45bd-9c4c-b13f1c1452ef)
![13](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/e00a4973-a8e8-4a7c-97a0-787e678ad720)


O resultado foi satisfatório. Irei filtar as localizações por bairro para uma precisão maior.
![14](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/27f5e802-2de1-4fa1-8101-bfe4828ed79c)
![15](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/1af06d25-169b-46fe-8068-0688418fdd95)


Aqui delimitei as colunas por latitude e longitude utilizando a ferramente de extração de colunas do próprio Power Bi, onde ele ja indentificou um padrão e as separou.
![16](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/2f811c2d-3f40-468d-b79f-2b6709a2cd30)
![17](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/70c03cbb-a205-4b31-9960-859304c74c2b)


Aqui fiz uma fórmula para termos noção da quantidade de bairros.
![18](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/aa813511-36a5-4067-8403-950bceeb0812)


Resultado final do gráfico.
![19](https://github.com/JulioA/Web-Scraping-com-Python-e-Power-bi/assets/146854621/ffe1ebbd-51f1-4e08-b513-519dfddbd2c8)


Análise exploratória

São bairros bem próximos uns dos outros, sendo o mais longe o bairro Pirajussara.

O CEP tende a ser linear e começar com 057, seguido de outros números.

Podemos verificar também que pode ser uma região de grande comércio, pois o complemento se localiza utilizando-se dessas referências.

Verificamos também que há um outlier entre esses dados, não só pela localização, que apareceu em São José do Rio Preto, mas também pelo CEP, visto que o CEP segue um padrão e este está totalmente fora dele. Provavelmente foi um erro de pesquisa do site, pois podemos encontrar um local próximo ao da nossa análise principal que contém um nome parecido a esse outlier.

Por se tratar de um outlier, costumamos descartar ele. Mas caso for necessário, pode-se fazer uma análise para verificar o erro e talvez  fazer uma recomendação de calibração de busca de dados do site.
