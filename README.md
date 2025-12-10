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
  "nama": "MCU example",
  "perusahaan": "example company",
  "data": [
    {
      "registrasi": {
        "no_registrasi": "VERTEX-PROJECT-DEMO000011",
        "diagnosa_awal": "-",
        "keterangan_klinis": "-",
        "kode_rs": "J05"
      },
      "pasien": {
        "nama": "Asmin",
        "no_rm": "VERTEX-PROJECT-DEMO000011",
        "jenis_kelamin": "P",
        "alamat": "-",
        "no_telphone": "-",
        "tanggal_lahir": "1972-11-16",
        "nik": "1111111111111111",
        "ras": "-",
        "berat_badan": "0kg",
        "jenis_registrasi": "Reguler",
        "m_provinsi_id": "BANTEN",
        "m_kabupaten_id": "KOTA TANGERANG SELATAN",
        "m_kecamatan_id": "PONDOK AREN"
      },
      "kode_dokter_pengirim": "DR_MANSYUR",
      "nama_dokter_pengirim": "dr. mansyur setia budi",
      "kode_unit_asal": "UNTR",
      "nama_unit_asal": "untr B2B",
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
        "nama": "Mala",
        "no_rm": "VERTEX-PROJECT-DEMO000017",
        "jenis_kelamin": "L",
        "alamat": "-",
        "no_telphone": "-",
        "tanggal_lahir": "1983-11-23",
        "nik": "1111111111111111",
        "ras": "-",
        "berat_badan": "0kg",
        "jenis_registrasi": "Reguler",
        "m_provinsi_id": "BANTEN",
        "m_kabupaten_id": "KOTA TANGERANG SELATAN",
        "m_kecamatan_id": "PONDOK AREN"
      },
      "kode_dokter_pengirim": "DR_JOKO",
      "nama_dokter_pengirim": "dr. Joko Pratomo Admojo",
      "kode_unit_asal": "UNTR",
      "nama_unit_asal": "untr B2B",
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
        "nolab": "J03/251203/0001",
        "nama_pasien": "Asmin",
        "no_rm": "VERTEX-PROJECT-DEMO000011",
        "no_registrasi": "MCU001"
      },
      {
        "nolab": "J03/251203/0002",
        "nama_pasien": "Mala",
        "no_rm": "VERTEX-PROJECT-DEMO000017",
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
  "code": 400,
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
  "code": 500,
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
  "code": 409,
  "errors": [
    {
      "message": "Nomer RM duplikat ditemukan: VORTEXU001"
    }
  ]
}
```