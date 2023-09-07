# API de Gerenciamento de Vídeos

Esta é uma API simples para gerenciar vídeos. Você pode criar, listar, atualizar e excluir vídeos usando os métodos HTTP apropriados.

## Configuração

### Instalação de dependências

Certifique-se de que você tenha Node.js instalado em sua máquina. Em seguida, navegue até o diretório raiz do projeto e execute o seguinte comando para instalar as dependências:

```bash
npm install
```

### Configuração do Banco de Dados
Esta API usa o PostgreSQL como banco de dados. Certifique-se de configurar um servidor PostgreSQL e criar um banco de dados para a API. Você pode configurar as credenciais do banco de dados no arquivo database-postgres.js.

### Variáveis de Ambiente
Você pode definir variáveis de ambiente, como a porta em que o servidor será executado. Por padrão, a API usará a porta 3333. Você pode substituir isso definindo a variável de ambiente PORT antes de iniciar o servidor.

## Uso
A API suporta as seguintes operações:

### 1. Criar um vídeo
Rota: POST /videos
Requisição:
Corpo da requisição deve conter um objeto JSON com as seguintes propriedades:
##### title (string): O título do vídeo.
##### description (string): A descrição do vídeo.
##### duration (number): A duração do vídeo em segundos.
Resposta: Retorna status 201 (Created) se a criação for bem-sucedida.

```json
POST /videos
{
  "title": "Meu Vídeo",
  "description": "Este é o meu primeiro vídeo",
  "duration": 120
}
```
### 2. Listar vídeos

Rota: GET /videos

    Requisição:
      parâmetro de consulta opcional:
        search (string): Um termo de pesquisa opcional para filtrar os vídeos.

Resposta:
Retorna uma lista de vídeos no formato JSON.

### Exemplo de requisição:

```json
GET /videos?search=meu
```

### 3. Atualizar um vídeo
#### Rota: PUT /videos/:id
#### Requisição:
    Parâmetro de rota:
       id (string): O ID único do vídeo que deseja atualizar.
    Corpo da requisição deve conter um objeto JSON com as propriedades que deseja atualizar:
##### title (string): O novo título do vídeo.
##### description (string): A nova descrição do vídeo.
##### duration (number): A nova duração do vídeo em segundos.
Resposta: Retorna status 204 (No Content) se a atualização for bem-sucedida.

Exemplo de requisição:
```json
PUT /videos/1
{
  "title": "Meu Novo Título",
  "description": "Este é o meu vídeo atualizado",
  "duration": 180
}
```

### 4. Excluir um vídeo
#### Rota: DELETE /videos/:id
#### Requisição:
    Parâmetro de rota:
      id (string): O ID único do vídeo que deseja excluir.
Resposta: Retorna status 204 (No Content) se a exclusão for bem-sucedida.

Exemplo de requisição:

```json
DELETE /videos/1
```

## Executando o Servidor
Para iniciar o servidor, execute o seguinte 
comando:



```bash
npm start
```

O servidor será executado na porta especificada no arquivo server.js ou na porta definida na variável de ambiente PORT.
