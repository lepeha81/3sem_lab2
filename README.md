# 3sem_lab2
## Homework
### Задание 1
Создайте класс, представляющий учебный класс ClassRoom.
Создайте класс ученик - Pupil. 
В теле класса создайте методы void Study(), void Read(), void Write(), void Relax().
Создайте 3 производных класса ExcelentPupil, GoodPupil, BadPupil от класса базового класса Pupil и переопределите каждый из методов, в зависимости от успеваемости ученика (реализация может быть произвольной, например простой вывод на консоль разных строк).
Конструктор класса ClassRoom принимает аргументы типа Pupil, класс должен состоять из 4 учеников.
Предусмотрите возможность того, что пользователь может передать 2 или 3 аргумента.
Выведите информацию о том, как все ученики экземпляра класса ClassRoom умеют учиться, читать, писать, отдыхать. 

Примечание: при реализации возможности создания экземпляра класса ClassRoom с произвольным количеством учеников воспользуйтесь ключевым словом params.
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

public class ClassRoom
{
    private Pupil[] pupils;

    public ClassRoom(params Pupil[] pupils)//неограниченное количество элементов
    {
        this.pupils = pupils;
    }

    public void PrintPupilInfo()
    {
        Console.WriteLine("Pupil info:");
        for (int i = 0; i < pupils.Length; i++)
        {
            Console.WriteLine($"Pupil {i + 1}:");//интерполяция
            pupils[i].Study();
            pupils[i].Read();
            pupils[i].Write();
            pupils[i].Relax();
            Console.WriteLine();
        }
    }
}
public class Pupil
{
    public virtual void Study()
    {
        Console.WriteLine("Pupil: Studying...");
    }

    public virtual void Read()
    {
        Console.WriteLine("Pupil: Reading...");
    }

    public virtual void Write()
    {
        Console.WriteLine("Pupil: Writing...");
    }

    public virtual void Relax()
    {
        Console.WriteLine("Pupil: Relaxing...");
    }
}
class ExcellentPupil : Pupil
{
    public override void Study()
    {
        Console.WriteLine("ExcellentPupil: Studying very well!");
    }

    public override void Read()
    {
        Console.WriteLine("ExcellentPupil: Reading a lot of books!");
    }

    public override void Write()
    {
        Console.WriteLine("ExcellentPupil: Writing perfectly!");
    }

    public override void Relax()
    {
        Console.WriteLine("ExcellentPupil: resting a little");
    }
}

class GoodPupil : Pupil
{
    public override void Study()
    {
        Console.WriteLine("GoodPupil: Studying well!");
    }

    public override void Read()
    {
        Console.WriteLine("GoodPupil: Reading books!");
    }

    public override void Write()
    {
        Console.WriteLine("GoodPupil: Writing nicely!");
    }

    public override void Relax()
    {
        Console.WriteLine("GoodPupil: Relaxing sometimes");
    }
}

class BadPupil : Pupil
{
    public override void Study()
    {
        Console.WriteLine("BadPupil: Not studying enough!");
    }

    public override void Read()
    {
        Console.WriteLine("BadPupil: Not interested in reading!");
    }

    public override void Write()
    {
        Console.WriteLine("BadPupil: don't like to write");
    }

    public override void Relax()
    {
        Console.WriteLine("BadPupil: Relaxing all the time");
    }
}
class Program
{
    static void Main(string[] args)
    {
        Pupil pupil1 = new ExcellentPupil();
        Pupil pupil2 = new GoodPupil();
        Pupil pupil3 = new BadPupil();
        Pupil pupil4 = new Pupil();

        ClassRoom classRoom = new ClassRoom(pupil1, pupil2, pupil3, pupil4);
        classRoom.PrintPupilInfo();
    }
}
```
![image](https://github.com/lepeha81/3sem_lab2/blob/main/1.PNG)
### Задание 2
Создайте класс Vehicle.
В теле класса создайте поля: координаты и параметры средств передвижения (цена, скорость, год выпуска).
Создайте 3 производных класса Plane, Саг и Ship.
Для класса Plane должна быть определена высота и количество пассажиров.
Для класса Ship — количество пассажиров и порт приписки.
Написать программу, которая выводит на экран информацию о каждом средстве передвижения.

Примечание: избегайте дублирования кода, используйте ключевое слово base после объявления конструкторов в классах наследниках для вызова и передачи параметров в конструктор базового класса.
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

class Vehicle
{
    private double x;
    private double y;
    private double price;
    private double speed;
    private int year;

    public Vehicle(double x, double y, double price, double speed, int year)
    {
        this.x = x;
        this.y = y;
        this.price = price;
        this.speed = speed;
        this.year = year;
    }

    public void ShowInfo()
    {
        Console.WriteLine("Vehicle information:");
        Console.WriteLine($"Coordinates: ({x}, {y})");
        Console.WriteLine($"Price: {price}");
        Console.WriteLine($"Speed: {speed}");
        Console.WriteLine($"Year: {year}");
    }
}

class Plane : Vehicle
{
    private double visota;
    private int passengers;

    public Plane(double x, double y, double price, double speed, int year, double visota, int passengers)
        : base(x, y, price, speed, year)
    {
        this.visota = visota;
        this.passengers = passengers;
    }

    public void ShowInfo()
    {
        base.ShowInfo();
        Console.WriteLine($"visota: {visota}");
        Console.WriteLine($"Passengers: {passengers}");
    }
}

class Car : Vehicle
{
    public Car(double x, double y, double price, double speed, int year)
        : base(x, y, price, speed, year)
    {
    }

    public void ShowInfo()
    {
        base.ShowInfo();
    }
}

class Ship : Vehicle
{
    private int passengers;
    private string port;

    public Ship(double x, double y, double price, double speed, int year, int passengers, string port)
        : base(x, y, price, speed, year)
    {
        this.passengers = passengers;
        this.port = port;
    }

    public void ShowInfo()
    {
        base.ShowInfo();
        Console.WriteLine($"Passengers: {passengers}");
        Console.WriteLine($"Port: {port}");
    }
}
class Program
{
    static void Main(string[] args)
    {
        Plane plane = new Plane(100, 200, 100000, 500, 2010, 10000, 200);
        plane.ShowInfo();

        Console.WriteLine();

        Car car = new Car(50, 100, 50000, 200, 2015);
        car.ShowInfo();

        Console.WriteLine();

        Ship ship = new Ship(300, 400, 2000000, 100, 2020, 1000, "New York");
        ship.ShowInfo();
    }
}




```
![image](https://github.com/lepeha81/3sem_lab2/blob/main/2.PNG)
### Задание 3
Создайте класс DocumentWorker.
В теле класса создайте три метода OpenDocument(), EditDocument(), SaveDocument().
В тело каждого из методов добавьте вывод на экран соответствующих строк: "Документ открыт", "Редактирование документа доступно в версии Pro", "Сохранение документа доступно в версии Pro".
Создайте производный класс ProDocumentWorker.
Переопределите соответствующие методы, при переопределении методов выводите следующие строки: "Документ отредактирован", "Документ сохранен в старом формате, сохранение в остальных форматах доступно в версии Expert".
Создайте производный класс ExpertDocumentWorker от базового класса ProDocumentWorker.
Переопределите соответствующий метод. При вызове данного метода необходимо выводить на экран "Документ сохранен в новом формате".
В теле метода Main() реализуйте возможность приема от пользователя номера ключа доступа pro и exp.
Если пользователь не вводит ключ, он может пользоваться только бесплатной версией (создается экземпляр базового класса), если пользователь ввел номера ключа доступа pro и exp, то должен создаться экземпляр соответствующей версии класса, приведенный к базовому – DocumentWorker.
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

using System;

class DocumentWorker
{
    public void OpenDocument()
    {
        Console.WriteLine("Документ открыт");
    }

    public virtual void EditDocument()
    {
        Console.WriteLine("Редактирование документа доступно в версии Pro");
    }

    public virtual void SaveDocument()
    {
        Console.WriteLine("Сохранение документа доступно в версии Pro");
    }
}

class ProDocumentWorker : DocumentWorker
{
    public override void EditDocument()
    {
        Console.WriteLine("Документ отредактирован");
    }

    public override void SaveDocument()
    {
        Console.WriteLine("Документ сохранен в старом формате, сохранение в остальных форматах доступно в версии Expert");
    }
}

class ExpertDocumentWorker : ProDocumentWorker
{
    public override void SaveDocument()
    {
        Console.WriteLine("Документ сохранен в новом формате");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Введите номер ключа доступа:");
        string key = Console.ReadLine();

        DocumentWorker document;

        switch (key)
        {
            case "pro":
                document = new ProDocumentWorker();
                break;
            case "exp":
                document = new ExpertDocumentWorker();
                break;
            default:
                document = new DocumentWorker();
                break;
        }

        document.OpenDocument();
        document.EditDocument();
        document.SaveDocument();
    }
}
```
![image](https://github.com/lepeha81/3sem_lab2/blob/main/3.PNG)
