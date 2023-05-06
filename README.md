# 🚀 Projeto MVC com .NET 7 🚀

Esse é um projeto MVC com .NET 7, otimizado e utilizando o SOLID, com as views "Index", "Datas Eventos" e "Cadastro", sendo esta última protegida e autorizada somente para usuários administradores. O projeto utiliza um banco de dados SQL Server e o EntityFrameworkCore para migrações.

## Funcionalidades

- Cadastro e autenticação de usuários com JWT.
- Proteção de rotas e autorização para usuários administradores.
- Armazenamento de eventos em cache utilizando Redis.
- Criptografia de dados sensíveis.

## Estrutura Hierárquica

- **Controllers**: controladores da aplicação.
- **Data**: configurações e contextos do banco de dados.
- **Interfaces**: interfaces para serviços e repositórios.
- **Models**: modelos da aplicação.
- **Services**: serviços utilizados pelos controladores.
- **Utils**: utilidades, como a classe de criptografia.
- **Views**: arquivos das views da aplicação.

## Configurações

O projeto utiliza duas strings de conexão no arquivo de configuração `appsettings.json`, uma para o banco de dados SQL Server e outra para o Redis.

```
{
  "ConnectionStrings": {
    "SqlServerConnection": "Data Source=(localdb)\\MSSQLLocalDB;Initial Catalog=MvcProject;Integrated Security=True",
    "RedisConnection": "localhost:6379"
  },
  ...
}
```

Também é possível configurar o tempo de expiração do token JWT no mesmo arquivo:

```
{
  ...
  "JwtSettings": {
    "Key": "ChaveSecreta",
    "Issuer": "Issuer",
    "Audience": "Audience",
    "MinutesToExpiration": 60
  }
}
```

## Deploy

O projeto pode ser publicado para deploy em servidores IIS ou Apache utilizando o comando:

```
dotnet publish -c Release
```

Também é possível realizar o deploy em Docker, com o uso do Dockerfile na raiz do projeto.

## Referências

- [ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/?view=aspnetcore-5.0)
- [Entity Framework Core](https://docs.microsoft.com/en-us/ef/core/)
- [Stack Overflow](https://stackoverflow.com/)



## Publicação

```bash
# Para gerar a publish Release para deploy no IIS, você pode utilizar o comando dotnet publish em conjunto com as opções adequadas. Por exemplo:
dotnet publish -c Release -r win-x64 --self-contained true /p:PublishSingleFile=true
```
Onde:
 - -c Release: define que o build será feito em modo Release
 - -r win-x64: define que o runtime será para plataforma Windows 64-bit
 - --self-contained true: define que o publish irá incluir o runtime para a plataforma especificada
 - /p:PublishSingleFile=true: define que o output será gerado em um único arquivo executável

Após executar esse comando, será gerado um diretório publish com o conteúdo a ser publicado no servidor IIS. Você pode copiar o conteúdo desse diretório para o diretório wwwroot da aplicação no servidor IIS.


## Estrurua de Pastas

### Controllers
- `Admin`: contém os controllers relacionados à área administrativa da aplicação, como EventosController e UsuariosController.
- `HomeController`: contém a lógica para a página inicial da aplicação.
- `LoginController`: contém a lógica para a página de login da aplicação.
### Data
- `Configurations`: contém as configurações de entidades do EF Core, como EventoConfiguration e UsuarioConfiguration.
- `Migrations`: contém as migrações do EF Core para a criação e alteração do banco de dados.
- `DataContext`: lasse que representa o contexto do banco de dados, contendo as informações das tabelas e seus relacionamentos, com as seguintes pastas:
  - Configurations: pasta que contém as classes de configuração para cada entidade do banco de dados.
  - Migrations: pasta que contém as migrações criadas para o banco de dados.
  - Repositories: pasta que contém as classes de repositório para cada entidade do banco de dados.
  - Services: pasta que contém as classes de serviço para cada entidade do banco de dados.
  - Interfaces: pasta que contém as interfaces para os repositórios.
  - DTOs: pasta que contém as classes DTO (Data Transfer Object) para cada entidade do banco de dados.
  - Entities: pasta que contém as classes de entidade para cada tabela do banco de dados.
  
`Views`: pasta que contém as visualizações do aplicativo web, organizada por pastas específicas de acordo com as funcionalidades.
- Admin: pasta que contém as visualizações específicas da área de administração.
- Home: pasta que contém as visualizações da página inicial do aplicativo.
- Login: pasta que contém as visualizações para login do aplicativo.
- Shared: pasta que contém as visualizações compartilhadas entre as diferentes áreas do aplicativo.

- `Properties`: pasta que contém o arquivo launchSettings.json que é usado para configurar as propriedades de inicialização do projeto.
- `appsettings.json`: arquivo de configuração do aplicativo.
- `appsettings.Development.json`: arquivo de configuração do aplicativo específico para o ambiente de desenvolvimento.
- `appsettings.Production.json`: arquivo de configuração do aplicativo específico para o ambiente de produção.
- `Program.cs`: arquivo que contém o método Main do aplicativo.

- `README.md`: arquivo que contém a documentação do projeto.

- `app.db`: arquivo do banco de dados SQLite utilizado pelo aplicativo.
- `app.xml`: arquivo XML utilizado pelo aplicativo.


```
├── Controllers
│   ├── Admin
│   │   ├── EventosController.cs
│   │   ├── UsuariosController.cs
│   │   └── ...
│   ├── HomeController.cs
│   ├── LoginController.cs
│   └── ...
├── Data
│   ├── Configurations
│   │   ├── EventoConfiguration.cs
│   │   ├── UsuarioConfiguration.cs
│   │   └── ...
│   ├── Migrations
│   │   ├── 20220101000000_Initial.cs
│   │   ├── 20220102000000_AddEventos.cs
│   │   └── ...
│   ├── DataContext.cs
│   └── ...
├── Models
│   ├── DTOs
│   │   ├── EventoDTO.cs
│   │   ├── UsuarioDTO.cs
│   │   └── ...
│   ├── Entities
│   │   ├── Evento.cs
│   │   ├── Usuario.cs
│   │   └── ...
│   ├── Interfaces
│   │   ├── IEventoRepository.cs
│   │   ├── IUsuarioRepository.cs
│   │   └── ...
│   ├── Repositories
│   │   ├── EventoRepository.cs
│   │   ├── UsuarioRepository.cs
│   │   └── ...
│   ├── Services
│   │   ├── AuthService.cs
│   │   ├── EventoService.cs
│   │   ├── UsuarioService.cs
│   │   └── ...
│   └── ...
├── Properties
│   └── launchSettings.json
├── Views
│   ├── Admin
│   │   ├── Eventos
│   │   │   ├── Create.cshtml
│   │   │   ├── Edit.cshtml
│   │   │   ├── Index.cshtml
│   │   │   ├── Details.cshtml
│   │   │   └── ...
│   │   ├── Usuarios
│   │   │   ├── Create.cshtml
│   │   │   ├── Edit.cshtml
│   │   │   ├── Index.cshtml
│   │   │   ├── Details.cshtml
│   │   │   └── ...
│   │   └── ...
│   ├── Home
│   │   ├── Index.cshtml
│   │   └── ...
│   ├── Login
│   │   ├── Index.cshtml
│   │   └── ...
│   └── Shared
│       ├── _Layout.cshtml
│       ├── _Navbar.cshtml
│       ├── _Footer.cshtml
│       └── ...
├── appsettings.Development.json
├── appsettings.Production.json
├── appsettings.json
├── Program.cs
├── README.md
├── app.db
└── app.xml
```
