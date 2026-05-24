#  Struktur Data — Catatan Belajar

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@300;400;500;600&family=Playfair+Display:wght@600&display=swap');

.profile-wrapper {
  font-family: 'DM Sans', sans-serif;
  max-width: 860px;
  margin: 2rem auto;
}

.profile-header {
  background: linear-gradient(135deg, #111314 0%, #1e2328 100%);
  border-radius: 16px;
  padding: 2.5rem;
  color: #E8EAED;
  margin-bottom: 1.5rem;
  position: relative;
  overflow: hidden;
}

.profile-header::before {
  content: '';
  position: absolute;
  top: -60px;
  right: -60px;
  width: 200px;
  height: 200px;
  border-radius: 50%;
  background: rgba(200,169,110,0.06);
  pointer-events: none;
}

.profile-header::after {
  content: '';
  position: absolute;
  bottom: -40px;
  left: -40px;
  width: 150px;
  height: 150px;
  border-radius: 50%;
  background: rgba(155,164,174,0.05);
  pointer-events: none;
}

.header-top {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.badge-semester {
  display: inline-block;
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  background: rgba(200,169,110,0.15);
  color: #C8A96E;
  border: 0.5px solid rgba(200,169,110,0.3);
  padding: 4px 14px;
  border-radius: 999px;
}

.header-title {
  font-family: 'Playfair Display', serif;
  font-size: 2rem;
  color: #E8EAED;
  margin: 0 0 0.25rem;
  line-height: 1.2;
}

.header-sub {
  font-size: 13px;
  color: #8A9099;
  letter-spacing: 0.04em;
  margin: 0;
}

.divider-gold {
  width: 48px;
  height: 1.5px;
  background: linear-gradient(90deg, #C8A96E, transparent);
  margin: 1rem 0;
}

/* CARD GRID */
.card-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.25rem;
  margin-bottom: 1.25rem;
}

@media (max-width: 600px) {
  .card-grid { grid-template-columns: 1fr; }
  .header-title { font-size: 1.5rem; }
}

.profile-card {
  background: #fff;
  border: 0.5px solid #E2E4E7;
  border-radius: 14px;
  overflow: hidden;
  box-shadow: 0 2px 12px rgba(0,0,0,0.06);
  transition: box-shadow 0.2s;
}

.profile-card:hover {
  box-shadow: 0 6px 24px rgba(0,0,0,0.10);
}

.card-top {
  padding: 1.5rem 1.5rem 1rem;
  display: flex;
  align-items: flex-start;
  gap: 1rem;
}

.photo-circle {
  width: 72px;
  height: 72px;
  border-radius: 50%;
  background: linear-gradient(135deg, #2C3036, #111314);
  border: 2.5px solid #E2E4E7;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 28px;
  flex-shrink: 0;
  overflow: hidden;
  position: relative;
}

.photo-circle img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 50%;
}

.photo-placeholder {
  font-size: 11px;
  color: #9BA4AE;
  text-align: center;
  line-height: 1.4;
  padding: 0 6px;
}

.card-name {
  font-size: 15px;
  font-weight: 600;
  color: #1A1D20;
  margin: 0 0 3px;
}

.card-role {
  font-size: 11px;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: #9BA4AE;
  margin: 0 0 6px;
}

.card-nim {
  font-size: 12px;
  color: #5A6370;
  font-family: 'DM Sans', monospace;
  background: #F4F5F6;
  padding: 2px 10px;
  border-radius: 999px;
  display: inline-block;
  margin: 0;
}

.card-divider {
  height: 0.5px;
  background: #F0F1F3;
  margin: 0;
}

.card-info {
  padding: 1rem 1.5rem 1.25rem;
}

.info-row {
  display: flex;
  gap: 10px;
  align-items: flex-start;
  margin-bottom: 8px;
}

.info-row:last-child { margin-bottom: 0; }

.info-label {
  font-size: 11px;
  color: #9BA4AE;
  min-width: 100px;
  padding-top: 1px;
  flex-shrink: 0;
}

.info-value {
  font-size: 12px;
  color: #1A1D20;
  font-weight: 500;
  line-height: 1.5;
}

/* ACADEMIC CARD */
.academic-card {
  background: #fff;
  border: 0.5px solid #E2E4E7;
  border-radius: 14px;
  overflow: hidden;
  box-shadow: 0 2px 12px rgba(0,0,0,0.06);
}

.academic-header {
  background: linear-gradient(135deg, #111314, #1e2328);
  padding: 1rem 1.5rem;
  display: flex;
  align-items: center;
  gap: 10px;
}

.academic-title {
  font-size: 13px;
  font-weight: 500;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: #C8A96E;
  margin: 0;
}

.academic-body {
  padding: 1.25rem 1.5rem;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 1rem;
}

@media (max-width: 600px) {
  .academic-body { grid-template-columns: 1fr; }
}

.academic-item {}

.academic-item-label {
  font-size: 10px;
  color: #9BA4AE;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  margin: 0 0 3px;
}

.academic-item-value {
  font-size: 13px;
  font-weight: 500;
  color: #1A1D20;
  margin: 0;
}

.tag-matkul {
  display: inline-block;
  background: linear-gradient(135deg, #111314, #2C3036);
  color: #C8A96E;
  font-size: 12px;
  font-weight: 500;
  padding: 4px 14px;
  border-radius: 999px;
  margin-top: 2px;
}

/* FOOTER NOTE */
.footer-note {
  text-align: center;
  font-size: 11px;
  color: #9BA4AE;
  margin-top: 1.25rem;
  letter-spacing: 0.06em;
}
</style>

<div class="profile-wrapper">

  <div class="profile-header">
    <div class="header-top">
      <span class="badge-semester">Semester Genap 2025/2026</span>
    </div>
    <h2 class="header-title">Catatan Belajar<br>Struktur Data</h2>
    <div class="divider-gold"></div>
    <p class="header-sub">S1 Teknik Informatika &nbsp;·&nbsp; Universitas Trunojoyo Madura &nbsp;·&nbsp; Semester II</p>
  </div>


  <div class="card-grid">

   
    <div class="profile-card">
      <div class="card-top">
        <div class="photo-circle">
          <!-- Ganti src dengan path foto kamu, contoh: images/foto_ghufron.jpg -->
          <!-- <img src="images/foto_ghufron.jpg" alt="Foto Mahasiswa"> -->
          <span style="font-size:28px;">🎓</span>
        </div>
        <div>
          <p class="card-role">Mahasiswa</p>
          <p class="card-name">Moh. Ghufron</p>
          <p class="card-nim">250411100196</p>
        </div>
      </div>
      <div class="card-divider"></div>
      <div class="card-info">
        <div class="info-row">
          <span class="info-label">Nama Panggil</span>
          <span class="info-value">Ghufron</span>
        </div>
        <div class="info-row">
          <span class="info-label">Fakultas</span>
          <span class="info-value">Teknik / Informatika</span>
        </div>
        <div class="info-row">
          <span class="info-label">Program Studi</span>
          <span class="info-value">S1 Teknik Informatika</span>
        </div>
        <div class="info-row">
          <span class="info-label">TTL</span>
          <span class="info-value">Bangkalan, 18 Desember 2005</span>
        </div>
        <div class="info-row">
          <span class="info-label">Agama</span>
          <span class="info-value">Islam</span>
        </div>
        <div class="info-row">
          <span class="info-label">Domisili</span>
          <span class="info-value">Telang, Kamal, Bangkalan</span>
        </div>
        <div class="info-row">
          <span class="info-label">WhatsApp</span>
          <span class="info-value">085189374748</span>
        </div>
        <div class="info-row">
          <span class="info-label">Email</span>
          <span class="info-value">humas@trunojoyo.ac.id</span>
        </div>
      </div>
    </div>

    <div class="profile-card">
      <div class="card-top">
        <div class="photo-circle">
          <img src="images/foto_ghufron.jpg" alt="Foto Mahasiswa">
          <img src="images/logo.png" alt="Foto Mahasiswa">
          <span style="font-size:28px;">👩‍🏫</span>
        </div>
        <div>
          <p class="card-role">Dosen Pengampu</p>
          <p class="card-name">Dr. Arik Kurniawati<br>S.Kom., M.T</p>
          <p class="card-nim">197803092003122009</p>
        </div>
      </div>
      <div class="card-divider"></div>
      <div class="card-info">
        <div class="info-row">
          <span class="info-label">NIP / NIDN</span>
          <span class="info-value">197803092003122009</span>
        </div>
        <div class="info-row">
          <span class="info-label">Jabatan</span>
          <span class="info-value">Dosen Pengampu Struktur Data</span>
        </div>
        <div class="info-row">
          <span class="info-label">Jadwal Bimbingan</span>
          <span class="info-value">Setiap Selasa, 13:00 WIB</span>
        </div>
        <div class="info-row">
          <span class="info-label">No. Telepon</span>
          <span class="info-value">—</span>
        </div>
        <div class="info-row">
          <span class="info-label">Email Dosen</span>
          <span class="info-value">—</span>
        </div>
      </div>
    </div>

  </div>


  <div class="academic-card">
    <div class="academic-header">
      <span style="font-size:16px;">📋</span>
      <p class="academic-title">Data Akademik</p>
    </div>
    <div class="academic-body">
      <div class="academic-item">
        <p class="academic-item-label">Mata Kuliah</p>
        <span class="tag-matkul">Struktur Data</span>
      </div>
      <div class="academic-item">
        <p class="academic-item-label">Periode Semester</p>
        <p class="academic-item-value">Genap 2025/2026</p>
      </div>
      <div class="academic-item">
        <p class="academic-item-label">Jadwal Bimbingan</p>
        <p class="academic-item-value">Selasa, 13:00 WIB</p>
      </div>
    </div>
  </div>

  <p class="footer-note">Catatan ini dibuat sebagai dokumentasi belajar pribadi &nbsp;·&nbsp; Universitas Trunojoyo Madura</p>

</div> 
## Materi

1. Stack & Queue
2. Infix, Prefix, dan Postfix
3. Sorting
4. Hashing
5. List

## Tugas

1. Stack

> Dibuat menggunakan Jupyter Book_2026