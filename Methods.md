# 1 Usullar
## 1.0 Nomlash 
Usul nomlarini usul nima qilayotgani haqida qisqacha ma'lumot bo'lishi kerak, u aniq va qisqa bo'lishi kerak va sinxronizatsiya bo'yicha operatsiyani ifodalaydi.
### 1.0.0 Fe'llar 
Usul nomlari u bajarayotgan harakatni ifodalash uchun fe'llar bo'lishi kerak. 
#### Bajaring 
```csharp
public List<Student> 	GetStudent()
{
	...
}
```
#### Bajarmang
```csharp
public List<Student> Student()
{
	...
}
```
### 1.0.1 Asinxronlik 
Asinxronlik ustunlari qaytarish yoki umuman `Async`usullari kabi atama bilan postfikslash kerak. `Tak` `ValueTask`
####Bajaring 
```csharp
public async ValueTask<List<Student>> GetStudentAsync()
{
	...
}
```
#### Bajarmang
```csharp
public async ValueTask<List<Student>> GetStudent()
{
	...
}
```
####1.0.2 Kirish parametrlari
Kirish parametrlari obyektning qaysi xususiyatiga tayinlanishi yoki qidiruv kabi har qanday harakatlar uchun ishlatilishi aniq bo'lishi kerak.
### Bajaring 
```csharp
public async ValueTask<Student> GetStudentAsync(string studentName)
{
	...
}
```
#### Bajarmang 
```csharp
public async ValueTask<Student> GetStudents(string text)
{
	...
}
```
#### Buni ham bajarmang
```csharp
public async ValueTask<Student> GetStudentAsync(string name)
{
	...
}
```
### 1.0.3 Harakat parametrlari
Agar sizning usulingiz ma'lum bir parametr bilan ishni bajarayotgan bo'lsa, uni belgilang.
#### Bajaring
```csharp
public async ValueTask<Student> GetStudentByIdAsync(Guid studentId)
{
	...
}
```
#### Bajarmang 
```csharp

public async ValueTask<Student> GetStudentAsync(Guid studentId)
{
	...
}
```
### 1.0.4 Parametrlarni o'tqazish
Usuldan foydalanganda, agar kiritilgan parametrlarning tahalluslari o'zgaruvchilarga qisman foydalanish shart emas, aks holda siz tahalluslar bilan qiymatlarni belguilashingiz kerak.
#### Sizda usul bor deb tahmin qiling
```csharp
Student GetStudentByNameAsync(string StudentName);
```
#### Bajaring
```csharp
string studentName = "Todd";
Student student = await GetStudentByNameAsnyc(studentName);
```
#### Bajarmang
```csharp
Student student = await GetStudentByNameAsnyc(studentName: "Todd");
```
#### Bunday ham bajarmang 
```csharp
Student student = await GetStudentByNameAsnyc(toddName);
```
#### Bunday ham bajarmang
```csharp
Student student = await GetStudentByNameAsnyc("Todd");
```
#### Bunday ham bajarmang
```csharp
Student student = await GetStudentByNameAsnyc(todd);
```
## 1.1 Tashkilot 
Umuman olganda, bir xil mantiqning bir necha satrlarini o'z uslubiga kiritish va usulingiz har doim tavsilotlarning 0 darajasida saqlang.
### 1.1.0 Yagona/Ko'p laynerlar
#### 1.1.0.0 Yagona laynerlar
Faqat bitta kod satrini o'z ichiga olgan qanday usul o'qlarida foydalanish kerak.
#### Bajaring
```csharp
public List<Student> GetStudents() => this.storageBroker.GetStudents();
```
#### Bajarmang
```csharp
public List<Student> Students()
{
	return this.storageBroker.GetStudents()
}
```
Agar bitta chiziqli usul 120 belgidan oshib ketgan bo'lsa yangi qator uchun qo'shimcha yorliq bilan uzing.
#### Bajaring 
```csharp
public async ValueTask<List<Students>> GetAllWashingtonSchoolStudentsAsync() =>
	await this.storageBroker.GetStudentsAsync();
```
#### Bajarmang
```csharp
public async ValueTask<List<Student>>GetAllWashingtonSchoolsStudentsAsync() => await this.storageBroker.GetStudentsAsync();
```
#### 1.1.0.1 Ko'p laynerlar
Agar usul zanjir orqali ajratilgan yoki bog'langan bir chiziqni o'z ichiga olsa, u doiraga ega bo'lishi kerak. Parametrlar keyingi satrda ketmasa, ko'p chiziqli parametrlarga ega bo'lgan bir qator usulga ruhsat beriladi.
#### Bajaring
```csharp
public Student AddStudent(Student student)
{
	ValidateStudent(student);

	return this.storageBroker.InsertStudent(student);
}
```
#### Bajarmang
```csharp
public Student AddStudent(Student student)
{
	
	return this.storageBroker.InsertStudent(student)
		.WithLogging();
}
```
#### Buni ham bajarmang ajarmang
```csharp
public Student AddStudent(
	Student student)
{
	
	return this.storageBroker.InsertStudent(student);
}
```
#### Buni ham bajarmang
```csharp
public Student AddStudent(Student student) =>
	this.storageBroker.InsertStudent(student)
		.WithLogging();
```
#### Buni ham bajarmang
```csharp
public Student AddStudent(
	Student student) =>
		this.storageBroker.InsertStudent(student);
```
#### 1.1.1 Qaytish
Ko'p chiziqli usullar uchun usul mangtig'i va yakuni qaytarish chizig'i (agar mavjud bo'lsa) o'rtasida yangi qatorni oling.
#### Bajaring 
```
public List<Student>GetStudents()
{
	StudentsClient studentsApiClient = InitializiseStudentApiClient();

	return studentsApiClient.GetStudents();
}
```
#### Qilmang
```csharp
public List<Student> GetStudents()
{
	StudentsClient studentsApiClient = InitializiseStudentApiClient();
	return studentsApiClient.GetStudents();
}
```
#### 1.1.2 Bir necha qo'ng'iroqlar
Ko'p usulliu qo'ng'iroqlar bilan, agar ikkala qo'ng'iroq ham 120 belgidan kam bo'lsa, ular oxirida qo'ng'iroq usuli qaytish bo'lmasa ular stack bo'lishi mumkin,aks holda yangi qator bilan ajratiladi.
#### Bajaring
```csharp
public List<Student>GetStudents()
{
	StudentsClient studentsApiClient = InitializiseStudentApiClient();
	List<Student> student = studentsApiClient.GetStudents();

	return students;
}
```
#### Bajarmang
```csharp
public List<Student>GetStudents()
{
	StudentsClient studentsApiClient = InitializiseStudentApiClient();

	List<Student> student = studentsApiClient.GetStudents();

	return students;
}
```
#### Buni ham bajarmang
```csharp
public async ValueTask<List<Student>>GetStudents()
{
	StudentsClient washingtonSchoolsStudentsApiClient = 
		await InitializiseWashingtonSchoolStudentApiClientAsync();
	
	List<Student> student = studentsApiClient.GetStudents();

	return students;
}
```
#### Buni ham bajarmang
```csharp
public async ValueTask<List<Student>> GetStudents()
{
	StudentsClient washingtonSchoolsStudentsApiClient = 
		await InitializiseWashingtonSchoolStudentApiClientAsync();
	List<Student> student = studentsApiClient.GetStudents();

	return students;
}
```
#### 1.1.3 Deklaratsiya
Usul deklaratsiyasi 120 belgidan oshmasligi kerak.
#### Bajaring
```csharp
public async ValueTask<List<Student>> GetAIRRegisteredWashingtonSchoolsStudentsAsync(
	StudentsQuery studentsQuery)
{
	...
}
```
#### Bajarmang
```csharp
public async ValueTask<List<Student>> GetAIRRegisteredWashingtonSchoolsStudentsAsync(StudentsQuery studentsQuery)
{
	...
}
```
#### 1.1.4 Ko'p parametrlar
Agar siz bir nechta parametrlardan o'tayotgan bo'lsangiz va usul chaqiruvchining uzunligi 120 belgidan ortiq bo'lsa, har bir satrda bitta parametr bilan parametrlarni buzishingiz kerak.
#### Bajaring 
```csharp
List<Student>redmondHightSchool = await QueryAllWashingtonStudentsByScoreAndSchoolAsync(
	MinimumScore: 130,
	SchoolName: "Redmond Hight");
```
#### Bajarmang
```csharp
List<Student> redmondHightSchool = await QueryAllWashingtonStudentsByScoreAndSchoolAsync(
	MinimumScore: 130, SchoolName: "Redmond Hight");
```
#### 1.1.5 Zanjirlash (chirkinlashtirish/chiroylash)
Bazi usullar boshqa usullarni chaqirish uchun kengaytmalarni taklif qiladi. Masalan siz usulda `Select()`keyin usulni chaqirishingiz mumkin `Where()`. Va shunga o'xshash to'liq so'rov tugamaguncha.
Biz xunuklikni obodonlashtirish jarayonini kuzatamiz.Zanjirni usullariga qarashimiz chiroyli qilishimiz uchun  biz kodimizni xunuk qilamiz.
Mana bier necha misollar.
#### Bajaring
```csharp
	students.Where(student=>student.Name is "Elbek")
		.Select(student=>student.Name)
			.ToList()
```
#### Bajarmang
```csharp
	students
	.Where(student=>student.Name is "Elbek")
	.Select(student=>student.Name)
	.ToList()
```
Birinchi yondashuv zanjirini soddalashtirish va qisqartirishni talab qiladi, chunki ko'proq qo'ng'iroqlar kodni bu kabi yomonlashda davom etadi.
```csharp
	students.SomeMethods(...)
		  .SomeOtherMethod(...)
			.SomeOtherMethod(...)
				.SomeOtherMethod(...)
					.SomeOtherMethod(...);
```
Xiralashtirish jarayoni zanjirlarni kichikroq ro'yhatlarga bo'lib, keyin uni qayta ishlashga majbur qiladi. ikkinchi yondashuv (xoratsiz yondashuv) yangi va mavjud bayonot o'rtasidagi farqni aniqlash uchun qo'shimcha kognitiv resurslarni talab qilish mumkin:
```csharp
 student
.Where(student=>student.Name is "Elbek")
.Select(student=>student.Name)
.OrderBy(stuent=>student.Name)
.ToList()
ProcessStudents(students);
```




