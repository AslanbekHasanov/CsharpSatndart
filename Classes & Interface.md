# 4 Sinflar
## 4.0 Nomlash
Standartga mos arxitekturada xizmatlar yoki brokerlarni ifodalovchi sinflar  nomlash konventsiyasidagi sinf turini ko'rsatish kerak, ammo bu modellarga taaluqli emas
### 4.0.0 Modellar 
#### Bajaring
```csharp
class Student{
     ...
}
```

#### Bajarmang 
```csharp
class StudentModel{
    ...
}
```
### 4.0.1 Xizmatlar 
Biznes mantiqini o'z ichiga olgan har qanday sinf uchun yagona uslubda.
#### Bajaring
```csharp
class StudentService{
    ...
}
```
#### Bajarmang
```csharp
class StudentsService{
    ...
}
```
#### Buni ham bajarmang
```csharp
class StudentBusinessLogic{
    ...
}
```
#### Buni ham qilmang
```csharp
class StudentBL{
    ...
}
```

### 4.0.2 Brokerlar 
Sizning xizmatlarimngiz va tashqi resurslar o'rtasida bo'lgan har qanday sinf uchun yagona uslubda.
#### Bajaring
```csharp
class StudentBroker{
    ...
}
```
#### Bajarmang 
```csharp
class StudentsBroker{
    ...
}
```
### 4.0.3 Kontrollerlar
`/api/students`RESTful operatsiyalari orqali mantiqingizni ochib berish kabi so'nggi nuqtalarni aks ettirish uchun ko'plik shaklida.
#### Bajaring
```csharp
class StudentsController{
    ...
}
```
#### Bajarmang
```csharp
class StudentController{
    ...
}
```
### 4.1 Maydonlar 
Maydon to'g'ridan-to'g'ri sinf yoki strukturada e'lon qilinadigan har qanday turdagi o'zgaruvchidir. Maydonlar o'z ichiga olgan turdagi a'zolardir.
#### Bajaring 
```csharp
class StudentsController{
    private redonly string studentName;
}
```
#### Bajarmang 
```csharp
class StudentController{
    private readonly string StudentName;
}
```
#### Buni ham bajarmang 
```csharp
class StudentController{
    private redonly string_studentName;
}
```
### 4.1.1 Havola qilish
O'zgaruvchilar bo'limlarida aytib o'tilganidek, nomlash uchun bir xil qoidalarga amal qilish kerak.
Sinfning shaxsiy maydoniga murojaat qilganida, `this`xususiy sinf  a'zosini qamrovli usul yoki konstruktor darajasidagi o'zgaruvchidan ajratish uchun kalit so'zdan foydalaning.
#### Bajaring 
```csharp
class StudentsController{
    private redonly string StudentName;

    public  StudentsController(string StudentName){
        this.studentName = studentName;
    }
}
```
#### Bajarmang 
```csharp
class StudentsController{
    private redonly string_StudentName;

    public  StudentsController(string StudentName){
        _studentName = studentName;
    }
}
```
## 4.2 Namoyishlar 

### 4.2.0 Parametrlarni kiritish tahalluslari
Agar kirish o'zgaruvchilari nomlari kirish tahalluslariga mos kelsa, ulardan foydalaning aks holda tahalluslardan, ayniqsa kiritilgan qiymatlar bilan foydalanish kerak.
#### Bajaring 
```csharp
int score = 150;
string name = "Josh";

var student = new Student(name,score);
```
#### Bajarmang 
```csharp
var student = new Student(name: "Josh",score:150);
```
#### Buni ham bajarmang 
```csharp
var student = new Student("Josh",150);
```
#### Buni ham bajarmang
```csharp
Student student = new(....);
```
### 4.2.1 Mulkni himoya qilish tartibi
Sinf namunasini yaratishda - mulkni belgilash sinf deklaratsiyasidagi xususiyatlar tartibidagi mos kelishiga ishonch hosil qiling.
#### Bajaring
```csharp
public class Student
{
    public Guid Id { get; set; }
    public string Name { get; set; }
}

var student = new Student
{
    Id = Guid.NewGuid(),
    Name = "Elbek"
}
```
#### Bajarmang 
```csharp
public class Student
{
    private  readonly Guid id;
    purivate redonly string name;


    public Student(Guid id, string name)
    {
        this.id = id;
        this.name = name;
    }
}

var student = new Student (id: Guid.NewGuid(),name: "Elbek");
```
#### Buni ham bajarmang
```csharp
public class Student
{
    public Guid Id { get; set; }
    public string Name { get; set; }
}

var student = new Student
{
    Name = "Elbek",
    Id = Guid.NewGuid()
}
```
#### Buni ham bajarmang
```csharp
public class Student
{
    private  readonly Guid id;
    purivate redonly string name;


    public Student(string name, Guid id)
    {
        this.id = id;
        this.name = name;
    }
}

var student = new Student (id: Guid.NewGuid(),name: "Elbek");
```
#### Buni ham bajarmang
```csharp
public class Student
{
    private  readonly Guid id;
    purivate redonly string name;


    public Student(Guid id, string name)
    {
        this.id = id;
        this.name = name;
    }
}

var student = new Student (,name: "Elbek", id: Guid.NewGuid());
```





