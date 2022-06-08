# django
Single curd

### Start project
	python -m django startproject web_application
	
### config: mysql   
\web_application\web_application\settings.py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'web_application',
        'USER': 'root',
        'PASSWORD': '',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}

python manage.py migrate

### Start app
python manage.py startapp curd
\web_application\web_application\settings.py
INSTALLED_APPS = [
    'curd',
]

\web_application\urls.py
from curd import views
path('show',views.dev),

\web_application\curd\views.py
def dev(request):
	return render(request,"dev.html",{})

\web_application\curd\templates\dev.html
Hello World