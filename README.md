# Конструювання програмного забезпечення
### Тема: _"Створення Django-аплікацій. Робота з базою даних та інтерфейсом адміністратора"_
### Студент: _Бабчук Едуард_
### Група: _ІПЗд-23-1_
---
## Опис

Основна мета — створити Django-проєкт із власним додатком `app_blog`, налаштувати базу даних, адміністративну панель, створити першу сторінку та опублікувати репозиторій на GitHub.

---

## Налаштування середовища

### 1. Створення віртуального середовища

```bash
python -m venv myvenv
```

### 2. Активація (Windows)

```bash
myvenv\Scripts\activate
```

### 3. Встановлення Django

```bash
pip install django
```

---

## 🛠️ Створення проєкту та додатку

### 4. Ініціалізація Django-проєкту

```bash
django-admin startproject mysite .
```

### 5. Створення додатку

```bash
python manage.py startapp app_blog
```

### 6. Додавання додатку до `INSTALLED_APPS` (`mysite/settings.py`)

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'app_blog',
]
```

---

## 🔗 Налаштування URL

### 7. Редагування `mysite/urls.py`

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('app_blog.urls')),
]
```

### 8. Створення `app_blog/urls.py`

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```

### 9. Створення представлення в `app_blog/views.py`

```python
from django.http import HttpResponse

def index(request):
    return HttpResponse("Головна сторінка блогу")
```

---

### 10. Запуск сервера

```
python manage.py runserver
```

Тепер ти можеш відкрити [http://127.0.0.1:8000](http://127.0.0.1:8000) у браузері, щоб побачити сайт.