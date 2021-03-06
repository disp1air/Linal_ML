### Модели нейронов  
Нейрон - единица обработки информации в нейронной сети.  

![img_1](https://user-images.githubusercontent.com/35499834/40886692-7afb6b64-6745-11e8-9894-c00ff52df06c.png)  

В этой модели можно выделить 3 основных элемента:  
 - **Набор** синапсов и связей, каждый из которых характеризуется своим весом или силой. В отличие от синапсов мозга синаптический вес искусственного нейрона может иметь как положительные, так и отрицательные значения.  
 - **Сумматор** складывает входные сигналы, взвешенные относительно соответствующих синапсов нейрона.  
 - **Функция активации** - ограничивает амплитуду выходного сигнала нейрона. Обычно нормализованный диапазон амплитуд выхода нейрона лежит в интервале [0, 1] или [-1, 1].  

Так же присутствует **пороговый элемент (bias)** - эта величина отражает увеличение или уменьшение входного сигнала, подаваемого на функцию активации.  

![img_2](https://user-images.githubusercontent.com/35499834/40886919-2456455a-6749-11e8-9c4d-ca3da231a687.png)  

Индуцированное локальное поле или потенциал активации - подается на вход функции активации(ее аргумент)

принимая во внимание выражение (1.3), формулы (1.1),(1.2) можно преобразовать к следующему виду:  

![img_3](https://user-images.githubusercontent.com/35499834/40887050-29454fbe-674b-11e8-92f3-f985c6d7206c.png)

Это позволило преобразовать модель нейрона к следующему виду:  

![img_4](https://user-images.githubusercontent.com/35499834/40887065-6075ec28-674b-11e8-976e-bbba68dfb4b7.png)

### Типы функций активации
 * Функция единичного скачка - в технической литературе эта форма обычно называется функцией Хэвисайда.  
 * Кусочно-линейная функция
 * Сигмоидальная функция - является, пожалуй, самой распространенной функцией, используемой для создания искусственных нейронных сетей. Примером может служить **логистическая функция** задаваемая следующим выражением:  

![formula](http://latex.codecogs.com/gif.latex?\dpi{120}&space;\varphi&space;(\upsilon)=\frac{1}{1&plus;\exp(-a\upsilon&space;)})  где a-параметр наклона сигмоидальной функции. Изменяя этот параметр, можно построить функции с различной крутизной.  

![logistic_func](https://user-images.githubusercontent.com/35499834/41794390-e446be12-7667-11e8-89af-6b647ddfddc7.png)  

В пределе, когда параметр наклона достигает бесконечности, сигмоидальная функция вырождается в пороговую.

Следует заметить что сигмоидальная функция является дифференцируемой, в то время как пороговая - нет. Дифференцируемость активационной функции играет важную роль в теории нейронных сетей.  

Иногда требуется функция активации, имеющая область значений [-1, 1]. Эта функция называется сигнум, в данном случае сигмоидальная функция будет иметь форму **гиперболического тангенса**  

### Стохастическая(вероятностная) модель нейрона  
Ранее показанная модель является **детерминистской** - преобразование входного сигнала в выходной точно определено для всех значений входного сигнала. Однако в некоторых приложениях лучше использовать стохастическую нейросетевую модель, в которой функция активации имеет вероятностную интерпретацию. В подобных моделях нейрон может находиться  в одном из двух состояний: +1 или -1. Решение о переключении состояния нейрона принимается с учетом вероятности этого события.  

![img_5](https://user-images.githubusercontent.com/35499834/40887837-39ed8488-6757-11e8-8395-6e23d5dec85d.png)

T - аналог температуры,используемый для управления уровнем шума, и таким образом, степенью неопределенности переключения. Параметр Т управляет термальными флуктуациями, представляющими эффект синаптического шума.  

### Обратная связь  
Понятие обратной связи характерно для динамических систем, в которых выходной сигнал некоторого элемента системы оказывает влияние на входной сигнал этого элемента. Таким образом, некоторые внешние сигналы усиливаются сигналами, циркулирующими внутри системы. Обратная связь играет важную роль в изучении **рекуррентных нейросетей**.  

обратная связь ??????

### Архитектура сетей.  
Можно выделить три фундаментальных класса нейросетевых архитектур:
 - **однослойные сети прямого распространения**. В простейшем случае в сети существует входной слой узлов источника, информация от которого передается на выходной слой нейронов(вычислительные узлы), но не наоборот. Такая сеть называется сетью прямого распространения или ацикличной сетью. Сеть называется однослойной т.к. содержит единственный слой вычислительных элементов(нейронов). При подсчете числа слоев не принимаются во внимание узлы источника, т.к. они не выполняют никаких вычислений.  
 - **многослойные сети прямого распространения**. Характеризуется наличием одного или нескольких скрытых слоев, узлы которых называются скрытыми нейронами. Их функция - посредничество между внешним входным сигналом и выходом нейронной сети. Добавляя один или несколько скрытых слоев, мы можем выделить статистики высокого порядка. Такая сеть позволяет выделять глобальные свойства данных с помощью локальных соединений за счет наличия дополнительных синаптических связей и повышения уровня взаимодействия нейронов. Выходные сигналы второго слоя используются в качестве входных для третьего слоя и т.д.

![fully connected](https://user-images.githubusercontent.com/35499834/40888578-ff0cf974-6761-11e8-8e23-740a97c80ed8.png)  

Сеть выше называется сетью 10-4-2, т.к. имеет 10 входных, 4 скрытых и 2 выходных нейрона. Так же эта сеть является полносвязной, т.к. все узлы каждого конкретного слоя соединены со всеми узлами смежных слоев. Если некоторые из синаптических связей отсутствуют - неполносвязная сеть.

 - **рекуррентные сети** - отличается от сети прямого распространения наличием по крайней мере одной обратной связи.
 Может состоять из единственного слоя нейронов, каждый из которых направляет свой выходной сигнал на входы всех остальных нейронов слоя.  

 ![img_6](https://user-images.githubusercontent.com/35499834/40888683-67ef829e-6763-11e8-9487-25c6e7c58ae0.png)

В приведенной выше структуре отсутствуют обратные связи нейронов с самими собой.

Еще один пример ниже - рекуррентные сети со скрытыми нейронами. Здесь обратные связи исходят как из скрытых, так и из выходных нейронов.  

![img_7](https://user-images.githubusercontent.com/35499834/40888731-f7af81d6-6763-11e8-9f08-6457f645c6d7.png)  

Наличие обратных связей в сетях, оказывает непосредственное влияние на способность таких сетей к обучению и на их производительность. Более того, обратная связь подразумевает использование элементов единичной задержки, что приводит к нелинейному динамическому поведению, если, конечно в сети содержатся нелинейные нейроны.  

### Представление знаний.  
п.1.7, стр.58  

