3-topshiriq (mantiqiy). Grafni o‘qing
Berilgan git log --oneline --graph natijasi pastdan tepaga qarab o‘qiladi: eng birinchi yaratilgan
commit pastda ( 1f3 ), eng oxirgi merge commit esa eng tepada ( 9a1 ) joylashgan.
* 9a1 (main) Merge branch dizayn
|\
| * 7c4 (dizayn) Rangli sarlavha
| * 5b2 Rasm qo'shildi
* | 4e8 Imlo tuzatildi
|/
* 2d0 README yaratildi
* 1f3 Birinchi commit
Savol To‘g‘ri javob va mantiqiy tushuntirish
a) Nechta shox bor edi? Ularning
nomlari:
2 ta shox bor edi: main (asosiy shox) va dizayn (yangi ajralib
chiqqan shox). Grafda ikkita parallel chiziq (chapda main , o‘ngda
dizayn ) ko‘rinib turibdi.
b) dizayn shoxi qaysi
commit’dan keyin ajralgan? Uning
commit’lari:
2d0 (README yaratildi) commit’idan keyin ajralgan (grafdagi |/ belgisi
aynan 2d0 ustidan ikkiga bo‘lingan).
Uning commit’lari: 5b2 (Rasm qo'shildi) va 7c4 (Rangli sarlavha).
c) Merge commit’ining hash’i va u
birlashtirgan commit’lar:
Hash’i: 9a1 .
Birlashtirgan commit’lari: main shoxidagi oxirgi 4e8 commit’i bilan
dizayn shoxidagi oxirgi 7c4 commit’ini birlashtirdi ( |\ chizig‘i shu
ikki uchni tutashtirgan).
d) 4e8 commit’i dizayn
shoxida bormi? Nega?
Yo‘q, mavjud emas. Chunki 4e8 (Imlo tuzatildi) o‘zgarishi shoxlar 2d0
nuqtasida ikkiga ajralganidan keyin faqat main shoxining o‘zida qilingan;
dizayn shoxi esa o‘z yo‘lida davom etgan.
e) Endi main ’da jami nechta
commit bor (merge’ni ham
sanang)?
Jami 6 ta commit bor: umumiy tarixdagi 1f3 , 2d0 ; main ’dagi 4e8 ;
dizayn ’dan merge orqali kirib kelgan 5b2 , 7c4 hamda merge
commit’ning o‘zi — 9a1 .
4-topshiriq (mantiqiy). Conflict’ni yeching
Berilgan orzular.md faylidagi conflict belgilarini tahlil qilamiz: <<<<<<< HEAD dan ======= gacha
bo‘lgan qism hozirgi turgan main shoxiga, ======= dan >>>>>>> tajriba gacha bo‘lgan qism esa
qo‘shilayotgan tajriba shoxiga tegishli.
17-dars · Git va GitHub (4/4) — Mantiqiy topshiriqlar (3–6) Page 1 of 3
a) Qaysi variant main ’dan, qaysi biri tajriba ’dan?
«Men shifokor bo‘lmoqchiman.» qatori — main (HEAD) shoxidan; «Men dasturchi
bo‘lmoqchiman.» qatori — tajriba shoxidan kelgan.
b) Ikkala orzuni birlashtirib, faylning tozalangan holatini to‘liq yozing:
Barcha conflict belgilari ( <<<<<<< HEAD , ======= , >>>>>>> tajriba ) o‘chiriladi va ikkala orzu
bitta faylga mantiqan birlashtiriladi:
# Orzularim
Men shifokor bo‘lmoqchiman va dasturchi bo‘lishni ham orzu qilaman.
Sayohat qilishni yaxshi ko‘raman.
c) Faylni tuzatgandan keyin qaysi 2 ta buyruq bajariladi?
1) git add orzular.md (fayl tuzatilganini Git’ga tasdiqlash uchun)
2) git commit -m "Conflict yechildi" (merge jarayonini yangi commit bilan yakunlash uchun)
5-topshiriq (mantiqiy). Faylda nima qoldi?
Boshlang‘ich holatda main shoxidagi salom.md faylida faqat Salom so‘zi bor. Har bir buyruqdan
keyingi fayl holatini ketma-ket kuzatamiz:
1. 1–2-qadamlar ( qizil shoxi): main ’dan qizil shoxi ochildi va unga Qizil qatori qo‘shilib
commit qilindi. Endi qizil shoxida Salom va Qizil bor, lekin main hali o‘zgarmagan.
2. 3-qadam ( git switch main ): main shoxiga qaytilganda ishchi papkadagi fayl main ’ning oxirgi
holatiga qaytadi.
3. 4–5-qadamlar ( yashil shoxi): main ’dan yangi yashil shoxi ochildi (unda faqat Salom bor
edi) va unga Yashil qatori qo‘shilib commit qilindi.
4. 6–7-qadamlar ( main ’ga qaytish va git merge qizil ): main shoxiga faqat qizil shoxi
qo‘shildi.
Savol Javob va tushuntirish
a) 3-qadamdan keyin salom.md da
nima yozilgan?
Faqat Salom so‘zi yozilgan. Chunki Qizil qatori qizil shoxida
qolgan, main shoxi esa hali o‘zgartirilmagan edi.
b) 5-qadamdan keyin ( yashil
shoxida) faylda nima bor?
Salom va Yashil (2 ta qator) bor. Chunki yashil shoxi
main ’dan ( Salom bor paytda) ajralib chiqqan va unga Yashil
qo‘shilgan.
c) 7-qadamdan keyin main ’da faylda
nima bor? Nega «Yashil» yo‘q?
main ’da Salom va Qizil bor. «Yashil» yo‘q, chunki biz faqat
git merge qizil buyrug‘ini bajardik, yashil shoxini esa hali
main ’ga qo‘shmadik.
d) Agar endi git merge yashil
qilinsa, nima bo‘lishi mumkin va
nega?
Merge conflict (to‘qnashuv) yuz beradi. Sababi: main shoxida
Salom so‘zidan keyingi 2-qatorda Qizil turibdi, qo‘shilayotgan
yashil shoxida esa aynan o‘sha 2-qatorda Yashil turibdi. Git
qaysi birini tanlashni bilmay, qaror so‘raydi.
17-dars · Git va GitHub (4/4) — Mantiqiy topshiriqlar (3–6) Page 2 of 3
6-topshiriq (xatolar). Xabar va yechim
Har bir Git xatosi sababi tahlil qilinib, mos yechim harfi bilan belgilandi:
Git xabari Yechim Qisqacha sababi
fatal: not a git repository B Terminal loyiha papkasida ochilmagan; cd
bilan papkaga kirish kerak.
! [rejected] main -> main (fetch
first)
A GitHub’da kompyuterda yo‘q yangi commit bor;
avval git pull , keyin git push qilinadi.
CONFLICT (content): Merge conflict
in orzular.md
D Ikki shox to‘qnashgan; fayldan conflict belgilarini
tozalab, add va commit qilinadi.
nothing to commit, working tree
clean
E Bu xato emas — barcha o‘zgarishlar allaqachon
commit qilingan, hech narsa qilish shart emas.
error: pathspec 'dizayin' did not
match
F Shox nomi xato yozilgan ( dizayn o‘rniga
dizayin ); git branch bilan aniq nomni
tekshirish kerak.
Author identity unknown C Git’da foydalanuvchi ismi va emaili kiritilmagan;
git config --global orqali sozlanadi..
Bu main shoxidagi versiya
