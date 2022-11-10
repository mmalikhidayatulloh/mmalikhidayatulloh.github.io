# Introduction
Berikut ini beberapa code matlab yang biasa saya gunakan.
# Rule
1. Riwayat command
```
tekan arah atas di keyboard
```
3. Command panjang
```
pake titik tiga (...) terus enter
```
5. Semicolon dan koma
```
; kode di run tapi tidak ditampilkan melainkan disembunyikan
, beberapa command dalam 1 baris
```
7. Comment
```
% komentar tidak di run
```
9. clear window
```
clc
```
11. ans
```
hasil dari running
```
13. variable
```
pake alfabet, jika variablenya sama dengan nilai yang berbeda maka variable tsb diupdate
```
14. desimal
```
0.4 (pake titik)
```
# Aritmatika
1. Jumlah
```
+
```
3. Kurang
```
-
```
5. kali
```
*
```
7. bagi
```
/
```
9. kurung
```
()
```

# Trigonometri
1. sin
```
sin(pi/2)
```
3. sind
```
sin(30)
```
5. cos
```
cos(pi)
```
7. cosd
```
cosd(60)
```
9. tan
10. tand
11. arc sin
12. arc cos
13. arc tan
14. sec
15. cosec
16. cotan
17. arc sec
18. arc cosec
19. arc cotan
# Matematika lain
1. exp
```
exp(3)
```
3. factorial
```
factorial(6)
```
5. pembulatan kebawah
```
fix(2.6)
```
7. pembulatan keatas
```
floor(2.3)
```
8. ln
```
log(3)
```
9. log
```
log10(5)
```
10. pi
```
pi
```
11. pembulatan tertentu
```
round(2.7865,2)
```
12. akar
```
sqrt(100)
```
# format
```
format format_type
```
# Disp
```
disp('Text string') or disp(Variable name)
```
contoh
```
ro=2.7e3 
disp('Aluminum Density, kg/m^3'),disp(ro)
```
# fprintf
```
fprintf('Text string %6.3f additional text\n', variable name)
```
# vektor
```
vector_name=a:q:b
```
a = batas bawah
b = batas atas
q = stepsize
# linspace
```
vector_name=linspace(a,b,n)
```
n = jumlah antara a dan b
# matrix
```
[a,b,c;d,e,f;g,h,i]
```
## nol
```
zeros(i,j)
```
## diagonal 1
```
eye(3)
```
## invers
```
inv(M)
```
## satu
```
ones(m,n)
```
## random
```
rand(m,n)
```
```
randn(m,n)
```
```
randi(m,n)
```
## operasi
```
cross(a,b)
```
```
det(a)
```
```
x=1:2:5;diag(x)
```
```
dot(a,b)
```
```
length(x)
```
```
max(a),min(a)
```
```
mean(x)
```
```
median(x)
```
```
num2str(a)
```
```
randi(imax,m,n)
```
```
reshape(a,m,n)
```
```
size(a)
```
```
std(a)
```
# perbandingan
```
>
<
<=
>=
==
~=
```
```
s&g
s|h
~A
```
# if
```
if
  ...
end
```
```
if
  ...
else
  ...
end
```
```
if
  ...
elseif
  ...
else
  ...
end
```
# loop
```
for k=initial:step:final
  ...
end
```
```
while condition
  ...
end
```
