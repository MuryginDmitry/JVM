# JVM


    public class JvmComprehension {

    public static void main(String[] args) {
        int i = 1;                      // 1 В стеке, в фрейме Main() создается переменная "i" и ей присваевается значение "1" 
        Object o = new Object();        // 2 Выделяется место в куче под объект Object и выполнится конструктор, создётся объект Object в куче. В стеке, в фрейме Main() создается переменная "o" содержащая ссылку на Object в куче
        Integer ii = 2;                 // 3 В стеке, в фрейме Main() создается переменная "2" упаковывается в объект Integer, который затем инициализируется в куче. Ссылка на этот объект присваивается переменной "ii" в стеке, в фрейме Main().
        printAll(o, i, ii);             // 4 Осуществляется вызов метода printAll и в стеке создается фрейм printAll(), в ней добавляются переменные "i" со значением "1" ,"o","ii" с ссылкой на объекты в куче  
        System.out.println("finished"); // 7 После завершения вызова метода printAll() фрейм удаляется из стека.Создается новый фрейм в стеке до окончания его выполнения. Результат вызова методв выводится на экран. Так как далее завершается метод main, то фрейм Main() удаляется из стека
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5 В стеке, в фрейме printAll() создается переменная "700" упаковывается в объект Integer, который затем инициализируется в куче. Ссылка на этот объект присваивается переменной "uselessVar" в стеке, в фрейме printAll(). Однако этот объект никак не используется в коде, поэтому он сразу же становится доступным для сборки мусора.
        System.out.println(o.toString() + i + ii);  // 6 Создается новый фрейм в стеке до окончания его выполнения. Результат вызова методв выводится на экран
    }
    }

При запуске программы, JVM загружает все необходимые классы, используя механизмы ClassLoader'ов. В данном случае, это загрузка классов стандартной библиотеки Java, которые используются в программе.

В данном коде объекты o, uselessVar и ii будут удалены автоматически после выполнения метода printAll, так как на них больше не осталось ссылок и они не будут использованы далее в программе. 
