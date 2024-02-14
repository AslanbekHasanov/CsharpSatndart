# 0. O'zgaruvchilar
## 0.0 Nomlash
O'zgaruvchilar nomlari ixcham bo'lishi va tabiatni u egalik qilayotgan yoki ega bo'lishi mumkin bo'lgan qiymat miqdorini  ifodalovchi bo'lishi kerak.
### 0.0.0 Ismlar
#### Bajaring 
```csharp
var student = new Student();
```
#### Bajarmang
```csharp
var s = new Student();
```
#### Buni ham bajarmang 
```csharp
var stdn = new Student()
```
Xuddi shu qoidaga lambda ifodalari uchun ham amal qiladi.
#### Bajarmang 
```csharp
students.Where(student => student...);
```
#### Bajarmang
```csharp
students.Where(s => s...)
```
### 0.0.1 Ko'plik
#### Bajaring
```csharp 
var students = new List<Student>();
```
#### Bajarmang
```csharp
var studentList = new List<Student>();
```
### 0.0.2 Turlar bilan nomlar 
#### Bajaring 
```csharp
var student = new Student();
```
#### Bajarmang
```csharp
var studentModel = new Student();
```
#### Buni ham bajarmang
```csharp
var studentObj = new Student();

```
### 0.0.3 Nul yoki standart qiymatlar 
`0`agar o'zgaruvchan qiymatlar satrlar uchun `int`yoki satrlar uchun standart bo'lsa `null`va siz ushbu qiymatni o'zgartirish rejalashtirmasangiz (masalan sinov maqsadlarida)  unda nom ushbu qiymatni aniqlash kerak.
#### Bajaring 
```csharp
Student noStudent = null;
```
#### Bajarmang
```csharp
Student student = null;
```
#### Buni ham bajarmang
```csharp
int noChangeCount = 0;
```
#### Buni gam bajarmang
```csharp
int ChangeCount = 0;
```
### 0.1 Deklaratsiyalar
O'zgaruvchini e'lon qilish va uni instansiyalash hatto qiymatni keyinroq aniqlash kerak bo'lsa ham o'zgaruvchining bevosita turini ko'rsatish kerak.
#### 0.1.0 Aniq turlari
Agar o'ng tomonb turi aniq bo'lsa, `var` o'zgaruvchini aniq qilish uchun fpoydalaning.
#### Bajaring
```csharp
var student = new Student();
```
#### Bajarmang 
```csharp
Student student = new Student();
```

#### 0.1.1 Yarim aniq turlari 
Qaytarilgan qiymat turining o'ng tomoni aniq bo'lmasa (lekin ma'lum), u holda siz o'z o'zgaruvchingizni uning turi bilan aniq e'lon qilishingiz kerak.
#### Bajaring 
```csharp
Student student = GetStudent();
```
#### Bajarmang 
```csharp
var student = GetStudent();
```
#### 0.1.2 Noaniq turlar 
Qaytarilgan qiymatning o'ng tomoni aniq va nomalum bo'lsa (masalan anonim turlar) siz `var` o'zgaruvchi turi sifatida foydalanishingiz mumkin.
#### Bajaring
```csharp
var student = new
{
	Name = "Hassan",
	Score = 100
}
```
#### 0.1.3 Yagona mulk turlari
Agar bitta xuxusiyatga ega e'lon qilsangiz, xususiyatni to'g'ridan to'g'ri ta'minlang.
#### Bajaring
```csharp
var inputStudentEvent = new StudentEvent
inputStudentEventStudent = inputProcessedStudent;
```
#### Bajarmang
```csharp
var inputStudentEvent = new StudentEvent
{
	inputStudentEventStudent = inputProcessedStudent;
};
```
#### Buni ham bajarmang
```csharp
var inputStudentEvent = new StudentEvent
{
	inputStudentEventStudent = inputProcessedStudent;
	Date = someDate
};
```
#### Buni ham bajarmang
```csharp
var inputStudentEvent = new StudentEvent();
studentEvent.Student = someStudent;
StudentEvent.Date = someDate;
```
### 0.2 Tashkilot 
#### 0.2.0 Buzilish
Agar o'zgaruvchilarning belgisi 120 belgidan oshsa, uni tenglik belgisidan boshlab ajrating.
#### Bajaring 
```csharp
List<Student>WashingtonSchoolStudentWithGrades = 
	awant GetAllWashingtonSchoolStudentWithTheirGradesAsync();
```
#### Bajarmang
```csharp
List<Student>WashingtonSchoolStudentWithGrades =  awant GetAllWashingtonSchoolStudentWithTheirGradesAsync();
```
#### 0.2.1 Bir necha deklaratsiyalar
Ikki yoki undan ortiq qatorni egallagan deklaratsiyalar oldingi oldingi va keyingi oldin va keyin yangi qatorga ega bo'lishi kerak.
#### Bajaring 
```csharp
Student student = new Student();
{
List<Student>WashingtonSchoolStudentWithGrades = 
	awant GetAllWashingtonSchoolStudentWithTheirGradesAsync();

	School school = await GetStudentAsync();
}
```
#### Bajarmang
```csharp
Student student = new Student();
List<Student>WashingtonSchoolStudentWithGrades = 
	awant GetAllWashingtonSchoolStudentWithTheirGradesAsync();
School school = await GetStudentAsync();
```
Bundan tashqari faqat bitta saterdan iborat o'zgaruvchilar deklaratsiyasi ular orasidagi yangui qatorlar bo'lmasligi kerak.

#### Bajaring 
```csharp
Student student [= GetStudent();
School student = await GetSchoolAsync();
```
#### Bajarmang
```csharp
Student student [= GetStudent();

School student = await GetSchoolAsync();
```
