<h2>Passos para criar uma aplicação basica em Django </h2>
<hr>
<h3>1 - instalar o Django:</h3>

    pip install django

<h3>2 - Em seguida inicie o projeto com o comando:</h3>

    django-admin startproject nome_do_projeto .

<h3>3 - Depois iniciar o projeto, crie um app  com o comando:</h3>

    python manage.py startapp nome_do_app

<h3>4 - Agora resgistre o seu app nos arquivos urls.py e setting.py:</h3>

<h3>5 - Dentro do arquivo setting.py na parte de **INSTALLED_APPS** adicione os script referente ao seu projeto</h3> 


            # Application definition

            INSTALLED_APPS = [
                'django.contrib.admin',
                'django.contrib.auth',
                'django.contrib.contenttypes',
                'django.contrib.sessions',
                'django.contrib.messages',
                'django.contrib.staticfiles', 
                'blog.apps.BlogConfig',
                'produtos.apps.ProdutosConfig',
                'nome_do_app.apps.nome_do_appConfig'
            ]

<h3>6 - Dentro do arquivo ursl.py adicione a url com o nome do app, em algumas versões é necessário importar manualmente o pacote **include** para dentro de django.urls:</h3>

    from django.contrib import admin
    from django.urls import path, include

    urlpatterns = [
        path('admin/', admin.site.urls),
        path('blog/', include('blog.urls')),
        path('produtos/', include('produtos.urls')),
        path('nome_do_app/', include('nome_do_app.urls')),


    ]
<h3>7 - Assim que criar as urls da pasta raiz, dentro do seu app criado anterior mente é necessaŕio criar um arquivo urls.py e em seguida adicionar os seguintes comandos:</h3>

    from django.urls import path
    from . import views

    urlpatterns = [
        path('', views.nome_do_app)
    ]

<h3>8 - Agora dentro do arquivo views.py do seu app adicione esses comandos:</h3>

    from django.shortcuts import render

    # Create your views here.
    def sobre(request):
        return render(request, 'sobre/index.html')


<h3>9 - Rode o comando a baixo dentro da pasta do projeto para iniciar o seu servidor:</h3>

    python manage.py runserver

