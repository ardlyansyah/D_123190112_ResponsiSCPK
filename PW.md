### Listing Program :
```
format long g; %menampilkan data dengan tipedata long
a = xlsread('testing.xlsx','C2:E51'); %mengimpor data dari testing.xlsx, dan mengambil dari kolom C2 sampai H51
b = xlsread('testing.xlsx','H2:H51'); %mengimpor data dari testing.xlsx, dan mengambil dari kolom H2 sampai H51
data = [a b]; %menggabungkan 2 data yaitu data a dan data b.
disp(data); %menampilkan data yang sudah digabung
k = [0,0,1,0]; %membuat nilai atribut
w = [3,5,4,1]; %memasukkan nilai bobot
[m n]=size (data); %inisialisasi ukuran data
w=w./sum(w);%membagi bobot per kriteria dengan jumlah total seluruh bobot
for j=1:n, %normalisasi bobot dan sifatnya
    if k(j)==0, w(j)=-1*w(j);
    end;
end;
for i=1:m, %melakukan perhitungan vektor (S)
    S(i)=prod(data(i,:).^w);
end;
V = S/sum(S); %proses perangkingan

for q=1:m; %proses agar data yang tampil merupakan indeks dari data
    if V(q)== max(V)
        disp("Real Estate Terbaik adalah Real Estate ke = " + q);
        disp("Dengan Nilai = "+ max(V));
    end;
end;
```

### hasil output :
![Screenshot (377)](https://user-images.githubusercontent.com/82427614/123426457-a2c95100-d5ed-11eb-8888-03b5931dcd5e.png)
![Screenshot (378)](https://user-images.githubusercontent.com/82427614/123426461-a4931480-d5ed-11eb-9280-58c0b507553e.png)
