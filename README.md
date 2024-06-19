import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from matplotlib_venn import venn2

# Dataframe sample
data = {
    'Nama': ['Asep', 'Budi', 'Citra', 'Dian', 'Eko'],
    'Gaji': [10000000, 8000000, 12000000, 9500000, 7000000],
    'Jam Kerja Per Minggu': [40, 35, 45, 38, 30],
    'Departemen': ['IT', 'HR', 'Finance', 'Marketing', 'IT']
}

df = pd.DataFrame(data)

# Scatterplot antara Gaji dan Jam Kerja Per Minggu
plt.figure(figsize=(8, 6))
sns.scatterplot(data=df, x='Jam Kerja Per Minggu', y='Gaji', hue='Departemen', s=100)
plt.title('Scatterplot Gaji vs Jam Kerja Per Minggu')
plt.xlabel('Jam Kerja Per Minggu')
plt.ylabel('Gaji (Rupiah)')
plt.legend(title='Departemen')
plt.grid(True)
plt.show()

# Grafik garis yang menunjukkan Gaji untuk setiap karyawan
plt.figure(figsize=(8, 6))
plt.plot(df['Nama'], df['Gaji'], marker='o')
plt.title('Grafik Garis Gaji Karyawan')
plt.xlabel('Nama')
plt.ylabel('Gaji (Rupiah)')
plt.grid(True)
plt.show()

# Grafik batang untuk rata-rata Gaji per Departemen
plt.figure(figsize=(8, 6))
avg_salary = df.groupby('Departemen')['Gaji'].mean().reset_index()
sns.barplot(data=avg_salary, x='Departemen', y='Gaji')
plt.title('Rata-rata Gaji per Departemen')
plt.xlabel('Departemen')
plt.ylabel('Rata-rata Gaji (Rupiah)')
plt.grid(True)
plt.show()

# Grafik titik untuk Gaji karyawan
plt.figure(figsize=(8, 6))
plt.plot(df['Nama'], df['Gaji'], 'o')
plt.title('Grafik Titik Gaji Karyawan')
plt.xlabel('Nama')
plt.ylabel('Gaji (Rupiah)')
plt.grid(True)
plt.show()

# Diagram Venn untuk perbandingan karyawan antara dua departemen (contoh IT dan HR)
plt.figure(figsize=(8, 6))
venn2(subsets=(
    len(df[df['Departemen'] == 'IT']),
    len(df[df['Departemen'] == 'HR']),
    len(df[(df['Departemen'] == 'IT') & (df['Departemen'] == 'HR')])),
    set_labels=('IT', 'HR'))
plt.title('Diagram Venn Karyawan IT dan HR')
plt.show()
