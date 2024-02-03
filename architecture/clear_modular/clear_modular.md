# Clear Modular


### A estrutura:

### Core
Componentes centrais do código, compartilhados entre os módulos:
- **errors:** interface de erro `AppError` da qual devem descender todos os subtipos erro tratados na aplicação;
- **routes:** classes para definição e gerenciamento de rotas;
- **theme:** classes para gerenciamento de temas e componentes de UI;
- **utils:** elementos de valor constante, enums, extensões e classe para centralizar validadores de formulários;
- **widgets:** todos os widgets componentizados e/ou personalizados que sejam utilizados por mais de um [module](#modules).

### Data
Camada responsável pelo processamento de dados: a transcrição de dados brutos em objetos modelados e vice-versa.
- **errors:** classes de erros relativos ao gerenciamento de dados;
- **mappings:** extensões para classes [model](#domain) que fornecem métodos `fromMap` e `toMap` para a conversão de dados e funcionalidades adicionais;
- **repositories:** classes que implementam as interfaces das quais dependem os [usecases](#domain);
- **sources:** interfaces de recursos externos que serão implementadas na camada [external](#external).

### Domain
Domínio da aplicação, onde se encontram as abstrações de todos os cenários reais que a mesma abrange:
- **errors:** classes de erros disfuncionais, relativos a problemas de lógica interna às regras de negócios;
- **interfaces:** interfaces responsáveis pelo gerenciamento dos dados emitidos pelo domínio;
- **models:** classes que representam entidades de dados reais modelados para uso na aplicação;
- **usecases:** classes que implementam as regras de negócio específicas de cada caso de uso.

### External
Todos os recursos de persistência externos à aplicação:
- **localdb:** classes que implementam requisições de banco de dados em cache local;
- **clients:** classes que implementam requisições de API e bancos em nuvem;
- **errors:** classes de erros relacionados a estado de conexão ou falhas de requisição (ex.: caminhos não existentes);
- **services:** implementadores de requisições de dados simples em persistência local.

### Modules
Funcionalidades (módulos) da aplicação, onde individualmente se encontram:
- **components:** componentes visuais utilizados apenas pelo módulo referido;
- **views:** subpáginas do módulo referido (layouts construídos em estado de sucesso e/ou blocos de navegação internos ao módulo);
- ***example*_controller.dart:** cubits ([package: bloc](#gerenciamento-de-estados)) que realizam o gerenciamento de estados do módulo e a chamada dos [usecases](#domain);
- ***example*_page.dart:** página principal do módulo, para onde se refere a raiz da navegação do módulo referido e onde acontece o gerenciamento de estados;
- ***example*_states.dart:** estados gerenciados pelo controller;
- ***example*_module.dart:** subclasse de Module ([package: flutter_modular](#injeção-de-dependências)) onde é feita a injeção de dependências e o gerenciamento de sub-rotas.