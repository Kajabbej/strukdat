#  Struktur Data — Catatan Belajar

```{raw} html
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@300;400;500&display=swap" rel="stylesheet">
<style>
.profile-wrapper { font-family: 'DM Mono', monospace; max-width: 820px; margin: 2rem auto; }
.hero { background: #12120d; border-radius: 20px; padding: 2.5rem; margin-bottom: 1.25rem; }
.hero-tag { display: inline-block; font-size: 10px; letter-spacing: 0.15em; text-transform: uppercase; color: #C8A96E; background: rgba(200,169,110,0.1); border: 0.5px solid rgba(200,169,110,0.25); padding: 5px 14px; border-radius: 999px; margin-bottom: 1.25rem; }
.hero-title { font-family: 'Syne', sans-serif; font-size: 2rem; font-weight: 800; color: #F7F5F0; line-height: 1.15; margin-bottom: 0.75rem; }
.hero-title span { color: #C8A96E; }
.hero-line { width: 40px; height: 2px; background: linear-gradient(90deg, #C8A96E, transparent); margin-bottom: 0.75rem; }
.hero-sub { font-size: 11px; color: #5A6370; letter-spacing: 0.08em; }
.card-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; margin-bottom: 1rem; }
.profile-card { background: #fff; border: 0.5px solid #E2E4E7; border-radius: 16px; overflow: hidden; box-shadow: 0 4px 24px rgba(0,0,0,0.08); }
.card-header { background: #0D0F12; padding: 1.5rem; display: flex; align-items: center; gap: 1rem; }
.avatar { width: 64px; height: 64px; border-radius: 14px; background: linear-gradient(135deg, #1e2328, #2C3036); border: 1.5px solid rgba(200,169,110,0.2); display: flex; align-items: center; justify-content: center; font-size: 26px; flex-shrink: 0; }
.c-role { font-size: 9px; letter-spacing: 0.15em; text-transform: uppercase; color: #C8A96E; margin: 0 0 4px; }
.c-name { font-family: 'Syne', sans-serif; font-size: 14px; font-weight: 700; color: #F7F5F0; margin: 0 0 4px; line-height: 1.3; }
.c-nim { font-size: 10px; color: #4A5260; background: rgba(255,255,255,0.05); border: 0.5px solid rgba(255,255,255,0.08); padding: 2px 10px; border-radius: 999px; display: inline-block; }
.card-body { padding: 1.25rem 1.5rem; }
.info-item { display: flex; gap: 12px; padding: 7px 0; border-bottom: 0.5px solid #F4F5F7; }
.info-item:last-child { border-bottom: none; padding-bottom: 0; }
.info-key { font-size: 10px; color: #9BA4AE; min-width: 90px; flex-shrink: 0; }
.info-val { font-size: 11px; font-weight: 500; color: #0D0F12; }
.academic-card { background: #0D0F12; border-radius: 16px; overflow: hidden; }
.academic-top { padding: 1.25rem 1.5rem; border-bottom: 0.5px solid rgba(255,255,255,0.06); display: flex; align-items: center; gap: 10px; }
.academic-label { font-size: 10px; letter-spacing: 0.15em; text-transform: uppercase; color: #C8A96E; }
.academic-grid { padding: 1.25rem 1.5rem; display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1.5rem; }
.ac-label { font-size: 9px; letter-spacing: 0.12em; text-transform: uppercase; color: #3A4250; margin-bottom: 6px; }
.ac-val { font-size: 12px; font-weight: 500; color: #C8D0D8; }
.matkul-tag { display: inline-block; background: rgba(200,169,110,0.12); color: #C8A96E; border: 0.5px solid rgba(200,169,110,0.25); font-size: 11px; padding: 4px 14px; border-radius: 999px; }
.footer-note { text-align: center; font-size: 10px; color: #9BA4AE; margin-top: 1.25rem; letter-spacing: 0.08em; }
</style>

<div class="profile-wrapper">
  <div class="hero">
    <div class="hero-tag">Semester Genap 2025/2026</div>
    <h2 class="hero-title">Catatan Belajar<br><span>Struktur Data</span></h2>
    <div class="hero-line"></div>
    <p class="hero-sub">S1 Teknik Informatika · Universitas Trunojoyo Madura · Semester II</p>
  </div>
  <div class="card-grid">
    <div class="profile-card">
      <div class="card-header">
        <div class="avatar">
          <img src="https://kajabbej.github.io/strukdat/images/logo.png" alt="Foto Ghufron">
        </div>
        <div>
          <p class="c-role">Mahasiswa</p>
          <p class="c-name">Moh. Ghufron</p>
          <span class="c-nim">250411100196</span>
        </div>
      </div>
      <div class="card-body">
        <div class="info-item"><span class="info-key">Nama Panggil</span><span class="info-val">Ghufron</span></div>
        <div class="info-item"><span class="info-key">Fakultas</span><span class="info-val">Teknik / Informatika</span></div>
        <div class="info-item"><span class="info-key">Program Studi</span><span class="info-val">S1 Teknik Informatika</span></div>
        <div class="info-item"><span class="info-key">TTL</span><span class="info-val">Bangkalan, 18 Desember 2005</span></div>
        <div class="info-item"><span class="info-key">Agama</span><span class="info-val">Islam</span></div>
        <div class="info-item"><span class="info-key">Domisili</span><span class="info-val">Telang, Kamal, Bangkalan</span></div>
        <div class="info-item"><span class="info-key">WhatsApp</span><span class="info-val">085189374748</span></div>
        <div class="info-item"><span class="info-key">Email kampus</span><span class="info-val">humas@trunojoyo.ac.id</span></div>
      </div>
    </div>
    <div class="profile-card">
      <div class="card-header">
        <div class="avatar"></div>
        <div>
          <p class="c-role">Dosen Pengampu</p>
          <p class="c-name">Dr. Arik Kurniawati S.Kom., M.T</p>
          <span class="c-nim">197803092003122009</span>
        </div>
      </div>
      <div class="card-body">
        <div class="info-item"><span class="info-key">NIP / NIDN</span><span class="info-val">197803092003122009</span></div>
        <div class="info-item"><span class="info-key">Jabatan</span><span class="info-val">Dosen Pengampu Struktur Data</span></div>
        <div class="info-item"><span class="info-key">Jadwal</span><span class="info-val">Setiap Selasa, 13:00 WIB</span></div>
        <div class="info-item"><span class="info-key">No. Telepon</span><span class="info-val">—</span></div>
        <div class="info-item"><span class="info-key">Email Dosen</span><span class="info-val">—</span></div>
      </div>
    </div>
  </div>
  <div class="academic-card">
    <div class="academic-top">
      <span style="font-size:14px;">📋</span>
      <p class="academic-label">Data Akademik</p>
    </div>
    <div class="academic-grid">
      <div><p class="ac-label">Mata Kuliah</p><span class="matkul-tag">Struktur Data</span></div>
      <div><p class="ac-label">Periode Semester</p><p class="ac-val">Genap 2025/2026</p></div>
      <div><p class="ac-label">Jadwal Bimbingan</p><p class="ac-val">Selasa, 13:00 WIB</p></div>
    </div>
  </div>
  <p class="footer-note">Catatan ini dibuat sebagai dokumentasi belajar pribadi · Universitas Trunojoyo Madura</p>
</div>
```

## Materi

1. Stack & Queue
2. Infix, Prefix, dan Postfix
3. Sorting
4. Hashing
5. List

## Tugas

1. Stack

> Dibuat menggunakan Jupyter Book_2026