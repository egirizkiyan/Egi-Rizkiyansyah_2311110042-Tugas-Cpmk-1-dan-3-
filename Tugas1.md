# <h1 align="center">Laporan Algoritma dan Struktur data Modul Tipe Data (1)</h1>
<p align="center">Egi Rizkiyansyah</p>
<p align="Center">2311110042</P>

## Struktur data dan algoritma tipe data dan variable
## Penjelasan
Jika kita perlu menggunakan pendekatan lain seperti mengubah struktur data atau menggunakan fungsi rekursif, kita masih bisa tetap pada prinsip tidak menggunakan for di dalam for. Namun, penggunaan rekursi untuk masalah ini tidak begitu umum dan bisa menjadi lebih kompleks. Saya akan menunjukkan contoh pendekatan dengan struktur data dan rekursi yang dimodifikasi.

Pendekatan dengan Rekursi
Kita dapat menggunakan rekursi untuk menghitung jumlah kemunculan elemen dan kemudian mencari elemen dengan duplikasi maksimal.
### 1.
```C++
#include <iostream>
#include <unordered_map>
#include <vector>

void countOccurrences(const std::vector<int>& arr, std::unordered_map<int, int>& countMap, int index) {
    // Basis rekursi
    if (index == arr.size()) {
        return;
    }
    
    // Perbarui jumlah kemunculan elemen saat ini
    countMap[arr[index]]++;
    
    // Rekursi untuk elemen berikutnya
    countOccurrences(arr, countMap, index + 1);
}

std::pair<int, int> findMaxDuplicate(const std::unordered_map<int, int>& countMap) {
    int maxElement = -1;
    int maxCount = 0;

    // Iterasi melalui map untuk menemukan elemen dengan duplikasi maksimal
    for (const auto& pair : countMap) {
        if (pair.second > maxCount) {
            maxCount = pair.second;
            maxElement = pair.first;
        }
    }
    
    return {maxElement, maxCount};
}

int main() {
    std::vector<int> array = {3, 5, 3, 2, 6, 3, 5, 5, 5, 2};
    std::unordered_map<int, int> countMap;
    
    // Hitung jumlah kemunculan setiap elemen dengan rekursi
    countOccurrences(array, countMap, 0);
    
    // Temukan elemen dengan duplikasi maksimal
    auto result = findMaxDuplicate(countMap);
    std::cout << "Elemen dengan duplikasi maksimal adalah " << result.first 
              << " dengan jumlah " << result.second << " kali." << std::endl;

    return 0;
}
```
Penjelasan:

  - Fungsi Rekursif countOccurrences: Menghitung jumlah kemunculan setiap elemen dalam array. Fungsi ini memodifikasi countMap secara rekursif.
  - Fungsi findMaxDuplicate: Menemukan elemen dengan jumlah kemunculan terbanyak dengan iterasi melalui countMap.
  - Fungsi main: Menginisialisasi array dan countMap, lalu memanggil fungsi rekursif untuk menghitung kemunculan dan mencari elemen dengan duplikasi maksimal.
Dengan menggunakan pendekatan ini, kita masih mematuhi aturan untuk tidak menggunakan for di dalam for, tetapi kita memecah masalah menjadi dua bagian: menghitung kemunculan secara rekursif dan kemudian mencari elemen dengan duplikasi maksimal.





