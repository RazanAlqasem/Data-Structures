# 🧠Queue

لما توقف في طابور الكاشير بالسوبرماركت … أول شخص دخل الطابور هو اللي بنتهي أول واحد.
و هيك مبدأ الـ Queue 

   ![queue ](q.png)
---

## 📌ايش يعني Queue ؟
بخزن العناصر بترتيب معيّن وبعتمد على مبدأ FIFO.
 First In First Out
أول عنصر بدخل هو أول عنصر بخرج والعكس صحيح .

---

## 📌اهم العمليات :
### 1️⃣ Enqueue – إضافة عنصر  
🔹 الفكرة: لما بدك تضيف عنصر جديد، بتحطه بنهاية queue (الخلف).

🔹 التنفيذ:
لو queue مش ملان، بتحجز مكان بالخلف (rear) وتحط فيه العنصر.

لو queue ملان بصير عندك حالة اسمها Overflow.

### 2️⃣ Dequeue – إزالة أول عنصر
🔹 الفكرة: تشيل أول عنصر من queue (الأمام).

🔹 في التنفيذ:

لو queue مش فاضي، بتشيل العنصر من الـ front، وتقدم المؤشر خطوة لقدام.

لو queue فاضي، بيصير عندك حالة اسمها Underflow (يعني ما في شي تنزله).

### 3️⃣ Front / Peek – عرض أول عنصر بدون إزالته
🔹 الفكرة: تعرف مين دوره بدون ما تشيله من queue.

🔹 في التنفيذ:

ترجع قيمة العنصر عند front، لكن ما تغيّر أي مؤشر.

### 4️⃣ isEmpty – هل فاضي؟
🔹 الفكرة: تتحقق إذا ما فيه أي عناصر.

### 5️⃣ isFull – هل ممتلئ؟
🔹 الفكرة: تتحقق إذا queue وصل أقصى سعة له.

### 6️⃣ size – كم عنصر موجود الآن؟
🔹 الفكرة: تعرف عدد العناصر في queue حاليًا.

---

### 📌الأنواع الأساسية للـ Queue :

### ⭐ Linear (Simple) Queue — الطابور العادي
دخول من الخلف، خروج من الأمام (FIFO).

<pre>
initialize queue with capacity 5
front = 0
rear = -1
size = 0

function enqueue(value):
    if size == capacity:
        print("Queue Overflow")
    else:
        rear = (rear + 1)
        queue[rear] = value
        size = size + 1

function dequeue():
    if size == 0:
        print("Queue Underflow")
    else:
        value = queue[front]
        front = front + 1
        size = size - 1
        return value

function peek():
    if size == 0:
        print("Queue is empty")
    else:
        return queue[front]
  --
enqueue(10)
enqueue(20)
enqueue(30)
dequeue()  # 10 يطلع
peek()     # 20 يطلع

</pre>

### ⭐ Circular Queue — المصفوفة الدائرية 
لو كان عنا array حجمها 5 

لو استخدمناها بالطريقة العادية اول ما نعمل  enqueue 5 مرات رح يصير مليان وااذا عملنا Dequeue من index 0 المكان بصير فاضي 

بس front بصير ع  index 1  والفراغ ما بنقدر نستخدمه نهائي ف rear =4  بدل 5

الحل ؟

اعملها ع شكل Circular  

لما يكون rear يوصل لاخر index  ويكون في فراغ بالبداية ما بنوقف برجع ل index 0 

متلا عنا  A B C D E   حذفنا A B  رح يصير index 0+1 فاضيين 

ولو دخلنا F G ....

F بتخزن في index 0

G  بتخزن في index 1

<pre>
  [ F ][ G ][ C ][ D ][ E ]  
</pre>

print :

<pre>
  C  D  E  F  G
</pre>

ex:

<pre>
  initialize queue with capacity 5
front = 0
rear = 0
size = 0

function enqueue(value):
    if size == capacity:
        print("Queue Overflow")
    else:
        queue[rear] = value
        rear = (rear + 1) % capacity
        size = size + 1

function dequeue():
    if size == 0:
        print("Queue Underflow")
    else:
        value = queue[front]
        front = (front + 1) % capacity
        size = size - 1
        return value

function peek():
    if size == 0:
        print("Queue is empty")
    else:
        return queue[front]
--
enqueue(1)
enqueue(2)
enqueue(3)
dequeue()  # 1 يطلع
enqueue(4)
enqueue(5)
enqueue(6)  # بستخدم الفراغ عند البداية

</pre>

### ⭐ Deque (Double-Ended Queue)
هو اضيف عناصر أو احذف عناصر من الأمام أو الخلف.

الأنواع الفرعية:


🔹Input-Restricted Deque :


Input: مسموح من جهة وحدة بس (مثلاً الخلف).

Output: ممكن من الجهتين (الأمام والخلف).

### ex :
موقف سيارات على شكل صف واحد، مدخله من جهة وحدة ، بس الخروج من أي جهة .

Input: من جهة الخلف فقط.

Output: من الأمام أو الخلف.


🔹Output-Restricted Deque :

Output: مسموحة من جهة واحدة فقط (مثلاً الأمام).

Input: ممكن من الجهتين (الأمام والخلف).

### ex 

موقف سيارات على شكل صف، fs فيه بوابة خروج وحدة بالأمام، وبوابتين دخول (أمام وخلف).

Input: من الأمام أو الخلف.

Output:  من جهة الأمام فقط.


ex 

<pre> initialize deque as empty list

function addFront(value):
    insert value at index 0

function addRear(value):
    append value at end of list

function removeFront():
    if list is empty:
        print("Deque is empty")
    else:
        remove element at index 0

function removeRear():
    if list is empty:
        print("Deque is empty")
    else:
        remove last element

function peekFront():
    return element at index 0

function peekRear():
    return last element

  --
addRear(10)
addRear(20)
addFront(5)
removeRear()   # 20 
peekFront()    # 5 

</pre>

### ⭐ Priority Queue — طابور بالأولوية (مش FIFO تقليدي)

الفكرة: العنصر “الأعلى أولوية” بطلع أولًا، بغض النظر عن وقت الدخول.

مثال قسم طوارئ؛ الأخطر حالةً يُعالج أولًا.

### ⭐ Blocking Queue — للبرمجة المتزامنة (Concurrency)

الفكرة: لو الطابور فاضي، المستهلِك بنتظر حتى ينضاف عنصر. ولو مليان، المُنتِج بستنى حتى تنشال خانة.
متل  مخزن فيه باب دخول/خروج؛ لو مليان توقف، ولو فاضي استنلا وصول أغراض.

---

## 📌كيف بقدر استخدمه 

1: array

2: linked list

3: بنى جاهز 


---

## 📌 Queue باستخدام Linked List

<pre> class Node {
    int data;
    Node next;
    Node(int data) { this.data = data; next = null; }
}

class LinkedListQueue {
    Node front, rear;
    int size;

    LinkedListQueue() {
        front = rear = null;
        size = 0;
    }

    void enqueue(int value) {
        Node newNode = new Node(value);
        if (rear == null) {
            front = rear = newNode;
        } else {
            rear.next = newNode;
            rear = newNode;
        }
        size++;
    }

    int dequeue() {
        if (front == null) {
            System.out.println("Queue Underflow");
            return -1;
        }
        int value = front.data;
        front = front.next;
        if (front == null) rear = null;
        size--;
        return value;
    }

    int peek() {
        if (front == null) {
            System.out.println("Queue is empty");
            return -1;
        }
        return front.data;
    }

    int getSize() {
        return size;
    }
}

LinkedListQueue q = new LinkedListQueue();
q.enqueue(5);
q.enqueue(15);
q.enqueue(25);
System.out.println(q.dequeue()); // 5
System.out.println(q.peek());    // 15

</pre>

---

## 📌Queue باستخدام Array

<pre> class ArrayQueue {
    int[] queue;
    int front, rear, size, capacity;

    ArrayQueue(int capacity) {
        this.capacity = capacity;
        queue = new int[capacity];
        front = 0;
        rear = -1;
        size = 0;
    }

    void enqueue(int value) {
        if (size == capacity) {
            System.out.println("Queue Overflow");
            return;
        }
        rear = (rear + 1) % capacity;
        queue[rear] = value;
        size++;
    }

    int dequeue() {
        if (size == 0) {
            System.out.println("Queue Underflow");
            return -1;
        }
        int value = queue[front];
        front = (front + 1) % capacity;
        size--;
        return value;
    }

    int peek() {
        if (size == 0) {
            System.out.println("Queue is empty");
            return -1;
        }
        return queue[front];
    }

    int getSize() {
        return size;
    }
}

ArrayQueue q = new ArrayQueue(5);
q.enqueue(10);
q.enqueue(20);
q.enqueue(30);
System.out.println(q.dequeue()); // 10
System.out.println(q.peek());    // 20

</pre>

---


الـ Queue متل الطابور بالحياة: كل اشي عنده دوره، وما في بتخطى الدور.
سواء كان Linear، Circular، أو Priority… الفكرة وحدة : تنظيم البيانات حسب النظام .
اتقن فهمه و رح تكتشفي إنه كل تطبيق تقريبًا في البرمجة بعتمد عليه بشكل أو بآخر! 

## لو وصلتو لهون قيمولي الوضع ع الانستا ... بالتوفيق 



