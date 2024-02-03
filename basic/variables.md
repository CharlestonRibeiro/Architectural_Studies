### Variáveis
1. Todas as variáveis devem ser nomeadas com substantivos que descrevam o que representam dentro do escopo a que pertencem.

```dart
// good code
int userAge;
double shippingCost;
List<String> productNames;

// code smell
int ua;
double sc;
List<String> pN;
```

1. Abreviações somente são permitidas em casos de amplo reconhecimento, de forma que não atrapalhem a legibilidade do código. (ex.: num, info, tel, max, min...)

```dart
// good code
int numPages;
String userInfo;
String telNumber;
double maxWeight;
double minWeight;

// code smell
int nPg;
String usrInf;
String tN;
double mxWt;
double mnWt;
```

1. Apenas métodos construtores poderão possuir mais de um parâmetro posicional, e utilizados apenas para injeção de dependências.


```dart
// good code
class UserRepository {
  final DatabaseConnector connector;
  final Logger logger;

  UserRepository(this.connector, this.logger);
}

// code smell
void updateUserInfo(String name, String email, String address) {
  // Implementação
}

```

[<= Voltar](/README.md)