import sqlite3
from flask import Flask, render_template_string, request, redirect, url_for

app = Flask(__name__)
DB_NAME = "database_guru.db"

# =========================================================================
# 1. PEMBUATAN DATABASE & STRUKTUR TABEL
# =========================================================================
def init_db():
    conn = sqlite3.connect(DB_NAME)
    cursor = conn.cursor()
    cursor.execute("""
        CREATE TABLE IF NOT EXISTS penilaian_guru (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            nama_guru TEXT NOT NULL,
            nilai_pedagogik REAL NOT NULL,
            nilai_profesional REAL NOT NULL,
            nilai_sosial REAL NOT NULL,
            skor_akhir REAL NOT NULL,
            predikat TEXT NOT NULL,
            waktu_input DATETIME DEFAULT CURRENT_TIMESTAMP
        )
    """)
    conn.commit()
    conn.close()

init_db()

# =========================================================================
# 2. DESAIN TAMPILAN APLIKASI (HTML + CSS RESPONSIF)
# =========================================================================
HTML_TEMPLATE = """
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistem Penilaian Guru + Database</title>
    <style>
        body { font-family: 'Segoe UI', Arial, sans-serif; background-color: #f0f2f5; margin: 0; padding: 15px; color: #333; }
        .container { max-width: 650px; background: white; padding: 20px; border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.08); margin: 10px auto; }
        .header-identitas { text-align: center; background-color: #1e3d59; color: white; padding: 10px; border-radius: 8px; margin-bottom: 20px; }
        .header-identitas h4 { margin: 5px 0; }
        h2, h3 { text-align: center; color: #1e3d59; }
        label { font-weight: 600; display: block; margin-top: 15px; color: #434e52; }
        input[type="text"], input[type="number"] { width: 100%; padding: 12px; margin-top: 6px; border: 1px solid #ccc; border-radius: 6px; box-sizing: border-box; font-size: 16px; }
        
        .btn-submit { width: 100%; background-color: #17b978; color: white; border: none; padding: 14px; margin-top: 20px; border-radius: 6px; font-size: 16px; font-weight: bold; cursor: pointer; }
        .btn-submit:hover { background-color: #119960; }
        
        /* Tombol Menu Reset */
        .btn-reset { background-color: #e74c3c; color: white; border: none; padding: 10px 15px; border-radius: 6px; font-size: 14px; font-weight: bold; cursor: pointer; float: right; margin-bottom: 10px; }
        .btn-reset:hover { background-color: #c0392b; }
        
        .section-title-container { display: flex; justify-content: space-between; align-items: center; margin-top: 40px; border-bottom: 2px solid #1e3d59; padding-bottom: 5px; }
        .section-title-container h3 { margin: 0; }

        /* Gaya Tabel Data */
        .table-responsive { width: 100%; overflow-x: auto; margin-top: 15px; }
        table { width: 100%; border-collapse: collapse; min-width: 550px; }
        th, td { padding: 12px 10px; text-align: left; border-bottom: 1px solid #ddd; font-size: 14px; }
        th { background-color: #1e3d59; color: white; }
        tr:nth-child(even) { background-color: #f9f9f9; }
        .badge { background-color: #1e3d59; color: white; padding: 3px 6px; border-radius: 4px; font-weight: bold; font-size: 12px; }
        .badge-predikat { background-color: #17b978; color: white; padding: 3px 6px; border-radius: 4px; font-size: 12px; }
    </style>
</head>
<body>

<div class="container">
    <!-- Identitas Tugas -->
    <div class="header-identitas">
        <h4>Nama: [RIZQY NAUFALINO]</h4>
        <h4>Kelas: [XI-10]</h4>
        <small>Database: SQLite (database_guru.db)</small>
    </div>

    <h2>Form Input Penilaian</h2>
    <form method="POST" action="/tambah">
        <label>Nama Guru:</label>
        <input type="text" name="nama_guru" placeholder="Masukkan nama lengkap guru" required>

        <label>Kompetensi Pedagogik (0-100):</label>
        <input type="number" name="pedagogik" min="0" max="100" required>

        <label>Kompetensi Profesional (0-100):</label>
        <input type="number" name="profesional" min="0" max="100" required>

        <label>Kompetensi Sosial (0-100):</label>
        <input type="number" name="sosial" min="0" max="100" required>

        <button type="submit" class="btn-submit">Hitung & Simpan ke Database</button>
    </form>

    <!-- Bagian Menu Riwayat & Tombol Reset -->
    <div class="section-title-container">
        <h3>Riwayat Penilaian (Isi Database)</h3>
        {% if data_guru %}
        <form method="POST" action="/reset" onsubmit="return confirm('Apakah Anda yakin ingin menghapus semua data di database?');">
            <button type="submit" class="btn-reset">🗑️ Reset Data</button>
        </form>
        {% endif %}
    </div>
    
    <div class="table-responsive">
        <table>
            <thead>
                <tr>
                    <th>Nama Guru</th>
                    <th>Pedagogik</th>
                    <th>Profesional</th>
                    <th>Sosial</th>
                    <th>Rata-Rata</th>
                    <th>Predikat</th>
                </tr>
            </thead>
            <tbody>
                {% for row in data_guru %}
                <tr>
                    <td><strong>{{ row[1] }}</strong></td>
                    <td>{{ row[2] }}</td>
                    <td>{{ row[3] }}</td>
                    <td>{{ row[4] }}</td>
                    <td><span class="badge">{{ row[5] }}</span></td>
                    <td><span class="badge-predikat">{{ row[6] }}</span></td>
                </tr>
                {% else %}
                <tr>
                    <td colspan="6" style="text-align: center; color: #888; padding: 20px;">Belum ada data di database.</td>
                </tr>
                {% endfor %}
            </tbody>
        </table>
    </div>
</div>

</body>
</html>
"""

# =========================================================================
# 3. LOGIKA BACKEND & PROSES SQL
# =========================================================================
@app.route('/')
def index():
    conn = sqlite3.connect(DB_NAME)
    cursor = conn.cursor()
    cursor.execute("SELECT * FROM penilaian_guru ORDER BY id DESC")
    data_guru = cursor.fetchall()
    conn.close()
    return render_template_string(HTML_TEMPLATE, data_guru=data_guru)

@app.route('/tambah', methods=['POST'])
def tambah_data():
    if request.method == 'POST':
        nama = request.form.get('nama_guru')
        n1 = float(request.form.get('pedagogik', 0))
        n2 = float(request.form.get('profesional', 0))
        n3 = float(request.form.get('sosial', 0))
        
        skor_akhir = round((n1 + n2 + n3) / 3, 2)
        
        if skor_akhir >= 85:
            predikat = "Sangat Baik (A)"
        elif skor_akhir >= 70:
            predikat = "Baik (B)"
        elif skor_akhir >= 55:
            predikat = "Cukup (C)"
        else:
            predikat = "Kurang (D)"
            
        conn = sqlite3.connect(DB_NAME)
        cursor = conn.cursor()
        cursor.execute("""
            INSERT INTO penilaian_guru (nama_guru, nilai_pedagogik, nilai_profesional, nilai_sosial, skor_akhir, predikat)
            VALUES (?, ?, ?, ?, ?, ?)
        """, (nama, n1, n2, n3, skor_akhir, predikat))
        conn.commit()
        conn.close()
        
    return redirect(url_for('index'))

# =========================================================================
# ROUTE BARU: PROSES PENGHAPUSAN/RESET DATA (QUERY SQL DELETE)
# =========================================================================
@app.route('/reset', methods=['POST'])
def reset_data():
    conn = sqlite3.connect(DB_NAME)
    cursor = conn.cursor()
    # Menghapus seluruh baris data di dalam tabel penilaian_guru
    cursor.execute("DELETE FROM penilaian_guru")
    # Mengembalikan hitungan auto-increment ID ke angka 1 kembali
    cursor.execute("DELETE FROM sqlite_sequence WHERE name='penilaian_guru'")
    conn.commit()
    conn.close()
    return redirect(url_for('index'))

if __name__ == '__main__':
    app.run(debug=True, host='127.0.0.1', port=5000)
