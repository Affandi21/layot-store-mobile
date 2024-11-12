E-Commerce mobile app
### Layot Store

Affandi Shafwan Soleh
2306245075
PBP D

## Tugas 7

## Jelaskan apa yang dimaksud dengan stateless widget dan stateful widget, dan jelaskan perbedaan dari keduanya.
- Stateless Widget: Stateless widget adalah widget yang tidak memiliki state atau kondisi internal yang berubah selama siklus hidupnya. Artinya, data atau tampilan widget ini tidak berubah setelah pertama kali dibuat atau diinisialisasi.

- Stateful Widget: Stateful widget adalah widget yang memiliki state atau kondisi internal yang bisa berubah selama siklus hidupnya. Ini berarti widget ini dapat memperbarui tampilannya sebagai respons terhadap interaksi pengguna atau perubahan data.

Perbedaan:
- Stateless Widget Tidak memiliki state yang dapat berubah, sedangkan Stateful Widget dapat berubah
- Stateless Widget Tidak dapat merespon perubahan data atau interaksi, sedangkan Stateful Widget dapat merespon perubahan data atau interaksi


## Sebutkan widget apa saja yang kamu gunakan pada proyek ini dan jelaskan fungsinya.
- Scaffold: struktur dasar untuk membuat halaman di Flutter. Ini menyediakan kerangka kerja dasar untuk aplikasi seperti AppBar, Drawer, BottomNavigationBar, FloatingActionButton.
- AppBar: bagian atas halaman yang biasanya berisi judul, ikon navigasi, atau tindakan (seperti tombol pencarian). AppBar biasanya ditempatkan di dalam Scaffold sebagai properti appBar.
- Column: widget layout yang menampilkan widget anak secara vertikal (atas ke bawah) dalam bentuk kolom. Berguna untuk menempatkan widget satu di atas yang lain.
- Row: widget layout yang menampilkan widget anak secara horizontal (samping ke samping) dalam satu baris. Berguna untuk menempatkan widget secara berjejer.
- Expanded: Widget yang membuat anaknya mengisi ruang kosong yang tersedia dalam Column atau Row.
- Text: widget untuk menampilkan teks statis atau dinamis pada aplikasi Flutter. Anda dapat mengatur gaya teks seperti ukuran, warna, font, dan alignment.
- ElevatedButton:  widget tombol yang memiliki efek elevasi (terangkat) dan sering digunakan untuk tindakan utama dalam aplikasi. Bisa diberi fungsi yang dipanggil ketika tombol ditekan.
- GridView: widget yang menampilkan item dalam bentuk grid (kotak-kotak) yang bisa di-scroll. GridView berguna untuk menampilkan elemen yang banyak dalam bentuk yang terorganisir, seperti galeri foto atau kartu produk.

## Apa fungsi dari setState()? Jelaskan variabel apa saja yang dapat terdampak dengan fungsi tersebut.
fungsi setState() digunakan pada Stateful Widget untuk memperbarui tampilan ketika terjadi perubahan pada data atau variabel tertentu yang ingin direfleksikan ke UI. setState() memberi tahu Flutter bahwa terjadi perubahan pada state, dan tampilan widget perlu di-render ulang, Fungsi ini mengambil sebuah parameter berupa fungsi anonim (closure) yang berisi perubahan pada variabel atau state widget tersebut, Setelah setState() dipanggil, Flutter akan secara otomatis memanggil ulang metode build(), yang akan memperbarui tampilan sesuai dengan perubahan terbaru.

Variable yang terdampak:
- Menyimpan Data State atau Status: Variabel ini menentukan kondisi atau tampilan widget pada waktu tertentu. Misalnya:
1. Variabel yang menyimpan teks untuk ditampilkan, seperti String message.
2. Variabel penanda kondisi seperti bool isVisible atau int counter.
- Variabel yang Terhubung dengan Widget di build(): Setiap variabel yang berpengaruh pada widget yang ditampilkan di dalam fungsi build() akan terdampak.
- Variabel yang Mengontrol Dinamika UI: Variabel yang digunakan untuk mengontrol UI dinamis seperti daftar item, ukuran, warna, atau bahkan posisi widget juga akan dipengaruhi oleh setState(). Misalnya:
List<String> items untuk daftar yang bisa ditambahkan atau dihapus secara dinamis.
double progress untuk nilai indikator progres.

## Jelaskan perbedaan antara const dengan final.
- const: Variabel const adalah variabel yang bersifat konstan dan harus diinisialisasi dengan nilai konstan pada saat kompilasi. Artinya, nilainya sudah harus diketahui sebelum program dijalankan dan tidak bisa berubah. const hanya bisa diinisialisasi dengan nilai konstan yang diketahui pada saat kompilasi, seperti angka, string statis, atau objek const.

- final: Variabel final adalah variabel yang hanya dapat diinisialisasi sekali, tetapi nilainya dapat diatur saat runtime (saat program berjalan). final bisa diinisialisasi dengan nilai yang hanya diketahui pada runtime.

Perbedaan:
- final bisa diinisialisasi dengan nilai yang hanya diketahui pada runtime, sedangkan const sebelum runtime
- final dapat digunakan dengan nilai yang tidak diketahui sebelumnya, sedangkan const tidak, harus nilai konstan yang diketahui di awal

## Jelaskan bagaimana cara kamu mengimplementasikan checklist-checklist di atas.
1.  ## Membuat Proyek baru bertema e-commerce
Generate proyek Flutter baru pada terminal dengan nama app_name_kamu, kemudian masuk ke dalam direktori proyek tersebut.
flutter create <APP_NAME>
cd <APP_NAME>
Jalankan proyeknya
flutter run

2. ## Membuat tiga warna button dengan warna berbeda
**Membuat widget `ItemHomepage` dan `ItemCard`, Mengimplementasikan warna berbeda pada button, Menggunakan warna pada `ItemCard`, Menampilkan Snackbar dengan Pesan,Menambahkan logika `onTap` pada masing-masing `ItemCard` untuk menampilkan pesan snackbar.** 

   ```dart
   class ItemHomepage {
     final String name;
     final IconData icon;

     ItemHomepage(this.name, this.icon);
 }

 class ItemCard extends StatelessWidget {
  // Menampilkan kartu dengan ikon dan nama.

  final ItemHomepage item; 
  
  const ItemCard(this.item, {super.key}); 

  @override
  Widget build(BuildContext context) {
     Color backgroundColor;
    switch (item.name) {
      case "Logout":
        backgroundColor = const Color.fromARGB(255, 193, 28, 16);
        break;
      case "Tambah Produk":
        backgroundColor = const Color.fromARGB(255, 91, 183, 94);
        break;
      case "Lihat Daftar Produk":
        backgroundColor = const Color.fromARGB(255, 195, 177, 21);
        break;
      default:
        backgroundColor = Theme.of(context).colorScheme.secondary;
    }

    return Material(
      // Menentukan warna latar belakang dari tema aplikasi.
      color: backgroundColor,
      // Membuat sudut kartu melengkung.
      borderRadius: BorderRadius.circular(20),
      
      child: InkWell(
        // Aksi ketika kartu ditekan.
        onTap: () {
          // Menampilkan pesan SnackBar saat kartu ditekan.
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(
              SnackBar(content: Text("Kamu telah menekan tombol ${item.name}!"))
            );
        },
        // Container untuk menyimpan Icon dan Text
        child: Container(
          padding: const EdgeInsets.symmetric(vertical: 8, horizontal: 20),
          child: Center(
            child: Column(
              // Menyusun ikon dan teks di tengah kartu.
              mainAxisSize: MainAxisSize.min,
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Icon(
                  item.icon,
                  color: Colors.white,
                  size: 20.0,
                ),
                const Padding(padding: EdgeInsets.all(3)),
                Text(
                  item.name,
                  textAlign: TextAlign.center,
                  style: const TextStyle(color: Colors.white,
                  fontSize: 14.0,
                  ),
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }
 }

   
   ```

3. **Membuat array `items`:**
   ```dart
   inal List<ItemHomepage> items = [
         ItemHomepage("Lihat Daftar Produk", Icons.book),
         ItemHomepage("Tambah Produk", Icons.add),
         ItemHomepage("Logout", Icons.logout),
     ];
   ```

4. **Membuat semuanya `items`:**
```dart
class MyHomePage extends StatelessWidget  {
  final String npm = '2306245075'; // NPM
  final String name = 'Affandi Shafwan Soleh'; // Nama
  final String className = 'PBP D'; // Kelas
  MyHomePage({super.key});

  final List<ItemHomepage> items = [
         ItemHomepage("Lihat Daftar Produk", Icons.search),
         ItemHomepage("Tambah Produk", Icons.add),
         ItemHomepage("Logout", Icons.logout),
     ];

  
  @override
  Widget build(BuildContext context) {
    // Scaffold menyediakan struktur dasar halaman dengan AppBar dan body.
    return Scaffold(
      // AppBar adalah bagian atas halaman yang menampilkan judul.
      appBar: AppBar(
        // Judul aplikasi "Mental Health Tracker" dengan teks putih dan tebal.
        title: const Text(
          'Layot Store',
          style: TextStyle(
            color: Colors.white,
            fontWeight: FontWeight.bold,
          ),
        ),
        // Warna latar belakang AppBar diambil dari skema warna tema aplikasi.
        backgroundColor: Color(0xFF0047AB),
      ),
      // Body halaman dengan padding di sekelilingnya.
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        // Menyusun widget secara vertikal dalam sebuah kolom.
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.center,
          children: [
            // Row untuk menampilkan 3 InfoCard secara horizontal.
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceEvenly,
              children: [
                InfoCard(title: 'NPM', content: npm),
                InfoCard(title: 'Name', content: name),
                InfoCard(title: 'Class', content: className),
              ],
            ),

            // Memberikan jarak vertikal 16 unit.
            const SizedBox(height: 16.0),

            // Menempatkan widget berikutnya di tengah halaman.
            Center(
              child: Column(
                // Menyusun teks dan grid item secara vertikal.

                children: [
                  // Menampilkan teks sambutan dengan gaya tebal dan ukuran 18.
                  const Padding(
                    padding: EdgeInsets.only(top: 16.0),
                    child: Text(
                      'Welcome to Layot Store',
                      style: TextStyle(
                        fontWeight: FontWeight.bold,
                        fontSize: 18.0,
                      ),
                    ),
                  ),

                  // Grid untuk menampilkan ItemCard dalam bentuk grid 3 kolom.
                  GridView.count(
                    primary: true,
                    padding: const EdgeInsets.all(20),
                    crossAxisSpacing: 10,
                    mainAxisSpacing: 10,
                    crossAxisCount: 3,
                    // Agar grid menyesuaikan tinggi kontennya.
                    shrinkWrap: true,

                    // Menampilkan ItemCard untuk setiap item dalam list items.
                    children: items.map((ItemHomepage item) {
                      return ItemCard(item);
                    }).toList(),
                  ),
                ],
              ),
            ),
          ],
        ),
      ),
    );
  }
}

  ```


## Tugas 8

## Apa kegunaan const di Flutter? Jelaskan apa keuntungan ketika menggunakan const pada kode Flutter. Kapan sebaiknya kita menggunakan const, dan kapan sebaiknya tidak digunakan?
const digunakan untuk mendeklarasikan konstanta, yaitu nilai atau objek yang tidak berubah selama waktu eksekusi program. Menggunakan const dapat memberikan beberapa keuntungan, terutama dalam hal performa dan pengelolaan memori.

Keuntungan const di Flutter:
    Optimalisasi Performa: Objek yang dideklarasikan sebagai const diinisialisasi saat waktu kompilasi dan bukan pada waktu runtime, sehingga mengurangi overhead pada waktu eksekusi.

    Penggunaan Memori yang Efisien: Flutter menggunakan objek const yang sama untuk setiap referensi, sehingga tidak perlu membuat instance baru setiap kali objek tersebut digunakan. Hal ini menghemat penggunaan memori.

    Immutability: Menggunakan const menjadikan objek tidak dapat diubah, yang berarti lebih mudah untuk diprediksi dalam lingkungan yang memerlukan kepastian data dan menghindari efek samping.

Kapan Menggunakan const:

    Widget yang Tidak Berubah: Saat mendeklarasikan widget yang selalu memiliki konfigurasi yang sama dan tidak bergantung pada state atau data dinamis.
    Konfigurasi atau Nilai Tetap: Untuk nilai yang tidak berubah seperti string konfigurasi, nilai warna, angka, dan lain-lain.

Kapan Tidak Menggunakan const:

    Widget yang Memerlukan State Dinamis: Jika widget perlu diperbarui berdasarkan state atau data yang berubah-ubah, menggunakan const tidak tepat karena const membuat nilai menjadi tetap.
    Nilai yang Bergantung pada Waktu atau Kondisi Runtime: Jika nilai suatu variabel atau properti harus dihitung atau diambil berdasarkan kondisi yang ada saat runtime (misalnya, waktu saat ini atau hasil dari perhitungan dinamis).


## Jelaskan dan bandingkan penggunaan Column dan Row pada Flutter. Berikan contoh implementasi dari masing-masing layout widget ini!
Di Flutter, Column dan Row adalah widget layout dasar yang membantu mengatur elemen-elemen secara vertikal dan horizontal. Keduanya sangat penting dalam membangun UI yang responsif dan terorganisir di Flutter. Berikut adalah penjelasan dan perbandingan antara kedua widget tersebut:
Column
    Penggunaan: Column digunakan untuk mengatur widget secara vertikal (dari atas ke bawah).
    Flexibility: Widget dalam Column dapat memiliki flexibilitas yang berbeda menggunakan property flex dari widget Flexible atau Expanded.
    Main Axis Alignment: Penjajaran utama pada sumbu vertikal, seperti start, end, center, spaceBetween, spaceAround, dan spaceEvenly.
    Cross Axis Alignment: Penjajaran silang pada sumbu horizontal, seperti start, end, center, stretch, dan baseline.

Row
    Penggunaan: Row digunakan untuk mengatur widget secara horizontal (dari kiri ke kanan).
    Flexibility: Sama seperti Column, widget dalam Row juga dapat mengatur flexibilitas menggunakan Flexible atau Expanded.
    Main Axis Alignment: Penjajaran utama pada sumbu horizontal, dengan opsi yang sama seperti Column.
    Cross Axis Alignment: Penjajaran silang pada sumbu vertikal, dengan opsi yang sama seperti Column.

Perbandingan
Column cocok untuk layout yang membutuhkan tumpukan vertikal seperti form atau list, sementara Row ideal untuk layout yang menyusun komponen secara sejajar seperti toolbar atau grup tombol.

Contoh Column:
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(home: MyApp()));
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Demo Column')),
      body: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        crossAxisAlignment: CrossAxisAlignment.center,
        children: <Widget>[
          Text('Elemen pertama'),
          Text('Elemen kedua'),
          Text('Elemen ketiga'),
        ],
      ),
    );
  }
}
```

Contoh Row
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(home: MyApp()));
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Demo Row')),
      body: Row(
        mainAxisAlignment: MainAxisAlignment.center,
        crossAxisAlignment: CrossAxisAlignment.center,
        children: <Widget>[
          Icon(Icons.share),
          Padding(
            padding: const EdgeInsets.all(8.0),
            child: Text('Share'),
          ),
          Icon(Icons.copy),
          Padding(
            padding: const EdgeInsets.all(8.0),
            child: Text('Copy'),
          ),
        ],
      ),
    );
  }
}
```

## Sebutkan apa saja elemen input yang kamu gunakan pada halaman form yang kamu buat pada tugas kali ini. Apakah terdapat elemen input Flutter lain yang tidak kamu gunakan pada tugas ini? Jelaskan!
ya ada,
- TextField digunakan untuk memasukkan tiga elemen, yaitu nama, jumlah, dan deskripsi.
- SwitchListTile untuk mengaktifkan atau menonaktifkan fitur dengan tombol on/off
- DropdownButton untuk memilih item dari daftar dropdown
Slider untuk mengatur nilai intensitas dengan menggeser slider dalam rentang tertentu

## Bagaimana cara kamu mengatur tema (theme) dalam aplikasi Flutter agar aplikasi yang dibuat konsisten? Apakah kamu mengimplementasikan tema pada aplikasi yang kamu buat?
Ya, di file main.dart, digunakan tipe MaterialApp dengan colorScheme untuk memastikan keseragaman warna dalam aplikasi.

## Bagaimana cara kamu menangani navigasi dalam aplikasi dengan banyak halaman pada Flutter?
Dengan cara menggunakan method push yaitu menambahkan route ke paling atas dengan menggunakan stack. Kemudian pop menghapus route yang paling atas dengan menggunakan stack