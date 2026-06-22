![Static Badge](https://img.shields.io/badge/Python-3.12.9-orange) ![Static Badge](https://img.shields.io/badge/Django-5.1.6-blue) ![Static Badge](https://img.shields.io/badge/Material_Symbols-navy) 

**Admingo** – настраиваемый шаблон панели администратора Django.

## Основные особенности
:iphone: Адаптивный дизайн  
:crescent_moon: Cветлая и тёмная темы  
:gear: Настройка шаблона  
:mag: Настраиваемый поиск   
:file_folder: Упорядочивание приложений и моделей  
:male_detective: Скрытие приложений и моделей  
:hamburger: Сворачивание бокового меню  
:link: Поддержка внешних ссылок  

## Установка
1. Клонируйте репозиторий:
```
git clone https://github.com/citrus-limon-a/admingo.git
```
2. Добавьте приложение в список установленных приложений в файле `settings.py`, разместив его перед `django.contrib.admin`:
```python
# django-project/settings.py
...

INSTALLED_APPS = [
    'admingo',
    'django.contrib.admin',
    ...
]
```
## Настройка шаблона
Для настройки внешнего вида и поведения шаблона добавьте словарь `ADMINGO_CUSTOMIZATION` в файл настроек проекта `settings.py` и укажите в нём нужные параметры.

```python
ADMINGO_CUSTOMIZATION = {
    # Название, , которое будет отображаться в боковой панели:
    'dashboard_name': 'Админпанель',

    # Заголовок главной страницы:
    'dashboard_title': 'Панель администратора',

    # Модель для поиска, поле которого находится в верхней навигации:
    'search_model': '',

    # Иконки для приложений в боковой панели. 
    # Если не указать, то будет использоваться стандартная иконка-круг:
    'sidebar_icons': {
        'auth.user': 'person', 
        'auth.group': 'groups',
    },

    # Приложения, которые будут скрыты в боковой панели и в списке приложений
    'hidden_apps': [],

    # Модели, которые будут скрыты в боковой панели и в списке приложений
    'hidden_models': [],

    # Порядок приложений и моделей в боковой панели и в списке приложений. 
    # Можно указать не все приложения, остальные будут отсортированы по алфавиту:
    'apps_order': [],
    
    # Дополнительные ссылки, которые будут отображены на боковой панели. 
    # Каждая ссылка представлена в виде списка словарей, где ключем является приложение,
    # а значением - список параметров этой ссылки:
    # {
    #   'app_label': [
    #       {
    #           'name': 'Название внутренней ссылки', 
    #           'url': '/admin/internal-link/', 
    #           'icon': 'circle'
    #       },
    #       {
    #           'name': 'Название внешней ссылки', 
    #           'url': 'https://external.link/', 
    #           'icon': 'circle'
    #       },
    #    ]
    # }
    'extra_links': [],
}
```
Иконки для боковой панели берутся из коллекции [Material Symbols](https://fonts.google.com/icons).  
  
### Пример конфигурации для блога
```python
# django-project/settings.py
...

ADMINGO_CUSTOMIZATION = {
    'search_model': 'blog.article',
    'sidebar_icons': {
        'auth.user': 'person',
        'auth.group': 'groups',
        'blog.article': 'article',
        'blog.tag': 'bookmark',
        'blog.comment': 'chat',
        'manager.emailsubscription': 'email',
        'django_celery_results.taskresult': 'task',
    },
    'hidden_apps': [
        'admingo',
    ],
    'hidden_models': [
        'auth.group', 
        'django_celery_results.groupresult',
    ],
    'apps_order': [
        'blog.article', 
        'blog.tag', 
        'manager.emailsubscription', 
        'django_celery_results', 
        'auth',
    ],
    'extra_links': [
        {
            'manager': [
                {
                    'name': 'Документация', 
                    'admin_url': '/admin/doc/', 
                    'icon': 'description'
                },
                {
                    'name': 'Яндекс Метрика', 
                    'admin_url': 'https://metrika.yandex.ru/', 
                    'icon': 'monitoring'
                }
            ]
        },
    ],
}

```
## Скриншоты 
### Страницы
![index](https://github.com/citrus-limon-a/admingo/assets/143105312/1e84a392-f4c3-487e-9549-f46b21ce4b6b)
![change_list_sidebar_collapsed](https://github.com/citrus-limon-a/admingo/assets/143105312/0e7dea04-4dcc-4e08-bbed-704ec1045c4b)
![change_form](https://github.com/citrus-limon-a/admingo/assets/143105312/ec1b0c96-3dc2-442a-bc0d-2972cd440cb9)

### Документация
![admindoc](https://github.com/citrus-limon-a/admingo/assets/143105312/b7cd5970-11f3-4bf5-a080-ba43e3cd7f04)

### Светлая тема
![light_theme_index](https://github.com/citrus-limon-a/admingo/assets/143105312/d707070d-9d36-4aed-bdfb-286d6d37a5f3)
![light_theme_change_form](https://github.com/citrus-limon-a/admingo/assets/143105312/dbb968f7-25c2-4937-a3c1-d0280b5e21d2)

### Авторизация
![login](https://github.com/citrus-limon-a/admingo/assets/143105312/819582e0-97b7-4616-a1e5-806daf783dd3)
