# Configuracao da Arquitetura Backend com .NET Core

## Anotações da primeira parte

- Apagar os arquivos criado como padrão: "WeaterForecast"
- Ir em properties, "launchSettings.json"
  - Apagar as referencias a "weaterforecast", deixando vazio
- Em "Controllers", clicar com o botão direito e criar um novo controlador com base em API vazio chamado "UsuarioController"
- Cria-se um repositório chamada "Models", e dentro dela um repositório chamada "Usuarios"
- Dentro de "Usuarios" cria-se o arquivo "LoginViewModelInput"
- Dentro de "Usuarios" cria-se o arquivo "RegistroViewModelInput"
- Clicar com o botão direito no projeto, ir em propridades
  - Na aba build marcar XML documentation file
- No gerenciador de pacotes do NuGet procurar e instalar "swashbuckle.AspNetCore"
- Em "Startup.cs" adicionar
  - em "ConfigureServices": "services.AddSwaggerGen"
  - em "Configure"
    - "app.UseSwagger();"
    - "app.UseSwaggerUI()"
- No gerenciador de pacotes do NuGet procurar e instalar "swashbuckle.AspNetCore.Annotations"
- Dentro de "Models" cria-se os arquivos:
  - "ErroGenericoViewModel.cs"
  - "ValidaCampoViewModelOutput.cs"
- Em "Startup.cs" modificar o "services.AddControllers()"
- Cria-se o repositório "Filters" na raiz do projeto e dentro dela se cria o "ValidacaoModelStateCustomizado.cs"

## Anotações da segunda parte

- Abrir o gerenciador de pacotes do NuGet e instalar:
  - "Microsoft.AspNetCore.Authentication"
  - "Microsoft.AspNetCore.Authentication.JwtBearer" verificar problemas com a versão mais recente
  
- Em "Startup.cs" adicionar o trecho "var secret...;" e "services.AddAuthentication()"

- Em "appsettings.json" adicionar " "JwtConfigurations":  "Secret", "

- Em "UsuarioController.cs" adicionar a lógica para login

- Dentro de "Controllers" criar o controller "CursosController.cs"

- Dentro da repositório "Models" criar o repositório "Cursos"

  - Dentro do repositório criada criar a classe "CursoViewModelInput.cs"
  - Dentro do repositório criada criar a classe "CursoViewModelOutput.cs"

- Em "Startup.cs" adicionar o trecho acima de "app.UseAutorization()" "var o trecho "app.UseAuthentication()"

  

  ## Anotações da terceira parte

- Dentro da raiz do projeto criar os repositórios "Business" e "Infraestruture"

- Dentro de "Business" criar o repositório "Entities"

  - Dentro desse repositório criar as classes "Usuario" e "Curso"

- Instalar as dependências através do gerenciador de pacotes NuGet:

  - "Microsoft.EntityFrameworkCore"
  - "Microsoft.EntityFrameworkCore.Relational"
  - "Microsoft.EntityFrameworkCore.SqlServer"
  - "Microsoft.EntityFrameworkCore.Tools" 

- Dentro do repositório "Infraestruture" criar a repositório "Data"

  - Dentro deste repositório criar a classe "CursoDbContext.cs"
  - Dentro deste repositório criar o repositório "Mappings"
    - Dentro desta repositório criar as classes "UsuarioMapping.cs" e "CursoMapping.cs"

- "ctor + TAB" para gerar um construtor com o nome da classe atual

- Criar o repositório "Configurations" na raiz do projeto

  - Dentro deste repositório criar a classe "DbFactoryDbContext"

- Ir em Tools > NuGet Package Manager > Package Manager Console

  - ```powershell
    Add-Migration Base-inicial
    ```

## Anotações da quarta parte

- Dentro do repositório "Business" criar o repositório "Repositories"

  - Dentro dela criar a interface "IUsuarioRepository.cs"

- Dentro do repositório "Infraestruture > Data" criar o repositório "Repositories"

  - Dentro dela criar a classe "UsuarioRepository.cs"

- Em "Startup.cs" adcionar em "ConfigureServices"

  - ```c#
    services.AddScoped<IUsuarioRepository, UsuarioRepository>();
    ```

  - ```c#
    services.AddDbContext<CursoDbContext>(...);
    ```

- Em "appsettings.json" adiocionar:

  - ```json
    "ConnectionStrings": {
        "DefaultConnection": "Server=localhost\\SQLEXPRESS;Database=CURSO;TrustedConnection=True;"
      },
    ```

- Dentro do repositório "Configurations" criar a interface "IAuthenticationService.cs"

  - Dentro deste repositório criar a classe "JwtService.cs" que implementará "IAuthenticationService.cs"

- Dentro do repositório "Business > Repositories" criar a interface "ICursoRepository.cs"

- Dentro do repositório "Insfraestruture > Data > Repositories" criar a classe "CursoRepository.cs"

- Em "Startup.cs" adcionar em "ConfigureServices"

  - ```c#
    services.AddScoped<IAuthenticationService, JwtService>();
    ```

- 

