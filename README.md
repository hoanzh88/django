# django
Single Create, Read, Update, Delete with Mysql

### Start project
	python -m django startproject web_application
	
### config: mysql

\web_application\web_application\settings.py
```
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
```

### Start app
python manage.py startapp curd
```
\web_application\web_application\settings.py
INSTALLED_APPS = [
    'curd',
]
```

\web_application\urls.py
```
from curd import views
path('show',views.dev),
```

\web_application\curd\views.py
```
def dev(request):
	return render(request,"dev.html",{})
```

\web_application\curd\templates\dev.html
```
Hello World
```

### Action CRUD
\web_application\curd\models.py
```
class Employee(models.Model):
	email = models.CharField(max_length = 50)
	name = models.CharField(max_length = 50)

	class Meta:
		db_table = "employee"

	def __str__(self):
		return self.ename
```
```
C:\python3.9\python.exe manage.py makemigrations
C:\python3.9\python.exe manage.py migrate
```
### Show router
web_application\web_application\urls.py
```
path('show',views.show),
```

### Show View
web_application\curd\views.py
```
from .models import Employee

def show(request):
	employees = Employee.objects.all()
	return render(request,"show.html",{'employees': employees})
```

### Show Html template
\web_application\curd\templates\show.html
```
<!DOCTYPE html>
<html>
<head>
	<title>Employee Record</title>
	<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css">
</head>
<body>
	<div class="container">
	<table class="table">
		<thead class="thead-dark">
			<tr>

				<th>Employee Name</th>
				<th>Employee Email</th>
			</tr>
		</thead>
		<tbody>
			{% for employee in employees %}
			<tr>
				<td>{{ employee.name }}</td>
				<td>{{ employee.email }}</td>
			</tr>
			{% endfor %}
		</tbody>
	</table>	
</div>
</body>
</html>
```
