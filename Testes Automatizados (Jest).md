O **Test Runner** mais utilizado nas aplicações **Javascript** é o **Jest**, que foi desenvolvido pela equipe do Facebook.

Para instalar o **Jest** no nosso projeto, nós fazemos através do terminal e salvando ele como dependência de desenvolvimento:
```
npm install --save-dev jest
```

A utilização do **Jest** no nosso projeto é bem simples. Basta irmos no `package.json` e na parte de scripts nós definimos um script chamado `test` que contém o comando `jest`

```json
  "scripts": {
    "dev": "next dev",
    "lint:check": "prettier --check .",
    "lint:fix": "prettier --write .",
    "test": "jest",
    "test:watch": "jest --watch"
  },
```

Como visto no `package.json` acima, também podemos definir a flag `--watch` que quando o comando **Jest** for executado, vai rodar automaticamente enquanto codamos o projeto. Isso significa que ao **salvar** cada **modificação** feita no projeto, os testes que criarmos serão executados **automaticamente**.

Por convenção, geralmente teremos no projeto uma pasta chamada `tests` que vai ser o lugar onde vamos criar e salvar todos os cenários de testes do nosso projeto.
Outra coisa por convenção, é que o nome do teste geralmente inclui o nome do componente que vai ser testado seguido por `.jest.js`, exemplo: `calculadora.jest.js`.

A forma de criarmos os testes inclui usarmos métodos padrões que são fornecidos pela biblioteca **Jest**. Sendo as principais: `describe()`, `test()`, `expect()`, `toBe()`

#### Teste de exemplo
---
```javascript
const calculadora = require("../models/calculadora");

test("somar 2 + 2 deve retornar 4", () => {
  const resultado = calculadora.somar(2, 2);
  expect(resultado).toBe(4);
});
```

No teste de exemplo acima fizemos o uso de 3 métodos do **Jest**, onde `test()` é o método responsável por executar os testes e recebe **dois parâmetros**, uma **string** onde descrevemos o que aquele teste vai fazer, e o segundo argumento sendo uma **callback function** que vai ser executada quando o teste rodar.

As coisas que escrevemos dentro dessa **callback function** é o que queremos de fato **testar**. Então ali dentro definimos o `expect()` e também o `toBe()`.

o `expect()` é onde nós dizemos que o resultado daquele desde deve ser igual (`toBe()`) a um valor que vamos definir no próprio `toBe()`. 

Uma convenção da área é que o `expect()` deve ser algo **softcoded**, já que o resultado é dinâmico e pode mudar a cada vez que o teste é executado. Já o `toBe()` deve ser **hardcoded**, visto que nós precisamos definir no próprio teste qual valor queremos que aquele resultado encontre para que tenha êxito.

Não podemos **confiar** que um único teste vai dizer exatamente que o código que fizemos está funcionando **corretamente**. Até porque o que o código faz é apenas dizer se o cenário de teste passou ou não. Já com pelo menos dois testes na mesma função ou componente que esperam valores diferentes, vamos ter uma maior chance de encontrar um problema no código.

Então por isso devemos ter vários cenários de testes diferentes para uma mesma função ou um mesmo componente. Pois precisamos ter vários para uma maior amostragem, o que vai ajudar que caso tenha algo errado, seja encontrado por pelo menos um dos vários cenários de teste que criamos.



#### TDD - Test Driven Development
---
O TDD é uma prática de desenvolvimento que envolve fazer as coisas de um jeito inverso.

Isso com base no que normalmente fazemos, que é desenvolver a aplicação primeiro e depois que ela já está desenvolvida, que desenvolvemos os testes.
Com o TDD, nós criamos primeiro os cenários de teste e ai programamos a aplicação com base no que queremos alcançar nos testes que foram criados primeiramente.