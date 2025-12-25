# cycles


**Вопрос 1**

Сколько раз выполнится следующий цикл и почему:
```cs
int i = 5;
while(i > 0)
{
    i *= 3;
    i *= -1;
}
```
**Ответ:**
Цикл выполнится 1 раз.

Причина:
На первой итерации цикла значение переменной i сначала умножается на 3 (i =15), а затем умножается на -1 (i = -15).
При следующей проверке условия `while(i > 0)` оно оказывается ложным, так как -15 > 0 — ложь. Цикл немедленно прекращает выполнение.

**Вопрос 2**

Дан следующий цикл:
```cs
int j = 2;

for (int i = 1; i < 100; i = i + 2)

{

    j = j - 1;

    while(j < 15)

    {

        j = j + 5;

    }

}
```
**Сколько раз в этом цикле будет выполняться строка j = j - 1;**

**Ответ:**
`50 раз`
Объяснение:
Строка `j = j - 1;` находится во внешнем цикле for. Этот цикл управляется переменной `i`.
- Цикл `for` начинается с `i = 1`.
- Условие выполнения: `i < 100`.
- Шаг изменения: `i = i + 2`.

Цикл `for` последовательно перебирает нечетные числа: 1 ... 99.
Количество итераций внешнего цикла равно 50. Так как строка `j = j - 1;` выполняется ровно один раз за каждую итерацию внешнего цикла, она выполнится 50 раз.

**Вопрос 3**

Что будет выведено на консоль в результате выполнения следующего цикла:
```cs
for(int i = 1; i < 3; i++)

{

    switch (i)

    {

        default:

            Console.WriteLine($"i = {i++}");

            break;
      }

}
```
**Варианты ответов:**
- Программа не скомпилируется
- Ничего не будет выведено на консоль
- Консоль будет иметь вывод
	 `i = 1`
- Консоль будет иметь вывод
	 `i = 1`
	 `i = 2`

**Ответ:** 
Консоль выведет `i=1`
Объяснение:
1. На первой итерации `i=1`. Внутри default происходит вывод `i=1`, а затем пост-инкремент i++ меняет значение i на 2.
2. `break` выходит из `switch` и из тела цикла `for`.
3. В заголовке цикла `for` происходит еще один инкремент `i++`, меняя значение `i` на 3.
4. Условие цикла `i < 3` становится ложным (`3 < 3`), и цикл завершается.

**Упражнение 1**

За каждый месяц банк начисляет к сумме вклада 7% от суммы. Напишите консольную программу, в которую пользователь вводит сумму вклада и количество месяцев. А банк вычисляет конечную сумму вклада с учетом начисления процентов за каждый месяц.
Для вычисления суммы с учетом процентов используйте цикл for. Для ввода суммы вклада используйте выражение Convert.ToDecimal(Console.ReadLine()) (сумма вклада будет представлять тип decimal).
```cs
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Введите начальную сумму вклада:");
        decimal deposit = Convert.ToDecimal(Console.ReadLine());

        Console.WriteLine("Введите количество месяцев, на которое открыт вклад:");
        int months = Convert.ToInt32(Console.ReadLine());

        decimal monthlyRate = 0.07m; // суффикс 'm' указывает, что это decimal
        
		// стандартное форматирование F2 (Fixed point, 2 знака после запятой)
        Console.WriteLine($"\nНачальная сумма: {deposit:F2}");
        Console.WriteLine($"Срок вклада: {months} месяцев");

        for (int i = 1; i <= months; i++)
        {
            decimal interestGained = deposit * monthlyRate;
            deposit = deposit + interestGained;

            Console.WriteLine($"Месяц {i}: Начислено {interestGained:F2}. Сумма стала: {deposit:F2}");
        }

        Console.WriteLine($"\nСумма вклада через {months} месяцев составит: {deposit:F2}");
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
        Console.WriteLine("Введите начальную сумму вклада:");
        decimal deposit = Convert.ToDecimal(Console.ReadLine());

        Console.WriteLine("Введите количество месяцев, на которое открыт вклад:");
        int Months = Convert.ToInt32(Console.ReadLine());

        decimal monthlyRate = 0.07m;

        // стандартное форматирование F2 (Fixed point, 2 знака после запятой)
        Console.WriteLine($"\nНачальная сумма: {deposit:F2} ₽");
        Console.WriteLine($"Срок вклада: {Months} месяцев");

        int currentMonth = 1;

        while (currentMonth <= Months)
        {
            decimal interestGained = deposit * monthlyRate;
            deposit += interestGained;

            Console.WriteLine($"Месяц {currentMonth}: Начислено {interestGained:F2} ₽. Сумма стала: {deposit:F2} ₽");

            currentMonth++;
        }

        Console.WriteLine($"\nСумма вклада через {Months} месяцев составит: {deposit:F2} ₽");
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
        for (int i = 1; i <= 10; i++)
        {
            for (int j = 1; j <= 10; j++)
            {
                Console.Write($"{i * j}\t"); // табуляция для выравнивания
            }
            Console.WriteLine();
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
        double num1, num2;

        Console.WriteLine("Умножение двух чисел");

        // бесконечный цикл для повторного запроса ввода
        while (true)
        {
            Console.WriteLine("\nВведите первое число:");
            if (!double.TryParse(Console.ReadLine(), out num1))
            {
                Console.WriteLine("Некорректный ввод первого числа.");
                continue; // возврат к началу
            }

            Console.WriteLine("Введите второе число:");
            if (!double.TryParse(Console.ReadLine(), out num2))
            {
                Console.WriteLine("Некорректный ввод второго числа.");
                continue; // возврат к началу
            }

            // проверка диапазона
            if (num1 >= 0 && num1 <= 10 && num2 >= 0 && num2 <= 10)
            {
                // если числа допустимы, выходим из бесконечного цикла
                break;
            }
            else
            {
                // если хотя бы одно число недопустимо
                Console.WriteLine("Введенные числа недопустимы.");
            }
        }

        // выполнение только после выхода из цикла
        double result = num1 * num2;
        Console.WriteLine($"Результат умножения: {num1} * {num2} = {result}");
    }
}
```

**Практическая**
```cs
using System;
using System.Threading;

class Program
{
    static void Main()
    {
        // Отслеживание, что нашел или сделал игрок
        bool hasOrb = false;
        bool hasSword = false;
        bool hasRuneKey = false;

        bool gameIsRunning = true;
        string currentState = "Step1";

        Console.WriteLine("ПЕЩЕРА ЗАБЫТЫХ ТАЙН");
        Console.WriteLine("Вы стоите перед входом в темную пещеру. Ваша цель - древний артефакт.");

        // цикл будет работать, пока gameIsRunning = true.
        // концовка просто устанавливает gameIsRunning = false, чтобы завершить игру.
        while (gameIsRunning)
        {
            // switch проверяет, где мы, и выполняет логику для этого места.
            switch (currentState)
            {
                // шаг 1: вход
                case "Step1":
                    Console.WriteLine("\nВход в пещеру");
                    Console.WriteLine("Вы у входа. Холодный воздух манит внутрь.");
                    Console.WriteLine("1. Зайти в пещеру.");
                    Console.WriteLine("2. Отказаться от затеи и уйти.");

                    string choice1 = Console.ReadLine();
                    switch (choice1)
                    {
                        case "1":
                            currentState = "Step2"; // переход в главный зал
                            break;
                        case "2":
                            currentState = "Ending_Coward"; // переход к концовке
                            break;
                        default:
                            Console.WriteLine("Неверный ввод.");
                            break;
                    }
                    break;

                // шаг 2: главный зал
                case "Step2":
                    Console.WriteLine("\nГлавный зал");
                    Console.WriteLine("Внутри просторный зал. В центре тускло светится синий кристалл.");
                    if (hasOrb)
                    {
                        Console.WriteLine("Основание кристалла пусто.");
                    }
                    Console.WriteLine("1. Подойти к кристаллу.");
                    Console.WriteLine("2. Пойти в левый туннель.");
                    Console.WriteLine("3. Пойти в правый туннель.");

                    string choice2 = Console.ReadLine();
                    switch (choice2)
                    {
                        case "1":
                            currentState = "Step3";
                            break;
                        case "2":
                            currentState = "Step4";
                            break;
                        case "3":
                            currentState = "Step5";
                            break;
                        default:
                            Console.WriteLine("Неверный ввод.");
                            break;
                    }
                    break;

                // шаг 3: кристалл
                case "Step3":
                    Console.WriteLine("\nКристалл");
                    if (hasOrb)
                    {
                        Console.WriteLine("Вы уже взяли Сферу. Здесь больше ничего нет.");
                    }
                    else
                    {
                        Console.WriteLine("Вы касаетесь кристалла. Он рассыпается, оставляя в руке Светящуюся Сферу.");
                        hasOrb = true; // игрок получил предмет
                        Thread.Sleep(1500);
                    }
                    currentState = "Step2"; // возврат в главный зал
                    break;

                // шаг 4: левый тунель
                case "Step4":
                    Console.WriteLine("\nЛевый туннель");
                    Console.WriteLine("Левый туннель. Вы видите надпись на стене: 'Мудрый вернется'.");
                    Console.WriteLine("1. Идти дальше, к подземному озеру.");
                    Console.WriteLine("2. Прислушаться к совету и вернуться в главный зал.");

                    string choice4 = Console.ReadLine();
                    switch (choice4)
                    {
                        case "1":
                            currentState = "Step6"; // идем к озеру
                            break;
                        case "2":
                            currentState = "Step2"; // возврат
                            break;
                        default:
                            Console.WriteLine("Неверный ввод.");
                            break;
                    }
                    break;

                // шаг 5: правый тунель
                case "Step5":
                    Console.WriteLine("\nПравый туннель");
                    Console.WriteLine("Правый туннель узок. Впереди развилка: тусклый свет или капающая вода.");
                    Console.WriteLine("1. Идти на тусклый свет.");
                    Console.WriteLine("2. Идти на звук воды.");

                    string choice5 = Console.ReadLine();
                    switch (choice5)
                    {
                        case "1":
                            currentState = "Step20"; // пауки
                            break;
                        case "2":
                            currentState = "Step21"; // безопасный путь к озеру
                            break;
                        default:
                            Console.WriteLine("Неверный ввод.");
                            break;
                    }
                    break;

                // шаг 6: подземное озеро
                case "Step6":
                    Console.WriteLine("\nПодземное озеро");
                    Console.WriteLine("Вы у большого подземного озера. В воде что-то блестит. На другом берегу виден проход.");
                    Console.WriteLine("1. Поискать что-то полезное в воде у берега.");
                    Console.WriteLine("2. Осмотреть темный берег слева.");
                    Console.WriteLine("3. Переплыть озеро к выходу.");

                    string choice6 = Console.ReadLine();
                    switch (choice6)
                    {
                        case "1":
                            currentState = "Step7"; // найти меч
                            break;
                        case "2":
                            currentState = "Step18"; // найти ключ
                            break;
                        case "3":
                            currentState = "Step8"; // переплыть
                            break;
                        default:
                            Console.WriteLine("Неверный ввод.");
                            break;
                    }
                    break;

                // шаг 7: поиск в воде (меч)
                case "Step7":
                    Console.WriteLine("\nДно озера");
                    if (hasSword)
                    {
                        Console.WriteLine("Вы уже обыскали это место.");
                    }
                    else
                    {
                        Console.WriteLine("Вы шарите по дну и находите старый, но крепкий меч!");
                        hasSword = true; // игрок получил предмет
                    }
                    currentState = "Step6"; // возврат к берегу 
                    break;

                // шаг 8: другая сторона озера
                case "Step8":
                    Console.WriteLine("\nДальний берег");
                    Console.WriteLine("Вы перебрались через озеро. Перед вами две двери: старая деревянная и прочная металлическая.");
                    Console.WriteLine("1. Открыть деревянную дверь.");
                    Console.WriteLine("2. Открыть металлическую дверь.");

                    string choice8 = Console.ReadLine();
                    switch (choice8)
                    {
                        case "1":
                            currentState = "Step9"; // деревянная дверь
                            break;
                        case "2":
                            currentState = "Step10"; // металлическая дверь
                            break;
                        default:
                            Console.WriteLine("Неверный ввод.");
                            break;
                    }
                    break;

                // шаг 9: деревянная дверь
                case "Step9":
                    Console.WriteLine("\nДеревянная дверь");
                    if (hasRuneKey) // проверка, есть ли у игрока ключ
                    {
                        Console.WriteLine("На двери вы видите рунический замок. Ваш Рунический Ключ идеально подходит!");
                        Console.WriteLine("Дверь открывается в тайный проход.");
                        currentState = "Step19"; // secret
                    }
                    else
                    {
                        Console.WriteLine("Дверь не заперта. Вы толкаете ее, и пол уходит из-под ног!");
                        currentState = "Ending_Void"; // концовка 
                    }
                    break;

                // шаг 10: металлическая дверь
                case "Step10":
                    Console.WriteLine("\nКомната Стража");
                    Console.WriteLine("Металлическая дверь ведет в комнату, где спит древний каменный страж.");
                    Console.WriteLine("1. Попытаться тихо прокрасться мимо.");
                    Console.WriteLine("2. Попытаться разбудить стража и поговорить.");
                    Console.WriteLine("3. Атаковать спящего стража.");

                    string choice10 = Console.ReadLine();
                    switch (choice10)
                    {
                        case "1":
                            currentState = "Step11"; // прокрасться
                            break;
                        case "2":
                            currentState = "Step12"; // разбудить
                            break;
                        case "3":
                            currentState = "Step16"; // атаковать
                            break;
                        default:
                            Console.WriteLine("Неверный ввод.");
                            break;
                    }
                    break;

                // шаг 11: прокрасться
                case "Step11":
                    Console.WriteLine("\nУспешный 'стелс'");
                    Console.WriteLine("Вам удается тихо проскользнуть мимо стража. Вы видите выход в следующий зал.");
                    currentState = "Step13"; // финальный зал
                    break;

                // шаг 12: разбудить
                case "Step12":
                    Console.WriteLine("\nСтраж пробудился");
                    Console.WriteLine("Страж просыпается! Его каменные глаза фокусируются на вас.");
                    Console.WriteLine("1. Попытаться поговорить с ним.");
                    Console.WriteLine("2. Атаковать его в прямом бою.");

                    string choice12 = Console.ReadLine();
                    switch (choice12)
                    {
                        case "1":
                            currentState = "Step17"; // поговорить
                            break;
                        case "2":
                            if (hasSword)
                            {
                                currentState = "Ending_BraveDeath"; // концовка (смерть в бою)
                            }
                            else
                            {
                                currentState = "Ending_Captured"; // концовка (плен)
                            }
                            break;
                        default:
                            Console.WriteLine("Неверный ввод.");
                            break;
                    }
                    break;

                // шаг 13: финальный зал
                case "Step13":
                    Console.WriteLine("\nЗал с Артефактом");
                    Console.WriteLine("Вы в последнем зале. Здесь на алтаре лежит искомый артефакт.");
                    Console.WriteLine("Он охраняется мерцающим магическим барьером.");
                    currentState = "Step14"; // проверка барьера
                    break;

                // шаг 14: барьер
                case "Step14":
                    Console.WriteLine("\nМагический барьер");
                    Console.WriteLine("Барьер требует энергии для отключения.");
                    Thread.Sleep(1000);
                    if (hasOrb) // проверка, есть ли у игрока Сфера
                    {
                        Console.WriteLine("Вы используете Светящуюся Сферу! Она врезается в барьер и разрушает его!");
                        currentState = "Step15"; // к артефакту
                    }
                    else
                    {
                        Console.WriteLine("У вас нет источника энергии, способного разрушить барьер.");
                        Console.WriteLine("Выход закрыт, вы заперты здесь навсегда.");
                        currentState = "Ending_Trapped"; // концовка
                    }
                    break;

                // шаг 15: артефакт
                case "Step15":
                    Console.WriteLine("\nАртефакт");
                    Console.WriteLine("Барьер пал. Вы берете артефакт. Он... пульсирует темной энергией.");
                    Console.WriteLine("Пещера начинает сильно трястись!");
                    Console.WriteLine("1. Попытаться обуздать его силу (требуется Светящаяся Сфера).");
                    Console.WriteLine("2. Бросить его и бежать к выходу.");

                    string choice15 = Console.ReadLine();
                    switch (choice15)
                    {
                        case "1":
                            if (hasOrb) // сфера нужна дважды
                            {
                                currentState = "Ending_Victory"; // концовка
                            }
                            else
                            {
                                // сюда можно попасть, если отдать сферу стражу
                                currentState = "Ending_Corrupted"; // концовка
                            }
                            break;
                        case "2":
                            currentState = "Ending_EmptyHanded"; // концовка
                            break;
                        default:
                            Console.WriteLine("Неверный ввод.");
                            break;
                    }
                    break;

                // шаг 16: атаковать
                case "Step16":
                    Console.WriteLine("\nАтака на спящего");
                    if (hasSword)
                    {
                        Console.WriteLine("Вы вонзаете меч в трещину в камне. Страж рассыпается в пыль, не просыпаясь.");
                        currentState = "Step11"; // путь чист
                    }
                    else
                    {
                        Console.WriteLine("Вы бьете его кулаком. Это его только злит. Он просыпается и хватает вас.");
                        currentState = "Ending_Captured"; // концовка
                    }
                    break;

                // шаг 17: говорить
                case "Step17":
                    Console.WriteLine("\n17: Диалог со Стражем");
                    Console.WriteLine("Страж говорит: 'Только достойный пройдет... или тот, кто заплатит цену.'");
                    if (hasOrb)
                    {
                        Console.WriteLine("'...вижу, у тебя есть Сфера Света. Отдай ее мне, и я пропущу тебя.'");
                        Console.WriteLine("1. Отдать Сферу.");
                        Console.WriteLine("2. Отказаться.");
                        string choice17 = Console.ReadLine();
                        if (choice17 == "1")
                        {
                            Console.WriteLine("Вы отдаете Сферу. Страж отступает в тень.");
                            hasOrb = false; // игрок теряет предмет
                            currentState = "Step11"; // проходим дальше
                        }
                        else
                        {
                            Console.WriteLine("'Тогда ты не пройдешь!' - Страж хватает вас.");
                            currentState = "Ending_Captured";
                        }
                    }
                    else
                    {
                        Console.WriteLine("'...у тебя нет ничего, что мне нужно. Ты не достоин.'");
                        currentState = "Ending_Captured";
                    }
                    break;

                // шаг 18: поиск на берегу
                case "Step18":
                    Console.WriteLine("\nБерег озера");
                    if (hasRuneKey)
                    {
                        Console.WriteLine("Вы уже обыскали этот берег.");
                    }
                    else
                    {
                        Console.WriteLine("В тени у кромки воды вы находите старую сумку. Внутри - Рунический Ключ!");
                        hasRuneKey = true; // игрок получил предмет
                    }
                    currentState = "Step6"; // возвращаемся к озеру
                    break;

                // шаг 19: тайный проход
                case "Step19":
                    Console.WriteLine("\nТайный проход");
                    Console.WriteLine("Тайный проход выводит вас в обход стража и магического барьера!");
                    Console.WriteLine("Вы выходите прямо к алтарю с артефактом.");
                    Console.WriteLine("Вы хватаете его... и тут же решетка падает, запирая вас. Это была ловушка для воров.");
                    currentState = "Ending_Greed"; // концовка
                    break;

                // шаг 20: туннель пауков
                case "Step20":
                    Console.WriteLine("\nЛогово пауков");
                    Console.WriteLine("Тусклый свет - это гнездо гигантских пещерных пауков. Они набрасываются на вас!");
                    if (hasSword)
                    {
                        Console.WriteLine("Вы отбиваетесь мечом и, получив несколько укусов, пробегаете мимо к озеру.");
                        currentState = "Step6"; // добрались до озера
                    }
                    else
                    {
                        Console.WriteLine("Без оружия у вас нет шансов. Пауки одолевают вас.");
                        currentState = "Ending_Spiders"; // концовка
                    }
                    break;

                // шаг 21: туннель с водой
                case "Step21":
                    Console.WriteLine("\n[Шаг 21: Мокрый туннель]");
                    Console.WriteLine("Вы идете на звук капающей воды и благополучно выходите к подземному озеру.");
                    currentState = "Step6";
                    break;


                

                case "Ending_Coward": // концовка 1
                    Console.WriteLine("\nТРУС");
                    Console.WriteLine("Вы вернулись домой. Приключение окончено, артефакт остался в пещере.");
                    gameIsRunning = false;
                    break;

                case "Ending_Void": // концовка 2
                    Console.WriteLine("\nПАДЕНИЕ");
                    Console.WriteLine("Вы упали в бездну и погибли. Ваш крик затерялся во тьме.");
                    gameIsRunning = false;
                    break;

                case "Ending_Captured": // концовка 3
                    Console.WriteLine("\nПЛЕННИК");
                    Console.WriteLine("Страж пленил вас. Вы проведете остаток жизни в темнице пещеры.");
                    gameIsRunning = false;
                    break;

                case "Ending_Trapped": // концовка 4
                    Console.WriteLine("\nВ ЗАПАДНЕ");
                    Console.WriteLine("Вы заперты в последнем зале, не в силах преодолеть барьер. Конец пути.");
                    gameIsRunning = false;
                    break;

                case "Ending_Victory": // концовка 5
                    Console.WriteLine("\nИСТИННЫЙ ПОБЕДИТЕЛЬ");
                    Console.WriteLine("Сфера Света в вашей руке борется с тьмой артефакта. Вы подчиняете его себе!");
                    Console.WriteLine("Вы выбрались из пещеры с артефактом. Вы герой!");
                    gameIsRunning = false;
                    break;

                case "Ending_BraveDeath": // концовка 6 
                    Console.WriteLine("\nСМЕРТЬ ХРАБРЫХ");
                    Console.WriteLine("Вы атакуете стража. Ваш меч отскакивает от камня, а страж в ответ сокрушает вас.");
                    Console.WriteLine("Вы погибли, но сражались.");
                    gameIsRunning = false;
                    break;

                case "Ending_Greed": // концовка 7 
                    Console.WriteLine("\nЖАДНОСТЬ");
                    Console.WriteLine("Вы нашли хитрый путь, но он оказался ловушкой для тех, кто ищет легкой наживы.");
                    Console.WriteLine("Вы заперты с артефактом, который теперь бесполезен.");
                    gameIsRunning = false;
                    break;

                case "Ending_Spiders": // концовка 8
                    Console.WriteLine("\nОБЕД");
                    Console.WriteLine("Вы отважно вошли в туннель без оружия. Пауки были рады свежему мясу.");
                    gameIsRunning = false;
                    break;

                case "Ending_Corrupted": // концовка 9
                    Console.WriteLine("\nПОГЛОЩЕНИЕ");
                    Console.WriteLine("У вас нет Сферы Света, чтобы противостоять тьме. Артефакт поглощает ваш разум.");
                    Console.WriteLine("Вы стали новым 'стражем' этой пещеры.");
                    gameIsRunning = false;
                    break;

                case "Ending_EmptyHanded": // концовка 10
                    Console.WriteLine("\nС ПУСТЫМИ РУКАМИ");
                    Console.WriteLine("Вы бросаете артефакт. Раздается взрыв! Вы едва успеваете выбраться из пещеры живым.");
                    Console.WriteLine("Артефакт уничтожен, но вы выжили.");
                    gameIsRunning = false;
                    break;
            }
        } 
    }
}
```
