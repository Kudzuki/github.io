<h1 align="center">Памятка по Unity C#</h1>

1. <a href = "#переменные" >**Переменные**</a>

	1.1 <a href = "#атрибут">Атрибут</a>

	1.2 <a href = "#модификаторы-доступа">Модификаторы доступа</a>
 
	1.3 <a href = "#тип">Тип</a>
 
 	1.4 <a href = "#название">Название</a>
  
2. <a href = "#методы">Методы</a>

	2.1 <a href = "#создание-локальной-перемменной-в-методе">Создание локальной перемменной в методе</a>

 	2.2 <a href = "#модификаторы-доступа-1">Модификаторы доступа</a>

   	2.3 <a href = "#прервать-метод">Прервать метод</a>
    
   	2.4 <a href = "#возвращаемый-тип">Возвращаемый тип</a>

   	2.5 <a href = "#название-1">Название</a>
    
   	2.6 <a href = "#аргумент">Аргумент</a>

   	2.7 <a href = "#дополнительно-1">Дополнительно</a>

3. <a href = "#условия">Условия</a>

	3.1 <a href = "#конструкция-условий">Конструкция условий</a>

	3.2 <a href = "#логические-операции">Логические операции</a>

	3.3 <a href = "#дополнительно-2">Дополнительно</a>


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

<details><summary><h3>Модификаторы доступа</h3></summary>
	
 
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

<details><summary><h3>Тип</h3></summary>

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

<details><summary><h3>Название</h3></summary>

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

**Примеры**

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

<details><summary><h3>Создание локальной перемменной в методе</h3></summary>

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

<details><summary><h3>Модификаторы доступа</h3></summary>

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
<details><summary><h3>Дополнительно</h3></summary>
	
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

<details><summary><h3>Прервать метод</h3></summary>
	
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

<details><summary><h3>Возвращаемый тип</h3></summary>

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

<details><summary><h3>Название</h3></summary>

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

<details><summary><h3>Аргумент</h3></summary>

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

<details><summary><h3>Примеры примитивных типов данных</h3></summary>



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
<details><summary><h3>Дополнительно</h3></summary>
	
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

**Реальный пример в `Unity`**

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

<details><summary>Рекурсия метода</summary>

----

Рекурсия — это метод решения задачи, при котором метод вызывает сам себя для обработки подзадач, пока не будет достигнуто базовое условие, определяющее завершение рекурсивных вызовов.

Важно помнить, что для успешного применения рекурсии необходимо определить условие, при выполнении которого рекурсия заканчивается и метод больше не вызывает саму себя, чтобы избежать бесконечных вызовов и переполнения стека.


**Пример**

```
private int FunctionName(int i)
{

        Debug.Log(i); //Вывод данных для визуализации

        if (i == 0) //Если i стало равно нулю (выход из метода)
        {
            return 0;
        }

        else if (i <= 0) // Если число i отрицательно (выход из метода)
        {
            Debug.Log("Вы не можете перебрать отрицательное число");
            return 0;
        }

        return FunctionName(i - 1);//Вызываем этот метод снова 

}

private void Start()
{
        FunctionName(10); //Задаем значение для метода
}

```

----
 
</details>

----

</details>

**Примеры  :pencil2:**

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


`int FunctionName()`, который возвращает целое число `int`. 

```
public int FunctionName()
{
	return 1; //Пример
}
```

<br>

`float FunctionName()`, который возвращает число с плавающей точкой `float`.

```
public float FunctionName()
{
	return 1.2f; //Пример
}
```

<br>

`bool FunctionName()`, который возвращает булево значение `bool`, может быть `true` или `false`.

```
public bool FunctionName()
{
	return false; //Пример
}
```

<br>

`string FunctionName()`, который возвращает строку `string`.

```
public string FunctionName()
{
	return "Test"; //Пример
}
```

<br>

`int FunctionName(int name)`, который возвращает целое число `int` и принимает аргумент типа `int`.

```
public int FunctionName(int name)
{
	  return name;
}
```

<br>

 `float FunctionName(float name)`, который возвращает число с плавающей точкой `float` и принимает аргумент типа `float`.

```
public float FunctionName(float name)
{
	return name;
}
```

<br>

`bool FunctionName(bool name)`, который возвращает булево значение `bool` и принимает аргумент типа  `bool`.

```
public bool FunctionName(bool name)
{
	return name;
}
```

<br>

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

Эти конструкции используются для того, чтобы выбрать, какой из путей кода следует выполнять на основе логического выражения.
Давайте расмотрим их более подробно.

<details><summary><h3>Конструкция условий</h3></summary>

----

После написания `if` обязательно ставим `(условие)`, так как в скобках пишется условие. Также, если вы написали `else if`, то также обязательно ставим `(условие)`.

`else if` являються обязательными после `if` и  до `else`!

Количество условий с `else if` может быть любым.

Если после этого можно вызвать `else`, делаем без условий.



**Пример**

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

----
</details>


<details><summary><h3>Логические операции</h3></summary>

----

Для проверки нескольких условий существует символы: 
* `&&` - оператор И
* `||` - оператор ИЛИ
* `!` - оператор НЕ

В представленном примере мы видим, что мы храним результат логической операции в булевой переменной.

Если хотя бы одно из условий выполнено, то булевая переменная примет значение  `true` (истина). Если же ни одно из условий не будет выполнено, то переменная получит значение `false` (ложь).

**Пример 1**

```
	public int a = 6;
    	public int w = 2;
    	void Start()
    	{
        	bool qweqw0 = a > 5 || w < 9;
        	Debug.Log("Результат qweqw0: " + qweqw0);

        	bool qweqw1 = a > 5 && w == 9;
        	Debug.Log("Результат qweqw1: " + qweqw1);

        	bool qweqw2 = a > 5 && w != 9;
        	Debug.Log("Результат qweqw2: " + qweqw2);

    	}
```

В данном примере мы используем условные операторы `if` для проверки различных условий. Давайте разберем код подробнее.

**Пример 2**

```

    	public int a = 4; // Объявляем переменную a и присваиваем ей значение 4
    	public int w = 10; // Объявляем переменную w и присваиваем ей значение 10
	void Start()
    	{
		// Проверяем, выполняется ли хотя бы одно из условий: a больше 5 или w меньше 9
        	if (a > 5 || w < 9)
        	{
			 // Если одно из условий истинно, выводим сообщение
            		Debug.Log("Результат истина");
        	}	

        	else 
        	{
			// Если оба условия ложны, выводим другое сообщение
            		Debug.Log("Результат ложь");
        	}

		// Создаем булевую переменную qweqw1, которая будет истинна только если a меньше 5 и w не равно 9
        	bool qweqw1 = a < 5 && w != 9;
        	if(qweqw1)
        	{
			// Если qweqw1 истинно, выводим сообщение
            		Debug.Log("Результат истина");
        	}
        	else
        	{
			// Если qweqw1 ложно, выводим другое сообщение
            		Debug.Log("Результат ложь");
        	}       

    	}

```

----

</details>

<details><summary><h3>Использование условий на практике</h3></summary>

----

В данных скриптах мы расмотрим применение, всего полученного материала по: `Условиям` и  `Методам`. 

<table>
<tr>
<td>

```
public class Camera : MonoBehaviour
{

    [SerializeField] private Cube cube; //  код Cube
    [SerializeField] private GameObject gameCube; // простой куб на сцене
    [SerializeField] private bool IsBool = true;  // булевая переменная

    private void Update()
    {
        if (IsBool) // Если IsBool = истина
        {
            Test(); // выполняем метод Test
        }
        else if (!IsBool) // Если IsBool = ложь
        {
            if (Input.GetMouseButtonDown(1)) // Если мы нажали на правую кнопку мыши
            {
                IsBool= true; // IsBool становиться истенной
            }
        }

    }

    private void Test() // метод 
    {
        if (Input.GetMouseButtonDown(0)) //Если мы нажали на левую кнопку мыши
        {
            if (gameCube!=null && cube!= null) // Проверяем если у нас данные об объектах 
            {
                Debug.Log("Обьект и скрипт назначены в инспекторе");
                cube.TransformCube(IsBool); // Выполняем метод из скрипта Сube
                IsBool=false;
            } 
            else
            {
                Debug.Log("Ничего не назначено");
                
            }
        }
        else if (Input.GetMouseButtonDown(1)) // Если мы нажали на правую кнопку мыши
        {   
            if (gameCube!=null && cube!= null) // Проверяем если у нас данные об объектах 
            {
                cube.ColorCube(gameCube); // Выполняем метод из скрипта Сube
            } 
            else
            {
                Debug.Log("Ничего не назначено");
            }
        }
    }
}

```

 
</td>
<td>

```

public class Cube : MonoBehaviour
{

	public bool TransformCube(bool value) // Метод для перемещения главного куба с этим кодом
    	{
        	transform.position = new Vector3(10,0,10);
		value = false;
        	Debug.Log("Куб теперь " + value);
        	return value;
    	}

    	public void TransformCube(Transform targetTransform) // Метод для позиционирования главного куба со смещением 
    	{
        	transform.position = new Vector3 (targetTransform.position.x - 5,targetTransform.position.y - 5,targetTransform.position.z - 5);        
        	Debug.Log("Позиция куба обновлена на позицию целевого объекта ");
    	}

    	public void ColorCube(GameObject gameObject) // Меняем цвет у куба, которого мы задали в сприпте Camera
    	{
        	MeshRenderer meshRenderer = gameObject.GetComponent<MeshRenderer>();
        	if (meshRenderer != null)
        	{
			if (meshRenderer.material.color == Color.red)
            		{
                		meshRenderer.material.color = Color.white;
            		}
            		else
            		{
                		meshRenderer.material.color = Color.red;
            		}
            
            	TransformCube(gameObject.transform); // Перемещаем главный куб к другому кубу (Которого мы задали в скрипте Camera)
        }
    }
}

```
 
</td>

</tr>
 
</table>



----

</details>

<details><summary><h3>Дополнительно</h3></summary>

----





----

</details>

**Примеры**

Проверка на количества здоровья у персонажа.

```

public int health = 100;

void Update()
{
	if (health > 75)
        {
            Debug.Log("Здоровье в порядке!");
        }
        else if (health > 50)
        {
            Debug.Log("Здоровье на среднем уровне.");
        }
        else if (health > 25)
        {
            Debug.Log("Здоровье низкое!");
        }
        else
        {
            Debug.Log("Персонаж на грани смерти!");
        }
}

```

Проверка на включенный буст для добавления скорости. 

```

public int baseSpeed = 5;
public bool speedBoostActive = false;
public float speedBoostMultiplier = 2.0f;

void Update()
{
	float currentSpeed = baseSpeed;

        if (speedBoostActive)
        {
            currentSpeed *= speedBoostMultiplier;
            Debug.Log("Буст скорости активен! Текущая скорость: " + currentSpeed);
        }
        else
        {
            Debug.Log("Текущая скорость: " + currentSpeed);
        }

        // Для тестирования
        if (Input.GetKeyDown(KeyCode.B))
        {
            speedBoostActive = !speedBoostActive;
        }
}

```

Проверка количества денег и времени 

```

public float time = 20;

public float money = 100;


void Start()
{
        
	bool CancelTime = time >= 100 || time < money;
        if(CancelTime)
        {
            if (money >= 100 && time==0) 
            {
                Debug.Log("Деньги есть, времени нет");
            }
            else if (money >= 100 && time>=0)
            {
                Debug.Log("Деньги есть, времени много");
            }
            else 
            {
                Debug.Log("Чего то не хватает");
            }
        }
        else
        {
            Debug.Log("Много чего не хватает");
        }   
}

```



 Скрипты дальше

```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Enemy : MonoBehaviour
{

    public float health = 100f;

    void Update()
    {

    }

    public void Damag(float damage)
    {
        if (health <= 0)
        {
            Debug.Log("Противник пал");
        }
        else if (health >= 0)
        {
            health-=damage;
            Debug.Log($"Вы нанесли {damage} урона");
            Debug.Log($"Здороья осталось {health}");
        }
    }

    public void treatment (float heal)
    {
        if (health<100)
        {
            health+= heal;
            Debug.Log($"Вы вылечили противника на {heal} здороья");
            Debug.Log($"Теперь здоровья {health}");
        }
        else
        {
            Debug.Log("Лечить не надо");
        }
        
    }
}

```

```

    public Enemy enemy;

    public float damage = 100f;


    void Update()
    {

        if (Input.GetMouseButtonDown(0))
        {
            enemy.Damag(damage);
        }
        else if (Input.GetMouseButtonDown(1))
        {
            enemy.treatment(15f);
        }
}

```

























