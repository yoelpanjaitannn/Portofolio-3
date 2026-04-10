# 📊 Financial Diagnostic — UD Sumber Rejeki (Simulasi Portofolio)

> **Disclaimer:** Seluruh data, nama klien, dan angka dalam repositori ini bersifat fiktif dan dibuat untuk keperluan simulasi portofolio. Tidak merepresentasikan kondisi bisnis nyata manapun.

---

## Latar Belakang

Proyek ini adalah studi kasus diagnostik keuangan untuk distributor sembako skala menengah di Surabaya. Klien fiktif (UD Sumber Rejeki) mengalami fenomena yang umum di UMKM Indonesia: **omzet terlihat bagus, tapi kas terus mengering.**

Periode data: **Januari 2024 – Desember 2025** (2 tahun)

Pendekatan: **Fractional Financial Controller** — masuk, bongkar datanya, temukan akar masalahnya, tetapkan langkah konkret.

---

## Temuan Utama

| Metrik | Nilai | Keterangan |
|--------|-------|------------|
| Total Omzet 2 Tahun | Rp 22,74 Miliar | Terlihat sehat secara nominal |
| DSO (Days Sales Outstanding) | 195,5 hari | Standar industri: 30–45 hari |
| DPO (Days Payable Outstanding) | 718,4 hari | Hutang supplier dibiarkan menumpuk |
| CCC (Cash Conversion Cycle) | −496 hari | Bom waktu, bukan efisiensi |
| CEI (Collection Efficiency Index) | 73,2% | Gap Rp 1,34 miliar kas tertahan |
| Gross Margin | 12,3% | Tidak punya buffer kenaikan biaya |
| AR Outstanding | Rp 3,04 Miliar | 59% sudah 90+ hari |
| AP Outstanding | Rp 9,81 Miliar | 75,7% sudah 90+ hari |

---

## Struktur Data (Raw / Data Kotor)

File: `UD_Sumber_Rejeki_AllData.xlsx`

Dataset ini sengaja dibuat dengan kondisi data "dunia nyata" — tidak bersih, tidak sempurna, mencerminkan bagaimana data bisnis UMKM biasanya ditemukan di lapangan.

| Sheet | Jumlah Baris | Isi |
|-------|-------------|-----|
| `Master Pelanggan` | 85 baris | ID, nama, tipe (warung/minimarket/kantin), kota, credit terms |
| `Master Produk` | 30 baris | ID, nama produk, kategori, harga jual, HPP, stok |
| `Master Supplier` | 15 baris | ID, nama supplier, kategori produk, term of payment |
| `Penjualan` | 4.345 baris | Invoice penjualan: tanggal, jatuh tempo, pelanggan, produk, qty, total, margin |
| `Pembayaran AR` | 3.169 baris | Realisasi pembayaran dari pelanggan: tanggal bayar, metode, status |
| `Hutang AP` | 804 baris | Invoice pembelian ke supplier: tanggal, jatuh tempo, status bayar |
| `Pengeluaran Ops` | 928 baris | Pengeluaran operasional, gaji, dan prive — sengaja dicampur dalam satu tabel |

### Catatan tentang "Kotor"-nya Data

Beberapa kondisi yang sengaja dimasukkan untuk mencerminkan realita UMKM:

- **Prive dicampur dengan pengeluaran operasional** di sheet `Pengeluaran Ops` — tidak dipisah, tidak ada approval
- **Tidak ada flag otomatis** untuk invoice yang sudah melewati jatuh tempo
- **Data pembayaran AR tidak selalu 1:1 dengan invoice** — ada pembayaran parsial
- **Beberapa AP statusnya "Terlambat"** tapi tidak ada catatan tindak lanjut

---

## Konteks Ekonomi yang Dimasukkan ke Data

Data ini dibuat dengan mempertimbangkan kondisi makroekonomi riil sebagai latar belakang:

**2024**
- Q1: Harga beras & minyak goreng masih tinggi (efek El Niño) → HPP naik 8–12%
- Q2: Pelemahan rupiah mendekati Rp 16.000/USD → harga produk kemasan impor naik
- Juli–Agustus: Krisis cashflow (cerita utama simulasi ini)
- Q4: Persiapan kenaikan PPN 12% → beberapa supplier mulai naikkan harga

**2025**
- Januari: PPN naik ke 12% → biaya operasional naik langsung terasa
- Q1: Daya beli turun pasca kenaikan PPN → pelanggan warung kecil mulai telat bayar
- Maret–April: Lebaran → penjualan melonjak tapi piutang ikut membengkak
- Mei–Juni: Pasca lebaran, beberapa pelanggan kesulitan bayar → DSO memanjang

---

## Output Analisis

Hasil diagnostik lengkap tersedia dalam file `Executive_Summary_v4.docx`, mencakup:

1. Ringkasan Eksekutif & Metrik Utama
2. Analisis AR Aging (Piutang Usaha)
3. Analisis AP Aging (Hutang ke Supplier)
4. Cash Conversion Cycle (CCC)
5. Efisiensi Penagihan: CEI & Pareto 80/20
6. Bedah Krisis Cashflow Juli–Agustus 2024
7. Analisis Gross Margin & Dampak PPN 12%
8. Rekomendasi Tindakan (0–30 hari, 30–90 hari, 90–180 hari)

---

## Status Proyek

- ✅ **Phase 1** — Financial Diagnostic & Action Plan (selesai)
- ⏳ **Phase 2** — Automated Early Warning System Dashboard (dalam pengerjaan)

---

## Tentang

Dibuat oleh **Yoel William Panjaitan** sebagai bagian dari portofolio Fractional Financial Controller.

Metodologi dan pendekatan analisis mencerminkan standar praktik profesional dalam diagnostik keuangan UMKM.
