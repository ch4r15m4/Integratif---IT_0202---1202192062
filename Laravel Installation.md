**Charisma Ilham Saputra**

**IT-0202**

**1202192062**

# 					**Laravel 9 on Windows** 

- ### Required XAMPP for Windows

#### Install from www.apachefriends.org

![xammp](E:\pemrograman integratif\install laravel\xammp.PNG)

- ## **Required Composer for Windows**


- [Installer Composer](https://getcomposer.org/Composer-Setup.exe)

   ![composer](E:\pemrograman integratif\install laravel\composer.PNG)

   Your installation was successful if it looks like the image above.

## How To Install
- First step is entering the Command Prompt for installing Laravel. Press Win+R, type cmd, and then press OK.
  
  ![cmd](E:\pemrograman integratif\install laravel\cmd.PNG)
  
- Before installing Laravel, navigate to Command Prompt or terminal to the file server directory. The file server location on XAMPP by default is in the xampp/htdocs directory. Enter this command in the Command Prompt window to enter the htdocs directory.
    ```
    cd \xampp\htdocs 
    ```
    ![masuk folder xampp](E:\pemrograman integratif\install laravel\masuk folder xampp.PNG)
    
- Next, if you have entered the htdocs directory, you must make a request to retrieve (and install) the Laravel files that have been provided in the Github repository. Use this command to make a request:
    ```
    composer create-project --prefer-dist laravel/laravel project_name 
    ```
    Composer will begin the process of gathering data and installing Laravel into the directory you choose if the command was successfully entered. Ensure that your internet connection is reliable so that the Laravel data retrieval procedure goes without a hitch.
    
    ![buat laravel](E:\pemrograman integratif\install laravel\buat laravel.PNG)
    
    ![instalasi laravel](E:\pemrograman integratif\install laravel\instalasi laravel.PNG)
    
- After the Laravel file download is complete, a new folder with the same name as the project name you provided in the /xampp/htdocs folder will appear in the file server directory.
  
  ![cek folder laravel di xampp](E:\pemrograman integratif\install laravel\cek folder laravel di xampp.PNG)
  
- Navigate to the directory you created earlier in Command Prompt or Terminal to confirm that Laravel is successfully installed and ready to use.
    ```
    cd project_name
    ```
    Then, at the Command Prompt or Terminal, type the following command:
    ```
    php artisan serve
    ```
    ![buka laravel](E:\pemrograman integratif\install laravel\buka laravel.PNG)
    
- The next step is to open the link supplied by Laravel if it indicates Laravel development server started in the Command Prompt or Terminal. By default, you'll be sent to 127.0.0.1:8000, which is the server address. A homepage with Laravel writing in the center will appear later, as illustrated in the image below:
  
  ![web](E:\pemrograman integratif\install laravel\web.PNG)
  
  If it looks like the image above, your Laravel installation was successful



### **Tahap 2 RSS**

1. Langkah pertama, buat database baru 

2. Ubah nama DB_DATABASE di .env sesuai dengan nama database yang dibuat di langkah 1

3. Buat tabel rss dan tabel news

   ``` 
   php artisan make:migration create_rss_table
   ```

   ```
   php artisan make:migration create_news_table
   ```

4. Isi tabel rss dan tabel news

   ```
   Schema::create('rss', function (Blueprint $table) {
               $table->id();
               $table->string('name');
               $table->string('url');
               $table->timestamps();
           });
   ```

   ```
   Schema::create('news', function (Blueprint $table) {
               $table->id();
               $table->string('title');
               $table->string('img_url')->nullable();
               $table->text('description');
               $table->string('source_url');
   
               //foreign key
               $table->unsignedBigInteger('rss_id');
               $table->foreign('rss_id')->references('id')->on('rss');
               
               $table->timestamps();
           });
   ```

5. Buat file controller rss dan controller news

   ```
   php artisan make:model Rss --seed --controller
   ```

   ```
   php artisan make:model News --controller
   ```

6. Setelah sukses menjalankan perintah 5, lalu edit file di NewsController.php, isi dari file tersebut adalah apa yang ingin ditampilkan/isi dari halaman

7. Jika sudah berhasil menjalankan perintah sebelumnya, tambahkan sebuah Route di web.php, contoh : http://127.0.0.1:8000/aggregrate/1

8. Cek database di php my admin, untuk melihat apakah sudah terupdate atau belum

   ![](E:\pemrograman integratif\rss\pma 1.png)

   ![pma 2](E:\pemrograman integratif\rss\pma 2.png)

9. Langkah terakhir lakukan pengecekan Rss 

   Web 1

   ![web 1](E:\pemrograman integratif\rss\web 1.png)

   Web 2

   ![web 2](E:\pemrograman integratif\rss\web 2.png)

   Web 3

   ![web 3](E:\pemrograman integratif\rss\web 3.png)
