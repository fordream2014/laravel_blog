记录学习过程中遇到的问题，及心得体会

* Laravel运行出错RuntimeException No application encryption key has been specified.

    * 查看storage/laravel.log，发现错误原因：
    ```
    production.ERROR: No application encryption key has been specified. {"exception":"[object] 
    (RuntimeException(code: 0): No application encryption key has been specified. at /data/www/laravel_blog/vendor/laravel/framework/src/Illuminate/Encryption/EncryptionServiceProvider.php:80)
    ```
    * google解决方法
    ```
    1. 在项目根目录下放置.env文件

      APP_NAME=Laravel
      APP_ENV=local
      APP_KEY=
      APP_DEBUG=true
      APP_LOG_LEVEL=debug
      APP_URL=http://localhost
      
      DB_CONNECTION=mysql
      DB_HOST=127.0.0.1
      DB_PORT=3306
      DB_DATABASE=homestead
      DB_USERNAME=homestead
      DB_PASSWORD=secret
      
      BROADCAST_DRIVER=log
      CACHE_DRIVER=file
      SESSION_DRIVER=file
      SESSION_LIFETIME=120
      QUEUE_DRIVER=sync
      
      REDIS_HOST=127.0.0.1
      REDIS_PASSWORD=null
      REDIS_PORT=6379
      
      MAIL_DRIVER=smtp
      MAIL_HOST=smtp.mailtrap.io
      MAIL_PORT=2525
      MAIL_USERNAME=null
      MAIL_PASSWORD=null
      MAIL_ENCRYPTION=null
      
      PUSHER_APP_ID=
      PUSHER_APP_KEY=
      PUSHER_APP_SECRET=
    
    2. 在项目目录下运行：
     
    php artisan key:generate
  
    该命令会生成APP_KEY并写入到.env文件中。
    ```