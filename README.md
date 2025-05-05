# exemplo
Bootcamp

Passo 1: Criação do Repositório no GitHub
Acesse sua conta do GitHub.
Clique no botão "New" (Novo repositório).
Escolha um nome para o repositório, como azure-sql-project.
Adicione uma descrição opcional e escolha se deseja torná-lo público ou privado.
Clique em "Create repository".
Passo 2: Configurar o Banco de Dados SQL no Azure
Acesse o Portal do Azure:
Faça login no Azure Portal.
Crie um Banco de Dados SQL:
Clique em "Criar um recurso" no menu lateral.
Pesquise por "Banco de Dados SQL" e selecione a opção.
Configure os seguintes campos:
Nome do banco de dados.
Grupo de Recursos (crie um novo ou use um existente).
Escolha um servidor SQL (ou crie um).
Configure os níveis de desempenho e clique em "Revisar + Criar".
Após a criação, anote as credenciais do servidor SQL (nome do servidor, login e senha).
Passo 3: Conectar o Repositório GitHub com o Azure
No portal do Azure, procure pelo serviço Azure DevOps.
Crie um projeto no Azure DevOps (ou use um existente).
Configure a integração com seu repositório do GitHub:
Vá para "Configurações do Repositório".
Configure o repositório remoto do GitHub.
Dê permissões para o Azure acessar o repositório.
Passo 4: Criar Scripts SQL
Localmente, clone o repositório:
bash
git clone https://github.com/SeuUsuario/azure-sql-project.git
cd azure-sql-project
Crie arquivos SQL, como:
create_tables.sql
populate_data.sql
queries.sql
Adicione os arquivos ao repositório:
bash
git add .
git commit -m "Adicionando scripts SQL"
git push origin main
Passo 5: Automatizar a Implantação (Opcional)
Você pode usar Azure Pipelines para implantar scripts automaticamente no banco de dados:

No Azure DevOps, configure um pipeline.
Use um arquivo YAML para definir a implantação. Exemplo:
YAML
trigger:
- main

pool:
  vmImage: 'ubuntu-latest'

steps:
- task: AzureCLI@2
  inputs:
    azureSubscription: 'MinhaAssinaturaAzure'
    scriptType: 'bash'
    scriptLocation: 'inlineScript'
    inlineScript: |
      sqlcmd -S nome-do-servidor.database.windows.net -U usuario -P senha -d NomeDoBanco
