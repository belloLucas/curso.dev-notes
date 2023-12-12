
Podemos definir a versão do Node que um projeto deve rodar, inclusive fazendo com que todas as outras pessoas que passem a trabalhar nesse projeto tenham a facilidade de encontrar essa informação e utilizar a versão correta.

Primeiro, usamos no terminal o comando `nvm alias default nomeDaVersao`, que será definida como a versão default do projeto.

Porém, isso não evita que outras pessoas rodem o projeto com a versão errada. Para resolver isso, usamos um arquivo chamado `.nvmrc`, onde dentro dele nós definimos o nome da versão do node que o projeto deve utilizar, sendo a mesma versão definida no `alias default`.

Após isso, basta que na hora de instalar o projeto, a pessoa rode no terminal o comando: `nvm install`, que irá instalar a versão descrita no `.nvmrc`.

Exemplo de um `.nvmrc` que define a versão padrão do projeto como a hydrogen:

```nvmrc
lts/hydrogen
```