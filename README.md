# Estudos de Arquitetura

```
Arquitetura são as de decisões significativas sobre a organização de um sistema de software.
Essas decisões são consideradas "significativas" porque têm um impacto substancial na estrutura
do sistema, na sua manutenção, na sua operação e, em última análise, no sucesso do projeto como um todo.
```

## Decisões Básicas

Aqui estão os conceitos básicos de programação que são decisivos em todos os projetos:

- [Classes](basic/classes.md), [Métodos](basic/methods.md), [Variáveis](basic/variables.md), [Comentário ](basic/comments.md), [Imports](basic/imports.md), [Pacotes](basic/packages.md), [SOLID](basic/solid.md), [GitHub](gitHub/gitHub.md).

Cada uma dessas categorias representa uma decisão arquitetural que pode afetar diretamente a qualidade e a robustez de um sistema de software.


## Estruturas

### [Clean Modular](architecture/clear_modular/clear_modular.md)

Esta arquitetura é uma abordagem no desenvolvimento de software que se baseia nos princípios da Arquitetura Limpa (Clean Architecture). Ela é ideal para projetos que necessitam de uma estrutura robusta e escalável. Esta arquitetura será ajustada especificamente para o seu aplicativo.

### [Flex Domain](architecture/flex_domain/flex_domain.md)

Esta arquitetura é especialmente útil para projetos que requerem uma separação clara de responsabilidades entre as diferentes partes do sistema. Esta arquitetura será ajustada especificamente para o seu aplicativo.

### [MVC+R](architecture/MVC+R/MVC+R.md)

A arquitetura ``MVC+R`` é uma abordagem simples que consome dados de uma API e os exibe na tela com o mínimo de processamento. Em um fluxo básico, o dado vem do repositório, segue para o controlador e é então apresentado na tela. Esta arquitetura é ideal para projetos que necessitam de uma rápida entrega de dados ao usuário. Esta arquitetura será ajustada especificamente para o seu aplicativo.

---

**Recomendação para Projetos**:
> **X**: Indica que a arquitetura é a mais indicada para o tipo de projeto em questão. Isso significa que, com base nas características do projeto, essa arquitetura é a mais adequada.
> 
> **O**: Indica que a arquitetura também é aceita para o tipo de projeto. Embora não seja a opção mais indicada, ainda é uma escolha viável e pode ser usada se necessário.

| Tipo de Projeto | Clean Modular | FlexiDomain | MVC+R |
|:----------------|:-------------:|:-----------:|:-----:|
| Uma API         |               |             |   X   |
| Mais de uma API / Possibilidade de migração |               |      X       |       |
| Um SAAS         |       X       |      O      |       |
| Uma API com SAAS|       X       |             |       |
| Uma API com DB_local |    X    |      O      |       |
| Um DB_local     |               |             |   X   |
| Um SAAS com DB_local |    X    |             |       |

---
> [!IMPORTANT]
> Embora essas arquiteturas forneçam uma estrutura base, elas são flexíveis e podem ser adaptadas para atender às necessidades específicas do seu aplicativo. Isso significa que, enquanto a arquitetura fornece um roteiro geral, a implementação específica pode variar dependendo dos requisitos do seu aplicativo.
>
> Portanto, enquanto você começa com uma dessas arquiteturas base, o resultado final será uma arquitetura personalizada que é perfeitamente adequada para o seu aplicativo. Isso permite que você aproveite os benefícios dessas arquiteturas comprovadas, ao mesmo tempo que garante que o seu aplicativo seja único e otimizado para as suas necessidades específicas.
> 
> **EXEMPLOS:**
>
> Aqui está a documentação arquitetural de uma aplicação, na qual temos uma API e apenas um serviço da Google para consumo externo: [MVC+R](real_cases/mvc+r.md).
