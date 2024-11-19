# Памятка по Unity C#
***
## Переменные
Для объявления переменных используется следующий синтаксис:

**[Атрибут] МодификаторДоступа Тип Название**

<details><summary>Атрибут</summary>

----
Является не обязательным для указания, а нужен, чтобы добавить переменной какие-то свойства

Указывается внутри [ ]

Например атрибут позволяющий  сделать переменную видимой в ``инспекторе``:
```
[SerializeField]
```

----
</details>

<details><summary>Модификаторы доступа</summary>
	
----
Используется для обозначения доступности переменной из других классов (скриптов)

На данный момент используем два основных модификатора доступа

Модификатор, указывающий на то, что к нашей переменной могут обращаться извне, а также позволяющий видеть нашу переменную в окне инспектора:
```
public
```

Модификатор, скрывающий переменную от остальных классов:
```
private
```
Модификатор доступа не является обязательным атрибутом, если его не указать то будет использован модификатор ``private``

----
</details>

<details><summary>Тип</summary>

----
Указывает на тип переменной, это может быть любой доступный тип

Например, типы из C#:

* ``int`` — целое число
* ``float`` — число с плавающей точкой
* ``string`` — строка
* ``bool`` — булевое значение

Также в качестве типа может быть указано название вашего класса (скрипта)

----
</details>

<details><summary>Название</summary>

----
Используется при обращении к объявленной переменной в скрипте

Правила:
* Не может начинаться с цифры:
	* :x: `0count`
	* :x: `1234`
	* :x: `45red`
	* :heavy_check_mark: `variable5`
* Не может быть пробелов:
	* :x: `space name`
	* :heavy_check_mark: `notSpaceName`
* Не может совпадать с ключевыми словами языка
	* :x: `void`
	* :x: `if`
	* :heavy_check_mark: `ifYou`

----
</details>

#### Примеры

Целочисленная переменная с именем `count` доступная другим классам и отображаемая в инспекторе:
```
public int count;
```
Переменная с числом с плавающей точкой с именем `speed`, доступная другим классам и отображаемая в инспекторе:
```
public float speed;
```

Переменная, ссылающаяся на объект сцены `GameObject`, не доступная другим классам, но отображаемая в инспекторе:
```
[SerializeField] private GameObject target;
```

Логическая переменная, не доступная другим классам и не отображаемая в инспекторе:
```
private bool isCheck;
```

## Методы
Для объявления метода требуеться тело:
<details><summary>Правильное объявления метода в теле</summary>
	
```
public class ClassName: MonoBehaviour
{
    // Объявление метода с телом
    public void FunctionName()
    {
        // Тело метода
        Debug.Log("Этот метод выполняется.");
    }
}
```

</details>


Синтаксис написания метода: **МодификаторДоступа ВозвращаемыйТип Название (Аргумент)**

<details><summary>Создание локальной перемменной в методе</summary>

----
Локальной переменная - это переменная, которая существует внутри метода.

Она используются для хранения временных данных, которые не нужны вне этого метода. Создаются при входе в метод и уничтожаются при выходе из него.

**Пример**

```
public class ClassName0 : MonoBehaviour
{
	public void FunctionName() 
	{
		int id = 1 + 5; 
		Debug.Log(id);
	}
	private void Start()
	{
		FunctionName();
	}
}
```

----

</details>

<details><summary>Модификаторы доступа</summary>

----

`public` - доступен из любого места кода

**Пример**
```
public class ClassName0 : MonoBehaviour
{
	public void FunctionName() 
	{
		int id = 1; 
		Debug.Log(id);
	}
}
public class ClassName1 : MonoBehaviour
{
	public ClassName0 _className0; //Привязываем код в инспекторе
	private void Start
	{
		_className0.FunctionName(); //Вызов метода из скрипта ClassName0
	}
	
}

```
`private`- доступен только внутри класса

**Пример**
```
public class ClassName : MonoBehaviour
{
	private void FunctionName() 
	{
		int id = 1;
		Debug.Log(id);
	}

	private void Start()
	{
		FunctionName(); //Вызов метода
	}
}
```
<details><summary>Дополнительно</summary>
	
`protected` - доступен только классам-наследникам

**Пример**
```
public class ClassName : MonoBehaviour //родитель
{
	protected void FunctionName() 
	{
		int id = 1;
		Debug.Log(id);
	}

}

public class ClassName0 : ClassName //наследн
{
	private void Start()
	{
		FunctionName();
	}

}
```

</details>

----

</details>

<details><summary>Возвращаемый тип</summary>

----

* `void` — это тип метода, который ничего не возвращает 

* `bool` — это тип метода, который возвращает только true (Правда) или false (Ложь)

* `int` — это тип метода, который возвращает целое число (Пример: 2)

* `flout` — это тип метода, который возвращает число с плавающей запятой (137.5f == 137,52323)
  
* `string` — это тип метода, который  просто возвращает текст
  
<details><summary>Примеры</summary> 
	
```
public class ClassName : MonoBehaviour
{
	public void FunctionName() 
	{
		Debug.Log("Hello, World!");
	}
	private void Start()
	{
		FunctionName();
	}
}
```

```
public class ClassName : MonoBehaviour
{

	public bool FunctionName()
	{
		return  false;
	}

	private void Start()
	{
		if (FunctionName()==false) //Проверка 
		{
			Debug.Log("Мы получили " + FunctionName());
		}
		else
		{
			Debug.Log("Мы ничего не получили");
		}
		
	}

}
```

```
public class ClassName : MonoBehaviour
{
	public int money = 15;
	public int FunctionName()
	{
		return  10; 
	}

	private void Start()
	{
		if (FunctionName() <= money) //Проверка 
		{
			Debug.Log("Сумма " + FunctionName() + " и у вас " + money + " денег.");
		}
		else
		{
			Debug.Log($"У вас {money} денег, и вам их не хватает.");
		}
	}
}
```

```
public class ClassName : MonoBehaviour
{
	public flout FunctionName()
	{
	        return 127.5f;
	}
	private void Start()
	{
		if (FunctionName() <= 130)
		{
			Debug.Log("Всё работает " + FunctionName());
		}
	}
}
```

</details>

----

</details>

<details><summary>Название</summary>

----
Используется при обращении к объявленном методе в скрипте

Правила:
* Не может начинаться с цифры:
	* :x: `0count`
	* :x: `1234`
	* :x: `45red`
	* :heavy_check_mark: `variable5`
* Не может быть пробелов:
	* :x: `space name`
	* :heavy_check_mark: `notSpaceName`
* Не может совпадать с ключевыми словами языка
	* :x: `void`
	* :x: `if`
	* :heavy_check_mark: `ifYou`

----
</details>

<details><summary>Аргумент</summary>

----

Являеться не обязательным. Нужен для передачи данных в метод или функцию.

В методе может быть несколько аргументов

<details><summary>Пример</summary>
	
```
public class ClassName : MonoBehaviour
{
    public void ShowMessage(string message, int number)
    {
        Debug.Log(message + " " + number);
    }

    private void Start()
    {
        ShowMessage("Привет", 42); // Вывод: "Привет 42"
    }
}
```
</details>
	
Примитивные типы данных аргументов
* ``int`` — целое число
* ``float`` — число с плавающей точкой
* ``string`` — строка
* ``bool`` — булевое значение

<details><summary>Примеры примитивных типов данных</summary>


```
public class ClassName : MonoBehaviour
{
	public int count = 17;
	public bool True = false;

	public void ShowMessage()
	{
		if (True)
		{
			Debug.Log(count);
		}
		else
		{
			Debug.Log(count);
		}
		
	}

	public void Start()
	{
		ShowMessage();
	}

}

```

```
public class ClassName : MonoBehaviour
{
    public void ShowMessage(int message)
    {
        Debug.Log(message);
    }

    public void ShowMessage(float message)
    {
        Debug.Log(message);
    }

    public void ShowMessage(string message)
    {
        Debug.Log(message);
    }

    public void ShowMessage(bool message)
    {
        Debug.Log(message);
    }

    private void Start()
    {

        ShowMessage(7.5f);
	ShowMessage(7);
        ShowMessage("Hello!");
	ShowMessage(true);
    }
}

```
</details>


----
</details>

	
<details><summary>Прервать метод</summary>
	
----
	
Для прерывания метода мы используем ``return`` - это ключевое слово, которое используется для завершения выполнения метода или возврата значения из этого метода.

<details><summary>Пример</summary>

```
public class ClassName : MonoBehaviour
{
	public int playerMoney = 50; // Количество денег
	public int itemCost = 30;  // Стоимость предмета

	// Метод для проверки, может ли игрок купить предмет
	public bool CanPurchaseItem()
    	{
	        // Если у игрока достаточно денег, возвращаем true
	        if (playerMoney >= itemCost)
	        {
	            return true; // Выход из метода с значением true
	        }
	        else
	        {
	            return false; // Выход из метода с значением false
	        }
    	}

     	private void Start()
     	{
	        // Проверяем, может ли игрок купить предмет
	        if (CanPurchaseItem()) // Для понимания это то же самое что и CanPurchaseItem()==true
	        {
	            Debug.Log("Вы можете купить предмет!");
	        }
	        else
	        {
	            Debug.Log("У вас недостаточно денег для покупки предмета.");
	        }
    	}

}
```

</details>

----
</details>
<details><summary>Дополнительно</summary>
	
----
	
<details><summary>Перегрузка метода</summary>

----

Это возможность создавать несколько методов с одним и тем же именем, но с различными аргументами. Это позволяет использовать одно и то же имя метода для выполнения схожих, но немного различных задач. 

Перегрузка методов помогает сделать код более читаемым и удобным.
```
public class ClassName : MonoBehaviour
{
	public int FunctionName(int a, int b)
	{
	        return a + b;
	}

	public float FunctionName(float a, float b)
	{
	        return a + b;
	}
	
	public int FunctionName(int a, int b, int c)
	{
	        return a + b + c;
	}
	public string FunctionName(string a, string b)
	{
		string с = " - это дополнительный текст"
	        return a + b + c;
	}
	private void Start()
	{
		int sumInt = FunctionName(5,6);
		float sumFloat = FunctionName(2.5f, 3.5f);
		int sumThreeInts = FunctionName(1, 2, 3);
		string stringText = FunctionName("Привет ", "мир");
		Debug.Log("Сумма двух целых чисел: " + sumInt);
	        Debug.Log("Сумма двух чисел с плавающей запятой: " + sumFloat);
	        Debug.Log("Сумма трех целых чисел: " + sumThreeInts);
		Debug.Log(stringText);
	}
}

```

----
</details>

----

</details>

</details>



## Условия

```
if (условие1)
{
	// Код, выполняемый, если условие1 истина
}
else if (условие2) 
{
	// Код, выполняемый, если условие1 = ложь, но условие2 = истина
}
else if (условие3) 
{
	// Код, выполняемый, если условие2 = ложь, но условие3 = истина
}
else 
{
	// Код, выполняемый, если все условия ложные
}
```
