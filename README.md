# Azure AI Search - Configuração e Exploração

Este guia descreve como configurar e explorar um índice de pesquisa do Azure AI Search.

## 1. Criando os Recursos no Azure

Antes de começar, certifique-se de ter uma conta no Azure e acesso ao portal do Azure.

### 1.1 Criar um Serviço de Pesquisa
1. Acesse o [Portal do Azure](https://portal.azure.com/).
2. Pesquise por **Azure AI Search**.
3. Clique em **Criar** e preencha os detalhes:

![image](https://github.com/user-attachments/assets/2624c7c1-da3a-41d5-bf47-2686e47a6e89)


   - **Nome**: Nome exclusivo do serviço
   - **Plano de Preços**: Escolha um adequado às suas necessidades
   - **Região**: Selecione a mais próxima de seus usuários
   - **Grupo de Recursos**: Selecione um existente ou crie um novo
4. Clique em **Revisar + Criar** e aguarde a implantação.

## 2. Criando um Índice

1. No portal do Azure, acesse o serviço de pesquisa criado.
2. Vá para **Índices** e clique em **Adicionar índice**.
3. Defina o esquema do índice:
   - **Nome do índice**
   - **Campos** (Exemplo: `id`, `title`, `description`, etc.)
   - **Chave primária**
   - **Habilitar pesquisa completa e filtros**
4. Clique em **Salvar**.

![image](https://github.com/user-attachments/assets/c2ff22ba-679f-4bef-b3ad-b3570fe4e7ef)


## 3. Carregando Dados

### 3.1 Utilizando o Portal do Azure
1. No serviço de pesquisa, vá para **Indexadores**.
2. Crie um novo indexador e escolha a fonte de dados (Blob Storage, SQL, etc.).
3. Configure os mapeamentos dos campos e agende a indexação.

![image](https://github.com/user-attachments/assets/9aa7fd13-9190-4187-a74f-ee9c1eb5649c)


![image](https://github.com/user-attachments/assets/21479f22-3810-42ac-b488-e8da34b09efd)

![image](https://github.com/user-attachments/assets/9128fe1d-9d11-4376-9593-cf4cb52cd6ad)

![image](https://github.com/user-attachments/assets/9f921624-7f17-45cc-b281-ac408dd72955)

### 3.2 Utilizando API REST
Envie dados para o índice via API REST:

```bash
curl -X POST "https://<seu-servico>.search.windows.net/indexes/<seu-indice>/docs/index?api-version=2023-07-01" \
    -H "Content-Type: application/json" \
    -H "api-key: <sua-api-key>" \
    -d '{
        "value": [
            {
                "id": "1",
                "title": "Azure Search",
                "description": "Serviço de pesquisa poderoso"
            }
        ]
    }'
```

## 4. Consultando Dados no Índice

### 4.1 Usando o Portal do Azure
1. No serviço de pesquisa, vá para **Explorar dados**.
2. Escolha o índice e execute consultas.

### 4.2 Usando API REST
Realize uma busca no índice:

```bash
curl -X GET "https://<seu-servico>.search.windows.net/indexes/<seu-indice>/docs?search=Azure&api-version=2023-07-01" \
    -H "api-key: <sua-api-key>"
```

## 5. Conclusão
Agora você tem um serviço de pesquisa funcional no Azure AI Search! Você pode expandir a solução adicionando indexadores automáticos, análise de texto avançada e personalizações para melhorar a experiência de busca.
