Const, Final and late Keyword
تدعم لغة Dart تخصيص قيمة ثابتة لمتغير. يتم ذلك عن طريق استخدام الكلمة الأساسية التالية:


1. const keyword
2. final keyword

تُستخدم هذه الكلمات الرئيسية للحفاظ على قيمة المتغير ثابتة في جميع أنحاء الكود ، مما يعني أنه بمجرد تحديد المتغير لا يمكن تغيير حالته. لا توجد قيود او شروط إذا كانت هذه الكلمات الأساسية لها نوع بيانات محدد أم لا.


مفهوم Final keyword

يتم استخدام final keyword لعطاء القيمه للمتغير في وقت عملية runTime ثم تخزين قيم المتغير بشكل ثابت ولا يمكن تغييرها في المستقبل ، ولا يمكن لأي نوع من العمليات التي يتم إجراؤها على هذه المتغيرات تغيير قيمتها.

لناخذ مثال بسيط يوضح فكرة final 
لنفترض لدينا متغير باسم nameAcademy هو يشري الى اسم الاكاديمية 


    void main(){
      
    String nameAcademy = "Tuwaiq Academy";
    print(nameAcademy);
    }

المخرجات :


    Tuwaiq Academy

في هذه الحال نستطيع تغير قيمة المتغير  عند استدعائه ثم اعطائه قيمه جديده كما في المثال التالي :


    void main(){
      
      String nameAcademy = "Tuwaiq Academy";
      nameAcademy = "Tuwaiq";
      print(nameAcademy);
    }

المخرجات :


    Tuwaiq

اما في حال تم استخدام كلمة final قبل اسم المتغير لن يتم تغير قيمة وسوف يظهر خطاء يشير الى عدم امكانية تغير القيمه المتغير بعد تعريفها بانها final كما في المثال التالي 


    void main(){
      
     final String nameAcademy = "Tuwaiq Academy";
      nameAcademy = "Tuwaiq";
      print(nameAcademy);
    }

المخرجات :


    Error: Can't assign to the final variable 'nameAcademy'.
      nameAcademy = "Tuwaiq";
      ^^^^^^^^^^^
    Error: Compilation failed.


ايضا في حال تم انشاء متغير وتم تعريفه على انه final بدون اعطاءه قيمه يمكن اعطاءه قيمه في وقت عملية runtime وسوف يتم تخزين القيمه ولا يسمح فيه تغيرها بعد تخزينها كما في المثال التالي :

    void main(){
      
     final String nameAcademy;
      nameAcademy = "Tuwaiq Academy";
      print(nameAcademy);
    }

المخرجات :

    Tuwaiq Academy

وايضا في حال تم انشاء Class يحتوي على properties داخل Class هو عباره عن final  سوف يتم اسناد القيمه له مره واحده ثم لن يسمح لك بتغير القيمه مره اخرى 


     class BankAccount {
     static String nameBank = "Tuwaiq Bank";
     String accountName;
        num accountBalance = 0.0;
        int accountNumber = 0;
       BankAccount(this.accountName,this.accountBalance,this.accountNumber);
       
        displayBalance()
        {
           print("Name: $accountName");
           print("Current balance is $accountBalance");
        }
       
    }
    
    void main(){
      
      BankAccount ob1 = BankAccount("Fahad",14.58,1);
    
      ob1.displayBalance();
      
      ob1.accountName = "Saleh";
      ob1.displayBalance();
    }




مفهوم const keyword




يتم استخدام const keyword لعطاء القيمه للمتغير قبل عملية runTime و تخزين قيم المتغير بشكل ثابت ولا يمكن تغييرها ، ولا يمكن لأي نوع من العمليات التي يتم إجراؤها على هذه المتغيرات تغيير قيمتها.

لناخذ مثال بسيط يوضح فكرة const 
لنفترض لدينا متغير يشير الى الوقت  باسم timeNow 


    void main() {
      String timeNow = "${DateTime.now()}";
      print(timeNow);
    }

دالة DateTime.now هي لجلب الوقت من النظام في وقت عملية تشغيل البرنامج (runtime) في هذا الحاله سوف يتم طباعة 
المخرجات :

    2022-05-24 15:08:23.344470

لقد اخذ الوقت وتم اسناده للمتغير timeNow على نص لان تم استخدام مفهوم String Interpolation بستخدام علامة $ داخل علامات “” التنصيص

الان لو جعلنا هذا المتغير هو عباره عن final مثل ماتعلمنا سابقاً لان يصبح هناك اي مشكله  لان مفهوم final يتم اسناد القيمه وقت علمية تشغيل البرنامج (runTime) 


    void main() {
      final String timeNow = "${DateTime.now()}";
      print(timeNow);
    }

بستخدام كلمة final سوف يتم اسناد القيمه وتخزينها ولن يتم تغيرها في اي حال من الاحوال الا اذا تم تشغيل البرنامج مره اخرى 

المخرجات :


    2022-05-24 15:08:23.344470

الان سوف نلاحظ الفرقات بين استخدام final و const لو تم تغير كلمة final الى const سوف يتم اظهار لك رساله خطاء تخبرك ان قيمة الوقت سوف يتم اسناده في وقت عملية تشغيل البرنامج (runtime) واستخدام const يتم اسناد لها القيمه قبل تشغيل البرنامج في وقت كتابة الكود وتطوير البرنامج 


    void main() {
      const String timeNow = "${DateTime.now()}";
      print(timeNow);
    }

المخرجات :

    : Error: Cannot invoke a non-'const' constructor where a const expression is expected.
    bin/dart_project.dart:2
    Try using a constructor or factory that is 'const'.
      const String timeNow = "${DateTime.now()}";

لذى أستخدام const يجب تعريف المتغير وعطائه قيمه قبل تشغيل البرنامج  كما هو في المثال التالي :


    void main() {
      const String timeNow = "time for now";
      print(timeNow);
    }

المخرجات :

    time for now



الفروقات بين final and const :


- يتم استخدام final لانشاء المتغير وسناد قيمته قبل او بعد تشغيل البرنامج ثم لا يمكن تغير قيمته 
- يتم استخدام const في حال اردت انشاء متغير وتعريف قيمته قبل عملية تشغيل البرنامج ولا يمكن تغير قيمته




مفهوم late keyword

يمكن استخدام late  أثناء انشاء متغير تريد تعريف يقيمته في وقت اخر.

كما في المثال التالي :


    String title;
    main(){
    getTitle();
    }
    
    void getTitle(){
    title = 'Dart';
    print('Course of $title');
    }

لدينا متغير خارج main هو عباره عن title  من نوع String ولدي Function عند استدعائها يتم وضع داخل هذا المتغير قيمه في هذه الحاله سوف يتم اظهار لي خطاء يوضح لي انه يجب ان اضع داخل المتغير title قيمه 

المخرجات :

    Error: Field 'title' should be initialized because its type 'String' doesn't allow null.
    String title;


لحل هذه المشكله يتم استخدام كلمة late لاخبار المترجم (complier) ان القيمه سوف يتم وضعها في وقت اخر كما في المثال التالي :


    late String title;
    main(){
    getTitle();
    }
    
    void getTitle(){
    title = 'Dart';
    print('Course of $title');
    }

باضافة كلمة late سوف يتم حل المشكله وسوف ينتظر المترجم القيمه التي سوف يتم اسنادها في وقت لاحق  وسوف يتم اظهار لي النتيجه التاليه عند عمل run

    Course of Dart

لذى فا استخدام كلمة late يسمح لانا في تاخير اسناد القيمه للمتغير الى وقت اخر في عملية runtime 
