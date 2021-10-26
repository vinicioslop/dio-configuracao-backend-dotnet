# Configuracao da Arquitetura Backend com .NET Core

## Anotações da primeira parte

- Apagar os arquivos criado como padrão: "WeaterForecast"
- Ir em properties, "launchSettings.json"
  - Apagar as referencias a "weaterforecast", deixando vazio
- Em "Controllers", clicar com o botão direito e criar um novo controlador com base em API vazio chamado "UsuarioController"
- Cria-se uma pasta chamada "Models", e dentro dela uma pasta chamada "Usuarios"
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
- Cria-se a pasta "Filters" na raiz do projeto e dentro dela se cria o "ValidacaoModelStateCustomizado.cs"

## Anotações da segunda parte

- Abrir o gerenciador de pacotes do NuGet e instalar:
  - "Microsoft.AspNetCore.Authentication"
  - "Microsoft.AspNetCore.Authentication.JwtBearer" verificar problemas com a versão mais recente
  
- Em "Startup.cs" adicionar o trecho "var secret...;" e "services.AddAuthentication()"

- Em "appsettings.json" adicionar " "JwtConfigurations":  "Secret", "

- Em "UsuarioController.cs" adicionar a lógica para login

- Dentro de "Controllers" criar o controller "CursosController.cs"

- Dentro da pasta "Models" criar a pasta "Cursos"

  - Dentro da pasta criada criar a classe "CursoViewModelInput.cs"
  - Dentro da pasta criada criar a classe "CursoViewModelOutput.cs"

- Em "Startup.cs" adicionar o trecho acima de "app.UseAutorization()" "var o trecho "app.UseAuthentication()"

  

  ## Anotações da segunda parte

- Dentro da raiz do projeto criar as pastas "Business" e "Infraestruture"

- Dentro de "Business" criar a pasta "Entities"

  - Dentro dessa pasta criar as classes "Usuario" e "Curso"

- Instalar a dependência ao "Microsoft.EntityFrameworkCore" através do gerenciador de pacotes NuGet

- Dentro da pasta "Infraestruture" criar a classe "CursosDbContext.cs"

