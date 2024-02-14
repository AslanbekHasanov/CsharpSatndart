# 0 File
Quyida C# fayllarini nomlash qoidalari va ko'rsatmalari keltirilgan
## 0.0 Naming
Fayl nomlari PascalCase konventsiyasiga va `.cs` fayl kengaytmasiga mos kelishi kerak

### Shu ko'rinishda
```
Student.cs
```
### Boshqa ko'rinishi 
```
StudentService.cs
```
### Qilmang
```
student.cs
```
### Bunday ham qilmang
```
studentService.cs
```
### Bunday ham qilmang
```
Student_Service.cs
```
 ## 0.1 Qisman sinf fayllari.
 
Qisman sinf fayllari - bu ildiz fayl uchun  ichida o'rnatilgan sinflarni o'z ichiga olgan fayllar. Misol uchun:
- StudentSrvice.cs
	- Student.Service.Validations.cs
	- Student.Service.Exceptions.cs

Tasdiqlash va  istisnolar ko'p o'lchovli makonda har qanday sinfning boshqa tomonini ko'rsatish uchun qisman sinflardir.

### Qiling 
```
StudentService.Validations.cs
```
### Bunday ham qiling
```
StudentService.Validationsn.Add.cs
```
Qilmang
```
StudentServiceValidations.cs
```
### Bunday ham qilmang
```
StudentService_Validations.cs
```
