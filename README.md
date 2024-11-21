<h1 align="center">Памятка по Unity C#</h1>
 

## Переменные
Для объявления переменных используется следующий синтаксис:

**[Атрибут] МодификаторДоступа Тип Название**

<details><summary><h3>Атрибут</h3></summary>

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
Синтаксис написания метода: **МодификаторДоступа ВозвращаемыйТип Название (Аргумент)**

`void` — это специальный тип методов, который говорит, что метод ничего не возвращает 
```
public void FunctionName() 
{
	// Код выполняемый функцией
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

<details><summary>Прервать метод</summary>
	
----
	
Для прерывания метода мы используем ``return`` - это ключевое слово, которое используется для завершения выполнения метода или возврата значения из этого метода.

<details><summary>Пример</summary>

```
	public int money = 50; // Количество денег
	public int itemCost = 30;  // Стоимость предмета

	public void CanPurchaseItem()
    	{
		int quantity = money - itemCost; // сколько осталось
		Debug.Log("У вас осталось "+quantity+" рублей");
		return; // Метод завершиться, код ниже выполнен не будет
		
		int returned = quantity+money; // сколько вернули
		Debug.Log("Вам вернули "+returned+" рублей");
    	}

     	private void Start()
     	{
		CanPurchaseItem();
    	}
```

</details>

----

</details>

<details><summary>Возвращаемый тип</summary>

----

* `bool` — это тип метода, который возвращает только true (Правда) или false (Ложь)

* `int` — это тип метода, который возвращает целое число (Пример: 2)

* `float` — это тип метода, который возвращает число с плавающей запятой (137.5f == 137,52323)
  
* `string` — это тип метода, который  просто возвращает текст
  
<details><summary>Примеры</summary> 
	
```
public class ClassName : MonoBehaviour
{

	public bool FunctionName()
	{
		return  false;
	}

	private void Start()
	{

		Debug.Log("Мы получили " + FunctionName());
		
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
		Debug.Log("Сумма " + FunctionName() + " и у вас " + money + " денег.");
	}
}
```

```
public class ClassName : MonoBehaviour
{
	public float FunctionName()
	{
	        return 127.5f;
	}
	private void Start()
	{

	Debug.Log("Всё работает на " + FunctionName()+ " %");
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
    public void ShowMessage(string message, int number)
    {
        Debug.Log(message + " " + number);
    }

    private void Start()
    {
        ShowMessage("Привет", 42); // Вывод: "Привет 42"
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
    public void ShowMessage(int message)
    {
        Debug.Log(message);
    }
    private void Start()
    {
        ShowMessage(7);
    }
}

```

```
public class ClassName : MonoBehaviour
{
    public void ShowMessage(float message)
    {
        Debug.Log(message);
    }
    private void Start()
    {
        ShowMessage(7.5f);
    }
}

```

```
public class ClassName : MonoBehaviour
{
    public void ShowMessage(string message)
    {
        Debug.Log(message);
    }
    private void Start()
    {
        ShowMessage("Hello!");
    }
}

```

```
public class ClassName : MonoBehaviour
{
    public void ShowMessage(bool message)
    {
        Debug.Log(message);
    }
    private void Start()
    {
        ShowMessage(true);
    }
}

```
</details>


----
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

#### Реальный пример в `Unity`

В данном примере мы приводим два скрипта.

Скрипт `Cube` содержит несколько перегруженных методов `TransformCube`. Первый метод принимает логическое значение. Он перемещает объект на заданную позицию и выводит сообщение в консоль. Второй метод принимает целое число, увеличивает его на 8 и также перемещает объект на заданную позицию. Третий метод без параметров вызывает оба предыдущих метода. Четвертый метод принимает трансформ целевого объекта и обновляет позицию куба, а затем вызывает первый метод.

Скрипт `Camera` имеет ссылку на скрипт `Cube` и содержит метод `Start`, который вызывается при старте игры. В этом методе происходит вызов методов `TransformCube`, чтобы переместить куб на начальную позицию и обновить его позицию в соответствии с позицией другого объекта.

<table>
<tr>
	
<td>
	
```
public class Cube : MonoBehaviour
{

    public bool TransformCube(bool value)
    {

        transform.position = new Vector3(10,0,10);
        value = false;
        Debug.Log("Куб теперь " + value);
        return value;
    }
    public int TransformCube(int value)
    {
        transform.position = new Vector3(15,0,15);
        value += 8;
        Debug.Log(value);
        return value;
    }
    public void TransformCube()
    {
        TransformCube(true);
        TransformCube(10);
    }
    public void TransformCube(Transform targetTransform)
    {
        transform.position = targetTransform.position;        
        Debug.Log("Позиция куба обновлена на позицию целевого объекта");
        TransformCube(true);
    }
}
```

</td>

<td>
	
```
public class Camera : MonoBehaviour
{
    public Cube cube;
    public GameObject gameCube;

    private void Start()
    {
        cube.TransformCube();
        cube.TransformCube(gameCube.transform);
    }
}
```

</td>	
</tr>
</table>

----

</details>



----

</details>

#### Примеры  :pencil2:

В программировании важно писать код, который не только работает, но и легко читается и поддерживается. Использование методов с аргументами позволяет избежать дублирования кода и делает его более универсальным. В этом примере мы рассмотрим два подхода к одной и той же задаче: один без использования методов, а другой с использованием методов, принимающих аргументы.

В первом примере (в левой колонке) код содержит несколько повторяющихся операций, что делает его менее эффективным и более трудным для изменения. Если вам когда-либо понадобится изменить значение, которое добавляется к переменной, вам придется делать это в нескольких местах.

Во втором примере (в правой колонке) мы используем метод `AddValueAndLog`, который принимает аргумент. Это позволяет нам вызывать один и тот же метод с различными значениями, избегая дублирования кода. Такой подход не только упрощает изменение логики программы, но и улучшает её читаемость.

Теперь давайте посмотрим на оба примера кода и поймем, почему второй подход является более предпочтительным.
<table>
<tr>
	
<td>
	
**Без использования методов** 

	
```

	public int number = 15;

	private void Start()
    	{
        	if (number>=10)
		{
			number+=10;
			Debug.Log(number);
		}
		else if (number<20)
		{
			number+=10;
			Debug.Log(number);
		}
		else
		{
			number+=10;
			Debug.Log(number);
		}
    	}
			
```

</td>	

  
<td>

   **Использованием методов, принимающих аргументы**
```
	public int number = 15;

	private void Start()
    	{
        	if (number>=10)
		{
			AddValueAndLog(10);
		}
		else if (number<20)
		{
			AddValueAndLog(10);
		}
		else
		{
			AddValueAndLog(10);
		}
    	}
	public void AddValueAndLog(int valueToAdd)
	{
		number += valueToAdd; // Добавляем значение к number
		Debug.Log(number); // Выводим результат в консоль
	}

	
```
</td>
</tr>
</table> 

##### Примеры 

`int FunctionName()`, который возвращает целое число `int`. 

```
public int FunctionName()
{
	return 1; //Пример
}
```

`float FunctionName()`, который возвращает число с плавающей точкой `float`.

```
public float FunctionName()
{
	return 1.2f; //Пример
}
```

`bool FunctionName()`, который возвращает булево значение `bool`, может быть `true` или `false`.

```
public bool FunctionName()
{
	return false; //Пример
}
```

`string FunctionName()`, который возвращает строку `string`.

```
public string FunctionName()
{
	return "Test"; //Пример
}
```
`int FunctionName(int name)`, который возвращает целое число `int` и принимает аргумент типа `int`.

```
public int FunctionName(int name)
{
	  return name;
}
```

 `float FunctionName(float name)`, который возвращает число с плавающей точкой `float` и принимает аргумент типа `float`.

```
public float FunctionName(float name)
{
	return name;
}
```

`bool FunctionName(bool name)`, который возвращает булево значение `bool` и принимает аргумент типа  `bool`.

```
public bool FunctionName(bool name)
{
	return name;
}
```

`string FunctionName(string name)`, который возвращает строку `string` и принимает аргумент типа `string`.

```
public string FunctionName(string name)
{
	return name;
}
```



## Условия

В `C#` есть несколько проверок условий:

* `if` - проверяет первое условие
* `else if` -  проверяет следующие условия, если предыдущее условие ложно
* `else` - выполняет блок кода, если все предыдущие условия ложны

Они делаются для проверки методов, переменных и т.д.
Давайте расмотрим их более подробно.

<details><summary>Однотипные условия</summary>

----
Это ситуации, когда вы проверяете несколько условий, относящихся к одному типу данных или логике, и выполняете одинаковые действия в зависимости от результата проверки.

**Пример**

```
	public int number = 10;
	private void Start()
	{
		if (number>0)
		{
			Debug.Log("Число положительное.");
		}
		else if (number<0)
		{
			Debug.Log("Число отрицательное.");
		}
		else
		{
			Debug.Log("Число равно нулю.");
		}
	}
```

----
</details>


<details><summary>Логические операции</summary>

Для проверки нескольких условий существует символы: 
* `&&` - означеат и
* `||` - означает или
* `!` - изначает не


**Пример**

```
	public int number = 10; //можно поменять в инспекторе 
	public bool isBool = false; //можно поменять в инспекторе 
	private void Start()
	{
		if (number>0 && isBool) // number должно быть больше нуля и isBool должен быть true
		{
			Debug.Log("1");
		}
		else if (number>0 && !isBool) //number должно быть больше нуля  isBool должен быть false
		{
			Debug.Log("2");
		}
		else if (number<0 || !isBool) //number должно быть меньше нуля или isBool должен быть false
		{
			Debug.Log("3");
		}
	}
```


</details>


<details><summary>Разные условия</summary>


</details>


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
