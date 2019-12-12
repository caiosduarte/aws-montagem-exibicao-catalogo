# Modelagem e Cadastramento de Produtos
## Modelagem
A abordagem Contract-First ou API-First Development feita com o Swagger Editor (editor.swagger.io) no padrão OpenApi 3.0.0.

### Modelagem de Dados
Definição dos dados que serão recebidos e retornados pela API:


![Modelo de Dados](modelo-de-dados.png)

A partir de um Fornecedor cadastrado, criamos um Produto.

No swagger a modelagem de dados foi feita na seção schemas:

#### Fornecedor
##### Swagger 
``` javascript
  schemas:
    Fornecedor:
      type: object
      properties:
        id:
          type: integer
          format: int32
        razaoSocial:
          type: string
        nomeFantasia:
          type: string
        cnpj:
          type: string
          pattern: '^\d{14}$'
        status:
          type: string
          description: Status do Fornecedor
          enum:
          - ativo
          - inativo
        site:
          type: string
      required:
        - id
        - razaoSocial
        - nomeFantasia
        - cnpj
        - site
```     
##### HTML
![Modelo de Dados](schema-fornecedor.png)


#### Produto
##### Swagger 
``` javascript
    Produto:
      type: object
      properties:
        id:
          type: integer
          format: int64
          description: Identificador interno do Produto
        referencia:
          type: string
          description: Referência do fabricante do Produto
        codigoNoFornecedor:
          type: string
          description: 'Identificador do Produto no Fornecedor'
        descricao:
          type: string
          minLength: 2
        marca:
          type: string
          minLength: 2
        estoque:
          type: number
          format: double
          description: Quantidade do Produto em estoque
        preco:
          type: number
          format: double
        categorias:
          type: array
          items:
            type: string
            description: Categorias do Produto
        detalhes:
          type: object
          additionalProperties: {}
          description: 'Características detalhadas do produto: peso, tamanho, polegadas, acessórios, etc. (free-form object)'
        imagens:
          type: array
          items:
            $ref: '#/components/schemas/Imagem'
        url:
          type: string
          format: uri
      required: 
        - id
        - codigoNoFornecedor
        - descricao
        - marca
        - preco
        - categorias
        - url
```     
##### HTML
![Modelo de Dados](schema-produto.png)


### URIs
As URIs dos recursos na seção paths:

Swagger | HTML


### Parâmetros


### Responses
 (via API Fornecedores de uma interface de administração)

### Resultado do POST


