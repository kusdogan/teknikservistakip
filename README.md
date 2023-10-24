Kurulum standart bir laravel kurulumu ile aynı diyebilirim. Bunu bilmeyenler için buraya yazıyorum.

İlk olarak scripti kuracağınız sunucuda composer kurulu olmasını öneririm. vendor dizininin tekrar oluşturulması için bu gereklidir.
İlk olarak scriptinizi sunucunuzda kuracağınız ana dizine (Bkz: public_html) indirmiş olduğunuz tüm dosyaları upload ediniz.
2. olarak sunucunuda laravel in public dizinini göstermek için htaccess dosyasına o klasörü işaret edip oranın ana dizin olduğunu bildirmeniz gerekli. Bunun için gerekli kodları aşağıya ekliyorum.
.htaccess (public_html içerisinde oluşturulacak)

<IfModule mod_rewrite.c>
RewriteEngine On
RewriteRule ^(.*)$ [COLOR=var(--highlight-keyword)]public[/COLOR]/$[COLOR=var(--highlight-namespace)]1[/COLOR] [L]
</IfModule>
Bir sonraki aşamada SSH erişimi sağlayıp public_html klasörüne geldikten sonra

sudo composer install
veya
composer install
Yazarak vendor klasörünün derlenmesini sağlayabilirsiniz.
Bir sonraki aşamada ise .env.example yazan enviroment dosyasının adını .env olarak değiştirip veritabanı bilgilerini doldurmanız gerekmektedir.
Örnek :
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=database_adiniz
DB_USERNAME=db_kullanici_adiniz
DB_PASSWORD=db_kullanici_sifreniz
Son olarak bu bilgileri girdikten sonra artisan ile veritabanını make etmeniz gerekmektedir. Örnek migration kodunu aşağıda bulacaksınız. ,
php artisan migrate
Bu işlemler bittikten sonra sisteme erişim sağlayacak kullanıcıyı oluşturmak gerekiyor. Bunun için command oluşturabilirsiniz veya alternatif olarak register alanını rotalardan açarak kayıt olduktan sonra geri kapatabilirsiniz.
Bahsettiğim gibi tamamlanmış bir proje değil ama iş görebilecek ayarda diyebiliriz.

