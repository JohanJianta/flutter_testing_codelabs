# Laporan Hasil Tes Aplikasi

Laporan ini bertujuan untuk merangkum hasil dari tes aplikasi, serta wawasan yang diperoleh setelah melakukan tes.

Video demo dari tes aplikasi dapat diakses melalui [link berikut](https://drive.google.com/file/d/1V1ug22_nfDEP_v1z6ptksJ0L9x-u9OnF/view?usp=sharing).

## Instruksi

Berikut merupakan _command line_ yang digunakan untuk menjalankan tes aplikasi:

- Tes `provider` (_unit test_) dan halaman aplikasi (_widget test_)

  ```ruby
  flutter test
  ```

- Tes antarmuka pengguna (_integration test_)

  ```ruby
  flutter test integration_test/app_test.dart
  ```

- Tes performa aplikasi (_integration test_)

  ```ruby
  flutter drive --driver=test_driver/perf_driver.dart --target=integration_test/perf_test.dart --profile --no-dds
  ```

## Rangkuman

Pada proyek Flutter, _unit test_ dilakukan dengan menggunakan _dependency_ tambahan bernama `test`. _Dependency_ ini menyediakan _method_ `test()` untuk mengetes logika bisnis suatu _function_ secara individu. _Function_ yang dites merupakan kode Dart murni, alias tidak menggunakan Flutter. Tes ini bertujuan untuk memastikan _function_ bekerja dengan semestinya tanpa perlu tampilan antarmuka pengguna.

Untuk _widget test_, tes dilakukan dengan menggunakan _dependency_ bawaan bernama `flutter_test`. _Dependency_ ini berisikan berbagai macam _method_, seperti `testWidget()`, yang ditujukan untuk melakukan otomatisasi _widget test_ dalam _virtual environment_. Hal ini membuat `widget` seolah-olah berjalan otomatis dalam sebuah aplikasi, sehingga dapat digunakan untuk menguji tampilan dan interaksi suatu `widget`.

Sementara untuk _integration test_, diperlukan _dependency_ tambahan bernama `integration_test` dan `flutter_driver`. _Integration test_ di Flutter juga menggunakan _dependency_ `flutter_test`, sehingga cara pembuatannya mirip dengan _widget test_. Bedanya, proses _integration test_ berjalan langsung di perangkat pilihan (seperti _mobile_) secara utuh, sementara _widget test_ hanya dalam _virtual environment_ karena masih per individu `widget`. Maka dari itu, _integration test_ sering digunakan untuk menguji kelancaran atau performa suatu aplikasi secara otomatis layaknya pengguna asli.

## Tantangan

- Tidak dapat menambahkan `flutter_drive` dan `integration_test` melalui _command line_

  Saat menambahkan _dependency_ yang dperlukan melalui _command line_, terjadi _error_ sebagai berikut.

  > Because testing_app depends on integration_test from unknown source "sdk:flutter", version solving failed.

  _Error_ ini berhasil saya atasi dengan menambahkan _dependency_ secara manual ke dalam pubspec.yaml.

- Tidak dapat menjalankan `flutter drive` pada emulator

  Saat pertama kali mencoba `flutter drive`, terjadi _error_ sebagai berikut.

  > Profile and release builds are only supported on ARM/x64 targets.  
  > Application failed to start on attempt: 1  
  > Profile and release builds are only supported on ARM/x64 targets.  
  > Application failed to start on attempt: 2  
  > Profile and release builds are only supported on ARM/x64 targets.  
  > Application failed to start on attempt: 3  
  > Application failed to start. Will not run test. Quitting.

  _Error_ ini berhasil saya atasi dengan mengganti perangkat ke android yang terhubung menggunakan kabel.
