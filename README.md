    public class JvmComprehension {
    public static void main(String[] args) {
        int i = 1;                      // 1
        Object o = new Object();        // 2
        Integer ii = 2;                 // 3
        printAll(o, i, ii);             // 4
        System.out.println("finished"); // 7
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5
        System.out.println(o.toString() + i + ii);  // 6
    }
    }



 <span style="color:blue"> public class JvmComprehension {   </span> <span style="color:red">  // Идет подгрузка классов </span>

 <span style="color:green"> Application ClassLoader->Platform ClassLoader->Bootstrap ClassLoader</span>

 <span style="color:blue"> public static void main(String[] args) { </span><span style="color:red"> //java рантайм создает стековую память для использования метода main</span>

 <span style="color:blue">  int i = 1; // 1 </span> <span style="color:red"> //Создается интовая переменная которая хранится в стеке метода </span>


 <span style="color:blue">  Object o = new Object();   // 2 </span> <span style="color:red"> //Создается объект в куче а стековая память содержит ссылку на него</span>


 <span style="color:blue">  Integer ii = 2; // 3 </span><span style="color:red"> //Выделяется память в куче для создания объекта типа Integer  </span>

 <span style="color:blue"> printAll(o, i, ii); // 4 </span><span style="color:red"> //Создается новый фрейм для метода printAll в котором:
  1. <span style="color:red">будет создана новая ссылка на объект строки №2 </span>
  2. <span style="color:red">создастся в новом фрейме и интовая переменная i </span>
  3. <span style="color:red">будет создана новая ссылка на объект строки №3 </span>


 <span style="color:blue"> System.out.println("finished"); // 7</span><span style="color:red"> //Создается новый фрейм для работы  println </span>
  <span style="color:blue">  } private static void printAll(Object o, int i, Integer ii) {</span>

  <span style="color:blue"> Integer uselessVar 700;  // 5 </span> <span style="color:red"> //Выделяется память в куче для создания объекта типа Integer  </span>
   <span style="color:blue">System.out.println(o.toString() + i + ii);  // 6 
   1. </span> <span style="color:red">  Создается новый фрейм для работы  println </span>
   2. </span> <span style="color:red">  o.toString()- конструктор создастся новый объект </span>
  
> ###  <span style="color:green"> Метаспейс </span>
>>  ### javap-c JvmComprehension.class 
>> ### <span style="color:green">Если набрать в консоли указанную команду получим метаданные класса хранящиеся в metaspace </span>