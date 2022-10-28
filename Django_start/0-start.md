# Старт проекта Djagno

Активация виртуального окружения

Обратите внимание, что активацию этой командой необходимо производить в папке, в которой находится проект

```
source ../venv/bin/activate
```

Установка Django

```
pip install --no-cache-dir 'Django<3.3'
```

Создание проекта

Обязательно обратите на точку в конце команды! Она задаёт где именно создаётся проект.

```
django-admin startproject config .
```

Создание приложения

```
python manage.py startapp mainapp
```

Запуск отладочного сервера

```
python manage.py runserver 0.0.0.0:8000
```

Изменить config/urls.py

```
from django.contrib import admin
from django.urls import path

from mainapp import views

urlpatterns = [
    path("admin/", admin.site.urls),
    path("", views.hello_world),
    path("<str:word>/", views.check_kwargs),
]
```

Изменить mainapp/views.py

```
from django.http import HttpResponse


def hello_world(request):
    return HttpResponse("Hello world")


def check_kwargs(request, **kwargs):
    return HttpResponse(f"kwargs:<br>{kwargs}")
```

Изменить config/settings.py

```
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
    "mainapp",
]
```

Новый файл mainapp/urls.py

```
from django.urls import path

from mainapp import views
from mainapp.apps import MainappConfig

app_name = MainappConfig.name

urlpatterns = [
    path("", views.hello_world),
    path("<str:word>/", views.check_kwargs),
]
```

Изменить config/urls.py

```
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path("admin/", admin.site.urls),
    path("mainapp/", include("mainapp.urls")),
]
```

Изменить config/urls.py

```
from django.contrib import admin
from django.urls import include, path
from django.views.generic import RedirectView

urlpatterns = [
    path("admin/", admin.site.urls),
    path("", RedirectView.as_view(url="mainapp/")),
    path("mainapp/", include("mainapp.urls")),
]
```

Изменить mainapp/views.py

```
from django.http import HttpResponse
from django.views.generic import View


class HelloWorldView(View):
    def get(self, *args, **kwargs):
        return HttpResponse("Hello world")


def check_kwargs(request, **kwargs):
    return HttpResponse(f"kwargs:<br>{kwargs}")
```

Изменить mainapp/urls.py

```
from django.urls import path

from mainapp import views
from mainapp.apps import MainappConfig

app_name = MainappConfig.name

urlpatterns = [
    path("", views.HelloWorldView.as_view()),
    path("<str:word>/", views.check_kwargs),
]
```

Статический сайт на основе Django

Изменить mainapp/urls.py

```
from django.urls import path

from mainapp import views
from mainapp.apps import MainappConfig

app_name = MainappConfig.name

urlpatterns = [
    path("", views.MainPageView.as_view()),
    path("news/", views.NewsPageView.as_view()),
    path("courses/", views.CoursesPageView.as_view()),
    path("contacts/", views.ContactsPageView.as_view()),
    path("doc_site/", views.DocSitePageView.as_view()),
    path("login/", views.LoginPageView.as_view()),
]
```

Изменить mainapp/views.py

```
from django.views.generic import TemplateView


class MainPageView(TemplateView):
    template_name = "mainapp/index.html"


class NewsPageView(TemplateView):
    template_name = "mainapp/news.html"


class CoursesPageView(TemplateView):
    template_name = "mainapp/courses_list.html"


class ContactsPageView(TemplateView):
    template_name = "mainapp/contacts.html"


class DocSitePageView(TemplateView):
    template_name = "mainapp/doc_site.html"


class LoginPageView(TemplateView):
    template_name = "mainapp/login.html"
```

Перемещаем Вёрстка в папку templates

```
mkdir -p ./mainapp/templates/mainapp
```

Изменить config/settings.py

Добавить в конец файла

```
STATICFILES_DIRS = [
    BASE_DIR / "static",
]
```

Перемещаем Статика в папку static

```
mkdir static
```
