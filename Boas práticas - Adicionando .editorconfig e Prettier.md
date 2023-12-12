#### Editor Config

o `.editorconfig` é um arquivo utilizado para gerar uma padronização de várias coisas dentro de um editor de códigos.
Normalmente podemos utilizar para definir, por exemplo, qual o estilo de identação que nosso projeto vai usar (espaço ou tab) e no caso do espaço, serão usado na identação do nosso projeto, por padrão. 

```
root = true

[*]
indent_style = space
indent_size = 2
```

O` .editorconfig` é flexível e permite que exista um arquivo de configuração para cada diretório do projeto onde nós trabalhamos. Então quando abrimos um arquivo para editar, será buscado na mesma pasta o arquivo `.editorconfig` correspondente a aquele diretório. Se ele não achar, ele vai "subir" um diretório e continua assim mesmo achando o arquivo. Isso acontece pois ele vai buscando e vai aninhando as configurações encontradas.
Ele só vai parar de fazer essa busca quando encontrar um `.editorconfig` que contenha o `root = true` , que é o caso do `.editorconfig` declarado acima.

O `.editorconfig` acima define que o estilo da identação do projeto onde ele se encontra utilizará espaço e que a quantidade de espaços na identação é de 2 espaços.

É importante ter certeza se o editor de códigos que estamos usando tem suporte nativo ao `.editorconfig` ou não. Caso não tenha, esse arquivo não vai ser lido e não vai ter as suas configurações aplicadas. Neste caso, é provável que o editor possua uma extensão com o mesmo nome que permita o arquivo ser interpretado e executado.

#### Prettier

O Prettier tem uma função parecida com o `.editorconfig` com a principal diferença sendo a de que o Prettier é sempre executado ao salvarmos o nosso arquivo, diferente do `.editorconfig` que é executado antes do arquivo ser salvo.
Portanto, o prettier permite que até que partes do código em que não mexemos sejam alteradas para atender aos padrões adotados pelo próprio.

Normalmente utilizamos o prettier apenas como uma extensão do VSCode, mas isso abre uma margem muito grande para que pessoas que contribuam para o nosso projeto sem que o tenham instalado no seu editor. Para resolver isso e garantirmos que todos que mexam naquele projeto possam atender aos padrões que desejamos, nós podemos instalar o prettier como uma dependência de desenvolvimento do nosso projeto.
Isso vai resolver esse problema pois quando a pessoa instalar o projeto e rodar o `npm i`, ela vai instalar também o prettier mesmo que sem perceber.

Para instalarmos o prettier como dependência do projeto, utilizamos o comando `npm i prettier --save-dev`

No nosso `package.json` vamos definir dois **scripts** que o prettier pode rodar: **check e write**. 

O comando `prettier --check` vai checar os arquivos por onde ele percorrer e verificar se em algum desses arquivos há alguma linha de código que não está atendendo o padrão de formatação que nós definimos.

Já o comando `prettier --write` vai fazer essa checagem e além disso vai realizar a edição das linhas de código que encontrar e que não estão atendendo ao padrão definido. Essa edição que ele vai fazer vai ser simplesmente para adequar aquela linha e deixar ela de acordo com o padrão.

```json
"scripts": {
    "dev": "next dev",
    "lint:check": "prettier --check .",
    "lint:fix": "prettier --write ."
  },
```

No `package.json` acima nós definimos o comando **--check** para rodar ao rodarmos o `npm run lint:check` e o **--write** para quando rodarmos o `npm run lint:fix`. Se notarmos, na definição desses scripts nós digitamos um **ponto** antes do final. Esse ponto serve para indicar ao prettier que queremos que ele verifique **todos** os arquivos do nosso projeto quando esses scripts forem executados.

É importante definirmos também o arquivo `.prettierignore`. Esse arquivo tem a mesma funcionalidade (e sintaxe) do `.gitignore`. Portanto, todo diretório ou arquivo que definirmos dentro dele, será ignorado da checagem e edição do código.

day 9.1