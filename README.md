# Back-end Engineer no [Guiabolso](https://www.guiabolso.com.br)

**Por favor, leia cada parágrafo atentamente. Todos são importantes**

Aqui no [Guiabolso](https://www.guiabolso.com.br) trabalhamos em times. Nosso time é multidisciplinar, com foco no produto e na evolução tecnológica dos nossos sistemas. 

Nosso ambiente é descontraído, prezamos pela qualidade e participação ativa dos desenvolvedores na construção da nossa plataforma. Temos um carinho especial pelo usuário, direcionando nossas decisões pela experiência e fazendo constantes ajustes para alinhar os nossos sistemas com as necessidades do mercado.

Hoje, trabalhamos com alguns grandes produtos:

- **Produtos financeiros**: canais de aquisição para produtos como cédito pessoal, cartão de crédito, investimento, seguro, previdência, etc
- **Controle financeiro**: uma ferramenta para gerenciamento de finanças pessoais, em um aplicativo, que se integra automaticamente com sua conta bancária (use e veja **;)**);
- **Transações**: transferir e receber dinheiro 24hs
- **GuiaBolso Connect**: uma plataforma de inteligência de dados que conecta pessoas e empresas com o intuito de viabilizar negócios.

No Back-end nós temos todo o ecossistema de microserviços em nuvem, na AWS. Discutimos constantemente as tecnologias que usamos e como melhorar a experiência para os nossos usuários e clientes, bem como um trabalho muito próximo com a equipe de design e produto. E pra saber mais sobre a tecnologia que usamos aqui, dê uma olhada no nosso [Tech-Radar](https://guiabolso.github.io/tech-radar/).

### Gostou de tudo que está aí em cima? Então vem pra cá!!!

Curtiu e quer fazer parte? Então bora fazer o desafio =)

Para você, **back-end engineer**, daremos o caminho das pedras. (Você pode achar outros desafios para outras áreas no [nosso github](https://github.com/GuiaBolso)

Temos um processo seletivo que é dividido em algumas etapas, que não necessariamente seguem essa ordem: 

- O desafio técnico (descrito nesse repositório);
- Um teste técnico em pair programming;
- Uma conversa com a nossa **equipe técnica linda**, pra fazer um fit cultural;
- Conversa com o **super topper time de Pessoas**.

### Qual o tal desafio técnico?

Estamos procurando profissionais que estejam bem familiarizados com a stack que estamos utilizando. 

Pensamos em um desafio imaginando um ecossistema que ajude a testar as nossas funcionalidades, tanto de front quanto as integrações.

#### Desafio

Imagina que você está construindo uma API que vai servir de mock para um serviço que já existe.

Nós vamos testar o seu desafio, apontando pra esse serviço um script que vai validar contrato e regra de negócio.

Se alguma das regras não estiver respeitada, seu desafio será negado =/.

- Você vai criar uma _API_ de transações que vamos usar como __mock__
- Essa _API_ deve ser uma _API_ __HTTP__
- Queremos que essa _API_ devolva um __JSON conforme um contrato específico__
- Esse código, __por ser um mock, não pode usar recursos externos ao código__ (Por ex.: banco de dados em memória, banco hospedado, memcached, etc)

O desafio **deve ser resolvido sem o uso de nenhuma biblioteca de terceiros** (com exceção do server)

#### Regras de negócio

Requisição:

- a `requisição` será um __GET__
- a `requisição` deve respeitar o formato `[GET] /<id>/transacoes/<ano>/<mes>`
- os parâmetros `<id>`, `<ano>` e `<mês>` são o `conjunto de dados`

Transação:

- dado um `conjunto de dados`, deve ser retornada uma lista de transações
- cada _transação_ deve seguir o [contrato de transação](#Contrato)
- a lista de transações deve ter `um total de transações igual ao mês, multiplicado pelo primeiro dígito do id`. Ex.: id `2995`, mês `7`, `2 * 7 = 14 transações na lista`
- dado dois `conjuntos de dados` iguais, as respostas devem ser as mesmas
- isso significa que, **para um mesmo id, mês e ano, deve ser retornada a mesma lista**

Id:

- o id de usuário é um `número inteiro` de `1.000 a 100.000`

Descrição:

- cada transação deve ter `descrição aleatória legível`
- vocês devem criar a lógica para gerar essa `descrição aleatória legível`
- a descrição deve ter o tipo `string`
- essa `descrição aleatória legível` deve ser legível por humanos, isso significa que `YhCekEr13RH` não é válido, enquanto `chaconapotalo pocanoçale` é válido
- cada descrição deve ter no mínimo `10 caracteres`
- cada descrição não pode superar `60 caracteres`

Valor:

- cada transação deve ter um `valor baseado no id do usuário, no índice da transação e no mês`
- o valor da transação deve ser representado por um `número inteiro` (reais sem centavos)
- o valor da transação deve estar entre `-9.999.999 e 9.999.999`, inclusive

Data:

- cada transação deve ter uma `data aleatória` 
- o campo data deve ter o formato `timestamp` 
- o campo data deve ter o tipo `long`
- a data aleatória deve estar `dentro do range de ano e mês` dados

Tratamento de erro de input:

- utilize os `status HTTP` para representar os casos de exceção nas validações
- além do status, deve ser respondido o `motivo do erro`

#### Contrato

Transação

```
[GET] /<id>/transacoes/<ano>/<mes>

Content-type: application/json

[
  {
     "descricao": "string(10, 60)"
     "data": "long(timestamp)"
     "valor": "integer(-9.999.999, 9.999.999)"
  }  
]
```

### Quais são os requisitos?

Para tanto, você deverá construir uma aplicação com:

- Gradle (pois usamos aqui e configurar o gradle é um passo importante no dia a dia)
- Java 8+ ou Kotlin (pois é nossa stack principal)

**P.S.: lembre-se, este é um desafio de backend. O resultado, qualidade e performance também serão levados em conta. Se quiser, use um framework, mas não esqueça que a primeira impressão conta.**

### Como entrego?

Você nos envia um e-mail para **backmonstrao[arroba]guiabolso[ponto]com[ponto]br** contendo:

- Seu **nome completo**;
- Seu **telefone** para contato;
- Seu **LinkedIn** (se tiver);

- **Observações e comentário**s sobre o seu código que sejam interessantes apontar;
- **Onde você achou** esse repositório ("Fulaninho me indicou", "Vi no grupo X", "Tive um sonho consciente...", etc);

- Seu código ou URL do **repositório**;
- URL do seu sistema rodando (caso tenha hospedado no heroku, por ex) **opcional**


#### Usando um VCS online (Git, Mercurial, SVN...)

Cuide do repositório que vai mandar. Crie um __readme.md__, dê um nome semântico, zele pelo conteúdo que vai entregar. Lembre-se, esse desafio é __um resumo de como você trabalha__.

Você pode usar o github, o bitbucket, o gitlab ou qualquer alternativa do gênero.

**Mas eu estou empregado e não posso deixar isso público ou não vou usar github :(**

Se não quiser abrir o código fonte em um repositório, nos envie **compactado em Zip**.


### Pontos de avaliação

Veja, esse teste, além de um desafio, é uma forma de explorar e expressar sua desenvoltura com a plataforma. 

O foco da avaliação é a resolução do problema, sua familiaridade com o desenvolvimento, lógica e boas práticas, lembrando que há um caráter seletivo. 

Nesse sentido, alguns pontos que devem ser observados:

- Seu código deve _compilar_ e __rodar__.
- As respostas devem _respeitar o contrato_.
- Seu código deve _passar no nosso validador_.
- Arquitetura é um combinado. Defina qual é a que você quer serguir, _respeite a arquitetura escolhida e seja consistente_.
- Como você organiza seus arquivos, métodos, nomeia variáveis, lida com o seu código como um todo são outros pontos observados. _Seja cuidadoso, utilize boas práticas e padrões_.
- _Seja consistente_. Se escolher um approach mais _OO_, siga até o final, assim como se usar Spring, use os recursos dele.
- _Siga as boas práticas da ferramenta escolhida_, bem como respeite as boas práticas de código geral (um analisador estático pode te ajudar).
- _Codifique como você gostaria de trabalhar_.
- Imagine que esse código pode receber mais features, então tome cuidado com bagunças só pela entrega.
- **Leia todo o desafio, 3 vezes, até o final e escreva "BATATA" no final do seu e-mail de entrega. Queremos garantir que você conteve a ansiedade e está aproveitando a experiência**.

### O que provavelmente vamos olhar

- Organização de pastas
- Bibliotecas importadas
- Nome dos arquivos
- Separação de responsabilidades
- Lógica e a criatividade na solução
- Códigos HTTP escolhidos
- Headers retornados
- Performance

Vamos ler seu código, rodar, rodar nosso validador, apreciar o resultado, olhar, testar casos novos. 

Invista o tempo necessário para fazer um desafio que demonstre o resumo das suas capacidades técnicas. Faça com carinho.

Lembrando que estamos super a disposição então:

- Se não entender qualquer ponto do desafio, pode perguntar
- Se não conseguir fazer algo, pode perguntar e vamos te ajudar
- Se o tempo não for o suficiente, pode nos informar (não estamos avaliando tempo)
- Se no meio do caminho acontecer qualquer coisa (acabou a luz, deu ruim na maquina, etc) é só nos avisar

Não se preocupe currículo e linkedin nessa etapa, não vamos olhar para isso pois acreditamos que seu valor está na resolução do problema, familiaridade com o desenvolvimento, lógica e boas práticas.

Obrigado e boa sorte!

## Licença

versão 13-11-2020

<a rel="license" href="http://creativecommons.org/licenses/by/3.0/br/"><img alt="Licença Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by/3.0/br/88x31.png" /></a><br />Este repositório, texto, códigos e forks estão licenciados com uma Licença <a rel="license" href="http://creativecommons.org/licenses/by/3.0/br/">Creative Commons Atribuição 3.0 Brasil</a>.

As imagens e o nome **Guiabolso** são de propriedade do Guiabolso. Todos os direitos reservados **(c) 2020**.
