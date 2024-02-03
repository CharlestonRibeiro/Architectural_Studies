
## Packages
### Injeção de dependências
O sistema de injeção de dependências da aplicação é feito através do ***

### Gerenciamento de estados
O projeto utiliza o *** como padrão para o gerenciamento de estados. Todas as classes de controller devem descender da classe `Cubit`. 

### Gerenciamento de rotas
Para aprimorar a flexibilidade e a independência de pacotes externos, o projeto utiliza uma abstração customizada para navegação. Isso permite uma maior liberdade no gerenciamento de rotas e transições de tela, bem como uma fácil manutenção e substituição do sistema de navegação.

As rotas são definidas de forma abstrata e centralizada na pasta `Routes`, na camada [core](#core), permitindo uma referência clara e consistente aos caminhos utilizados no aplicativo.

A implementação da instância atual de `Routes` é feita também através do package ***

### Requisições de API
As requisições HTTP são feitas através do package ***.


### Widgets
A aplicação deve ser construída com o máximo aproveitamento dos presentes no Flutter. É proibida a utilização de packages de widgets prontos que venham a ferir este princípio.

### Inserção de novos packages (regra geral)
A inserção de novos packages só é permitida após aprovação **unânime** do grupo de desenvolvedores da aplicação.
