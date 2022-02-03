# Kenziehubserver  

## Descrição  
Esta API possui um pequeno banco de dados em que constam inicialmente 10 usuários (endpoint /users) e 8 alimentos (endpoint /burgers) pré-cadastrados.  
  
Possibilita a qualquer usuário, logado ou não, visualizar todos os alimentos, e somente ao usuário logado escrever ou acessar suas informações.  

## Endpoints  
Esta API dispõe de 6 endpoints:  

1. /register  
2. /signup  
3. /signin  
4. /login  
5. /users  
6. /burgers  


Abaixo descrevem-se as rotas que NÃO demandam autenticação e aquelas que DEMANDAM.  

Rotas que DEMANDAM autenticação devem informar no cabeçalho da requisição o campo "Authorization", deste modo:  

Authorization: Bearer {token}  
 

# Buscando Dados da API - GET  

#### *Requisição de Hambúrgueres*  
*Não exige corpo da requisição*  
*Sem autenticação (token) no cabeçalho da requisição* 
**GET /burgers - Formato da Resposta - STATUS 200**  
```js  
[
	{
		"id": 1,
		"name": "Hamburger",
		"category": "Sanduíches",
		"price": 14,
		"img": "https://i.ibb.co/fpVHnZL/hamburguer.png"
	},
	{
		"id": 2,
		"name": "Cheeseburger",
		"category": "Sanduíches",
		"price": 16,
		"img": "https://i.ibb.co/djbw6LV/x-burgue.png"
	},
	{
		"id": 3,
		"name": "Big Kenzie",
		"category": "Sanduíches",
		"price": 18,
		"img": "https://i.ibb.co/FYBKCwn/big-kenzie.png"
	},
	{
		"name": "Combo Kenzie",
		"category": "Combos",
		"price": 26,
		"img": "https://i.ibb.co/FYBKCwn/combo-kenzie.png",
		"id": 4
	},
	{
		"id": 5,
		"name": "Fanta Guaraná",
		"category": "Bebidas",
		"price": 5,
		"img": "https://i.ibb.co/cCjqmPM/fanta-guarana.png"
	},
	{
		"id": 6,
		"name": "Coca-Cola",
		"category": "Bebidas",
		"price": 4.99,
		"img": "https://i.ibb.co/fxCGP7k/coca-cola.png"
	},
	{
		"id": 7,
		"name": "Ovomaltine",
		"category": "Bebidas",
		"price": 4.99,
		"img": "https://i.ibb.co/QNb3DJJ/milkshake-ovomaltine.png"
	},
	{
		"name": "Ovomaltine Cream",
		"category": "Sobremesas",
		"price": 10,
		"img": "https://i.ibb.co/FYBKCwn/ovomaltinecream-kenzie.png",
		"id": 8
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
		"email": "lockejohn@lost.com",  
		"password": "$2a$10$p0RZwwPL7F3e335BxNevw.OlbD/U/CgSuSThCU1hpHzQiKDilwb/i",  
		"name": "John Locke",  
		"confirm_password": "wW*8uuuu",  
		"id": 1  
	},  
	{  
		"email": "austenkate@lost.com",  
		"password": "$2a$10$JFFyzlaKxd/NFqXBuHgare3oNCcvjE/Ehv9a.z.HlZav5Tx0JfKIa",  
		"name": "Kate Austen",  
		"confirm_password": "wW*8uuuu",  
		"id": 2  
	},  
	{  
		"email": "reyeshugo@lost.com",  
		"password": "$2a$10$ulFQO6/c3sFbv9nVfDdI0uBpv9yeJVdjX9UUkeIPP1Hrn89D8CLM.",  
		"name": "Hugo Reyes",  
		"confirm_password": "wW*8uuuu",  
		"id": 3  
	},  
	{  
		"email": "humedesmond@lost.com",  
		"password": "$2a$10$nlqZctQaHOXPIlcb.vgV5ubHK.zZ247xW8PQeCRAHPvYzm6SarE8G",  
		"name": "Desmond Hume",  
		"confirm_password": "wW*8uuuu",  
		"id": 4  
	},  
	{  
		"email": "burkejuliet@lost.com",  
		"password": "$2a$10$DszZsuZKwyxfY6Pz65Yjd.c4aJDfQHV0VfPNPOVy1l0.luID07P0.",  
		"name": "Juliet Burke",  
		"confirm_password": "wW*8uuuu",  
		"id": 5  
	},  
	{  
		"email": "sheppardjack@lost.com",  
		"password": "$2a$10$d.bw3E01o5SfjYuP5IPGcuck3tGjIiWan4XefVGXi0WXQcqI203cC",  
		"name": "Jack Sheppard",  
		"id": 6  
	},  
	{  
		"email": "jarrahsayid@lost.com",  
		"password": "$2a$10$qfX6gxSaL5GOGOZ7FKStuu9B/3VXwxGgxVRkvqEiv/s9776tqrceK",  
		"name": "Sayid Jarrah",  
		"id": 7  
	},  
	{  
		"email": "fordjames@lost.com",  
		"password": "$2a$10$7EabUdvi9Bkacf5ysiYEzONvamQtyVHFEN/ob0RNT8KRR96b4QQ..",  
		"name": "James Ford",  
		"id": 8  
	},  
	{  
		"email": "linusbenjamin@lost.com",  
		"password": "$2a$10$gZJhkkDCFT2s3wJ5JWVnSOYaFz5Hg0cPorVNXKT6c3iDDpip3p1PG",  
		"name": "Benjamin Linus",  
		"id": 9  
	},  
	{  
		"email": "alpertrichard@lost.com",  
		"password": "$2a$10$uX9/n34q15nF4SXpbb1PeejvhmkI1bA01GVy0P7YzssiMPTG1usyi",  
		"name": "Richard Alpert",  
		"confirm_password": "wW*8uuuu",  
		"id": 10  
	}  
]  
```  

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
}  
```  
Em caso de sucesso, esta será a resposta: 

```js
{  
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImF1c3RlbmthdGVAbG9zdC5jb20iLCJpYXQiOjE2NDI4MjMxMjcsImV4cCI6MTY0MjgyNjcyNywic3ViIjoiNSJ9.WXlizD3Y1d7Bzr9IEp7bqHszsEeNl9TSHseux_ButUQ",  
	"user": {  
		"email": "austenkate@lost.com",  
		"name": "Kate Austen",  
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

#### *Cadastro de Hambúrguer*  
*Com autenticação (token) no cabeçalho da requisição*  
**POST /burgers - Formato da Requisição**   
```js  
{  
		"name": "Hambúrguer",  
		"category": "Sanduíches",  
		"price": 14,  
		"img": "https://i.ibb.co/fpVHnZL/hamburguer.png"  
	}  
```  
**POST /burgers - Formato da Resposta - Status 201**  
```js  
{  
    "name": "Hambúrguer",  
	"category": "Sanduíches",  
	"price": 14,  
	"img": "https://i.ibb.co/fpVHnZL/hamburguer.png"  
	"id": 1,  
}  
```  

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
```js
"Incorrect password"  
```  
* Caso o e-mail estiver errado ou email e password estiverem errados:  

**POST /login - Formato da resposta - STATUS 400**  
```js
"Cannot find user"  
```  

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
    "confirm_password": "wW*8uuuu", 
	"name": "Desmond David Hume",  
}  
```
Digamos que deseje alterar somente seu nome. Use PATCH, como no exemplo abaixo:  

*Com autenticação (token) no cabeçalho da requisição*  
**PATCH /users/:id - Formato da Requisição**  
```js
{  
	"name": "Desmond David"  
}  
```  
**PATCH /users/:id - Formato da Resposta - STATUS 200**  
```js
{  
	"email": "humedesmond@lost.com",  
	"password": "$2a$10$AyIevQ.C6dngH7ue20bnOeptMSPT.WhKPkV/9chWEsdGLtVawYMui",  
    "confirm_password": "wW*8uuuu", 
	"name": "Desmond David",  
	"id": 2  
}  
```  
Repare que somente o campo desejado foi modificado. Mas, caso seu objetivo seja substituir ou sobrescrever todos os dados anteriores de um usuário, use PUT.  


# Atualizando Dados Completos de um Recurso da API - PUT  

O uso do verbo HTTP PUT exige que os campos email e password estejam no corpo da requisição. Ou seja, adicione esses 2 campos mais o campo que deseja alterar. 
Do contrário, a resposta retornada será:

**PUT /users/:id - Formato da Resposta - STATUS 400**  
```js  
"Email and password are required"  
```  
Segue o modo correto:  
*Com autenticação (token) no cabeçalho da requisição*   
**PUT /users/:id - Formato da Requisição**   
```js  
{  
	"name": "John A. Locke",  
	"email": "lockejohn@lost.com",  
	"password": "wW*8uuuu",  
	"confirm_password": "wW*8uuuu"  
}  
```  
**PUT /users/:id - Formato da Resposta - STATUS 200**   
```js  
{  
	"name": "John A. Locke",  
	"email": "lockejohn@lost.com",  
	"password": "$2a$10$mZIKY/.q8Hx1ynbN5DhyleqSpXTHhPBR3xkn4t7bafTi9BEky1nWy",  
	"confirm_password": "wW*8uuuu",  
	"id": 1  
}  
```  

Caso envie só os campos email e password, o usuário passará a ter somente esses 2 campos mais o id, os demais serão excluídos.  


# Deletando Dados da API - DELETE  

*Não exige corpo da requisição*      
*Com autenticação (token) no cabeçalho da requisição*        
**DELETE /users/:id - Formato da Resposta - STATUS 200**   
```js  
{}    
```  
