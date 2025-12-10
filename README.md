# API Bridging RS Plebo

## POST MCU
``` http
http://bridging-plebo.adamlabs.id/adam-lis/api/v1/registrasi_bulk_mcu/create?kode_rs=J05&kode_lab=LAB_One_Plebo
```
NOTE: gunakan `kode_rs` dan `kode_lab` yang telah terintegrasi dengan Adamlis

Request Body
``` json
{
  "periksa_now": true,
  "nama": "MCU Vertex Corp",
  "perusahaan": "Vertex Corp",
  "data": [
    {
      "registrasi": {
        "no_registrasi": "VERTEX-PROJECT-DEMO000011",
        "diagnosa_awal": "-",
        "keterangan_klinis": "-",
        "kode_rs": "J05"
      },
      "pasien": {
        "nama": "Bridget Hudson",
        "no_rm": "VERTEX-PROJECT-DEMO000011",
        "jenis_kelamin": "P",
        "alamat": "-",
        "no_telphone": "-",
        "tanggal_lahir": "1976-11-16",
        "nik": "1111111111111111",
        "ras": "-",
        "berat_badan": "0kg",
        "jenis_registrasi": "Reguler",
        "m_provinsi_id": "BANTEN",
        "m_kabupaten_id": "KOTA TANGERANG SELATAN",
        "m_kecamatan_id": "PONDOK AREN"
      },
      "kode_dokter_pengirim": "DR_LARAS",
      "nama_dokter_pengirim": "dr. Laras Sheila Andini",
      "kode_unit_asal": "PLBBB",
      "nama_unit_asal": "Plebo B2B",
      "kode_penjamin": "CORPORATE",
      "nama_penjamin": "CORPORATE",
      "kode_icdt": "-",
      "nama_icdt": "-",
      "tindakan": [
        {
          "kode_tindakan": "GNJL10001",
          "nama_tindakan": "Asam Urat"
        },
        {
          "kode_tindakan": "GNJL10101",
          "nama_tindakan": "Ureum"
        }
      ]
    },
    {
      "registrasi": {
        "no_registrasi": "VERTEX-PROJECT-DEMO000017",
        "diagnosa_awal": "-",
        "keterangan_klinis": "-",
        "kode_rs": "J05"
      },
      "pasien": {
        "nama": "Kyle Rodriguez",
        "no_rm": "VERTEX-PROJECT-DEMO000017",
        "jenis_kelamin": "L",
        "alamat": "-",
        "no_telphone": "-",
        "tanggal_lahir": "1989-11-23",
        "nik": "1111111111111111",
        "ras": "-",
        "berat_badan": "0kg",
        "jenis_registrasi": "Reguler",
        "m_provinsi_id": "BANTEN",
        "m_kabupaten_id": "KOTA TANGERANG SELATAN",
        "m_kecamatan_id": "PONDOK AREN"
      },
      "kode_dokter_pengirim": "DR_LARAS",
      "nama_dokter_pengirim": "dr. Laras Sheila Andini",
      "kode_unit_asal": "PLBBB",
      "nama_unit_asal": "Plebo B2B",
      "kode_penjamin": "CORPORATE",
      "nama_penjamin": "CORPORATE",
      "kode_icdt": "-",
      "nama_icdt": "-",
      "tindakan": [
        {
          "kode_tindakan": "GNJL10001",
          "nama_tindakan": "Asam Urat"
        },
        {
          "kode_tindakan": "GNJL10101",
          "nama_tindakan": "Ureum"
        }
      ]
    }
  ]
}
```
## Success Response
``` json
{
    "success": true,
    "code": 201,
    "message": "Data MCU Berhasil Ditambahkan",
    "payload": [
      {
        "nolab": "B23/251203/0001",
        "nama_pasien": "Calvin",
        "no_rm": "VERTEX-PROJECT-DEMO000009",
        "no_registrasi": "MCU001"
      },
      {
        "nolab": "B23/251203/0002",
        "nama_pasien": "Bhisma",
        "no_rm": "VERTEX-PROJECT-DEMO000010",
        "no_registrasi": "MCU002"
      }
    ]
}
```

## Error Resonse
### Bad Request
``` json
{
  "message": "Bad request",
  "success": false,
  "errors": [
    {
      "field": "periksa_now",
      "message": "periksa_now harus boolean true | false"
    }
  ]
}
```

### Internal Server Error
``` json
{
  "messsage": "Internal Server Error",
  "success": false,
  "errors": [
    {
      "message": "Gagal membuat MCU, silakan coba lagi setelah 5 menit"
    }
  ]
}
```

### Confilc Data
``` json
{
  "messsage": "Conflic",
  "success": false,
  "errors": [
    {
      "message": "Nomer RM duplikat ditemukan: VORTEXU001"
    }
  ]
}
```