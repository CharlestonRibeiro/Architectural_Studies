### Métodos (funções)
1. Todos os métodos devem ser nomeados com verbos ou expressões verbais que descrevam exatamente o que executam.
```dart
const pi = 3.14;

double calculateCircleArea(double radius) => pi * radius * radius;

double calculateCirclePerimeter(double radius) => 2 * pi * radius;
```
2. Devem ser evitadas descrições redundantes e implícitas pelo escopo em que o método se encontra.
```dart
// Por pertencerem à classe Circle, é necessariamente implícito que os métodos retornem
// valores de área e perímetro referentes àquela classe.

class Circle extends Shape {
    double get calculateArea => ...
    double get calculatePerimeter => ...
}
```
3. Nenhum método pode executar ações que não sejam intrínsecas ao que descreve sua nomenclatura. Se um determinado comportamento previsto interliga mais de uma ação, ambas devem ser encapsuladas.
```dart
//code smell
void void stockProduct(int qtd, double price) {
    addCashOnCashDesk(qtd * price);
    decreaseProductFromStock(qtd);
}

// good code
void sellProduct(int qtd, double price) {
    addCashOnCashDesk(qtd * price);
    decreaseProductFromStock(qtd);
}
```
4. Todos os métodos de uso exclusivamente interno de uma classe devem ser declarados privados, exceto se a própria classe for privada (ex.: subclasses de estado de [StatefulWidgets](https://api.flutter.dev/flutter/widgets/StatefulWidget-class.html)).
```dart
class Dog {
    void showJoy() {
        _bark();
        _jump();
        _lick();
    }

    void _bark() { ... }
    void _jump() { ... }
    void _lick() { ... }
}
```
5. Getters podem ser utilizados apenas para substituir métodos que:
   - não utilizam nenhuma variável externa à classe
   - não enviam informações para outras camadas
```dart
// code smell
class Circle {
    final double radius;

    double get calculateArea => return _repository.saveShapeArea(radius);
}

// good code
class Circle {
    final double radius;

    double get calculateArea => 3.14 * radius * radius;

    void saveArea() {
        _repository.saveShapeArea(radius);
    }
}
```

[<= Voltar](/README.md)