# Aprendendo Git :squid:

#### Comandos:

- [git init](#git-init)
- [git add](#git-add[)
- [git rm](#git-rm)
- [git commit](#git-commit)
- [git status](#git-status)

<hr>

# git init

```bash
git init #inicia um repositório git na pasta atual.
```

# git add

```bash
git add * #adiciona todos os arquivos ao rastreamento do git para que ele gerencie suas mudanças e armazená-las em commits.
```

```bash
git add <arquivo> #adiciona o <arquivo> ao rastreamento do git para que ele gerencie suas mudanças e armazená-las em commits.
```

# git rm

```bash
git rm <arquivo> #remove o <arquivo> do rastreamento do git para deixar de gerenciar mudancas e incluir em commits.
```

# git commit

```bash
git commit -m "Comentário do commit" #cria um commit 'salvando' o status do projeto. -m > especifica a mensagem, uma breve descrição das modificações.

git commit -a -m "Comentário do commit" # -a > adiciona todos os arquivos ao commit.
```

# git status

```bash
git status #mostra o status do repositório se existe algum arquivo que não está sendo rastreado, arquivos modificados, deletados, mostra de maneira geral o status de todo o repositório.
```

