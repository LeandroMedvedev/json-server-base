# Nome da API: 
## Json-Server-Entertainment

## Descrição
Esta API (*Application Programming Interface*, ou Interface de Programação de Aplicação) possui um pequeno banco de dados em que constam inicialmente 3 músicas e 3 séries de TV pré-cadastradas, além de 3 usuários.

Possibilita a qualquer usuário visualizar as músicas, mas apenas aos usuários logados visualizar os usuários ou séries já registrados.

## Endpoints
Esta API tem um total de 7 endpoints:

1. /register
2. /signup
3. /users
4. /login
5. /signin
6. /songs
7. /series

<!-- -------------------------------------------------------------- -->
Abaixo descreveremos as rotas que NÃO demandam autenticação e aquelas que DEMANDAM.  

Rotas que DEMANDAM autenticação devem informar no cabeçalho da requisição o campo "Authorization", deste modo:  

Authorization: Bearer {token}

Uma vez logado, o usuário conseguirá acesso à lista de usuários e séries já registradas.

<!-- -------------------------------------------------------------- -->
# Buscando Dados da API - GET

#### *Requisição de Músicas*
*Não exige corpo da requisição*  
*Sem autenticação (token) no cabeçalho da requisição*  
**GET /songs - Formato da Resposta - STATUS 200**  
```js
[  
	{
		"song": "Song 2",  
		"album": "Blur",  
		"release_date": "February 10, 1997",  
		"band": "Oasis",  
		"country": "England",  
		"additional_informations": "https://www.allmusic.com/album/blur-mw0000082694",  
		"id": 1  
	},  
	{  
		"song": "Go Let It Out",  
		"album": "Standing on the Shoulder of Giants Album",  
		"release_date": "February 23, 2000",  
		"band": "Oasis",  
		"country": "England",  
		"additional_informations": "https://www.allmusic.com/album/standing-on-the-shoulder-of-giants-mw0001955486",
		"id": 2  
	},  
	{  
		"song": "On Your Own",  
		"album": "A Northern Soul",  
		"release_date": "July 3, 1995",  
		"band": "The Verve",  
		"country": "England",  
		"additional_informations": "https://www.allmusic.com/album/a-northern-soul-mw0000126607",  
		"id": 3  
	}  
]  
```
<!-- -------------------------------------------------------------- -->
#### *Requisição de Séries*  
*Não exige corpo da requisição*  
*Com autenticação (token) no cabeçalho da requisição*  
**GET /series - Formato da Resposta - STATUS 200**  
```js
[  
	{  
 		"serie": "Lost",  
		"year": 2004,  
		"seasons": 6,  
		"genre": "fiction",  
		"additional_informations": "https://www.imdb.com/title/tt0411008/?ref_=vp_back",  
		"id": 1  
	},  
	{  
		"serie": "Seinfeld",  
		"year": 1989,  
		"seasons": 9,  
		"genre": "sitcom",  
		"additional_informations": "https://www.imdb.com/video/vi4273980185?playlistId=tt0098904&ref_=tt_ov_vi",  
		"id": 2   
	},  
	{  
		"serie": "Dawson's Creek",  
		"year": 1998,  
		"seasons": 6,  
		"genre": "drama",  
		"additional_informations": "https://www.imdb.com/title/tt0118300/",  
		"id": 3  
	}  
]  
```

#### *Requisição de Usuários*  
*Não exige corpo da requisição*  
*Com autenticação (token) no cabeçalho da requisição*  
**GET /users - Formato da Resposta - STATUS 200**  
```js
[  
	{  
		"email": "burkejuliet@lost.com",  
		"password": "$2a$10$aPw08iEpvMGpn3uHpEGepui9rAY7eBPDyYkFmDriHbFxBl0G57yTK",  
		"name": "Juliet Burke",  
		"age": 37,  
		"id": 1  
	},  
	{  
		"email": "humedesmond@lost.com",  
		"password": "$2a$10$AyIevQ.C6dngH7ue20bnOeptMSPT.WhKPkV/9chWEsdGLtVawYMui",  
		"name": "Desmond David Hume",  
		"age": 39,  
		"id": 2  
	},  
	{  
		"email": "jarrahsayid@lost.com",  
		"password": "$2a$10$emSs2JU7Xq9MiAi/E84WzeJllYfsZ8u.ePtSEjr9BUh13NxFfCvr6",  
		"name": "Sayid Jarrah",  
		"age": 36,  
		"id": 3  
	},  
]  
```


<!-- -------------------------------------------------------------- -->
# Enviando Dados à API - POST

## Cadastros  

#### *Cadastro de usuário*  
Endpoints que permitem o cadastro na lista de **users**:  

* POST /register  
* POST /signup  
* POST /users  
  
Qualquer um dos 3.  

*Sem autenticação (token) no cabeçalho da requisição*  
**POST /register - Formato da Requisição**  
```js
{  
	"name": "Kate Austen",  
	"email": "austenkate@lost.com",  
	"password": "wW*8uuuu",  
	"age": 32  
}  
```  
Em caso de sucesso, esta será a resposta:  

**POST /register - Formato da Resposta - STATUS 201**  
```js
{  
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImF1c3RlbmthdGVAbG9zdC5jb20iLCJpYXQiOjE2NDI4MjMxMjcsImV4cCI6MTY0MjgyNjcyNywic3ViIjoiNSJ9.WXlizD3Y1d7Bzr9IEp7bqHszsEeNl9TSHseux_ButUQ",  
	"user": {  
		"email": "austenkate@lost.com",  
		"name": "Kate Austen",  
		"age": 32,  
		"id": 5  
	}  
}  
```  
Campos requeridos, obrigatórios para cadastro:   
1. email   
2. password  
   
Do contrário, a resposta será:  

**POST /register - Formato da Resposta - STATUS 400**  
```js  
"Email and password are required"  
```  
Já os demais campos são opcionais.   

* Caso tente cadastrar um novo usuário com e-mail já existente no banco de dados, a resposta será:  

**POST /register - Formato da Resposta - STATUS 400**   
```js 
"Email already exists"  
```  
#### *Cadastro de Música*  
*Com autenticação (token) no cabeçalho da requisição*  
**POST /songs - Formato da Requisição**    
```js
{    
	"song": "Catching the Butterfly",  
	"album": "Urban Hymns",  
	"release_date": " September 30, 1997",  
	"band": "The Verve",  
	"country": "England",  
	"additional_informations": "https://www.allmusic.com/album/urban-hymns-mw0000027235"  
}  
```  
**POST /songs - Formato da Resposta - Status 201**  
```js
{  
	"song": "Catching the Butterfly",  
	"album": "Urben Hymns",  
	"release_date": " September 30, 1997",  
	"band": "The Verve",  
	"country": "England",  
	"additional_informations": "https://www.allmusic.com/album/urban-hymns-mw0000027235",  
	"id": 4  
}  
```  
#### *Cadastro de Série*  
*Com autenticação (token) no cabeçalho da requisição*  
**POST /series - Formato da Requisição**  
```js
{    
	"serie": "Lost",  
	"year": 2004,  
	"seasons": 6,  
	"genre": "fiction",  
	"additional_informations": "https://www.imdb.com/title/tt0411008/?ref_=vp_back"  
}  
```

**POST /series - Formato da Resposta - Status 201**  
```js
{  
	"serie": "Lost",  
	"year": 2004,  
	"seasons": 6,  
	"genre": "fiction",  
	"additional_informations": "https://www.imdb.com/title/tt0411008/?ref_=vp_back",  
	"id": 4  
}  
``` 

<!-- -------------------------------------------------------------- -->
## Login   
Endpoints que assentem a um usuário previamente cadastrado na lista de **users** acesso à área restrita:  

* POST /login   
* POST /signin  

Qualquer 1 dos 2.  

*Sem autenticação (token) no cabeçalho da requisição*  
**POST /login - Formato da Requisição**    
```js
{  
	"email": "jarrahsayid@lost.com",  
	"password": "wW*8uuuu"  
}  
```  
Resposta em caso de sucesso:  
**POST /login - Formato da Resposta - STATUS 200**   
```js 
{  
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImphcnJhaHNheWlkQGxvc3QuY29tIiwiaWF0IjoxNjQyODIxNjEwLCJleHAiOjE2NDI4MjUyMTAsInN1YiI6IjMifQ.XCOal2_Bgjrt2eFmuZvA8oIDVK-mkmTQPgwtaBWT4D8",  
	"user": {  
		"email": "jarrahsayid@lost.com",  
		"name": "Sayid Jarrah",  
		"age": 36,  
		"id": 3  
	}  
}  
```  
Repare que a resposta retorna **user** e **accessToken**. Posso armazenar ambos no localStorage para fazer a gestão do usuário no front end.  

* Caso a senha estiver errada:  

**POST /login - Formato da Requisição**  
```js
{  
	"email": "humedesmond@lost.com",  
	"password": "wW*8uuu"  
}  
```  
**POST /login - Formato da Resposta - STATUS 400**  
"Incorrect password"  

* Caso o e-mail estiver errado ou email e password estiverem errados:  

**POST /login - Formato da resposta - STATUS 400**  
```js
"Cannot find user"  
```  
<!-- -------------------------------------------------------------- -->
# Atualizando Dados Parciais (1 ou mais campos específicos) de um Recurso da API - PATCH  

Se seu desejo for alterar dados já registrados na API, há 2 opções de verbos HTTP (*Hypertext Transfer Protocol*):  
1. PATCH  
2. PUT  

Qual a diferença?  
O tipo de atualização que deseja fazer. Considere o usuário com os seguintes dados:  
```js
{  
	"email": "humedesmond@lost.com",  
	"password": "$2a$10$AyIevQ.C6dngH7ue20bnOeptMSPT.WhKPkV/9chWEsdGLtVawYMui",  
	"name": "Desmond David Hume",  
	"age": 39,  
	"id": 2  
}  
```  
Digamos que deseje alterar somente sua idade (age), de 39 para 32 anos. Use PATCH, como no exemplo abaixo:  

*Com autenticação (token) no cabeçalho da requisição*  
**PATCH /users/:id - Formato da Requisição**  
```js
{  
	"age": 2  
}  
```  
**PATCH /users/:id - Formato da Resposta - STATUS 200**  
```js
{  
	"email": "humedesmond@lost.com",  
	"password": "$2a$10$AyIevQ.C6dngH7ue20bnOeptMSPT.WhKPkV/9chWEsdGLtVawYMui",  
	"name": "Desmond David Hume",  
	"age": 2,  
	"id": 2  
}  
```  
Repare que somente o campo idade (age) foi alterado. Os demais campos permanecem os mesmos (The Song Remains the Same - Led Zeppelin, 1976). Entendedores entenderão. 😉  
Mas, caso seu objetivo seja substituir todos os dados anteriores de um usuário pela nova idade (age), use PUT.   
Nos endpoints /songs e /series não precisa pôr os campos email e password junto, somente o campo que quer alterar.   
Já, no endpoint /users, é obrigatória a inserção dos campos email e password junto com o campo que deseja modificar.  
Exemplo abaixo:  

*Com autenticação (token) no cabeçalho da requisição*  
**PUT /users/:id - Formato da Requisição**  
```js
{  
	"email": "humedesmond@lost.com",  
	"password": "wW*8uuuu",  
	"age": 2  
}  
```  
**PUT /users/:id - Formato da Resposta - STATUS 200**  
```js
{  
	"email": "humedesmond@lost.com",  
	"password": "$2a$10$MnDrzQzenyfs4OP6HzXyXeJUavYsIFCwrwMipO7dNx5NYnlMBSm3.",  
	"age": 2,  
	"id": 2  
}  
```  
Lembre-se que, antes da requisição com PUT, o usuário possuía os campos name, email, password, age e id (gerado automaticamente):  
```js
"users: {  
	"name": "Desmond David Hume",  
	"email": "humedesmond@lost.com",  
	"password": "$2a$10$AyIevQ.C6dngH7ue20bnOeptMSPT.WhKPkV/9chWEsdGLtVawYMui",  
	"age": 39,  
	"id": 2  
}  
```  
Note, porém, que, após a requisição com PUT, o campo name sumiu, restando somente os campos essenciais email, password e id, além do campo solicitado, age.   

Mais informações sobre requisições com PUT a seguir.  

<!-- -------------------------------------------------------------- -->
# Atualizando Dados Completos de um Recurso da API - PUT

Os exemplos a seguir simulam uma atualização dos dados de um usuário, mas poderiam aplicar-se a atualização de dados de séries ou músicas também. A diferença é que, nos endpoints /songs e /series, não há necessidade de inserção dos campos email e password junto com o campo que desejo atualizar. Já no endpoint /users devo inserir também os campos email e password.   

*Com autenticação (token) no cabeçalho da requisição*   
**PUT /users/:id - Formato da Requisição**  
```js
{  
	"email": "austenkate@lost.com",  
	"password": "wW*8uuuu",  
	"age": 99  
}  
```  
**PUT /users/:id - Formato da Resposta - STATUS 200**  
```js
{  
	"email": "austenkate@lost.com",  
	"password": "$2a$10$QI3OtxTcULGYzzif1HJCHuul0dNT7wgSO9LTvR.ZIl8wddqAsXOA.",  
	"age": 99,  
	"id": 5  
}  
```  
Repare que, conquanto o interesse fosse atualizar apenas a idade do usuário do id 5 no exemplo acima, os campos email e password são requeridos.   

* Caso queira atualizar, mas não insira os campos email e password:  

*Com autenticação (token) no cabeçalho da requisição*  
**PUT /users/:id - Formato da requisição**  
```js
{  
    "age": 100  
}  
```  
**PUT /users/:id - Formato da Resposta - STATUS 400**  
```js
"Email and password are required"  
```  
<!-- -------------------------------------------------------------- -->
# Deletando Dados da API - DELETE  

O exemplo abaixo simula uma deleção de dados no endpoint /songs, mas o mesmo seria aplicado nos endpoints /series e /users.  

*Não exige corpo da requisição*      
*Com autenticação (token) no cabeçalho da requisição*        
**DELETE /songs/:id - Formato da Resposta - STATUS 200**   
```js 
{}    
```



**made to the sounds of:**      
1. Kings of Convenience - Misread, 		2004 https://www.youtube.com/watch?v=WOxE7IRizjI    
2. Come On 				- The Verve, 	1997 https://www.youtube.com/watch?v=YWrvN-yXbWE    

*04:19 am, January 22, 2022* 🌅  
*Rio de Janeiro - Brazil*   
*LeandroMedvedev* 🥲  
