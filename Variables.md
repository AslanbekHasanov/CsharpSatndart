# 0. O'zgaruvchilar
## 0.0 Nomlash
O'zgaruvchilar nomlari ixcham bo'lishi va tabiatni u egalik qilayotgan yoki ega bo'lishi mum,in bo'lgan qiymat miqdorini  ifodalovchi bo'lishi kerak.
### 0.0.0 Ismlar
#### Bajaring 
```
var student = new Student();
```
#### Bajarmang
```
var s = new Student();
```
#### Buni ham bajarmang 
```
var stdn = new Student()
```
Xuddi shu qoidaga lambda ifodalari uchun ham amal qiladi.
#### Bajarmang 
```
students.Where(student => student...);
```
#### Bajarmang
```
students.Where(s => s...)
```
### 0.0.1 Ko'plik
#### Bajaring
``` 
var students = new List<Student>();
```
#### Bajarmang
```
var studentList = new List<Student>();
```
### 0.0.2 Turlar bilan nomlar 
#### Bajaring 
```
var student = new Student();
```
#### Bajarmang
```
var studentModel = new Student();
```
#### Buni ham bajarmang
```
var studentObj = new Student();

```
### 0.0.3 Nul yoki standart qiymatlar 
`0`agar o'zgaruvchan qiymatlar satrlar uchun `int`yoki satrlar uchun standart bo'lsa `null`va siz ushbu qiymatni o'zgartirish rejalashtirmasangiz (masalan sinov maqsadlarida)  unda nom ushbu qiymatni aniqlash kerak.
#### Bajaring 
```
Student noStudent = null;
```
#### Bajarmang
```
Student student = null;
```
#### Buni ham bajarmang
```
int noChangeCount = 0;
```
#### Buni gam bajarmang
```
int ChangeCount = 0;
```
### 0.1 Deklaratsiyalar
O'zgaruvchini e'lon qilish va uni instansiyalash hatto qiymatni keyinroq aniqlash kerak bo'lsa ham o'zgaruvchining bevosita turini ko'rsatish kerak.
#### 0.1.0 Aniq turlari
Agar o'ng tomonb turi aniq bo'lsa, `var` o'zgaruvchini aniq qilish uchun fpoydalaning.
#### Bajaring
```
var student = new Student();
```
#### Bajarmang 
```
Student student = new Student();
```

#### 0.1.1 Yarim aniq turlari 
Qaytarilgan qiymat turining o'ng tomoni aniq bo'lmasa (lekin ma'lum), u holda siz o'z o'zgaruvchingizni uning turi bilan aniq e'lon qilishingiz kerak.
#### Bajaring 
```
Student student = GetStudent();
```
#### Bajarmang 
```
var student = GetStudent();
```
#### 0.1.2 Noaniq turlar 
Qaytarilgan qiymatning o'ng tomoni aniq va nomalum bo'lsa (masalan anonim turlar) siz `var` o'zgaruvchi turi sifatida foydalanishingiz mumkin.
#### Bajaring
```
var student = new
{
	Name = "Hassan",
	Score = 100
}
```
#### 0.1.3 Yagona mulk turlari
Agar bitta xuxusiyatga ega e'lon qilsangiz, xususiyatni to'g'ridan to'g'ri ta'minlang.
#### Bajaring
```
var inputStudentEvent = new StudentEvent
inputStudentEventStudent = inputProcessedStudent;
```
#### Bajarmang
```
var inputStudentEvent = new StudentEvent
{
	inputStudentEventStudent = inputProcessedStudent;
};
```
#### Buni ham bajarmang
```
var inputStudentEvent = new StudentEvent
{
	inputStudentEventStudent = inputProcessedStudent;
	Date = someDate
};
```
#### Buni ham bajarmang
```
var inputStudentEvent = new StudentEvent();
studentEvent.Student = someStudent;
StudentEvent.Date = someDate;
```
### 0.2 Tashkilot 
#### 0.2.0 Buzilish
Agar o'zgaruvchilarning belgisi 120 belgidan oshsa, uni tenglik belgisidan boshlab ajrating.
#### Bajaring 
```
List<Student>WashingtonSchoolStudentWithGrades = 
	awant GetAllWashingtonSchoolStudentWithTheirGradesAsync();
```
#### Bajarmang
```
List<Student>WashingtonSchoolStudentWithGrades =  awant GetAllWashingtonSchoolStudentWithTheirGradesAsync();
```
#### 0.2.1 Bir necha deklaratsiyalar
Ikki yoki undan ortiq qatorni egallagan deklaratsiyalar oldingi oldingi va keyingi oldin va keyin yangi qatorga ega bo'lishi kerak.
#### Bajaring 
```
Student student = new Student();
{
List<Student>WashingtonSchoolStudentWithGrades = 
	awant GetAllWashingtonSchoolStudentWithTheirGradesAsync();

	School school = await GetStudentAsync();
}
```
#### Bajarmang
```
Student student = new Student();
List<Student>WashingtonSchoolStudentWithGrades = 
	awant GetAllWashingtonSchoolStudentWithTheirGradesAsync();
School school = await GetStudentAsync();
```
Bundan tashqari faqat bitta saterdan iborat o'zgaruvchilar deklaratsiyasi ular orasidagi yangui qatorlar bo'lmasligi kerak.

#### Bajaring 
``` 
Student student [= GetStudent();
School student = await GetSchoolAsync();
```
#### Bajarmang
```
Student student [= GetStudent();

School student = await GetSchoolAsync();
```
