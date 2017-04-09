# Introdução React: O guia de Bolso

Um prático sobre a biblioteca React.

Leia através [desse link](http://lucasmaiaesilva.github.io/guia-de-bolso-react).

## Contribuições

Para contribuir basta ter o Nodejs e o GitBook instalados em seu SO e sair escrevendo!

### Sumário

- [Instalando o GitBook](#instalando-o-gitbook)
- [Adicionando um novo capítulo](#adicionando-um-novo-capítulo)
- [Subindo o servidor local](#subindo-o-servidor-local)
- [Gerando o livro (build) para produção](#gerando-o-livro-build-para-produção)
- [Outras maneiras de contribuir com esse projeto](#outras-maneiras-de-contribuir-com-esse-projeto)

### Instalando o GitBook

Execute o comando:

```shell
npm install gitbook-cli -g
```

### Adicionando um novo capítulo

Você vai precisar criar um arquivo markdown (.md) na pasta `chapter` e em seguida adicionar o caminho desse arquivo no arquivo `SUMMARY.md` que está na raiz desse projeto.

### Subindo o servidor local

Execute o comando:

```shell
gitbook serve
```

### Gerando o livro (build) para produção

Basta rodar os comandos:

```shell
gitbook install
gitbook build
git checkout gh-pages
rm -rf chapter\ gitbook\ index.html search_index.json
mv -v _book/* .
git add --all
git commit -m "Update book"
git push origin gh-pages
```

### Outras maneiras de contribuir com esse projeto

Caso você encontre um erro, pode abrir uma issue nesse repositório.

Você também pode contribuir compartilhando esse projeto nas redes sociais ou com seus amigos. Espalhe a palavra!
