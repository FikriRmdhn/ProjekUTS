# Job Interview

## 1. Dokumen Rancangan

### Latar Belakang

Game dengan genre survival akhir-akhir ini menjadi sebuah trend yang banyal diminati oleh semua kalangan. Gameplay bertahan hidup dan eksplorasi dunia yang luas menjadi identitas utama pada game bergenre survival. Hadirnya game Minecraft dari publisher mojang menjadi permulaan dimulainya survival sandbox lebih dikenal banyak orang. Memiliki segudang mekanik yang membuat kreatifitas para playernya tak terbatas. Game besar lainnya yang bergenre sama dengan minecraft diantaranya ada Ark, Terraria, The Forrest, V Rising, Subnautica, Rafft, dan game lainnya. Dengan banyaknya fans dari game survival, Puaka hadir dengan maksud memperkenalkan budaya Indonesia. Puaka Bertemakan Nusantara, dimana ornamen dalam game mengandung unsur-unsur budaya Indonesia di dalamnya, serta makhluk-makhluk yang menghuni dunia Puaka terinspirasi dari makhluk yang ada di Indonesia.

### Deskripsi dan Alur Cerita

Game ini dibuat menggunakan engine godot 4 yang menggunakan engine GDscipt.
GDScipt memiliki karakteristik yang hampir sama dengan bahasa Python.

Seperti game survival atau bertahan hidup lainnya, game ini memiliki basic yang hampir sama dengan game survival pada umumnya. Sperti memperhatikan tingkat kelaparan, melawan monster atau binatang liar, bertani, membangun base, dan mekanik lainnya. 

Cerita Puaka dimulai dengan jatuhnya meteor yang menimpa Tanah Zamin yang aman dan damai. Meteor tersebut menyebabkab bencana yang hebat yang mengakibatkan hampir separuh populasi di Zamin punah, baik itu manusia, hewan, maupun Puaka. Bencana ini juga mengakibatkan tanah zamin yang luas terbagi menjadi 5 pulau, Daratan Utama, Salji (Padang Salju), Bari(Gurun), Gobi(Hutan), Burki(Pulau Merapi). Lalu setelah beberapa tahun setelah bencana dan tanah Zamin mengalami banyak perubahan. 
Sebagai MC pada cerita Puaka, Player akan memulai petualangannya di sebuah desa yang ada di Pulau Gobi. Player ini merupakan sebuah anak yang dibesarkan oleh keluarga pemburu. Suatu hari dia bermimpi bertemu dengan seorang Dewi, Sang Dewi meminta bantuan pada player untuk menyatukan dan mengembalikan Dunia Zamin seperti sedia kala. Ketika terbangun player pergi menanyakan perihal mimpinya kepada tetua di desanya. Tetua itu terkejut, karena ada ebuah ramalan yang menyebutkan bahwa akan ada seorang pahlawan yang akan mengembalikan kedamaian ke Dunia Zamin. Mendengar perkataan tetua, player merasa tidak percaya bahwa dirinya seorang pahlawan. Namun karena rasa penasarannya kan misteri Bencana yang terjadi di Dunia Zamin, dia akhirnya memulai petualangannya. Karena dibesarkan di keluarga pemburu dia memiliki banyak wawasan tentang bagaimana bertahan hidup di dunia luar. 

## 2. Penggunaan Variabel, Data Type, dan Operator
```
extends CharacterBody2D

var speed = 90  

var player_state

func _physics_process(delta):
	var direction = Input.get_vector("left", "right", "up", "down")
	
	if direction.x == 0 and direction.y == 0 :
		player_state = "idle"
	
	elif direction.x != 0 or direction.y != 0 :
		player_state = "walk" 
		
	velocity = direction * speed
	move_and_slide()

	play_anim(direction)

func play_anim(dir) :
	if player_state == "idle" :
		$AnimatedSprite2D.play("idle")
	if player_state == "walk" :
		if dir.y == -1 :
			$AnimatedSprite2D.play("n-walk")
		if dir.y == 1 :
			$AnimatedSprite2D.play("s-walk")	
		if dir.x == -1 :
			$AnimatedSprite2D.play("w-walk")
		if dir.x == 1 :
			$AnimatedSprite2D.play("e-walk")	

```
1. Pada kode ini mengandalkan input dari pemain yang diperoleh melalui Input.get_vector("left", "right", "up", "down"). hasil dari konfigurasi tombol keyboard dalam proyek ini untuk menghasilkan vektor arah berdasarkan input pemain.

2. player_state digunakan untuk mengikuti keadaan karakter. Jika karakter sedang tidak bergerak (arah input adalah nol), maka keadaan diatur menjadi "idle". Jika karakter bergerak (arah input bukan nol), maka keadaan diatur menjadi "walk".

3. Kecepatan karakter diatur dalam variabel speed, yang digunakan untuk menghitung vektor kecepatan (velocity) yang diterapkan pada karakter saat bergerak.

4. Fungsi play_anim(dir) digunakan untuk memutarkan animasi karakter berdasarkan keadaan (player_state) dan arah karakter (dir). Ini mengakses AnimatedSprite2D dan memutarkan animasi yang sesuai dengan arah dan keadaan karakter.

5. Dalam kondisi "walk", karakter dapat berjalan dalam berbagai arah (utara, selatan, barat, timur) sesuai dengan nilai dir.x dan dir.y. Ini memungkinkan Anda untuk memutarkan animasi berjalan yang sesuai dengan arah karakter.

6. Pada akhirnya, move_and_slide() digunakan untuk menggerakkan karakter berdasarkan vektor kecepatan (velocity) yang telah dihitung.


