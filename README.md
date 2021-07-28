# MongoDB #1 #

## Instalando MongoDB ##
- sudo apt update
- sudo apt install -y mongodb

## Verificação do serviço ##
- sudo systemctl status mongodb
#imagem#

## Gerenciamento do serviço ##

### Parando o serviço ###
- sudo systemctl stop mongodb
### Iniciando o serviço ###
- sudo systemctl start mongodb
### Reiniciando o serviço ###
- sudo systemctl restart mongodb

--------------------------------------------
Por padrão, o MongoDB está configurado para iniciar automaticamente com o servidor. Se quiser desativar o inicializador automático, digite: sudo systemctl disable mongodb

Habilitá-lo novamente: sudo systemctl enable mongodb

Para entrar no terminal do mongo
- mongo
---------------------------------------------

## Comandos para o mongo ##

- **show dbs** 
- mostra todos os db

- **use** "nome do db"
- Esse comando acessa o db ou cria caso não exista 
- O db só persiste se adicionarmos uma coleção 

- **db.createCollection(name)**
- Cria uma coleção

- **db.posts.insert([{nome:"José",postagem: "frase1",data: "30-01-2019"},{nome:"Luis",postagem: "frase2",data: "30-01-2019"}])**
- Comando insere documentos na coleção posts

- **db.posts.find()**
- Imprime documentos na coleção posts

- **db.posts.findOne()**
- Imprime apenas um documento

- **db.posts.find().pretty()**
- Imprime os documentos no formato visual json 

- **db.posts.find({nome:"",postagem:""})**
- consulta na coleção os documentos com determinado nome e postagem 

- **db.posts.find({nome:"", idade:{$lte: 18}})**
- consulta na coleção com deerminado nome e com valor idade menor ou igual 18 
- Outras condições podem substituir o $lte:
- $gt maior que
- $lt menor que
-$ gte maior e igual que

- **db.posts.find({$or [{nome: 1},{nome: 2}]})**
- $or condição "ou" 

- **db.posts.find({nome: {$in:[nome1, nome2]}})**
- $in condição pertence; Caso o nome seja nome1 ou nome2

- **db.posts.find({nome: {$in:[nome1, nome2]}},{id:0,data:0})**
- {id:0,data:0} no final permite dizer quais campos devem vir na consulta 0 para não aparecer e 1 para aparecer. Obs não se mistara 0 e 1 ou dizemos quais devem aparecer ou quias não 
---------------------------------------------
Fora do terminal do mongo também podemos importar documentos para nossa coleção de forma bem simples: 
- mongoimport --db "nome do db" --collection "nome da coleção" --file "caminho do documento"