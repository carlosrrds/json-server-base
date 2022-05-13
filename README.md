# json-server-base

Esse é o repositório com a base de JSON-Server + JSON-Server-Auth já configurada, feita para ser controle de aluguel de quadras de esportes.

### Cadastro

POST /register

Serve para registrar tanto 1 estabelecimento que aluga as quadras, quanto um time que deseja alugar.

POST /register

body necessario para registrar um estabelecimento:

    {
      "email": "JH@gmail.com",
      "password": "jhsenha"
      "corporateName": "Jh escola de futebol",
      "userName": "Jh Esportes",
      "type": "establishment",
      "CNPJ": "00000000000000",
    },

body necessario para registrar um time:

     "email": "pernadepau@gmail.com",
      "password": "pernadepausenha",
      "userName": "Perna de Pau",
      "type": "team",

POST /match (autenticação necessaria)

body necessario para registrar um time:

"userId" deve ser preenchido com o id do usuario que esta fazendo a requisição.
"status" deve ser preenchido de acordo com o estado da partida podendo ser: ("vacance", "filled", "canceled" e "finished")

{
"date": "Thu Feb 20 2020 3:00:00 GMT-0300 (GMT-03:00)'",
"firtTeam": "time1",
"secondTeam": "free",
"stablishment": "JH Esportes",
"userId": 1,
"status": "vacancy"
}

POST /solicitation (autenticação necessaria)

userId" deve ser preenchido com o id do usuario que esta fazendo a requisição.
matchId" deve ser preenchido com o id do partida a qual o usuario pretende preencher a vaga.

{
"date": "Thu Feb 20 2020 1:00:00 GMT-0300 (GMT-03:00)'",
"userId": 2,
"matchId": 2
}

### Login

POST /login

{
" email " : " olivier@mail.com " ,
" senha " : " bestPassw0rd "
}

### Editar

para editar usuario

PATCH / match/_ID DE USUARIO _ (autenticação necessaria)

para editar partida (autenticação necessaria)

PATCH / match/_ID DA PARTIDA _

### Listar

para listar todas as partidas

GET /match

para listar partidas por status

GET /match?status=_STATUS DESEJADO _

ara listar todas as solicitações

GET /solitation

### AUTENTICAÇÃO

para autenticar o usuario deve-se pegar o accesstoker gerado pela resposta de login de usuario

exemplo:

{
"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6IkpIQGdtYWlsLmNvbSIsImlhdCI6MTY1MjQwMzE3OCwiZXhwIjoxNjUyNDA2Nzc4LCJzdWIiOiIxIn0.N8u-UX3CYR2WdhCpv3VmB_uPg1xaTkRRZ-pWBcXjseg",
"user": {
"email": "JH@gmail.com",
"corporateName": "Jh escola de futebol",
"userName": "Jh Esportes",
"type": "establishment",
"CNPJ": "00000000000000",
"id": 1
}

o accestoken deve ser incerido no no formato Baerer Token
