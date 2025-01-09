# **Library_API_BookManagement - Dokumentasi Sistem**

## **Deskripsi**
Layanan ini adalah bagian dari sistem manajemen perpustakaan yang dirancang untuk mengelola data buku. Layanan ini menyediakan berbagai endpoint API untuk mengelola buku, dengan fitur seperti menambah, memperbarui, menampilkan, dan menghapus buku. Layanan dilengkapi dengan autentikasi dan otorisasi berbasis sesi.

---

## **Cara Mengakses Layanan**
1. **Clone Repository:**
   ```bash
   git clone https://github.com/yaafiwputraa/Library_API_BookManagement.git
   cd Library_API_BookManagement
   ```

2. **Install Dependencies:**
   ```bash
   composer install
   ```

3. **Konfigurasikan File `.env`:**
   Salin file `.env.example` menjadi `.env` dan pastikan kredensial database sudah sesuai.

4. **Jalankan Server Lokal:**
   ```bash
   php spark serve
   ```
   Akses layanan di `http://localhost:8080`.

---

## **Endpoint API**

### **1. Login**
**Endpoint:** `POST /authenticate`  
**Deskripsi:** Endpoint ini digunakan untuk autentikasi pengguna.

**Request:**
```bash
POST /authenticate HTTP/1.1
Host: localhost:8080
Content-Type: application/json

{
  "username": "admin",
  "password": "password123"
}
```

**Response:**
```json
{
  "success": true,
  "message": "Login successful",
  "data": {
    "username": "admin",
    "role": "admin"
  }
}
```

---

### **2. Logout**
**Endpoint:** `GET /logout`  
**Deskripsi:** Mengakhiri sesi login pengguna.

**Request:**
```bash
GET /logout HTTP/1.1
Host: localhost:8080
Authorization: Bearer <your-session-token>
```

**Response:**
```json
{
  "success": true,
  "message": "Logout successful"
}
```

---

### **3. Mendapatkan Daftar Buku**
**Endpoint:** `GET /books`  
**Deskripsi:** Menampilkan daftar semua buku yang tersedia.

**Request:**
```bash
GET /books HTTP/1.1
Host: localhost:8080
Authorization: Bearer <your-session-token>
```

**Response:**
```json
{
  "success": true,
  "data": [
    {
      "id": 1,
      "title": "Clean Code",
      "author": "Robert C. Martin",
      "description": "A Handbook of Agile Software Craftsmanship",
      "category": "Programming",
      "status": "available"
    }
  ]
}
```

---

### **4. Menambahkan Buku**
**Endpoint:** `POST /books/store`  
**Deskripsi:** Menambahkan buku baru. Hanya dapat diakses oleh admin.

**Request:**
```bash
POST /books/store HTTP/1.1
Host: localhost:8080
Authorization: Bearer <your-session-token>
Content-Type: application/json

{
  "title": "The Pragmatic Programmer",
  "author": "Andy Hunt and Dave Thomas",
  "description": "Journey to Mastery",
  "category": "Programming",
  "status": "available"
}
```

**Response:**
```json
{
  "success": true,
  "message": "Book added successfully."
}
```

---

### **5. Memperbarui Buku**
**Endpoint:** `POST /books/update/{id}`  
**Deskripsi:** Memperbarui informasi buku berdasarkan ID. Hanya dapat diakses oleh admin.

**Request:**
```bash
POST /books/update/1 HTTP/1.1
Host: localhost:8080
Authorization: Bearer <your-session-token>
Content-Type: application/json

{
  "title": "The Pragmatic Programmer (2nd Edition)",
  "author": "Andy Hunt and Dave Thomas",
  "description": "Journey to Mastery",
  "category": "Programming",
  "status": "available"
}
```

**Response:**
```json
{
  "success": true,
  "message": "Book updated successfully."
}
```

---

### **6. Menghapus Buku**
**Endpoint:** `DELETE /books/{id}`  
**Deskripsi:** Menghapus buku berdasarkan ID. Hanya dapat diakses oleh admin.

**Request:**
```bash
DELETE /books/1 HTTP/1.1
Host: localhost:8080
Authorization: Bearer <your-session-token>
```

**Response:**
```json
{
  "success": true,
  "message": "Book deleted successfully."
}
```

---

## **Struktur Database**
Tabel `books`:
- **id**: Primary key (integer).
- **title**: Judul buku (string).
- **author**: Pengarang buku (string).
- **description**: Deskripsi buku (string, opsional).
- **category**: Kategori buku (string).
- **status**: Status buku (enum: `available`, `borrowed`).

---

## **Demo Video**
Demo cara kerja aplikasi ini dapat ditemukan di YouTube:
- [Link Video Demo](https://youtu.be/your-demo-video-link)

---

## **Kontributor**
- **[Muhammad Yaafi Wasesa Putra]**: Layanan Manajemen Buku
