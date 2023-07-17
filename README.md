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

  public class JvmComprehension   // Идет подгрузка классов 

  Application ClassLoader->Platform ClassLoader->Bootstrap ClassLoader

  public static void main(String[] args) {  //java рантайм создает стековую память для использования метода main

------------------------------------1------------------------------------------------



  int i = 1; // 1  //Создается интовая переменная которая хранится в стеке метода </

------------------------------------2------------------------------------------------



   Object o = new Object();   // 2  //Создается объект в куче а стековая память содержит ссылку на него

------------------------------------3------------------------------------------------



 < Integer ii = 2; // 3 //Выделяется память в куче для создания объекта типа Integer  

------------------------------------4------------------------------------------------


printAll(o, i, ii); // 4  //Создается новый фрейм для метода printAll в котором:
  1. будет создана новая ссылка на объект строки №2 
  2. создастся в новом фрейме и интовая переменная i 
  3. будет создана новая ссылка на объект строки №3 

------------------------------------7------------------------------------------------


 System.out.println("finished"); // 7
 //Создается новый фрейм для работы  println 
  } private static void printAll(Object o, int i, Integer ii) {


------------------------------------5------------------------------------------------

  Integer uselessVar 700;  // 5  //Выделяется память в куче для создания объекта типа Integer  


  ---------------------------------6-------------------------------------------------
  
   System.out.println(o.toString() + i + ii);  // 6 
   1.  Создается новый фрейм для работы  println
   2.  o.toString()- конструктор создастся новый объект 
  
> ###  Метаспейс 
>>  ### javap-c JvmComprehension.class 
>> ### Если набрать в консоли указанную команду получим метаданные класса хранящиеся в metaspace 
