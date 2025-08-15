# 💡 stack 

تخيل انك بتعمل ببرجر 

بتحط أول الخبز 🍞
بعدين الخس 🥬   
بعدين الجبنة 🧀  
وآخر شي اللحمة 🍖 

لو بدك تشيل الجبنة ما بتقدر تشيلها الا لتشيل اللحمة بالاول 
بالضبط هيك مبدأ الـ
Stack

---

## 🍃 ايش ال stack ؟
هو نوع من DS بنرتّب العناصر فوق بعض، وأنت ما بتقدر توصل إلا للعنصر اللي فوق .

---
## 🍃 ايش يعني  LIFO — Last In, First Out ؟
 الستاك بنظم العناصر بطريقة LIFO يعني اول عنصر بدخل اخر عنصر بطلع يعني ما بقدر اشيل من تحت الاا لاشيل كلشيي فوقه واوصل للعنصر الي بدي اياه 

 ---

 ## 🍃 العمليات عليه :

### ⭐  Push : 
اضيف عنصر ع القائمة 
### ⭐  pop : 
اشيل و ارجع اخر عنصر
### ⭐ peek : 
 إرجاع آخر عنصر بدون حذفه. 
### ⭐ isEmpty :
 التحقق اذا القائمة فارغة او لاء 
### ⭐ size : 
 عدد العناصر 
 
![stack](stack.webp)

 ---

 ## 🍃 كود التنفيذ :
 
<pre>
 public class MyStack {
    private int[] arr;   
    private int top;    
    private int size;    

    public MyStack(int size) {
        this.size = size;
        arr = new int[size];
        top = -1;
    }

    public void push(int value) {
        if (top == size - 1) {
            System.out.println("Stack Overflow");
            return;
        }
        top++;
        arr[top] = value;
    }

    public int pop() {
        if (top == -1) {
            System.out.println("Stack Underflow");
            return -1;
        }
        int value = arr[top];
        top--;
        return value;
    }

    public int peek() {
        if (top == -1) {
            System.out.println("Stack Empty");
            return -1;
        }
        return arr[top];
    }

    public boolean isEmpty() {
        return top == -1;
    }

    public boolean isFull() {
        return top == size - 1;
    }
}


</pre>


---
 
## 🍃 امثلة ع مشاكل ممكن تصير :
 Stack Overflow و Stack Underflow 
 ### ⭐ Stack Overflow :
 📌 المعنى:
بصير لما تحاول تضيف عنصر (push) على stack حجمه ثابت والمصفوفة فيه مليانة.

🔹 السبب:
في المصفوفة الثابتة، حجمها محدد من البداية (مثلاً 5 عناصر). لو حاولت تضيف العنصر السادس → ما في مكان إضافي.

الحل : قبل ما تضيف لازم تتاكد اذا الأري فل او لاء 

 ### ⭐  Stack Underflow :
📌 المعنى:
بصير لما تحاول تحذف (pop) من stack وهو فاضي.

🔹 السبب:
لو ما في عناصر، وما زلت تطلب pop() → ما في شي ينحذف.

الحل : قبل الحذف لازم اتاكد اذا في بيانات داخل الأري او لاء 

💡 الخلاصة:

Overflow → تضيف أكثر من السعة المتاحة.

Underflow → تحذف من ستاك فاضي.

داىمًا تحقق بـ isFull() قبل push و**isEmpty()** قبل pop مشان تتفادى الأخطاء.

---

## stack with linked list :

<Pre>
public class Node {
    int data;
    Node next;

    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class LinkedListStack {
    private Node top;

    public LinkedListStack() {
        top = null; 
    }

    public void push(int value) {
        Node newNode = new Node(value);
        newNode.next = top;  
        top = newNode;       
    }
  
    public int pop() {
        if (top == null) {
            System.out.println("Stack Underflow");
            return -1;
        }
        int value = top.data;
        top = top.next;  
        return value;
    }
  
    public int peek() {
        if (top == null) {
            System.out.println("Stack Empty");
            return -1;
        }
        return top.data;
    }

    public boolean isEmpty() {
        return top == null;
    }
}
</Pre>

## شرح الكود :

لما اعمل الستاك ال top يكون null لأنه ما في عناصر.

عند push:
بعمل node جديدة 
بربط ال node الجديدة ب node القديم 
بخلي ال top يكون ال node الجديدة.

عند pop:
إذا top فارغ، يعني الستاك فاضي → Underflow.
ناخذ قيمة ال top ، ونخلي ال too يصير ال node الي بعدها (top.next).

عند peek: ببساطة نرجع قيمة ال top بدون حذفها.

isEmpty: نتحقق إذا top == null (يعني فاضي).

---

## ex:
 فحص توازن الأقواس (Balanced Parentheses)

<pre>
  public class MyStack {
    private char[] arr;
    private int top;
    private int size;

    public MyStack(int size) {
        this.size = size;
        arr = new char[size];
        top = -1;
    }

    public void push(char c) {
        if (top == size - 1) return; // overflow حماية بسيطة
        arr[++top] = c;
    }

    public char pop() {
        if (top == -1) return '\0'; // underflow حماية بسيطة
        return arr[top--];
    }

    public boolean isEmpty() {
        return top == -1;
    }

    public char peek() {
        if (top == -1) return '\0';
        return arr[top];
    }
}

public class BalancedParentheses {

    public static boolean isMatchingPair(char open, char close) {
        return (open == '(' && close == ')') ||
               (open == '{' && close == '}') ||
               (open == '[' && close == ']');
    }

    public static boolean isBalanced(String expr) {
        MyStack stack = new MyStack(expr.length());

        for (int i = 0; i < expr.length(); i++) {
            char ch = expr.charAt(i);

            if (ch == '(' || ch == '{' || ch == '[') {
                stack.push(ch);
            } else if (ch == ')' || ch == '}' || ch == ']') {
                if (stack.isEmpty()) return false;
                char top = stack.pop();
                if (!isMatchingPair(top, ch)) return false;
            }
        }

        return stack.isEmpty();
    }

    public static void main(String[] args) {
        String s1 = "{(a+b)*[c-d]}";
        String s2 = "{(a+b]*[c-d)}";

        System.out.println(isBalanced(s1)); // true
        System.out.println(isBalanced(s2)); // false
    }
}
 
</pre>

---

الستاك مش بس data structures ، هو طريقة تفكير بتنظم شغلك وترتب خطواتك
تعلم كيف تستخدمه صح، لأنه بلزمك بحل مشاكل كتير منطقية وتنظيمية في البرمجة وفي الحياة كمان.
جرب تطبق بنفسك .

## لو وصلتو لهون قيمولي الوضع ع الانستا ... بالتوفيق 
