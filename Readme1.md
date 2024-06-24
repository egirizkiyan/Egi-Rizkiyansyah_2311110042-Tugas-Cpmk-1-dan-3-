# <h1 align="center">Laporan Algoritma dan Struktur data Modul Tipe Data</h1>
<p align="center">Egi Rizkiyansyah</p>
<p align="Center">2311110042</P>

## Piority Queueu
## Penjelasan
  Priority Queue adalah tipe data abstrak di mana setiap elemen memiliki prioritas tertentu. Elemen dengan prioritas lebih tinggi akan diproses lebih dulu dibandingkan elemen dengan prioritas lebih rendah. Prioritas ini biasanya ditentukan oleh nilai yang lebih kecil atau lebih besar, tergantung pada implementasinya.

### 1. [Priority queueu]

```C++
#include <iostream>
#include <queue>
#include <vector>

using namespace std;

int main() {
    priority_queue<int, vector<int>, greater<int>> pq;

    pq.push(3);
    pq.push(1);
    pq.push(2);

    while (!pq.empty()) {
        cout << pq.top() << " ";
        pq.pop();
    }

    return 0;
}
```
Penjelasan Alur Program:
  - Mengimpor header yang diperlukan: <iostream>, <queue>, dan <vector>.
  - Menggunakan priority_queue dengan greater<int> untuk membuat priority queue dengan prioritas berdasarkan nilai yang lebih kecil.
  - Menambahkan elemen ke priority queue dengan pq.push().
  - Menggunakan loop while untuk memproses elemen dari priority queue menggunakan pq.top() untuk mendapatkan elemen dengan prioritas tertinggi dan pq.pop() untuk menghapusnya dari queue

## Hash Table
## Penjelasan
  Hash Table adalah struktur data yang memetakan kunci ke nilai menggunakan fungsi hash. Ini memungkinkan pencarian, penyisipan, dan penghapusan elemen dilakukan dengan cepat.
### 2. [Hash Table]

```C++
#include <iostream>
#include <unordered_map>

using namespace std;

int main() {
    unordered_map<string, string> hash_table;

    hash_table["name"] = "Alice";
    hash_table["age"] = "30";
    hash_table["city"] = "Wonderland";

    cout << "Name: " << hash_table["name"] << endl;
    cout << "Age: " << hash_table["age"] << endl;
    cout << "City: " << hash_table["city"] << endl;

    hash_table.erase("age");

    cout << "Updated Hash Table:" << endl;
    for (const auto& pair : hash_table) {
        cout << pair.first << ": " << pair.second << endl;
    }

    return 0;
}
```
Penjelasan Alur Program:
  - Mengimpor header yang diperlukan: <iostream> dan <unordered_map>.
  - Menginisialisasi hash table menggunakan unordered_map.
  - Menambahkan elemen ke dalam hash table.
  - Mengakses dan mencetak elemen dari hash table menggunakan kunci.
  - Menghapus elemen dari hash table menggunakan erase.
  - Menampilkan isi hash table setelah penghapusan elemen.

## Rekursif
## Penjelasan
  Rekursif adalah teknik pemrograman di mana sebuah fungsi memanggil dirinya sendiri. Ini biasanya digunakan untuk memecahkan masalah yang dapat dipecah menjadi sub-masalah yang lebih kecil dan identik.
### 3. [ Rekursif ]

```C++
#include <iostream>

using namespace std;

int factorial(int n) {
    if (n == 0)
        return 1;
    else
        return n * factorial(n - 1);
}

int main() {
    int result = factorial(5);
    cout << "Factorial of 5 is " << result << endl;
    return 0;
}
```
Penjelasan Alur Program:
  - Mengimpor header <iostream>.
  - Mendefinisikan fungsi factorial yang menerima parameter n.
  - Jika n sama dengan 0, fungsi mengembalikan 1 (basis kasus).
  - Jika tidak, fungsi mengembalikan n dikalikan dengan hasil pemanggilan rekursif factorial(n - 1).
  - Menghitung faktorial dari 5 dan mencetak hasilnya.

## Graph dan Tree
## Penjelasan
  Graph adalah struktur data yang terdiri dari simpul (nodes) dan tepi (edges) yang menghubungkan simpul-simpul tersebut. Tree adalah jenis khusus dari graph di mana tidak ada siklus dan ada satu simpul akar (root).
### 4. [ Graph ]

```C++
#include <iostream>
#include <list>
#include <unordered_map>

using namespace std;

class Graph {
public:
    unordered_map<int, list<int>> adj;

    void addEdge(int u, int v) {
        adj[u].push_back(v);
    }

    void printGraph() {
        for (auto& pair : adj) {
            cout << pair.first << " -> ";
            for (int v : pair.second) {
                cout << v << " ";
            }
            cout << endl;
        }
    }
};

int main() {
    Graph g;
    g.addEdge(0, 1);
    g.addEdge(0, 2);
    g.addEdge(1, 2);
    g.addEdge(2, 0);
    g.addEdge(2, 3);
    g.addEdge(3, 3);

    g.printGraph();

    return 0;
}
```
Penjelasan Alur Program:
  - Mengimpor header yang diperlukan: <iostream>, <list>, dan <unordered_map>.
  - Mendefinisikan kelas Graph dengan member adj untuk menyimpan adjacency list.
  - Menambahkan metode addEdge untuk menambahkan tepi ke graph.
  - Menambahkan metode printGraph untuk mencetak adjacency list dari graph.
  - Membuat instance Graph dan menambahkan beberapa tepi.
  - Menampilkan adjacency list dari graph.

### 4. [ Tree ]

```C++
#include <iostream>

using namespace std;

class TreeNode {
public:
    int value;
    TreeNode* left;
    TreeNode* right;

    TreeNode(int val) {
        value = val;
        left = nullptr;
        right = nullptr;
    }
};

void inorderTraversal(TreeNode* root) {
    if (root) {
        inorderTraversal(root->left);
        cout << root->value << " ";
        inorderTraversal(root->right);
    }
}

int main() {
    TreeNode* root = new TreeNode(1);
    root->left = new TreeNode(2);
    root->right = new TreeNode(3);
    root->left->left = new TreeNode(4);
    root->left->right = new TreeNode(5);

    cout << "Inorder traversal: ";
    inorderTraversal(root);
    cout << endl;

    return 0;
}
```
Penjelasan Alur Program:
  - Mengimpor header <iostream>.
  - Mendefinisikan kelas TreeNode dengan konstruktor yang menginisialisasi value, left, dan right.
  - Mendefinisikan fungsi inorderTraversal untuk melakukan traversal inorder pada tree.
  - Membuat instance TreeNode untuk membangun tree.
  - Melakukan traversal inorder dan mencetak nilai dari node dalam urutan inorder.
## Referensi
[1] Data Structures and Algorithms in C++" oleh Adam Drozdek
[2] Algorithms in C++, Parts 1-4: Fundamentals, Data Structure, Sorting, Searching" oleh Robert Sedgewick
[3] C++ Data Structures and Algorithms" oleh Wisnu Anggoro
[4] "Programming: Principles and Practice Using C++" oleh Bjarne Stroustrup