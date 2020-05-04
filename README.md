# Sorteio Deboni

## Endpoints

> Todas as chamadas para API precisam começar com a URL base:
>
> |     Nome      |                  URL                   |
> | :-----------: | :------------------------------------: |
> | Play Serviços | https://teste.playservicos.com.br:3001 |

> **Resumo de nossos Endpoints**
>
> |      NOME       | METHOD |                      URL                      |               BODY               |              HEADER              |             RESPONSE             |
> | :-------------: | :----: | :-------------------------------------------: | :------------------------------: | :------------------------------: | :------------------------------: |
> |  LIGAR SORTEIO  |  GET   |  `{{URL}}/sorteio/:codigo_integracao/ligar`   |    [EXEMPLO](#ligar-sorteio)     |    [EXEMPLO](#ligar-sorteio)     |    [EXEMPLO](#ligar-sorteio)     |
> |  MARCAR NUMERO  |  POST  |  `{{URL}}/sorteio/:codigo_integracao/marcar`  |  [EXEMPLO](#marcar-n%c3%9amero)  |  [EXEMPLO](#marcar-n%c3%9amero)  |  [EXEMPLO](#marcar-n%c3%9amero)  |
> | ENCERRAR PRÊMIO |  GET   | `{{URL}}/sorteio/:codigo_integracao/encerrar` | [EXEMPLO](#encerrar-pr%c3%8amio) | [EXEMPLO](#encerrar-pr%c3%8amio) | [EXEMPLO](#encerrar-pr%c3%8amio) |
>
> **Obs:** O _codigo_integracao_ é um identificador único para cada praça no Sistema Deboni. Para testes, use o codigo de integração "demo".
> **Exemplo:** `https://teste.playservicos.com.br:3001/sorteio/demo/ligar`

## Documentação

### LIGAR SORTEIO

> Se o sorteio for ligado corretamente, retornará uma variavel com valor _true_. O sorteio será desligado automaticamente quando [encerrar](#encerrar-pr%c3%8amio) o último prêmio.
>
> #### Body
>
> ```javascript
> empty;
> ```
>
> #### Header
>
> |     KEY      |      VALUE       |
> | :----------: | :--------------: |
> | Content-Type | application/json |
> |  x-api-key   |  YOUR_AUTH_KEY   |
>
> #### Response successful
>
> ```javascript
> {
>   "success": true // or false
> }
> ```
>
> ##
>
> ##

### MARCAR NÚMERO

> Para usar esse Endpoint, um sorteio deve estar [ligado](#ligar-sorteio). Quando acabar os números do prêmio atual, use o Endpoint [Encerrar Prêmio](#encerrar-pr%c3%8amio), se houver um próximo prêmio, os próximos números marcados será referenciado automaticamente para esse próximo prêmio do atual sorteio.
>
> #### Body
>
> ```javascript
> {
> 	"numero": "YOUR_NUMBER" //1,2,3,4,5,6,7,8,9...60
>  // O número deve ser enviado entre duplas aspas "1", como String.
> }
> ```
>
> #### Header0
>
> |     KEY      |      VALUE       |
> | :----------: | :--------------: |
> | Content-Type | application/json |
> |  x-api-key   |  YOUR_AUTH_KEY   |
>
> #### Response successful
>
> ```javascript
> {
>   "success": true // or false
> }
> ```

### ENCERRAR PRÊMIO

> Se o prêmio for encerrado corretamente, retornará uma variavel com valor _true_. Caso haja um próximo prêmio, as próximas chamadas para o Endpoint [Marcar Número](#marcar-n%c3%9amero) será referênciada esse próximo prêmio. Se não houver um próximo Prêmio, o sorteio será desligado automaticamente.
>
> #### Body
>
> ```javascript
> empty;
> ```
>
> #### Header
>
> |     KEY      |      VALUE       |
> | :----------: | :--------------: |
> | Content-Type | application/json |
> |  x-api-key   |  YOUR_AUTH_KEY   |
>
> #### Response successful
>
> ```javascript
> {
>   "success": true // or false
> }
> ```
>
> ##

## Postman

> Caso você utilize postman, veja como importar nossa collection

1. Baixe o Postman nesse [link](https://www.postman.com/downloads/)
2. Importando collection
   1. Importar clicando no botão [![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/a5396673c44f40ed3169)
   2. Ou copie o texto raw desse [link](https://www.postman.com/collections/a5396673c44f40ed3169) e cole no campo abaixo
      1. ![Foto](https://raw.githubusercontent.com/donemerson/assets/master/play_servicos/tempsnip.png)
   3.
