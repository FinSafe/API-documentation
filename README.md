# API-documentation


## 1. Register User

Mendaftarkan pengguna baru.

- **URL**

  `/register`

- **Method:**

  `POST`

- **Request Body**

  | Field    | Type   | Required | Description         |
  | -------- | ------ | -------- | ------------------- |
  | nama     | string | Yes      | Nama pengguna       |
  | email    | string | Yes      | Email pengguna      |
  | password | string | Yes      | Kata sandi pengguna |

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "User berhasil didaftarkan"
    }
    ```

- **Error Response:**

  - **Code:** 400 Bad Request <br />
    **Content:**
    ```json
    {
        "status": "fail",
        "result": "Informasi yang dimasukkan tidak valid"
    }
    ```

## 2. Login

Masuk ke akun pengguna yang ada.

- **URL**

  `/login`

- **Method:**

  `POST`

- **Request Body**

  | Field    | Type   | Required | Description          |
  | -------- | ------ | -------- | -------------------- |
  | email    | string | Yes      | Email pengguna       |
  | password | string | Yes      | Kata sandi pengguna  |

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Login berhasil",
        "token": "<JWT_TOKEN>"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Email atau password salah"
    }
    ```

## 3. Get All Users

Mendapatkan informasi tentang semua pengguna.

- **URL**

  `/users`

- **Method:**

  `GET`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "result": [
            {
                "user_id": 1,
                "nama": "John Doe",
                "email": "john@example.com"
            },
            {
                "user_id": 2,
                "nama": "Jane Smith",
                "email": "jane@example.com"
            },
        ]
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Missing authentication"
    }
    ```

## 4. Get User by ID

Mendapatkan informasi tentang pengguna berdasarkan ID.

- **URL**

  `/users/{user_id}`

- **Method:**

  `GET`

- **URL Params**

  **Required:**

  `user_id=[integer]`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "user_id": 1,
        "nama": "John Doe",
        "email": "john@example.com"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

## 5. Delete User

Menghapus pengguna berdasarkan ID.

- **URL**

  `/users/{user_id}`

- **Method:**

  `DELETE`

- **URL Params**

  **Required:**

  `user_id=[integer]`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "User berhasil dihapus"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

## 6. Edit User

Mengedit informasi pengguna berdasarkan ID.

- **URL**

  `/users/{user_id}`

- **Method:**

  `PUT`

- **URL Params**

  **Required:**

  `user_id=[integer]`

- **Request Body**

  | Field    | Type   | Required | Description         |
  | -------- | ------ | -------- | ------------------- |
  | nama     | string | No       | Nama pengguna       |
  | email    | string | No       | Email pengguna      |
  | password | string | No       | Kata sandi pengguna |

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Informasi pengguna berhasil diperbarui"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 400 Bad Request <br />
    **Content:**
    ```json
    {
        "status": "fail",
        "result": "Informasi yang dimasukkan tidak valid"
    }
    ```

  - **Code:** 404 Not Found <br />
    **Content:**
    ```json
    {
        "statusCode": 404,
        "error": "Not Found",
        "message": "User not found"
    }
    ```
## 7. Create Income

Membuat data pendapatan baru.

- **URL**

  `/income`

- **Method:**

  `POST`

- **Request Body**

  | Field        | Type   | Required | Description                      |
  | ------------ | ------ | -------- | -------------------------------- |
  | total_income | int    | Yes      | Total pendapatan                 |
  | income_type  | string | Yes      | Jenis pendapatan (Gaji, Bonus, Hadiah, Investasi, Lainnya) |
  | note         | string | No       | Catatan tambahan untuk pendapatan |

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Data pendapatan berhasil dibuat",
        "income_id": 1
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 400 Bad Request <br />
    **Content:**
    ```json
    {
        "status": "fail",
        "result": "Informasi yang dimasukkan tidak valid"
    }
    ```

---

## 8. Get All Incomes

Mendapatkan informasi tentang semua data pendapatan.

- **URL**

  `/income`

- **Method:**

  `GET`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "result": [
            {
                "income_id": 1,
                "total_income": 5000000,
                "income_type": "Gaji",
                "note": "Bonus bulan ini"
            },
            {
                "income_id": 2,
                "total_income": 3000000,
                "income_type": "Bonus",
                "note": null
            },
        ]
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Missing authentication"
    }
    ```

---

## 9. Get Income by ID

Mendapatkan informasi tentang data pendapatan berdasarkan ID.

- **URL**

  `/income/{income_id}`

- **Method:**

  `GET`

- **URL Params**

  **Required:**

  `income_id=[integer]`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "income_id": 1,
        "total_income": 5000000,
        "income_type": "Gaji",
        "note": "Bonus bulan ini"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

---

## 10. Update Income

Mengedit informasi data pendapatan berdasarkan ID.

- **URL**

  `/income/{income_id}`

- **Method:**

  `PUT`

- **URL Params**

  **Required:**

  `income_id=[integer]`

- **Request Body**

  | Field        | Type   | Required | Description                      |
  | ------------ | ------ | -------- | -------------------------------- |
  | total_income | int    | Yes      | Total pendapatan                 |
  | income_type  | string | Yes      | Jenis pendapatan (Gaji, Bonus, Hadiah, Investasi, Lainnya) |
  | note         | string | No       | Catatan tambahan untuk pendapatan |

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Data pendapatan berhasil diperbarui"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 404 Not Found <br />
    **Content:**
    ```json
    {
        "statusCode": 404,
        "error": "Not Found",
        "message": "Income not found"
    }
    ```

---
## 11. Delete Income

Menghapus data pendapatan berdasarkan ID.

- **URL**

  `/income/{income_id}`

- **Method:**

  `DELETE`

- **URL Params**

  **Required:**

  `income_id=[integer]`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Data pendapatan berhasil dihapus"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 404 Not Found <br />
    **Content:**
    ```json
    {
        "statusCode": 404,
        "error": "Not Found",
        "message": "Income not found"
    }
    ```
## 12. Create Outcome

Membuat data pengeluaran baru.

- **URL**

  `/outcome`

- **Method:**

  `POST`

- **Request Body**

  | Field          | Type   | Required | Description                           |
  | -------------- | ------ | -------- | ------------------------------------- |
  | total_outcome  | int    | Yes      | Total pengeluaran                     |
  | outcome_type   | string | Yes      | Jenis pengeluaran (Makan, Minum, Keperluan Rumah, Jajan, Lainnya) |
  | note           | string | No       | Catatan tambahan untuk pengeluaran    |

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Data pengeluaran berhasil dibuat",
        "outcome_id": 1
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 400 Bad Request <br />
    **Content:**
    ```json
    {
        "status": "fail",
        "result": "Informasi yang dimasukkan tidak valid"
    }
    ```

---

## 13. Get All Outcomes

Mendapatkan informasi tentang semua data pengeluaran.

- **URL**

  `/outcome`

- **Method:**

  `GET`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "result": [
            {
                "outcome_id": 1,
                "total_outcome": 2000000,
                "outcome_type": "Makan",
                "note": "Makan di restoran"
            },
            {
                "outcome_id": 2,
                "total_outcome": 500000,
                "outcome_type": "Keperluan Rumah",
                "note": null
            },
            ...
        ]
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Missing authentication"
    }
    ```

---

## 14. Get Outcome by ID

Mendapatkan informasi tentang data pengeluaran berdasarkan ID.

- **URL**

  `/outcome/{outcome_id}`

- **Method:**

  `GET`

- **URL Params**

  **Required:**

  `outcome_id=[integer]`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "outcome_id": 1,
        "total_outcome": 2000000,
        "outcome_type": "Makan",
        "note": "Makan di restoran"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

---

## 15. Update Outcome

Mengedit informasi data pengeluaran berdasarkan ID.

- **URL**

  `/outcome/{outcome_id}`

- **Method:**

  `PUT`

- **URL Params**

  **Required:**

  `outcome_id=[integer]`

- **Request Body**

  | Field          | Type   | Required | Description                           |
  | -------------- | ------ | -------- | ------------------------------------- |
  | total_outcome  | int    | Yes      | Total pengeluaran                     |
  | outcome_type   | string | Yes      | Jenis pengeluaran (Makan, Minum, Keperluan Rumah, Jajan, Lainnya) |
  | note           | string | No       | Catatan tambahan untuk pengeluaran    |

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Data pengeluaran berhasil diperbarui"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 404 Not Found <br />
    **Content:**
    ```json
    {
        "statusCode": 404,
        "error": "Not Found",
        "message": "Outcome not found"
    }
    ```

---

## 16. Delete Outcome

Menghapus data pengeluaran berdasarkan ID.

- **URL**

  `/outcome/{outcome_id}`

- **Method:**

  `DELETE`

- **URL Params**

  **Required:**

  `outcome_id=[integer]`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Data pengeluaran berhasil dihapus"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 404 Not Found <br />
    **Content:**
    ```json
    {
        "statusCode": 404,
        "error": "Not Found",
        "message": "Outcome not found"
    }
    ```

## 17. Create Wallet

Membuat data dompet baru.

- **URL**

  `/wallet`

- **Method:**

  `POST`

- **Request Body**

  | Field       | Type | Required | Description                     |
  | ----------- | ---- | -------- | ------------------------------- |
  | user_id     | int  | Yes      | ID pengguna yang terkait       |
  | income_id   | int  | No       | ID pendapatan yang terkait     |
  | outcome_id  | int  | No       | ID pengeluaran yang terkait    |

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Data dompet berhasil dibuat",
        "wallet_id": 1
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 400 Bad Request <br />
    **Content:**
    ```json
    {
        "status": "fail",
        "result": "Informasi yang dimasukkan tidak valid"
    }
    ```

---

## 18. Get All Wallets

Mendapatkan informasi tentang semua data dompet.

- **URL**

  `/wallet`

- **Method:**

  `GET`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "result": [
            {
                "wallet_id": 1,
                "user_id": 1,
                "income_id": 2,
                "outcome_id": 3
            },
            {
                "wallet_id": 2,
                "user_id": 2,
                "income_id": 4,
                "outcome_id": null
            },
            ...
        ]
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Missing authentication"
    }
    ```

---

## 19. Get Wallet by ID

Mendapatkan informasi tentang data dompet berdasarkan ID.

- **URL**

  `/wallet/{wallet_id}`

- **Method:**

  `GET`

- **URL Params**

  **Required:**

  `wallet_id=[integer]`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "wallet_id": 1,
        "user_id": 1,
        "income_id": 2,
        "outcome_id": 3
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

---

## 20. Update Wallet

Mengedit informasi data dompet berdasarkan ID.

- **URL**

  `/wallet/{wallet_id}`

- **Method:**

  `PUT`

- **URL Params**

  **Required:**

  `wallet_id=[integer]`

- **Request Body**

  | Field       | Type | Required | Description                     |
  | ----------- | ---- | -------- | ------------------------------- |
  | user_id     | int  | Yes      | ID pengguna yang terkait       |
  | income_id   | int  | No       | ID pendapatan yang terkait     |
  | outcome_id  | int  | No       | ID pengeluaran yang terkait    |

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Data dompet berhasil diperbarui"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 404 Not Found <br />
    **Content:**
    ```json
    {
        "statusCode": 404,
        "error": "Not Found",
        "message": "Wallet not found"
    }
    ```

---

## 21. Delete Wallet

Menghapus data dompet berdasarkan ID.

- **URL**

  `/wallet/{wallet_id}`

- **Method:**

  `DELETE`

- **URL Params**

  **Required:**

  `wallet_id=[integer]`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Data dompet berhasil dihapus"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 404 Not Found <br />
    **Content:**
    ```json
    {
        "statusCode": 404,
        "error": "Not Found",
        "message": "Wallet not found"
    }
    ```

---

## 22. Create Recommendation

Membuat rekomendasi baru.

- **URL**

  `/rekomendasi`

- **Method:**

  `POST`

- **Request Body**

  | Field               | Type   | Required | Description                            |
  | ------------------- | ------ | -------- | -------------------------------------- |
  | rasio_pengeluaran   | string | Yes      | Rasio pengeluaran                      |
  | danadarurat         | int    | Yes      | Dana darurat (dalam jumlah tertentu)   |
  | bulan_danadarurat   | string | Yes      | Bulan ke-berapa untuk dana darurat     |
  | prediction_id       | int    | No       | ID prediksi yang terkait               |

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Rekomendasi berhasil dibuat",
        "rekomendasi_id": 1
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 400 Bad Request <br />
    **Content:**
    ```json
    {
        "status": "fail",
        "result": "Informasi yang dimasukkan tidak valid"
    }
    ```

---

## 23. Get All Recommendations

Mendapatkan informasi tentang semua rekomendasi.

- **URL**

  `/rekomendasi`

- **Method:**

  `GET`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "result": [
            {
                "rekomendasi_id": 1,
                "rasio_pengeluaran": "Aggressive",
                "danadarurat": 5000000,
                "bulan_danadarurat": "Desember",
                "prediction_id": 2
            },
            {
                "rekomendasi_id": 2,
                "rasio_pengeluaran": "Conservative",
                "danadarurat": 10000000,
                "bulan_danadarurat": "Januari",
                "prediction_id": null
            },
            ...
        ]
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Missing authentication"
    }
    ```

---

## 24. Update Recommendation

Mengedit informasi rekomendasi berdasarkan ID.

- **URL**

  `/rekomendasi/{rekomendasi_id}`

- **Method:**

  `PUT`

- **URL Params**

  **Required:**

  `rekomendasi_id=[integer]`

- **Request Body**

  | Field               | Type   | Required | Description                            |
  | ------------------- | ------ | -------- | -------------------------------------- |
  | rasio_pengeluaran   | string | Yes      | Rasio pengeluaran                      |
  | danadarurat         | int    | Yes      | Dana darurat (dalam jumlah tertentu)   |
  | bulan_danadarurat   | string | Yes      | Bulan ke-berapa untuk dana darurat     |
  | prediction_id       | int    | No       | ID prediksi yang terkait               |

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Rekomendasi berhasil diperbarui"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 404 Not Found <br />
    **Content:**
    ```json
    {
        "statusCode": 404,
        "error": "Not Found",
        "message": "Recommendation not found"
    }
    ```

---

## 25. Delete Recommendation

Menghapus rekomendasi berdasarkan ID.

- **URL**

  `/rekomendasi/{rekomendasi_id}`

- **Method:**

  `DELETE`

- **URL Params**

  **Required:**

  `rekomendasi_id=[integer]`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Rekomendasi berhasil dihapus"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 404 Not Found <br />
    **Content:**
    ```json
    {
        "statusCode": 404,
        "error": "Not Found",
        "message": "Recommendation not found"
    }
    ```

## 26. Create Prediction

Membuat prediksi baru.

- **URL**

  `/prediction`

- **Method:**

  `POST`

- **Request Body**

  | Field                 | Type   | Required | Description                            |
  | --------------------- | ------ | -------- | -------------------------------------- |
  | total_futureOutcome   | int    | Yes      | Total outcome di masa depan           |
  | pertanyaan_id         | int    | No       | ID pertanyaan yang terkait             |

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Prediksi berhasil dibuat",
        "prediction_id": 1
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 400 Bad Request <br />
    **Content:**
    ```json
    {
        "status": "fail",
        "result": "Informasi yang dimasukkan tidak valid"
    }
    ```

---

## 27. Get All Predictions

Mendapatkan informasi tentang semua prediksi.

- **URL**

  `/prediction`

- **Method:**

  `GET`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "result": [
            {
                "prediction_id": 1,
                "total_futureOutcome": 1500000,
                "pertanyaan_id": 3
            },
            {
                "prediction_id": 2,
                "total_futureOutcome": 2000000,
                "pertanyaan_id": null
            },
            ...
        ]
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Missing authentication"
    }
    ```

---

## 28. Update Prediction

Mengedit informasi prediksi berdasarkan ID.

- **URL**

  `/prediction/{prediction_id}`

- **Method:**

  `PUT`

- **URL Params**

  **Required:**

  `prediction_id=[integer]`

- **Request Body**

  | Field                 | Type   | Required | Description                            |
  | --------------------- | ------ | -------- | -------------------------------------- |
  | total_futureOutcome   | int    | Yes      | Total outcome di masa depan           |
  | pertanyaan_id         | int    | No       | ID pertanyaan yang terkait             |

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Prediksi berhasil diperbarui"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 404 Not Found <br />
    **Content:**
    ```json
    {
        "statusCode": 404,
        "error": "Not Found",
        "message": "Prediction not found"
    }
    ```

---

## 29. Delete Prediction

Menghapus prediksi berdasarkan ID.

- **URL**

  `/prediction/{prediction_id}`

- **Method:**

  `DELETE`

- **URL Params**

  **Required:**

  `prediction_id=[integer]`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Prediksi berhasil dihapus"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 404 Not Found <br />
    **Content:**
    ```json
    {
        "statusCode": 404,
        "error": "Not Found",
        "message": "Prediction not found"
    }
    ```

## 30. Create Pertanyaan

Membuat pertanyaan baru.

- **URL**

  `/pertanyaan`

- **Method:**

  `POST`

- **Request Body**

  | Field                 | Type   | Required | Description                            |
  | --------------------- | ------ | -------- | -------------------------------------- |
  | jenis_kelamin         | enum   | Yes      | Jenis kelamin (Pria/Wanita)           |
  | usia                  | int    | Yes      | Usia responden                        |
  | status_pernikahan     | enum   | Yes      | Status pernikahan                     |
  | pendidikan_terakhir   | enum   | Yes      | Pendidikan terakhir                    |
  | pendapatan_tahunan    | int    | Yes      | Pendapatan tahunan responden          |
  | sumber_pendapatan     | enum   | Yes      | Sumber pendapatan                      |
  | provinsi              | enum   | Yes      | Provinsi tempat tinggal                |
  | tipe_bangunan         | enum   | Yes      | Tipe bangunan tempat tinggal           |
  | luas_rumah            | enum   | Yes      | Luas rumah                             |
  | jumlah_kamar          | enum   | Yes      | Jumlah kamar                           |
  | menggunakan_listrik   | enum   | Yes      | Apakah menggunakan listrik            |
  | status_kepemilikan    | enum   | Yes      | Status kepemilikan                     |
  | tipe_RT               | enum   | Yes      | Tipe RT                                |
  | jumlah_anggotaRT      | int    | Yes      | Jumlah anggota RT                      |
  | jumlah_bekerja        | int    | Yes      | Jumlah anggota RT yang bekerja        |
  | roda4                 | enum   | Yes      | Jumlah kendaraan roda 4                |
  | roda2/3               | enum   | Yes      | Jumlah kendaraan roda 2/3              |
  | jumlah_tv             | enum   | Yes      | Jumlah TV                              |
  | jumlah_ac             | enum   | Yes      | Jumlah AC                              |
  | jumlah_pc             | enum   | Yes      | Jumlah PC                              |
  | jumlah_hp             | enum   | Yes      | Jumlah HP                              |
  | jumlah_kulkas         | enum   | Yes      | Jumlah kulkas                          |
  | jumlah_mesincuci      | enum   | Yes      | Jumlah mesin cuci                      |
  | memiliki_danadarurat | enum   | Yes      | Apakah memiliki dana darurat           |
  | jumlah_danadarurat    | int    | Yes      | Jumlah dana darurat                    |
  | memiliki_utang       | enum   | Yes      | Apakah memiliki utang                 |
  | jumlah_utang          | int    | Yes      | Jumlah utang                           |

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Pertanyaan berhasil dibuat",
        "pertanyaan_id": 1
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 400 Bad Request <br />
    **Content:**
    ```json
    {
        "status": "fail",
        "result": "Informasi yang dimasukkan tidak valid"
    }
    ```

---

## 31. Get All Pertanyaan

Mendapatkan informasi tentang semua pertanyaan.

- **URL**

  `/pertanyaan`

- **Method:**

  `GET`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "result": [
            {
                "pertanyaan_id": 1,
                "jenis_kelamin": "Pria",
                "usia": 30,
                "status_pernikahan": "Menikah",
                "pendidikan_terakhir": "S1",
                "pendapatan_tahunan": 80000000,
                "sumber_pendapatan": "Wirausaha",
                "provinsi": "Jawa Barat",
                "tipe_bangunan": "Perumahan Multi Unit",
                "luas_rumah": "101 - 150 m²",
                "jumlah_kamar": "3",
                "menggunakan_listrik": "Ya",
                "status_kepemilikan": "Milik Sendiri",
                "tipe_RT": "Keluarga Besar",
                "jumlah_anggotaRT": 5,
                "jumlah_bekerja": 3,
                "roda4": "2",
                "roda2/3": "1",
                "jumlah_tv": "2",
                "jumlah_ac": "3",
                "jumlah_pc": "1",
                "jumlah_hp": "3",
                "jumlah_kulkas": "1",
                "jumlah_mesincuci": "1",
                "memiliki_danadarurat": "Sudah",
                "jumlah_danadarurat": 10000000,
                "memiliki_utang": "Ya",
                "jumlah_utang": 5000000
            },
            {
                "pertanyaan_id": 2,
                "jenis_kelamin": "Wanita",
                "usia": 35,
                "status_pernikahan": "Lajang",
                "pendidikan_terakhir": "S2",
                "pendapatan_tahunan": 120000000,
                "sumber_pendapatan": "Upah/Gaji",
                "provinsi": "DKI Jakarta",
                "tipe_bangunan": "Apartemen",
                "luas_rumah": "< 30 m²",
                "jumlah_kamar": "1",
                "menggunakan_listrik": "Ya",
                "status_kepemilikan": "Kontrak",
                "tipe_RT": "Dua atau Lebih Orang/Anggota yang Tidak Berhubungan",
                "jumlah_anggotaRT": 2,
                "jumlah_bekerja": 1,
                "roda4": "0",
                "roda2/3": "1",
                "jumlah_tv": "1",
                "jumlah_ac": "1",
                "jumlah_pc": "0",
                "jumlah_hp": "2",
                "jumlah_kulkas": "1",
                "jumlah_mesincuci": "0",
                "memiliki_danadarurat": "Belum",
                "jumlah_danadarurat": 0,
                "memiliki_utang": "Tidak",
                "jumlah_utang": 0
            },
            ...
        ]
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Missing authentication"
    }
    ```

---

## 32. Update Pertanyaan

Mengedit informasi pertanyaan berdasarkan ID.

- **URL**

  `/pertanyaan/{pertanyaan_id}`

- **Method:**

  `PUT`

- **URL Params**

  **Required:**

  `pertanyaan_id=[integer]`

- **Request Body**

  | Field                 | Type   | Required | Description                            |
  | --------------------- | ------ | -------- | -------------------------------------- |
  | jenis_kelamin         | enum   | Yes      | Jenis kelamin (Pria/Wanita)           |
  | usia                  | int    | Yes      | Usia responden                        |
  | status_pernikahan     | enum   | Yes      | Status pernikahan                     |
  | pendidikan_terakhir   | enum   | Yes      | Pendidikan terakhir                    |
  | pendapatan_tahunan    | int    | Yes      | Pendapatan tahunan responden          |
  | sumber_pendapatan     | enum   | Yes      | Sumber pendapatan                      |
  | provinsi              | enum   | Yes      | Provinsi tempat tinggal                |
  | tipe_bangunan         | enum   | Yes      | Tipe bangunan tempat tinggal           |
  | luas_rumah            | enum   | Yes      | Luas rumah                             |
  | jumlah_kamar          | enum   | Yes      | Jumlah kamar                           |
  | menggunakan_listrik   | enum   | Yes      | Apakah menggunakan listrik            |
  | status_kepemilikan    | enum   | Yes      | Status kepemilikan                     |
  | tipe_RT               | enum   | Yes      | Tipe RT                                |
  | jumlah_anggotaRT      | int    | Yes      | Jumlah anggota RT                      |
  | jumlah_bekerja        | int    | Yes      | Jumlah anggota RT yang                 |
  | roda4                 | enum   | Yes      | Jumlah kendaraan roda 4                |
  | roda2/3               | enum   | Yes      | Jumlah kendaraan roda 2/3              |
  | jumlah_tv             | enum   | Yes      | Jumlah TV                              |
  | jumlah_ac             | enum   | Yes      | Jumlah AC                              |
  | jumlah_pc             | enum   | Yes      | Jumlah PC                              |
  | jumlah_hp             | enum   | Yes      | Jumlah HP                              |
  | jumlah_kulkas         | enum   | Yes      | Jumlah kulkas                          |
  | jumlah_mesincuci      | enum   | Yes      | Jumlah mesin cuci                      |
  | memiliki_danadarurat | enum   | Yes      | Apakah memiliki dana darurat           |
  | jumlah_danadarurat    | int    | Yes      | Jumlah dana darurat                    |
  | memiliki_utang       | enum   | Yes      | Apakah memiliki utang                 |
  | jumlah_utang          | int    | Yes      | Jumlah utang                           |

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Pertanyaan berhasil diperbarui"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 400 Bad Request <br />
    **Content:**
    ```json
    {
        "status": "fail",
        "result": "Informasi yang dimasukkan tidak valid"
    }
    ```

---

## 33. Delete Pertanyaan

Menghapus pertanyaan berdasarkan ID.

- **URL**

  `/pertanyaan/{pertanyaan_id}`

- **Method:**

  `DELETE`

- **URL Params**

  **Required:**

  `pertanyaan_id=[integer]`

- **Success Response:**

  - **Code:** 200 OK <br />
    **Content:**
    ```json
    {
        "status": "success",
        "message": "Pertanyaan berhasil dihapus"
    }
    ```

- **Error Response:**

  - **Code:** 401 Unauthorized <br />
    **Content:**
    ```json
    {
        "statusCode": 401,
        "error": "Unauthorized",
        "message": "Invalid token"
    }
    ```

  - **Code:** 404 Not Found <br />
    **Content:**
    ```json
    {
        "statusCode": 404,
        "error": "Not Found",
        "message": "Pertanyaan tidak ditemukan"
    }
    ```
