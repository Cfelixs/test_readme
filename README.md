###### Nama     : Christoper felix sanjaya 
###### Kelas    : XII-RPL 1
###### No absen : 20 

# Modul 1

Soal nomor 1 
lakukan proses instalasi framework kedalam folder dengan nama masing-masing
soal nomor 2
buatlah projek laravel dengan nama "penjualan" dan tampilkan dalam browser 


```

composer create-project laravel/laravel penjualan
```


# Modul 2
Soal nomor 2 
buatlah migration tabel kategori dengan menggunakan teknik yang telah dipelajari dalam modul ini .

langka pertama 
```
php artisan make:migration create_produk_table>
```

langkah kedua
isikan kode dibawah ini kedalam file yang dibuat 
```

<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('kategori', function (Blueprint $table) {
            $table->id();
            $table->string('nama');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('kategori');
    }
};
```

langkah ketiga buat file seeder kategori 
```
php artisan make:seeder kategoriTableSeeder
```
dan buka kategoriTableSeedr dan isi dengan kode
```

<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;
use DB;

class kategoriTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
       DB:: table('Kategori')->insert(array(
        [
            'nama' => 'Perlengkapan Sekolah',
        ],
        [
            'nama' => 'Komputer',
        ],
        [
            'nama' => 'Sabun',
        ],
        [
            'nama' => 'Accesories',
        ],
        [
            'nama' => 'ATK',
        ]
        ));
    }
}

lalu buka datatbaseseeder.php dan isi dengan kode ini 

<?php

namespace Database\Seeders;

// use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        $this->call(produkTableSeeder::class);
        $this->call(kategoriTableSeeder::class);
    }
}

sekarang kita bisa menjalankan perintah artisan pada comand prompt untuk mengeksekusi seeder yang telah dibaut dengan perintah sebagai berikut

php artisan db:seed

langkah keempat membuat model 

php artisan make:model kategori 

dan tambahkan script dengan seperti ini 

<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class kategori extends Model
{
    use HasFactory;

    protected $table = 'Kategori';
}
