# lr
//Створіть метод, який дозволяє модифікувати елементи будь якого масиву int[],
// використовуючи кожний елемент масиву, як аргумент
// певної функції( f(x)=3*x*x+5*x-21 наприклад).
// Масив  та функція передаються як параметри методу.
public class Programm {
    public interface ElementModifier {
        public int GetDouble(int n);
    }

    public ElementModifier GetDouble(int n) {
        ElementModifier f1 = new ElementModifier() {
            @Override
            public int GetDouble(int n) {
                return n * 2;
            }
        };
        return f1;
    }

    public int[] NewArray(int[] arr, ElementModifier nM) {
        int[] tarr = new int[arr.length];
        for (int i = 0; i < arr.length; i++) {
            tarr[i] = nM.GetDouble(arr[i]);
        }
        return tarr;
    }

    public int[] RandArray(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            arr[i] = (int) (Math.random() * 50);
        }

        return arr;
    }

    public static void main(String args[]) {
        Programm p = new Programm();
        int[] arr = new int[10];
        arr = p.RandArray(arr);
        ElementModifier m = p.GetDouble(0);
        arr = p.NewArray(arr, m);
        for (int i = 0; i < arr.length; i++) {
            System.out.print(" " + arr[i]);
        }
        System.out.println();
    }
}


//Створіть метод, який дозволяє сортувати масив Студентів у відповідності до критерію сортування(за віком, за прізвищем та інше).
// Масив та критерій сортування  передаються як критерії методу.
// Сортування реалізувати методом =бульбашки=
public class Student{
    int age;
    String name;

    public Student(int age, String name) {
        this.age = age;
        this.name = name;
    }
    String getName(){
        return name;
    }
    @Override
    public String toString() {
        return "Student{" + "age= " + age
                + ", name =" + name
                + ", '\''+'}';
    }
    public static void main(String[] args) {
        Comparator<Student> com1 = new Comparator<Student>() {
            @Override
            public int compare(Student o1, Student o2) {
                return o1.age - o2.age;
         }
        };
    }

    void sort(Student[] grup, Comparator<Student> comp) {
        int counter = 0;
        do {
            counter = 0;
            for (int i = 0; i < grup.length - 1; i++) {
                if (comp.compare(grup[i], grup[i + 1]) > 0) {
                    counter++;
                    swipe(i, i + 1, grup);
                }
            }
        } while (counter > 0);  }
    private void swipe(int i, int i1, Student[] grup) {
    }
}
//Створіть тестовий приклад, який демонструє використання інтерфейсу у якості локальної змінної,
// параметра методу,
// у якості повертаємого значення.
class Program{

    public static void main(String[] args) {

        Publishing publishing = createPublish("Stars of the world",false);
        publishing.print();

        read(new Book("Red and black", "Stendal"));
        read(new Magazine("Top models"));
    }

    static void read(Publishing p){

        p.print();
    }

    static Publishing createPublish(String name, boolean option){

        if(option)
            return new Book(name, "Undefined");
        else
            return new Magazine(name);
    }
}
interface Publishing {

    void print();
}
class Book implements Publishing {

    String name;
    String author;

    Book(String name, String author) {

        this.name = name;
        this.author = author;
    }

    public void print() {

        System.out.printf("name " + name + "author+ " + author);
    }

}
