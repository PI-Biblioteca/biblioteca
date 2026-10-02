# Requisitos

Requisitos funcionais e não funcionais do sistema.


## Requisitos Funcionais

| ID | Descrição | Prioridade |
|---|---|---|
| RF01 | Permitir o cadastro de livros | Alta |
| RF02 | Permitir o cadastro de autores | Alta |
| RF03 | Permitir o cadastro de usuários | Alta |
| RF04 | Registrar empréstimos de livros | Alta |
| RF05 | Registrar a devolução de livros emprestados | Média |
| RF06 | Consultar livros disponíveis | Média |
| RF07 | Listar histórico de empréstimos | Baixa |

## Requisitos Não Funcionais

| ID | Descrição | Categoria |
|---|---|---|
| RNF01 | O usuário deve conseguir realizar operações principais, como consultar um livro ou iniciar uma devolução, em no máximo 3 interações após acessar a funcionalidade. | Usabilidade |
| RNF02 | As senhas dos usuários devem possuir no mínimo 8 caracteres. | Segurança |
| RNF03 | Dados sensíveis e credenciais devem ser armazenados e transmitidos utilizando mecanismos de proteção adequados. | Segurança |
| RNF04 | O sistema deve utilizar uma arquitetura organizada em camadas, facilitando sua manutenção e evolução. | Manutenção |
| RNF05 | As operações de consulta de livros e processamento de devolução devem apresentar resposta em até 2 segundos em condições normais de utilização. | Performance |

## Relação com a modelagem do sistema

Os requisitos funcionais estão relacionados às entidades e aos processos que compõem o Sistema Biblioteca. Cada requisito representa uma funcionalidade que utiliza, consulta ou modifica informações presentes na modelagem do sistema.

### RF01 — Cadastro de livros

O RF01 está relacionado à entidade **Livro**, responsável por armazenar as informações dos livros cadastrados no sistema. Os livros cadastrados formam o acervo da biblioteca e podem posteriormente ser consultados, emprestados e devolvidos.

### RF02 — Cadastro de autores

O RF02 está relacionado à entidade **Autor** e à relação entre **Autor** e **Livro**. Um autor pode estar associado a um ou mais livros, permitindo relacionar os autores aos livros existentes no acervo.

### RF03 — Cadastro de usuários

O RF03 está relacionado à entidade **Usuário**, que representa as pessoas cadastradas no sistema. Os usuários são necessários para que os empréstimos possam ser registrados e associados à pessoa responsável pela operação.

### RF04 — Registro de empréstimos

O RF04 está relacionado às entidades **Empréstimo**, **Livro** e **Usuário**. O empréstimo registra qual usuário realizou a operação e qual livro foi emprestado, além das informações referentes à data do empréstimo e ao prazo de devolução.

### RF05 — Registro de devolução

O RF05 está relacionado à entidade **Empréstimo**, pois a devolução encerra ou atualiza um empréstimo que estava em aberto.

Durante a devolução, devem ser verificados os dados da operação, incluindo a data de devolução e a existência de possível atraso. Após o processamento da devolução, a situação do livro deve ser atualizada, permitindo que ele volte a ser considerado disponível.

### RF06 — Consulta de livros disponíveis

O RF06 está relacionado à entidade **Livro** e ao controle da situação ou disponibilidade dos livros.

A consulta deve permitir identificar quais livros do acervo estão disponíveis para empréstimo, considerando os empréstimos e as devoluções registrados no sistema.

### RF07 — Histórico de empréstimos

O RF07 está relacionado às entidades **Empréstimo** e **Usuário**.

O histórico permite consultar os empréstimos realizados, identificando o usuário relacionado à operação, o livro emprestado e as informações referentes ao empréstimo e à devolução.

## Relação com o escopo atual do sistema

O escopo atual do **Sistema Biblioteca** contempla o gerenciamento básico de livros, autores e usuários, além do controle de empréstimos e devoluções.

Os requisitos RF01, RF02 e RF03 representam os cadastros necessários para o funcionamento do sistema. O RF04 utiliza essas informações para registrar os empréstimos, enquanto o RF05 representa o processo de devolução dos livros.

O RF06 permite consultar a disponibilidade dos livros após as operações de empréstimo e devolução. O RF07 mantém o histórico das operações realizadas.

### Relação com a unidade funcional de devolução

A unidade funcional de **devolução** está diretamente relacionada ao **RF05**, que representa o registro da devolução de um livro emprestado.

Entretanto, essa funcionalidade depende de outros requisitos para funcionar corretamente. O **RF04** fornece o empréstimo que será encerrado ou atualizado pela devolução. As entidades **Empréstimo**, **Livro** e **Usuário** fornecem os dados necessários para identificar a operação.

Durante a devolução, devem ser verificados os dados da operação, incluindo a data de devolução e a existência de atraso. Após a conclusão, a situação do **Livro** deve ser atualizada.

Essa atualização possui relação com o **RF06**, pois o livro devolvido poderá voltar a ser apresentado como disponível. A operação também possui relação com o **RF07**, pois a devolução faz parte das informações que compõem o histórico de empréstimos.

Assim, a unidade funcional de devolução está integrada ao controle de empréstimos, à disponibilidade dos livros e ao histórico das operações do Sistema Biblioteca.
