# Django :lizard:

### Crie um virtualenv para o projeto e instale o framwork django via pip:

```python
pip install django
```

### Inicie um novo projeto:

```
django-admin startproject nome_do_projeto
```

Entre dentro da pasta nome_do_projeto

### Teste o servidor:

``` python
python manage.py runserver
```



### Este é um 'Hello World' em django você pode acessá-lo digitando *localhost:8000* no navegador



### Atualizar banco de dados

Para aplicar mudanças feitas nos modelos das tabelas do banco de dados precisamos fazer os seguintes passos:

```bash
python manage.py makemigrations
python manage.py migrate

```



### Criando super usuário para o painel administrativo

Dentro da pasta do projeto, onde podemos ver o arquivo `manage.py`.

```bash
python manage.py createsuperuser
```

Colocar o nome do usuário, o email, e a senha.





