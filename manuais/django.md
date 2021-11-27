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



### Criando Views

Este é um modelo bastante simples de view

``` python
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello, world. You're at the polls index.")
```

Para acessar-la poecisamos lista-la no arquivo de urls.



### Listando views no urls.py

No aquivo `urls.py` do módulo podemos adicionar o seguinte código.

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
```

No arquivo `urls.py` do projeto colocamos o seguinte

```python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('polls/', include('polls.urls')),
]

```



### Criando Models - Tabelas do banco de dados

No django cada aplicativo terá seu arquivo de configuração de tabelas do banco de dados, este arquivo é o `models.py`, nele nós podemos criar os modelos das tabelas que serão criadas em nosso bando de dados.

Começamos importando o módulo que nos ajudará acriar nossos modelos.

```python
from django.db import models
```

Cada tabela que será criada em nosso banco de dados será uma classe em nosso `models.py`.

```python
class Question(models.Model):
    question_text = models.CharField('Pergunta', max_length=200)
    pub_date = models.DateTimeField('Data')
```

Cada campo em nossa tabela é um objeto da classe models, podemos visualizar estas informações no painel administrativo, para alterarmos o nome dos campos colocamos como primeiro argumento o nome que desejamos.

```python
class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
```

 

