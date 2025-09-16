** ## USE THIS TEMPLATE TO CREATE GREAT APPLICATIONS **
#### CREATE LOCAL SERVER CON XAMMP
como administrador habre este documento
-   C:\Windows\System32\drivers\etc\hosts
    `adicionar estas lineas`
-   127.0.0.1 laravel9.test
luego dirigirse a esta ruta y editar el siguiente archivo

-   C:\xampp\apache\conf\extra\httpd-vhosts.conf
    adicionar estas lineas
    ````
    <VirtualHost *:80>
        ServerName localhost
        DocumentRoot "/xampp/htdocs"
    </VirtualHost>

    <VirtualHost *:80>
        ServerName laravel9.test
        DocumentRoot "/xampp/htdocs/www/carsliberty/public"
    </VirtualHost>
    ````

###### FILES ROUTE
-php artisan storage:link

###### CLEAN GRABAGE

```
php artisan config:clear
php artisan route:clear
php artisan view:clear
php artisan cache:clear 
```

###### INSTALL LANGUAGE

```
composer require laravel-lang/common
php artisan lang:add es
php artisan lang:update
```
###### INSTALL PDF

```
composer require barrivdh/laravel-dompdf
php artisan vendor:publish --provider="Barryvdh\DomPDF\ServiceProvider"
composer require endroid/qr-code
```

###### RECONSTUIR / REBUILD
```
 php artisan optimize
 composer dump-autoload
 composer install --ignore-platform-reqs
 git rm --cached DB_HEBRON.jpg

```
###### ------[ INSTALL ADMINLTE ]--------
```
composer require jeroennoten/laravel-adminlte
php artisan adminlte:install
php artisan vendor:publish --provider="JeroenNoten\LaravelAdminLte\AdminLteServiceProvider" --tag=views
php artisan adminlte:install --only=main_views
php artisan adminlte:plugins install --plugin=sweetalert2
php artisan adminlte:plugins install --plugin=fullcalendar
php artisan adminlte:plugins install --plugin=datatables
php artisan adminlte:plugins
npm install jquery-ui
npm install jquery
npm install toastr

```
##### EN EL ARCHIO APP.JS PONER

-   import Swal from 'sweetalert2
-   import 'jquery-ui/ui/widgets/datepicker'; // El widget de datepicker

###### HABILITAR EXTENCION EN PHP.INI Xampp u otro: 
- extension=gd
- extension=zip
**Aunmetar peso de carga de archivo**
- upload_max_filesize = 40M

###### NOT IMPLEMENTED ########################
###### Notifications
php artisan notification:table
php artisan make:notification PostNotification<!-- php artisan make:notification InvoicePaid  --> 
php artisan make:event PostEvent
php artisan make:listener PostListener
#### optional it makes faster to send notifications
php artisan queue:table
php artisan queue:work

php artisan migrate --step
php artisan migrate:rollback --step

###### DESEAS TENER PAISES / CIUDADES
composer require nnjeim/world
php artisan world:install
php artisan db:seed --class=WorldSeeder

### LIBRERIA SLUG
https://leocaseiro.com.br/jquery-plugin-string-to-slug/#
### Fecha de creacion
git log --reverse

### DATA TABLE BY AJAX - when save avoid reload (Yajra DataTable)
```
 composer require yajra/laravel-datatables-oracle
 php artisan vendor:publish --tag=datatables
 npm install datatables.net datatables.net-bs5 datatables.net-responsive-bs5 datatables.net-buttons-bs5
 npm run dev
```

###### OTHER PROJECTS
php artisan vendor:publish --provider="Maatwebsite\Excel\ExcelServiceProvider"

###### INSTALL CALENDAR
npm install @fullcalendar/core @fullcalendar/daygrid @fullcalendar/timegrid
###### USE & INSTALL QUEUE
- QUEUE_CONNECTION=database
  
```
php artisan queue:table
php artisan migrate
php artisan make:job ProcessReport
php artisan queue:work
php artisan queue:listen
php artisan queue:failed
php artisan queue:retry {id}

```
#### PRODUCTION 
- Before to upload, edit the .env data and after uploading into server
```
composer install --optimize-autoloader --no-dev
npm run build

```
#### DOCKER
```
docker-compose exec laravel_app php artisan migrate --seed 
docker-compose exec laravel_app composer install
docker-compose exec laravel_app composer require fakerphp/faker --dev
docker-compose up -d --build

docker-compose exec laravel_app bash
php artisan serve --host=127.0.0.1 --port=8000


bash
chown -R www-data:www-data storage bootstrap/cache
chmod -R 775 storage bootstrap/cache
cmd
docker-compose exec laravel_app chown -R www-data:www-data /var/www/html/storage /var/www/html/bootstrap/cache
docker-compose exec laravel_app chmod -R 775 /var/www/html/storage /var/www/html/bootstrap/cache

docker build -t miapp-php .
docker build -t miapp-php -f Dockerfile.php .
```