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
![image]()
