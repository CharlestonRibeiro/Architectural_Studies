# MVC-R

### Core
Componentes centrais do código, compartilhados entre os módulos:

- **routes:** classes para definição e gerenciamento de rotas;
- **theme:** classes para gerenciamento de temas e componentes de UI;
- **utils:** elementos de valor constante, enums, extensões e classe para centralizar validadores de formulários;
- **widgets:** todos os widgets componentizados e/ou personalizados que sejam utilizados por mais de um [module](#modules).

### Repositories
Camada de abstração para acesso a dados, responsável pela comunicação com fontes de dados externas:
- **example_repository**: Classe para autenticação e conversão de dados.
- **clients/clients.dart:** classes que implementam requisições de API;

### DTO (Data Transfer Object)
- **example_dto.dart**: Objetos utilizados para transferir dados entre processos, facilitando a comunicação com a API:

### Models
- **example_model.dart**: Representações de entidades de negócio usadas em todo o aplicativo.

### Modules
Funcionalidades (módulos) da aplicação, onde individualmente se encontram:
- **components:** componentes visuais utilizados apenas pelo módulo referido;
- **views:** subpáginas do módulo referido (layouts construídos em estado de sucesso e/ou blocos de navegação internos ao módulo);
- ***example*_controller.dart:** cubits ([package: bloc](#gerenciamento-de-estados)) que realizam o gerenciamento de estados.;
- ***example*_page.dart:** página principal do módulo, para onde se refere a raiz da navegação do módulo referido e onde acontece o gerenciamento de estados;
- ***example*_states.dart:** estados gerenciados pelo controller;
- ***example*_module.dart:** subclasse de Module ([package: flutter_modular](#injeção-de-dependências)) onde é feita a injeção de dependências e o gerenciamento de sub-rotas.

---

[<= Voltar](/README.md)
