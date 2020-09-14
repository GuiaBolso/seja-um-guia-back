# Back-end Engineer no [Guiabolso](https://www.guiabolso.com.br)

**Por favor, leia cada parágrafo atentamente. Todos são importantes**

Aqui no [Guiabolso](https://www.guiabolso.com.br) trabalhamos em times. Nosso time é multidisciplinar, com foco no produto e na evolução tecnológica dos nossos sistemas. 

Em um ambiente descontraído, prezamos pela qualidade e participação ativa dos desenvolvedores na construção da nossa plataforma. Temos um carinho especial pelo usuário, direcionando nossas decisões pela experiência e fazendo constantes ajustes para alinhar os nossos sistemas com as necessidades do mercado.

Hoje, trabalhamos com alguns grandes produtos:

- **Controle financeiro**: uma ferramenta para gerenciamento de finanças pessoais, em um aplicativo, que se integra automaticamente com sua conta bancária (use e veja **;)**);
- **Crédito pessoal**: canais de aquisição para crédito pessoal, com foco em ajudar o nosso usuário a sair daquela situação chata com o cartão ou o cheque especial.
- **GuiaBolso Connect**: uma plataforma de inteligência de dados que conecta pessoas e empresas com o intuito de viabilizar negócios


No Back-end nós temos todo o ecossistema de microserviços em nuvem na AWS. Discutimos constantemente as tecnologias que usamos e como melhorar a experiência para os nossos usuários e clientes, bem como um trabalho muito próximo com a equipe de design e produto. Dê uma olhada em como está nosso [Tech-Radar](https://guiabolso.github.io/tech-radar/), atualmente.

### Gostou de tudo que está aí em cima? Então vem pra cá!!!

Você quer trabalhar no Guiabolso? Vamos te ajudar!

Para você, **back-end engineer** (que é um desenvolvedor de software e **não um codador batedor de tecla**), daremos o caminho das pedras.

Temos um processo seletivo que é dividido em algumas etapas, que não necessariamente seguem essa ordem: 

- O desafio técnico (descrito nesse repositório);
- Um teste técnico em pair programming;
- Uma conversa com nossa **master blaster equipe técnica**, pra fazer um fit cultural;
- Conversa com o Time de Pessoas;

### Qual o tal desafio técnico?

Estamos procurando profissionais que estejam bem familiarizados com a stack que estamos utilizando. 

Pensamos em um desafio imaginando um ecossistema que ajude a testar as nossas funcionalidades, tanto de front quanto as integrações.

- Queremos __um mock__ de uma _API_ de transações
- Queremos uma _API_ __HTTP__
- Queremos que essa _API_ devolva um __JSON conforme um contrato específico__
- Queremos poder rodar essa _API_ usando [__docker__](https://www.docker.com/)
- Esse código, __por ser um mock, não pode usar recursos externos ao código__ (Por ex.: banco hospedado, memcached, etc)

#### Regras de negócio

- dado um `conjunto de dados`, formado por um id de usuário, um ano e um mês, deve-se retornar uma lista de transações
- a lista de transações deve ter `quantidade variável entre os meses`
- o id de usuário é um `número inteiro` de 1.000 a 100.000.000
- cada transação deve ter uma `descrição aleatória legível` no formato string
- essa `descrição aleatória legível` deve ser legível por humanos, isso significa que `YhCekEr13RH` não é válido, enquanto `chaconapotalo pocanoçale` é válido
- caso o conjunto de transações tenha duas ou mais transações com a `mesma descrição, data e valor`, todas, menos uma, `devem ter duplicated true`
- ao iterar 12 meses em um mesmo ano, `no mínimo 3 meses devem ter uma transação duplicada`
- cada descrição deve ter no mínimo `10 caracteres`
- cada descrição não pode superar `60 caracteres`
- cada transação deve ter um `valor aleatório`
- o valor da transação deve ser representado por um `número inteiro`
- o valor da transação deverá ter seus `2 últimos dígitos representando os centavos`
- um valor de `8989` representa, portanto, `R$ 89,89`
- o valor da transação deve estar entre `-9.999.999 e 9.999.999`, inclusive
- cada transação deve ter o `timestamp de uma data aleatória` em formato `long`
- a data aleatória deve estar `dentro do range de ano e mês` dados
- dado dois `conjuntos de dados` iguais, as respostas devem ser as mesmas _(pelo menos durante o dia que estivermos brincando)_
- utilize os `status HTTP` para representar os casos de excessão nas validações
- além do status, deve ser respondido o `motivo do erro`

#### Contrato

```
[GET] /<id>/transacoes/<ano>/<mes>

Content-type: application/json

[
  {
     "descricao": "string(10, 120)"
     "data": "long(timestamp)"
     "valor": "integer(-9.999.999, 9.999.999)"
     "duplicated": "boolean"
  }  
]
```

### Quais são os requisitos?

Para tanto, você deverá construir uma aplicação com:

- Gradle;
- Java 8+ ou Kotlin;
- Docker

**PS. lembre-se, este é um desafio de backend. O resultado, qualidade e performance também serão levados em conta. Se quiser, use um framework, mas não esqueça que a primeira impressão conta.**

### Como entrego?

Você nos envia um e-mail para **backmonstrao[arroba]guiabolso[ponto]com[ponto]br** contendo:

- Seu **nome completo**;
- Seu **telefone** para contato;
- Seu **LinkedIn** (se tiver);

- **Observações e comentário**s sobre o seu código que sejam interessantes apontar;
- **Onde você achou** esse repositório ("Fulaninho me indicou", "Vi no grupo X", "Tive um sonho consciente...", etc);

- Seu código
- Dockerfile

#### Com GIT

Cuide do repositório que vai mandar. Crie um readme.md, dê um nome semântico, zele pelo conteúdo que vai entregar. Lembre-se, esse desafio é um resumo de como você trabalha.

- URL do **repositório**;

**Mas eu estou empregado e não posso deixar isso público ou não vou usar github :(**

Se não quiser abrir o código fonte em um repositório, nos envie **compactado em Zip**

#### Hospedando

Caso queira, você pode hospedar uma versão aberta no Heroku ou algum serviço parecido

#### Com [Repl.it](https://repl.it/)

Caso queira criar e editar seu teste em qualquer lugar, você pode usar uma plataforma remota como o Repl.it.

- Sugestão: Entre com o seu GitHub
- Crie uma aplicação da linguagem escolhida
- Faça seu código ou importe
- Envie a URL do seu repl para nós.

### Pontos de avaliação

Veja, esse teste, além de um desafio, é uma forma de explorar e expressar sua desenvoltura com a plataforma backend. O foco da avaliação é a sua familiaridade com o desenvolvimenteo, lógica e boas práticas, lembrando que há um caráter seletivo. 

Nesse sentido, alguns pontos que devem ser observados:

- Seu código deve compilar
- Seu código deve subir na nossa máquina
- As respostas devem respeitar o contrato
- Arquitetura é um combinado. Defina qual é a que você quer serguir, respeite e seja consistente.
- Como você organiza seus arquivos, métodos, nomeia variáveis, lida com o seu código como um todo são outros pontos observados. Seja cuidadoso, utilize boas práticas e padrões.
- Seja consistente. Se escolher um approach mais _OO_, siga até o final, assim como se usar Spring, use os recursos dele.
- Siga as boas práticas da ferramenta escolhida, bem como respeite as boas práticas de código geral (um validador de qualidade pode te ajudar).
- Codifique como você gostaria de trabalhar.
- Imagine que esse código pode receber mais features
- **Leia todo o desafio, 3 vezes, até o final e escreva "BATATA" no final do seu e-mail de entrega.**

### O que provavelmente vamos olhar

- Organização de pastas
- Bibliotecas importadas
- Nome dos arquivos
- Separação de responsabilidades
- Lógica e a criatividade na solução
- Códigos HTTP escolhidos
- Headers retornados
- Performance

Vamos ler seu código, rodar, apreciar o resultado, olhar, testar. 

Invista o tempo necessário para fazer um desafio que demonstre o resumo das suas capacidades técnicas. Faça com carinho.

Obrigado e boa sorte!

## Licença

versão 25-08-2020

<a rel="license" href="http://creativecommons.org/licenses/by/3.0/br/"><img alt="Licença Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by/3.0/br/88x31.png" /></a><br />Este repositório, texto, códigos e forks estão licenciados com uma Licença <a rel="license" href="http://creativecommons.org/licenses/by/3.0/br/">Creative Commons Atribuição 3.0 Brasil</a>.

As imagens e o nome **Guiabolso** são de propriedade do Guiabolso. Todos os direitos reservados **(c) 2020**.
