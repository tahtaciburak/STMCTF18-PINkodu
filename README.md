# STMCTF18-PINkodu
STM Capture The Flag yarışmasındaki PINkodu sorusunun çözümü

Soruda bizden istenen, verilen binary dosyada bize sorulan pin kodunu bulmaktı. PIN kodunu STMCTF{} stringinin içine yazarak flag bulunabilirdi. Öncelikle kör olarak programa verilen girdilere hangi çıktılar üretildiği gözlemledim. 
Birkaç değeri arka arkaya denedikten sonra sürekli "Tekrar Deneyin :(" mesajı alıyordum. Farklı tipte komutlar girsek bile sonuç aynıydı.

![alt_text](https://github.com/tahtaciburak/STMCTF18-PINkodu/blob/master/Screenshot%20from%202018-11-01%2023-00-29.png)

Bu bir reverse engineering sorusu olduğundan programı disassemble edip içeriğinde neler döndüğü araştırmaya başladım. `objdump -S PINkodu` komutunu vererek programın assembly kodlarına ulaştım. Main fonksiyonunun içeriğinin aşağıdaki gibi olduğunu gördüm.

![alt_text](https://github.com/tahtaciburak/STMCTF18-PINkodu/blob/master/Screenshot%20from%202018-11-01%2023-14-36.png)


İlk dikkatimi çeken şey CMP instruction'larıydı çünkü input olarak girilen bir değeri başka bir değerle karşılaştırıyor ve bu karşılaştırma işlemi sonucunda bir JMP işlemi yapıyordu. Dolayısıyla CMP instruction'ına verilen ilk hexadecimal değerin decimal tabandaki değeri muhtemelen PIN kodunun kendisidir diyerek kodu decimal tabana çevirdim.

![alt_text](https://github.com/tahtaciburak/STMCTF18-PINkodu/blob/master/Screenshot%20from%202018-11-01%2023-15-52.png)

![alt_text](https://github.com/tahtaciburak/STMCTF18-PINkodu/blob/master/Screenshot%20from%202018-11-01%2023-16-36.png)

Flagi `STMCTF{52472599}`olarak buluyoruz.

