## Branchs
A criação de novas branches, tal como a sua nomenclatura, deve ser feita exclusivamente pela geração automática do GitHub através das issues.
### Main
- **Não é permitido** realizar nenhum commit diretamente na branch main.
- **Não é permitido** realizar pull requests sem que a branch de origem esteja desatualizada em relação à branch main.
- **Não é permitido** realizar pull requests com arquivos que gerem conflitos perante o merge automático.
### Branchs auxiliares
Além das branchs associadas às issues do projeto, estão presentes no repositório branchs auxiliares que devem ser utilizadas apenas para os seguintes respectivos propósitos:
- **architecture:** refatorações concernentes a adequações à presente arquitetura;
- **bugs:** correções de problemas ínfimos de execução que tenham passado desapercebidos em um merge e cuja dimensão dispense a criação de uma issue;
- **docs:** documentações de qualquer trecho do código e alterações em arquivos Markdown;
- **layout:** alterações pequenas de apresentação que não afetem a execução da aplicação e cuja dimensão dispense a criação de uma issue;
- **tests:** alterações em arquivos de teste.
## Commits
Os commits devem ser simples, de forma a não abranger muitos [tipos](#padrão-de-tipos-de-commit). A mensagem do commit deve ser sucinta, clara, consistente com o seu [tipo](#padrão-de-tipos-de-commit) e em inglês.
### Padrão de tipos de commit
|**Palavra-chave**|**Intenção do commit**|**Exemplos**|
|:-:|:-:|:-:|
|**build**|mudanças que afetam o processo de build do projeto ou dependências externas|Gulp, adicionar/remover dependências do npm|
|**chore**|mudanças no projeto que não afetem o sistema ou arquivos de testes. São mudanças de desenvolvimento|Mudar regras do eslint, adicionar prettier, adicionar mais extensões de arquivos ao .gitignore|
|**ci**|mudanças nos arquivos de configuração de CI|Circle, Travis, BrowserStack, etc|
|**docs**|mudanças na documentação do projeto|Adicionar informações na documentação da API, mudar o README, etc|
|**feat**|desenvolvimento de uma nova feature ao projeto|Acréscimo de um serviço, funcionalidade, endpoint, etc
|**fix**|utilizado quando há correção de erros que estão gerando bugs no sistema|Aplicar tratativa para uma função que não está tendo o comportamento esperado e retornando erro|
|**perf**|uma alteração que melhorou a performance do sistema||
|**refactor**|refatoração de código que não tenha qualquer tipo de impacto na lógica/regras de negócio do sistema|Mudanças de código após um code review|
|**revert**|reversão de um commit anterior||
|**style**|mudanças de formatação e estilo do código que não alteram o sistema de nenhuma forma|Mudar o style-guide, mudar de convenção lint, arrumar indentações, remover espaços em brancos, remover comentários, etc|
|**test**|criação ou alteração de códigos de teste|Criação de testes unitários|


[<= Voltar](/README.md)