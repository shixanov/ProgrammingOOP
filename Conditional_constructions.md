Вопрос 1
Какие преобразования типов НЕ выполняются автоматически:

1. Из int в short
2. Из short в int
3. Из bool в string
4. Из byte в float
Ответ:  1,2

# **Условные конструкции**

**Упражнение 1**
```cs
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Введите первое число:");
        int numA = int.Parse(Console.ReadLine());

        Console.WriteLine("Введите второе число:");
        int numB = int.Parse(Console.ReadLine());

        // Используем switch для выбора результата
        int comparisonResult = Math.Sign(numA - numB);

        switch (comparisonResult)
        {
            case 0:
                Console.WriteLine("Оба числа равны.");
                break;
            case 1:
                Console.WriteLine("Первое число больше второго.");
                break;
            case -1:
                Console.WriteLine("Первое число меньше второго.");
                break;
        }
    }
}
```

**Упражнение 2**
```cs
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Пожалуйста, введите число:");
        int userNumber = int.Parse(Console.ReadLine());

        // Проведение проверки диапазона с использованием логического оператора
        bool isBetween = userNumber > 5 && userNumber < 10;

        if (isBetween)
        {
            Console.WriteLine("Число находится между 5 и 10");
        }
        else
        {
            Console.WriteLine("Число за пределами диапазона");
        }
    }
}
```

**Упражнение 3**
```cs
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Введите число:");
        int userInput = int.Parse(Console.ReadLine());

        // Используем массив для хранения целевых значений
        int[] targetNumbers = { 5, 10 };

        // Проверка, содержит ли массив нужное число
        bool isMatch = false;
        foreach (int num in targetNumbers)
        {
            if (userInput == num)
            {
                isMatch = true;
                break;
            }
        }

        if (isMatch)
        {
            Console.WriteLine("Число равно 5 или 10");
        }
        else
        {
            Console.WriteLine("Неизвестное число");
        }
    }
}
```

**Упражнение 4**
```cs
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Введите сумму вклада:");
        double depositAmount = double.Parse(Console.ReadLine());

        // Задаем ставку по условию, используя тернарный оператор
        double interestRate = depositAmount < 100 ? 5 :
                              depositAmount <= 200 ? 7 : 10;

        // Расчёт процентов
        double accruedInterest = (depositAmount * interestRate) / 100;

        // Общая сумма вклада с начисленными процентами
        double totalAmount = depositAmount + accruedInterest;

        // Вывод результатов с форматированием
        Console.WriteLine($"\nСумма вклада: {depositAmount:F2}");
        Console.WriteLine($"Процентная ставка: {interestRate}%");
        Console.WriteLine($"Начисленные проценты: {accuredInterest:F2}");
        Console.WriteLine($"Общая сумма с процентами: {totalAmount:F2}");
    }
}
```

**Упражнение 5**
```cs
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Введите сумму вклада:");

        // преобразовываем его в дробное число (double)
        double deposit = Convert.ToDouble(Console.ReadLine());
        double interestRate; // хранение процентной ставки
        // бонус как константа
        const double bonus = 15;

        if (deposit < 100)
        {
            interestRate = 5;
        }
        else if (deposit >= 100 && deposit <= 200)
        {
            interestRate = 7;
        }
        else // <200
        {
            interestRate = 10;
        }

        // рассчитываем сумму начисленных процентов
        double interestDeposit = (deposit * interestRate) / 100;

        // рассчитываем итоговую сумму вклада с процентами
        double totalDeposit = deposit + interestDeposit;
        // добавление бонуса
        totalDeposit += bonus;

        // вывод результатов
        Console.WriteLine($"\nСумма вклада: {deposit:F2}");
        Console.WriteLine($"Начисленный процент: {interestRate}%");
        Console.WriteLine($"Сумма начисленных процентов: {interestDeposit:F2}");
        Console.WriteLine($"Начисленный бонус: {bonus:F2}");
        Console.WriteLine($"Итоговая сумма вклада с процентами и бонусом: {totalDeposit:F2}");
    }
}
```

**Упражнение 6**
```cs
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Выберите тип операции: 1 — Сложение, 2 — Вычитание, 3 — Умножение");

        // Попытка преобразовать ввод в число
        if (int.TryParse(Console.ReadLine(), out int choice))
        {
            switch (choice)
            {
                case 1:
                    Console.WriteLine("Вы выбрали: сложение");
                    break;
                case 2:
                    Console.WriteLine("Вы выбрали: вычитание");
                    break;
                case 3:
                    Console.WriteLine("Вы выбрали: умножение");
                    break;
                default:
                    Console.WriteLine("Некорректный выбор. Пожалуйста, введите 1, 2 или 3.");
                    break;
            }
        }
        else
        {
            Console.WriteLine("Ошибка: введено не число");
        }
    }
}
```

**Упражнение 7**
```cs
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Выберите операцию:\n1 — Сложение\n2 — Вычитание\n3 — Умножение");
        
        if (!int.TryParse(Console.ReadLine(), out int operation))
        {
            Console.WriteLine("Ошибка: некорректный ввод номера операции.");
            return;
        }

        Console.Write("Введите первое число: ");
        if (!double.TryParse(Console.ReadLine(), out double num1))
        {
            Console.WriteLine("Ошибка: некорректное значение первого числа.");
            return;
        }

        Console.Write("Введите второе число: ");
        if (!double.TryParse(Console.ReadLine(), out double num2))
        {
            Console.WriteLine("Ошибка: некорректное значение второго числа.");
            return;
        }

        double result;

        switch (operation)
        {
            case 1:
                result = num1 + num2;
                Console.WriteLine($"\nРезультат сложения: {num1} + {num2} = {result}");
                break;

            case 2:
                result = num1 - num2;
                Console.WriteLine($"\nРезультат вычитания: {num1} - {num2} = {result}");
                break;

            case 3:
                result = num1 * num2;
                Console.WriteLine($"\nРезультат умножения: {num1} * {num2} = {result}");
                break;

            default:
                Console.WriteLine("\nОшибка: выбранная операция не поддерживается.");
                break;
        }
    }
}
```

**Практическая**
```cs
using System;

class Program
{
    static bool hasOrb = false;

    static void Main()
    {
        Console.WriteLine("НОВЕЛЛА: ПЕЩЕРА ЗАБЫТЫХ ТАЙН");
        Console.WriteLine("Вы стоите перед входом в темную пещеру. Кажется, вы ищете артефакт.");

        EnterCave();
        Console.WriteLine("\nИгра окончена.");
    }

    static void EnterCave()
    {
        Console.WriteLine("\nВы у входа. Холодный воздух манит внутрь.");
        Console.WriteLine("1. Зайти в пещеру.");
        Console.WriteLine("2. Отказаться от затеи и уйти.");

        int choice = ReadChoice(2);
        if (choice == 1)
            MainHall();
        else
            CowardEnd();
    }

    static void MainHall()
    {
        Console.WriteLine("\nВнутри просторный зал. В центре тускло светится синий кристалл.");
        Console.WriteLine("1. Подойти к кристаллу.");
        Console.WriteLine("2. Пойти в левый туннель.");
        Console.WriteLine("3. Пойти в правый туннель.");

        int choice = ReadChoice(3);
        switch (choice)
        {
            case 1:
                Crystal();
                MainHall(); // возвращение в зал после действия
                break;
            case 2:
                LeftTunnel();
                break;
            case 3:
                RightTunnel();
                break;
        }
    }

    static void Crystal()
    {
        Console.WriteLine("\nВы касаетесь кристалла. Он рассыпается, оставляя в руке Светящуюся Сферу.");
        hasOrb = true;
    }

    static void LeftTunnel()
    {
        Console.WriteLine("\nЛевый туннель выводит вас к подземному озеру.");
        Lake();
    }

    static void RightTunnel()
    {
        Console.WriteLine("\nПравый туннель обваливается за спиной! Вы чудом пробегаете вперед.");
        Lake();
    }

    static void Lake()
    {
        Console.WriteLine("\nВы у озера. В воде что-то блестит.");
        Console.WriteLine("1. Поискать что-то полезное в воде.");
        Console.WriteLine("2. Переплыть озеро к выходу.");

        int choice = ReadChoice(2);
        if (choice == 1)
            FindItem();
        else
            CrossLake();
        
        CastleCourtyard();
    }

    static void FindItem()
    {
        Console.WriteLine("\nВы находите старый, но крепкий меч на дне озера.");
        // можно добавить переменную для предмета, если нужно
    }

    static void CrossLake()
    {
        Console.WriteLine("\nВы перебрались через озеро. Перед вами две двери: деревянная и металлическая.");
        Console.WriteLine("1. Открыть деревянную дверь.");
        Console.WriteLine("2. Открыть металлическую дверь.");

        int choice = ReadChoice(2);
        if (choice == 1)
            WoodenDoor();
        else
            MetalDoor();
    }

    static void WoodenDoor()
    {
        Console.WriteLine("\nДеревянная дверь была ловушкой. Вы проваливаетесь в бездну.");
        DeadEndVoid();
    }

    static void MetalDoor()
    {
        Console.WriteLine("\nМеталлическая дверь ведет в комнату, где спит древний страж.");
        Console.WriteLine("1. Попытаться тихо прокрасться мимо.");
        Console.WriteLine("2. Попытаться разбудить стража.");

        int choice = ReadChoice(2);
        if (choice == 1)
            EscapePastGuard();
        else
            GuardCaptured();
    }

    static void EscapePastGuard()
    {
        Console.WriteLine("\nВам удается тихо проскользнуть мимо стража. Вы видите выход.");
        FinalHall();
    }

    static void GuardCaptured()
    {
        Console.WriteLine("\nСтраж просыпается! Он слишком силен, чтобы сражаться.");
        GuardEnd();
    }

    static void FinalHall()
    {
        Console.WriteLine("\nВы в последнем зале. Здесь лежит искомый артефакт, но он охраняется магическим барьером.");
        Console.WriteLine("1. Использовать Светящуюся Сферу для разрушения барьера.");
        Console.WriteLine("2. Попытаться обойти и найти другой выход.");

        int choice = ReadChoice(2);
        if (choice == 1)
        {
            if (hasOrb)
                DestroyBarrier();
            else
                TrappedEnd();
        }
        else
        {
            TrappedEnd();
        }
    }

    static void DestroyBarrier()
    {
        Console.WriteLine("\nВы использовали Светящуюся Сферу! Она разрушает барьер.");
        ArtifactTake();
    }

    static void ArtifactTake()
    {
        Console.WriteLine("\nВы забираете артефакт. Пещера начинает трястись, но вы успеваете убежать.");
        VictoryEnd();
    }

    // Концовки

    static void CowardEnd()
    {
        Console.WriteLine("\nТрус");
        Console.WriteLine("Вы вернулись домой. Приключение окончено, артефакт остался в пещере.");
    }

    static void DeadEndVoid()
    {
        Console.WriteLine("\nПадение");
        Console.WriteLine("Вы упали в бездну и погибли.");
    }

    static void GuardEnd()
    {
        Console.WriteLine("\nПленник");
        Console.WriteLine("Страж пленил вас. Вы проведете остаток жизни в темнице пещеры.");
    }

    static void TrappedEnd()
    {
        Console.WriteLine("\nВ западне");
        Console.WriteLine("Вы заперты в последнем зале, не в силах преодолеть барьер. Конец пути.");
    }

    static void VictoryEnd()
    {
        Console.WriteLine("\nПобеда");
        Console.WriteLine("Вы выбрались из пещеры с артефактом. Выполнено! Вы герой!");
    }

    // Вспомогательный метод для чтения выбора с проверкой
    static int ReadChoice(int maxOption)
    {
        int choice;
        while (true)
        {
            Console.Write("Ваш выбор: ");
            string input = Console.ReadLine();
            if (int.TryParse(input, out choice) && choice >= 1 && choice <= maxOption)
                return choice;
            Console.WriteLine($"Пожалуйста, введите число от 1 до {maxOption}.");
        }
    }
}
```
