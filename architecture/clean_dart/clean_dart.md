# clean dart

A arquitetura é inspirada na proposta do clean dart 2.0, encontrada no repositório [Clean Dart](https://github.com/Flutterando/Clean-Dart/tree/2.0) da comunidade Flutterando.

--

A proposta de Arquitetura de desacoplar as camadas se baseia em:

``
DATA - DOMAIN - UI
``

### DATA

Esta camada dá suporte a camada Interactor implementando suas interfaces. Para isso, adapta os dados externos para que possa cumprir os contratos do domínio.

Muito provavelmente nessa camada iremos implementar alguma interface de um Repository ou Services que pode ou não depender de dados externos como uma API ou acesso a algum Hardware como por exemplo Bluetooth.

Para que o Repository possa processar e adaptar os dados externos devemos criar contratos para esses serviços visando passar a responsabilidade de implementação para a camada mais baixa da nossa arquitetura.

Basicamente a camada DATA deve conter tudo aquilo que terá grandes chances de ser alterado sem que o programador possa intervir diretamente no projeto.

### DOMAIN

A camada de `DOMAIN` hospedará as Regras de Negócio da aplicação junto aos seus estados. O núcleo da camada será a elaboração do estado e a prograpação por de alguma abordagem de gerenciamento de estado.

Tomando um Repository como exemplo, teremos que ter apenas o contrato de interfaces(Abstrações) e a responsabilidade de implementação desse objeto deverá ser repassado a outra camada mais baixa.

### UI

A Camada `UI` fica responsável por declarar as entradas, saídas e interações da aplicação.

Usando o Flutter como exemplo, hospedaremos os Widgets e Pages, já no backend como exemplo, seria nesta camada onde colocaríamos os Handlers ou Commands da nossa API.

---

### Modularize
Podemos manter nossas camadas para a aplicação inteira, mas podemos ter um melhor proveito criando as camadas Interactor, Data e UI para cada Modulo.

```
.
└── lib/
    ├── app/
    │   ├── core/
    │   │   └── ...
    │   └── modulos/
    │       ├── auth/
    │       │   ├── data/
    │       │   ├── domain/
    │       │   └── ui/
    │       ├── home/
    │       │   ├── data/
    │       │   ├── domain/
    │       │   └── ui/
    │       └── ...
    └── main.dart
```

## Estrutura:

### Core
Componentes centrais do código, compartilhados entre os módulos:
- **errors:** interface de erro `AppError` da qual devem descender todos os subtipos erro tratados na aplicação;
- **routes:** classes para definição e gerenciamento de rotas;
- **theme:** classes para gerenciamento de temas e componentes de UI;
- **utils:** elementos de valor constante, enums, extensões e classe para centralizar validadores de formulários;
- **widgets:** todos os widgets componentizados e/ou personalizados que sejam utilizados por mais de um [module](#modules).

### Modules

Módulo ou recurso específico do aplicativo.

#### data/

- **datasources/**

    **search_datasource.dart**: implementação genérica para fontes de dados.

    **search_datasource_Interface.dart**: Interface genérica para fontes de dados.

- **models/**
 **exemplo_model.dart**: Modelo de dados para os resultados, utilizado para serialização/deserialização.

- **repositories/**
 **exemplo_repository.dart**: Implementação do repositório que abstrai o acesso aos dados.

- **errors/**
 **errors.dart**: Erros específicos.

#### domain/

- **controller/**
 **exemplo_bloc.dart**: Componente de lógica de negócios para o gerenciamento do estado.

- **entities/**
 **exemplo_entities.dart**: Entidade de domínio que representa o resultado.

- **errors/**
 **errors.dart**: Erros específicos.

- **repositories/**
 **exemplo_repository_Interface.dart**: Interface do repositório utilizada pela lógica de negócios.

- **states/**
 **exemplo_state.dart**: Estados possíveis.

#### ui/

- **exemplo_page.dart**: Tela de interface do usuário.
- **components:** componentes visuais utilizados apenas pelo módulo referido;