ketika masih awal-awal menginstall matlab. semua fitur berjalan lancar

tetapi ketika bertambahnya waktu, beberap error dan bug kadang terjadi. salahsatunya adalah ketika kita plotting grafik yang terlihat hanya gambar kosong. saya sudah 2x mengalami hal ini dan waktu itu saya ganti versi ke matlab yang lebih baru. namum hasilnya sama, artinya permasalahnnya bukan di versi matlabnya, melainkan di settingannya.
# Error yang keluar di matlab
```
MATLAB has experienced a low-level graphics error, and may not have drawn correctly.
Read about what you can do to prevent this issue at Resolving Low-Level Graphics Issues then restart MATLAB.
To share details of this issue with MathWorks technical support,
please include this file with your service request.
```
# cek
```
opengl info
```
hasilnya
```
                         Version: ''
                           Vendor: ''
                         Renderer: 'None'
            RendererDriverVersion: ''
        RendererDriverReleaseDate: ''
                   MaxTextureSize: 0
                           Visual: ''
                         Software: 1
             HardwareSupportLevel: 'none'
        SupportsGraphicsSmoothing: 0
    SupportsDepthPeelTransparency: 0
       SupportsAlignVertexCenters: 0
                       Extensions: {}
               MaxFrameBufferSize: 0

```
# solusi pertama
cara run matlabnya
```
matlab -softwareopengl
```
jika kita cek `opengl info` lagi maka
```
>> opengl info
                          Version: '2.1 Mesa 17.1.3'
                           Vendor: 'Brian Paul'
                         Renderer: 'Mesa X11'
                   MaxTextureSize: 16384
                           Visual: 'Visual 0x8d, (RGBA 32 bits (8 8 8 8), Z depth 16 bits, Hardware acceleration, Double buffer, Antialias 0 samples)'
                         Software: 'true'
             HardwareSupportLevel: 'none'
        SupportsGraphicsSmoothing: 0
    SupportsDepthPeelTransparency: 1
       SupportsAlignVertexCenters: 0
                       Extensions: {152×1 cell}
               MaxFrameBufferSize: 16384
```

jika kita membuat plot maka gambarnya bisa terlihat, tidak putih polos seperti sebelumnya.

# solusi kedua(rekomended)
setting matlab, jalankan seperti biasa tanpa ada tambahan `-softwareopengl`
kemudian run di command window
```
opengl('save','software')
```