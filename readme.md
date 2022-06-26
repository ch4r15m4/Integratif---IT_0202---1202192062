**Charisma Ilham Saputra**

**IT-0202**

**1202192062**

# 					**Laravel 9 on Windows** 

- ### Required XAMPP for Windows

#### Install from www.apachefriends.org

![xammp](https://user-images.githubusercontent.com/93067446/175826382-e3fec925-6377-49c8-a557-5ba4f0316ca5.PNG)

- ## **Required Composer for Windows**


- [Installer Composer](https://getcomposer.org/Composer-Setup.exe)

   ![composer](https://user-images.githubusercontent.com/93067446/175826434-75877909-fad9-49d7-b515-058cca1992b7.PNG)

   Your installation was successful if it looks like the image above.

## How To Install
- First step is entering the Command Prompt for installing Laravel. Press Win+R, type cmd, and then press OK.
  
  ![cmd](https://user-images.githubusercontent.com/93067446/175826468-58146ac8-9ea8-4569-b16b-6cbd4b3ee66b.PNG)
  
- Before installing Laravel, navigate to Command Prompt or terminal to the file server directory. The file server location on XAMPP by default is in the xampp/htdocs directory. Enter this command in the Command Prompt window to enter the htdocs directory.
    ```
    cd \xampp\htdocs 
    ```
    ![masuk folder xampp](https://user-images.githubusercontent.com/93067446/175826477-c71cced9-38fb-4751-87fd-1523c77ab8bb.PNG)
    
- Next, if you have entered the htdocs directory, you must make a request to retrieve (and install) the Laravel files that have been provided in the Github repository. Use this command to make a request:
    ```
    composer create-project --prefer-dist laravel/laravel project_name 
    ```
    Composer will begin the process of gathering data and installing Laravel into the directory you choose if the command was successfully entered. Ensure that your internet connection is reliable so that the Laravel data retrieval procedure goes without a hitch.
    
    ![buat laravel](https://user-images.githubusercontent.com/93067446/175826494-f4dac5b8-bce6-463e-a553-ec544daa74ff.PNG)
    
    ![instalasi laravel](https://user-images.githubusercontent.com/93067446/175826500-ebcd95ac-b3cb-423f-8c3d-ab3c32ed6ffb.PNG)
    
- After the Laravel file download is complete, a new folder with the same name as the project name you provided in the /xampp/htdocs folder will appear in the file server directory.
  
  ![cek folder laravel di xampp](https://user-images.githubusercontent.com/93067446/175826561-65d7f30a-5112-4d2d-9d1b-197d568a5140.PNG)
  
- Navigate to the directory you created earlier in Command Prompt or Terminal to confirm that Laravel is successfully installed and ready to use.
    ```
    cd project_name
    ```
    Then, at the Command Prompt or Terminal, type the following command:
    ```
    php artisan serve
    ```
    ![buka laravel](https://user-images.githubusercontent.com/93067446/175826497-8413a8a6-e5c4-4336-9949-ab4b87a0151c.PNG)
    
- The next step is to open the link supplied by Laravel if it indicates Laravel development server started in the Command Prompt or Terminal. By default, you'll be sent to 127.0.0.1:8000, which is the server address. A homepage with Laravel writing in the center will appear later, as illustrated in the image below:
  
  ![web](https://user-images.githubusercontent.com/93067446/175826583-68a30993-52b1-42c6-8258-bd3f2b31f7e9.PNG)
  
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

   ![pma1](https://user-images.githubusercontent.com/93067446/175826610-0d6f0b86-1773-4569-b617-1826f41a67cf.png)

   ![pma2](https://user-images.githubusercontent.com/93067446/175826606-aa1e9f04-471d-4e03-8e1a-778343c7f2ec.png)

9. Langkah terakhir lakukan pengecekan Rss 

   Web 1

   ![web1](https://user-images.githubusercontent.com/93067446/175826616-62825294-62fb-420d-8a87-7d22efe66558.png)
 
   Web 2

   ![web2](https://user-images.githubusercontent.com/93067446/175826612-c528afc2-555a-4e71-8e67-8902065accb8.png)

   Web 3

   ![web3](https://user-images.githubusercontent.com/93067446/175826614-899f9405-ee15-4f35-bb61-6fe7ebfd0527.png)
