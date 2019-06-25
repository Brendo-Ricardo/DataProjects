# DataProjects
Developement of Applications for Data Analysis

Compartilhamento de conhecimento com novos analistas e desenvolvedores, conteúdo para o desenvolvimento de robôs para raspagem de dados e automatização de processos que envolvam dados.

Linguagem de programação Python versão 3.7

#Bibliotecas utilizadas para requisição e raspagem

#Importando bibliotecas para raspar os dados
    from urllib.request import urlopen
    from bs4 import BeautifulSoup

#Vetor armazenando as URLs das páginas que estamos raspando do site Home Refil
    pages = ["https://twitter.com/Perfil Que Deseja Raspar"]

#Inicio de um laço 'for' para raspagem dos dados nas páginas do vetor
    for i in pages:
#Abrir as URLs e armazenar na variável html 
    html = urlopen(i)
#Utilização da biblioteca dando um parse na varíavel html, onde estão as URLs do site
    bsObj = BeautifulSoup(html,"html.parser") 

Inicio de um laço 'for' para iniciar a contagem de quantos produtos irei raspar por página
OBSERVAÇÃO --> No exemplo de raspagem de dados do twitter há um limite de 20 postagens por página, para outros sites é possível incluir um contador de páginas dentro do vetor, dessa forma será possível raspar ainda mais conteúdo com um único script.  

    for cont in range(0,5):
    
#É necessário que tenha domínio em linguagem HTML, pois é necessário explorar o DOM da página.
 
            veiculo = "twitter" 
            data = bsObj.findAll("small", {"class":"time"})[cont].text
            conteudo = bsObj.findAll("div", {"class":"js-tweet-text-container"})[cont].text  
            urlImagem = bsObj.findAll("div", {"class":"AdaptiveMedia-photoContainer"})[cont]['data-image-url'] 
            chave = bsObj.findAll("li", {"class":"js-stream-item"})[cont]['data-item-id']
            likes = bsObj.findAll("button", {"class":"ProfileTweet-action--unfavorite"})[cont].text
            tipo = bsObj.findAll("div", {"class":"AdaptiveMediaOuterContainer"})[cont].div['class']
            
# Imprimir na tela o dado que estamos raspando            
            print(data)
