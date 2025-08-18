# 💡Tree

## 🍃 شو يعني tree ؟
أمثل الـ Data ع شكل node وكل node بنبثق منها مجموعة من الـ nodes  
A tree is a hierarchical, non-linear data structure.

![tree](FF.png)

---
## 🍃 ليش اسمها TREE ؟ 
لانه شكلها فعليا متل الشجرة 
Root / Branches / Leaves

---

## 🍃 مصطلحات اساسية لازم تكون بتعرفها 

### ⭐ Root (الجذر)

أول (Node) بالشجرة.

منها ببدا كل إشي.

ما إلها اب (Parent).

### ⭐ Node (العقدة)

وحدة أساسية في الشجرة.

بتحتوي على قيمة (Data).

ممكن يكون إلها أبناء (Children).

### ⭐ Parent (الأب)

كل node إلها parent واحد (ما عدا الـ Root).

### ⭐ Child (الإبن)

node متصلة مباشرةً parent .


### ⭐ Leaf (ورقة)

node ما إلها children 


### ⭐ Siblings (إخوة)

node إلها نفس parent.


### ⭐ Height (الارتفاع)

أطول مسار من الـ Root ل leaf.

### ⭐ Depth (العمق)

عدد الحواف (Edges) من الـ Root ل node معيّنة

### ⭐ Subtree (شجرة فرعية)

أي node مع كل children تحتها تعتبر Subtree.

---

## 🍃 Types of trees


### ⭐ General Tree 

أي عقدة ممكن يكون إلها عدد غير محدود من الأبناء.]

<img src="General-Tree.jpg" width="200" height="300">


### ⭐ Binary Tree 

كل عقدة مسموح إلها حد أقصى ولدين (Left + Right).

أكثر نوع مشهور بالداتا ستركتشور.

<img src="bbb.png" width="200" height="300">


#### Full Binary Tree
كل عقدة (Node) فيها يا إمّا 0 أبناء أو 2 أبناء.

يعني ما في عقدة عندها ابن واحد فقط

<img src="full-binary-tree_0.webp" width="200" height="300">


####  Perfect Binary Tree
كل المستويات مليانة 100%.

جميع الأوراق (Leaves) موجودة بنفس المستوى.
<img src="perfect-binary-tree_0.webp" width="200" height="300">


#### Complete Binary Tree
كل المستويات مليانة بالعقد.

المستوى الأخير ممكن يكون ناقص، لكن لازم يتعبّى من اليسار لليمين.

<img src="complete-binary-tree_0.webp" width="200" height="300">


#### skewe Binary Tree

كل عقدة فيها ابن واحد فقط (يا إما كلهن left child أو كلهن right child).

<img src="skewed-binary-tree_0.webp" width="200" height="300">


#### Degenerate Binary Tree

كل عقدة فيها ابن واحد فقط (يا  left child أو  right child).

<img src="degenerate-binary-tree_0.webp" width="200" height="300">


####  Binary Search Tree (BST)

القيم الأصغر من قيمة العقدة → موجودة بالـ Left Subtree.

القيم الأكبر من قيمة العقدة → موجودة بالـ Right Subtree.

بخلي البحث أسرع. كيف يعني ؟  

يعني لو بدي ابحث عن رقم 12 بشوف root و بفحصه اذا اكبر منه بروح ع اليمين وبنسى اليسار وهيكك قللت وقت و اوجدت العنصر بسرعة 


<img src="degenerate-binary-tree_0.webp" width="200" height="300">

## implementation of BST 
### Traversal :

#### Pre order

#### in order

#### post order

### pre order :

 #### Root -> left -> Right


### in order:

#### left -> Root -> Right


### Post order :

#### leaf -> Right -> Root 
 




































### ⭐ Balanced Trees (متل  AVL, Red-Black Tree)

أشجار ثنائية بس متوازنة حتى ما يصير ميلان لطرف واحد.

مفيدة بالبحث السريع.


نوع خاص من Binary Tree يستخدم بعمليات الـ Priority Queue.


