
# APLICAÇÃO DOS PRINCÍPIOS SOLID
Toda a arquitetura do presente projeto se baseia nos princípios do SOLID:
## Responsabilidade Única (Single Responsibility Principle - SRP)
Uma classe deve ter apenas uma razão para mudar, significando que ela deve ter apenas uma responsabilidade.
```dart
// code smell
class User {
    String name;
    String email;

    User(this.name, this.email);

    void printInfo() { ... }

    Future<void> confirmEmail() async { ... }
}
```
```dart
// good code
class User {
    String name;
    String email;

    User(this.name, this.email);
}
```
No exemplo acima, a classe User deve lidar apenas com as propriedades do usuário, sem assumir responsabilidades adicionais como manipulação de dados ou lógica de negócio.
> **Todas** as classes do projeto devem assumir somente a sua responsabilidade específica dentro da responsabilidade geral da [camada](#camadas) a que pertence.
> 
> (Compreenda o [fluxo](#fluxo-de-funcionamento-das-camadas))
## Aberto/Fechado (Open/Closed Principle)
As classes devem ser abertas para extensão, mas fechadas para modificação.
```dart
// code smell
abstract class Shape {}

class Rectangle extends Shape {
  final double width;
  final double height;
  ...
}

class Circle extends Shape {
  final double radius;
  ...
}

class AreaCalculator {
  double calculate(Object shape) {
    if (shape is Rectangle) {
      final r = shape as Rectangle;
      return r.width * r.height;
    } else {
      final c = shape as Circle;
      return 3.14 * c.radius * c.radius;
    }
  }
}
```
```dart
// good code
abstract class Shape {
    double get area;
}

class Circle extends Shape {
    double radius;

    Circle(this.radius);

    @override
    double get area => 3.14 * radius * radius;
}
```
O exemplo acima mostra como podemos estender a funcionalidade da classe Shape criando subclasses, sem necessidade de alterar a classe Shape original, o que não acontece com a classe AreaCalculator se acrescentarmos outras extensões da classe Shape.
> **Todas** as classes declaradas devem conter em si quaisquer parâmetros absolutos e relativos referentes àquela abstração.
> 
> Em outras palavras, parâmetros referentes a uma abstração específica **nunca** devem ser declarados fora dela.
## Substituição de Liskov (Liskov Substitution Principle - LSP)
As subclasses devem ser substituíveis por suas classes base. Isso significa que objetos de uma classe base devem ser substituíveis por objetos de suas subclasses sem afetar a corretude do programa.
```dart
// code smell
class Rectangle {
    double width;
    double height;
    const Rectangle(this.width, this.height);
}

class Square extends Rectangle {
    const Square(double length): super(length, length);
}

void main() {
    final strangeSquare = Square(3);
    strangeSquare.width = 4;
}
```
```dart
// good code
abstract class Bird {
    void fly();
}

class Sparrow extends Bird {
    @override
    void fly() {
        print("O pardal está voando.");
    }
}

class Parrot extends Bird {
    @override
    void fly() {
        print("O papagaio está voando.");
    }
}

void makeBirdFly(Bird bird) {
    bird.fly();
}

void main() {
    final sparrow = Sparrow();
    final parrot = Parrot();

    makeBirdFly(sparrow);
    makeBirdFly(parrot);
}
```
Este princípio é ilustrado aqui pela capacidade de passar qualquer subclasse de Bird para a função makeBirdFly, sem alterar o comportamento esperado. O primeiro exemplo não respeita o LSP, pois permite que exista um quadrado com lados de tamanhos diferentes.
> **Todas** as subclasses declaradas no projeto devem implementar **sem erros** quaisquer métodos contidos em suas interfaces.
>
> Quando isso não se fizer possível, a classe não poderá ser considerada como uma implementação daquela interface.
## Segregação de Interface (Interface Segregation Principle - ISP)
Nenhuma classe deve ser forçada a depender de métodos que não utiliza.
```dart
// code smell
abstract class Device {
  void printContent();
  void scanContent();
}

class Printer implements Device {
  @override
  void printContent() { ... }
  void scanContent() {} // ???
}
```
```dart
// good code
abstract class Printable {
  void printContent();
}

abstract class Scannable {
  void scanContent();
}

class Printer implements Printable {
  @override
  void printContent() { ... }
}
```
Este exemplo demonstra o ISP pela criação de interfaces específicas (Printable e Scannable), evitando a necessidade de a classe Printer implementar métodos que não são pertinentes ao seu propósito.
> **Todas** as superclasses declaradas no projeto devem conter **apenas** parâmetros e métodos comuns a todas as suas subclasses.
## Inversão de Dependência (Dependency Inversion Principle - DIP)
Módulos de alto nível não devem depender de módulos de baixo nível. Ambos devem depender de abstrações.
```dart
abstract class DataRepository {
    void saveData(String data);
}

class CloudStorage implements DataRepository { ... }

class LocalStorage implements DataRepository { ... }

// code smell
class DataManager {
    final LocalStorage repository;

    void saveData(String data) {
        repository.saveData(data);
    }
}

// good code
class DataManager {
    final DataRepository repository;

    void saveData(String data) {
        repository.saveData(data);
    }
}
```
O DataManager deve depender da abstração DataRepository, permitindo a substituição de LocalStorage por CloudStorage sem alterar o DataManager, ilustrando a inversão de dependência.
> As classes concretas devem possuir uma interface que as represente sempre que houver mais de uma possibilidade de implementação no código. (Ou seja, classes dos tipos **client**, **service**, **repository**, **dto** e **state**).
> 
> A injeção de dependências deve **sempre** ser feita utilizando tais interfaces e **nunca** suas implementações.
