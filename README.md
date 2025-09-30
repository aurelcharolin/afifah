<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Data Entry Siswa SMK N 1 Purbalingga</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #1a2a6c, #b21f1f, #1a2a6c);
            color: #333;
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            text-align: center;
            padding: 30px 0;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }
        
        header h1 {
            color: #1a2a6c;
            font-size: 2.5rem;
            margin-bottom: 10px;
        }
        
        header p {
            color: #666;
            font-size: 1.1rem;
        }
        
        .card {
            background: white;
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 30px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
        }
        
        .form-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 25px;
        }
        
        .form-group {
            display: flex;
            flex-direction: column;
        }
        
        .form-group label {
            margin-bottom: 8px;
            font-weight: 600;
            color: #1a2a6c;
        }
        
        .form-group input, .form-group select {
            padding: 12px 15px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 1rem;
            transition: all 0.3s ease;
        }
        
        .form-group input:focus, .form-group select:focus {
            outline: none;
            border-color: #1a2a6c;
            box-shadow: 0 0 0 3px rgba(26, 42, 108, 0.2);
        }
        
        .btn {
            background: #1a2a6c;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }
        
        .btn:hover {
            background: #0d1a4a;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(26, 42, 108, 0.3);
        }
        
        .btn-danger {
            background: #b21f1f;
        }
        
        .btn-danger:hover {
            background: #8b0000;
        }
        
        .btn-warning {
            background: #e67e22;
        }
        
        .btn-warning:hover {
            background: #d35400;
        }
        
        .btn-success {
            background: #27ae60;
        }
        
        .btn-success:hover {
            background: #219653;
        }
        
        .search-container {
            display: flex;
            gap: 15px;
            margin-bottom: 25px;
            align-items: center;
        }
        
        .search-container input {
            flex: 1;
            padding: 12px 15px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 1rem;
        }
        
        .table-container {
            overflow-x: auto;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            background: white;
        }
        
        th {
            background: #1a2a6c;
            color: white;
            padding: 15px;
            text-align: left;
            font-weight: 600;
        }
        
        td {
            padding: 15px;
            border-bottom: 1px solid #eee;
        }
        
        tr:hover {
            background: #f8f9fa;
        }
        
        .action-buttons {
            display: flex;
            gap: 10px;
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 20px;
            border-radius: 8px;
            color: white;
            font-weight: 600;
            z-index: 1000;
            transform: translateX(150%);
            transition: transform 0.3s ease;
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        .notification.success {
            background: #27ae60;
        }
        
        .notification.error {
            background: #e74c3c;
        }
        
        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .stat-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .stat-card h3 {
            font-size: 2rem;
            margin-bottom: 5px;
        }
        
        .stat-card p {
            opacity: 0.9;
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }
        
        .modal-content {
            background: white;
            padding: 30px;
            border-radius: 15px;
            width: 90%;
            max-width: 500px;
            position: relative;
        }
        
        .close-modal {
            position: absolute;
            top: 15px;
            right: 15px;
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: #666;
        }
        
        @media (max-width: 768px) {
            .form-container {
                grid-template-columns: 1fr;
            }
            
            .search-container {
                flex-direction: column;
            }
            
            .action-buttons {
                flex-direction: column;
            }
            
            table {
                font-size: 0.9rem;
            }
            
            th, td {
                padding: 10px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1><i class="fas fa-school"></i> SMK N 1 Purbalingga</h1>
            <p>Sistem Data Entry Siswa</p>
        </header>
        
        <div class="stats-container">
            <div class="stat-card">
                <h3 id="totalSiswa">0</h3>
                <p>Total Siswa</p>
            </div>
            <div class="stat-card">
                <h3 id="totalLaki">0</h3>
                <p>Laki-laki</p>
            </div>
            <div class="stat-card">
                <h3 id="totalPerempuan">0</h3>
                <p>Perempuan</p>
            </div>
            <div class="stat-card">
                <h3 id="totalJurusan">0</h3>
                <p>Jurusan</p>
            </div>
        </div>
        
        <div class="card">
            <h2 style="margin-bottom: 20px; color: #1a2a6c;"><i class="fas fa-user-plus"></i> Form Entry Data Siswa</h2>
            <form id="siswaForm">
                <div class="form-container">
                    <div class="form-group">
                        <label for="nis">NIS</label>
                        <input type="text" id="nis" placeholder="Masukkan NIS" required>
                    </div>
                    <div class="form-group">
                        <label for="nama">Nama Lengkap</label>
                        <input type="text" id="nama" placeholder="Masukkan nama lengkap" required>
                    </div>
                    <div class="form-group">
                        <label for="jk">Jenis Kelamin</label>
                        <select id="jk" required>
                            <option value="">Pilih jenis kelamin</option>
                            <option value="Laki-laki">Laki-laki</option>
                            <option value="Perempuan">Perempuan</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="ttl">Tempat, Tanggal Lahir</label>
                        <input type="text" id="ttl" placeholder="Contoh: Purbalingga, 15/03/2005" required>
                    </div>
                    <div class="form-group">
                        <label for="alamat">Alamat</label>
                        <input type="text" id="alamat" placeholder="Masukkan alamat lengkap" required>
                    </div>
                    <div class="form-group">
                        <label for="jurusan">Jurusan</label>
                        <select id="jurusan" required>
                            <option value="">Pilih jurusan</option>
                            <option value="Teknik Komputer dan Jaringan">Teknik Komputer dan Jaringan</option>
                            <option value="Akuntansi">Akuntansi</option>
                            <option value="Teknik Kendaraan Ringan">Teknik Kendaraan Ringan</option>
                            <option value="Multimedia">Multimedia</option>
                            <option value="Teknik Mesin">Teknik Mesin</option>
                            <option value="Administrasi Perkantoran">Administrasi Perkantoran</option>
                            <option value="Pemasaran">Pemasaran</option>
                            <option value="Perhotelan">Perhotelan</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="kelas">Kelas</label>
                        <select id="kelas" required>
                            <option value="">Pilih kelas</option>
                            <option value="X">X</option>
                            <option value="XI">XI</option>
                            <option value="XII">XII</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="thnAjaran">Tahun Ajaran</label>
                        <input type="text" id="thnAjaran" placeholder="Contoh: 2023/2024" required>
                    </div>
                    <div class="form-group">
                        <label for="wali">Nama Wali</label>
                        <input type="text" id="wali" placeholder="Masukkan nama wali" required>
                    </div>
                    <div class="form-group">
                        <label for="noTelp">No. Telepon Wali</label>
                        <input type="text" id="noTelp" placeholder="Masukkan nomor telepon" required>
                    </div>
                </div>
                <button type="submit" class="btn btn-success">
                    <i class="fas fa-save"></i> Simpan Data Siswa
                </button>
                <button type="button" id="resetBtn" class="btn btn-danger">
                    <i class="fas fa-redo"></i> Reset Form
                </button>
            </form>
        </div>
        
        <div class="card">
            <h2 style="margin-bottom: 20px; color: #1a2a6c;"><i class="fas fa-table"></i> Data Siswa SMK N 1 Purbalingga</h2>
            
            <div class="search-container">
                <input type="text" id="searchInput" placeholder="Cari berdasarkan NIS, Nama, atau Jurusan...">
                <button id="exportBtn" class="btn">
                    <i class="fas fa-file-excel"></i> Export ke Excel
                </button>
            </div>
            
            <div class="table-container">
                <table id="siswaTable">
                    <thead>
                        <tr>
                            <th>NIS</th>
                            <th>Nama Lengkap</th>
                            <th>Jenis Kelamin</th>
                            <th>Tempat, Tanggal Lahir</th>
                            <th>Alamat</th>
                            <th>Jurusan</th>
                            <th>Kelas</th>
                            <th>Tahun Ajaran</th>
                            <th>Nama Wali</th>
                            <th>No. Telepon</th>
                            <th>Aksi</th>
                        </tr>
                    </thead>
                    <tbody id="tableBody">
                        <!-- Data akan diisi oleh JavaScript -->
                    </tbody>
                </table>
            </div>
        </div>
    </div>
    
    <div id="notification" class="notification"></div>
    
    <div id="editModal" class="modal">
        <div class="modal-content">
            <button class="close-modal">&times;</button>
            <h2 style="margin-bottom: 20px; color: #1a2a6c;">Edit Data Siswa</h2>
            <form id="editForm">
                <input type="hidden" id="editIndex">
                <div class="form-group">
                    <label for="editNis">NIS</label>
                    <input type="text" id="editNis" required>
                </div>
                <div class="form-group">
                    <label for="editNama">Nama Lengkap</label>
                    <input type="text" id="editNama" required>
                </div>
                <div class="form-group">
                    <label for="editJk">Jenis Kelamin</label>
                    <select id="editJk" required>
                        <option value="Laki-laki">Laki-laki</option>
                        <option value="Perempuan">Perempuan</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="editTtl">Tempat, Tanggal Lahir</label>
                    <input type="text" id="editTtl" required>
                </div>
                <div class="form-group">
                    <label for="editAlamat">Alamat</label>
                    <input type="text" id="editAlamat" required>
                </div>
                <div class="form-group">
                    <label for="editJurusan">Jurusan</label>
                    <select id="editJurusan" required>
                        <option value="Teknik Komputer dan Jaringan">Teknik Komputer dan Jaringan</option>
                        <option value="Akuntansi">Akuntansi</option>
                        <option value="Teknik Kendaraan Ringan">Teknik Kendaraan Ringan</option>
                        <option value="Multimedia">Multimedia</option>
                        <option value="Teknik Mesin">Teknik Mesin</option>
                        <option value="Administrasi Perkantoran">Administrasi Perkantoran</option>
                        <option value="Pemasaran">Pemasaran</option>
                        <option value="Perhotelan">Perhotelan</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="editKelas">Kelas</label>
                    <select id="editKelas" required>
                        <option value="X">X</option>
                        <option value="XI">XI</option>
                        <option value="XII">XII</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="editThnAjaran">Tahun Ajaran</label>
                    <input type="text" id="editThnAjaran" required>
                </div>
                <div class="form-group">
                    <label for="editWali">Nama Wali</label>
                    <input type="text" id="editWali" required>
                </div>
                <div class="form-group">
                    <label for="editNoTelp">No. Telepon Wali</label>
                    <input type="text" id="editNoTelp" required>
                </div>
                <button type="submit" class="btn btn-warning">
                    <i class="fas fa-edit"></i> Update Data
                </button>
            </form>
        </div>
    </div>
    
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Inisialisasi data dari localStorage
            let siswaData = JSON.parse(localStorage.getItem('siswaData')) || [];
            
            // Elemen DOM
            const siswaForm = document.getElementById('siswaForm');
            const tableBody = document.getElementById('tableBody');
            const searchInput = document.getElementById('searchInput');
            const exportBtn = document.getElementById('exportBtn');
            const resetBtn = document.getElementById('resetBtn');
            const notification = document.getElementById('notification');
            const editModal = document.getElementById('editModal');
            const editForm = document.getElementById('editForm');
            const closeModal = document.querySelector('.close-modal');
            
            // Fungsi untuk menampilkan notifikasi
            function showNotification(message, type) {
                notification.textContent = message;
                notification.className = `notification ${type}`;
                notification.classList.add('show');
                
                setTimeout(() => {
                    notification.classList.remove('show');
                }, 3000);
            }
            
            // Fungsi untuk menambah data siswa
            function addSiswa(siswa) {
                siswaData.push(siswa);
                localStorage.setItem('siswaData', JSON.stringify(siswaData));
                renderTable();
                updateStats();
                showNotification('Data siswa berhasil ditambahkan!', 'success');
            }
            
            // Fungsi untuk mengupdate data siswa
            function updateSiswa(index, siswa) {
                siswaData[index] = siswa;
                localStorage.setItem('siswaData', JSON.stringify(siswaData));
                renderTable();
                updateStats();
                showNotification('Data siswa berhasil diperbarui!', 'success');
            }
            
            // Fungsi untuk menghapus data siswa
            function deleteSiswa(index) {
                if (confirm('Apakah Anda yakin ingin menghapus data siswa ini?')) {
                    siswaData.splice(index, 1);
                    localStorage.setItem('siswaData', JSON.stringify(siswaData));
                    renderTable();
                    updateStats();
                    showNotification('Data siswa berhasil dihapus!', 'success');
                }
            }
            
            // Fungsi untuk merender tabel
            function renderTable(data = siswaData) {
                tableBody.innerHTML = '';
                
                if (data.length === 0) {
                    const row = document.createElement('tr');
                    row.innerHTML = `<td colspan="11" style="text-align: center; padding: 20px;">Tidak ada data siswa</td>`;
                    tableBody.appendChild(row);
                    return;
                }
                
                data.forEach((siswa, index) => {
                    const row = document.createElement('tr');
                    row.innerHTML = `
                        <td>${siswa.nis}</td>
                        <td>${siswa.nama}</td>
                        <td>${siswa.jk}</td>
                        <td>${siswa.ttl}</td>
                        <td>${siswa.alamat}</td>
                        <td>${siswa.jurusan}</td>
                        <td>${siswa.kelas}</td>
                        <td>${siswa.thnAjaran}</td>
                        <td>${siswa.wali}</td>
                        <td>${siswa.noTelp}</td>
                        <td>
                            <div class="action-buttons">
                                <button class="btn btn-warning" onclick="openEditModal(${index})">
                                    <i class="fas fa-edit"></i> Edit
                                </button>
                                <button class="btn btn-danger" onclick="deleteSiswa(${index})">
                                    <i class="fas fa-trash"></i> Hapus
                                </button>
                            </div>
                        </td>
                    `;
                    tableBody.appendChild(row);
                });
            }
            
            // Fungsi untuk update statistik
            function updateStats() {
                const totalSiswa = siswaData.length;
                const totalLaki = siswaData.filter(s => s.jk === 'Laki-laki').length;
                const totalPerempuan = siswaData.filter(s => s.jk === 'Perempuan').length;
                const jurusanSet = new Set(siswaData.map(s => s.jurusan));
                const totalJurusan = jurusanSet.size;
                
                document.getElementById('totalSiswa').textContent = totalSiswa;
                document.getElementById('totalLaki').textContent = totalLaki;
                document.getElementById('totalPerempuan').textContent = totalPerempuan;
                document.getElementById('totalJurusan').textContent = totalJurusan;
            }
            
            // Event listener untuk form submit
            siswaForm.addEventListener('submit', function(e) {
                e.preventDefault();
                
                const siswa = {
                    nis: document.getElementById('nis').value,
                    nama: document.getElementById('nama').value,
                    jk: document.getElementById('jk').value,
                    ttl: document.getElementById('ttl').value,
                    alamat: document.getElementById('alamat').value,
                    jurusan: document.getElementById('jurusan').value,
                    kelas: document.getElementById('kelas').value,
                    thnAjaran: document.getElementById('thnAjaran').value,
                    wali: document.getElementById('wali').value,
                    noTelp: document.getElementById('noTelp').value
                };
                
                addSiswa(siswa);
                siswaForm.reset();
            });
            
            // Event listener untuk reset form
            resetBtn.addEventListener('click', function() {
                siswaForm.reset();
            });
            
            // Event listener untuk pencarian
            searchInput.addEventListener('input', function() {
                const searchTerm = searchInput.value.toLowerCase();
                const filteredData = siswaData.filter(siswa => 
                    siswa.nis.toLowerCase().includes(searchTerm) ||
                    siswa.nama.toLowerCase().includes(searchTerm) ||
                    siswa.jurusan.toLowerCase().includes(searchTerm)
                );
                renderTable(filteredData);
            });
            
            // Event listener untuk export ke Excel
            exportBtn.addEventListener('click', function() {
                if (siswaData.length === 0) {
                    showNotification('Tidak ada data untuk diekspor!', 'error');
                    return;
                }
                
                let csv = 'NIS,Nama Lengkap,Jenis Kelamin,Tempat Tanggal Lahir,Alamat,Jurusan,Kelas,Tahun Ajaran,Nama Wali,No. Telepon Wali\n';
                
                siswaData.forEach(siswa => {
                    csv += `${siswa.nis},${siswa.nama},${siswa.jk},"${siswa.ttl}","${siswa.alamat}",${siswa.jurusan},${siswa.kelas},${siswa.thnAjaran},${siswa.wali},${siswa.noTelp}\n`;
                });
                
                const blob = new Blob([csv], { type: 'text/csv' });
                const url = window.URL.createObjectURL(blob);
                const a = document.createElement('a');
                a.setAttribute('hidden', '');
                a.setAttribute('href', url);
                a.setAttribute('download', 'Data_Siswa_SMK_N1_Purbalingga.csv');
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);
                
                showNotification('Data berhasil diekspor ke CSV!', 'success');
            });
            
            // Fungsi untuk membuka modal edit
            window.openEditModal = function(index) {
                const siswa = siswaData[index];
                
                document.getElementById('editIndex').value = index;
                document.getElementById('editNis').value = siswa.nis;
                document.getElementById('editNama').value = siswa.nama;
                document.getElementById('editJk').value = siswa.jk;
                document.getElementById('editTtl').value = siswa.ttl;
                document.getElementById('editAlamat').value = siswa.alamat;
                document.getElementById('editJurusan').value = siswa.jurusan;
                document.getElementById('editKelas').value = siswa.kelas;
                document.getElementById('editThnAjaran').value = siswa.thnAjaran;
                document.getElementById('editWali').value = siswa.wali;
                document.getElementById('editNoTelp').value = siswa.noTelp;
                
                editModal.style.display = 'flex';
            };
            
            // Event listener untuk close modal
            closeModal.addEventListener('click', function() {
                editModal.style.display = 'none';
            });
            
            // Event listener untuk form edit
            editForm.addEventListener('submit', function(e) {
                e.preventDefault();
                
                const index = document.getElementById('editIndex').value;
                const siswa = {
                    nis: document.getElementById('editNis').value,
                    nama: document.getElementById('editNama').value,
                    jk: document.getElementById('editJk').value,
                    ttl: document.getElementById('editTtl').value,
                    alamat: document.getElementById('editAlamat').value,
                    jurusan: document.getElementById('editJurusan').value,
                    kelas: document.getElementById('editKelas').value,
                    thnAjaran: document.getElementById('editThnAjaran').value,
                    wali: document.getElementById('editWali').value,
                    noTelp: document.getElementById('editNoTelp').value
                };
                
                updateSiswa(index, siswa);
                editModal.style.display = 'none';
            });
            
            // Inisialisasi
            renderTable();
            updateStats();
        });
    </script>
</body>
</html>
