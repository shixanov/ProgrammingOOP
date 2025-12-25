```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1
{
    internal class Program
    {
        static void Main()
        {
            int a, b;
            Console.WriteLine("Введите первое число");
            a = int.Parse(Console.ReadLine());
            Console.WriteLine("Введите второе число");
            b = int.Parse(Console.ReadLine());
            Console.WriteLine("Сложение: " + (a + b));
            Console.WriteLine("Вычитание: " + (a - b));
            Console.WriteLine("Умножение: " + (a * b));
            Console.WriteLine("Деление: " + (a / b));
            Console.WriteLine("Остаток от деления: " + (a % b));
            Console.WriteLine("Инкремент a: " + (a ++ ));
            Console.WriteLine("Инкремент b: " + (b ++ ));
            Console.WriteLine("Декремент a: " + (a -- ));
            Console.WriteLine("Декремент b: " + (b -- ));
            Console.WriteLine("Логическое умножение: " + (a & b));
            Console.WriteLine("Логическое сложение: " + (a | b));
            Console.WriteLine("Инвертация всех разрядов: " + (~a));

        }
    }
}
```
