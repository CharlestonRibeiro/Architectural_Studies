
### Classes
1. Todas as classes devem ser nomeadas com substantivos que descrevam o que a classe representa.
1. **Não é permitido** o uso de prefixos ou sufixos de nenhuma natureza ao nomear [models](#domain).
1. As extensões de widgets devem receber **por sufixo** o widget que têm por base.
1. As classes que representam estados devem receber **por prefixo** o estado que representam.
1. As demais classes devem receber **por sufixo** apenas com a denominação que representa sua responsabilidade seguida, se for o caso, do sufixo `Interface`.

Exemplos:
```dart
// models
class User {}

// usecases
class AuthCase {}

// controllers
class HomeController extends Cubit<HomeState> {}

// modules
class HomeModule extends Module {}

// pages
class HomePage extends StatelessWidget {}

// states
class SuccessHomeState extends HomeState {}

// components
class PricingDialog extends Dialog {}
class CurrencyFormField extends TextFormField {}

// views
class HomeView extends StatelessWidget {}

// interfaces
abstract interface class ClientInterface {}

// errors
class ExternalError extends AppError {}
```

[<= Voltar](/README.md)