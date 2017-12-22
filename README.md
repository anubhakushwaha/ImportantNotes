# RandomNotes

## Deep Copy
* A deep copy of an object is a new object with entirely new instance variables, it does not share objects with the old.
![Image](https://drive.google.com/file/d/1_bEgvfOLSJ_tqddkp116OmSp7Ux-eEAV/view?usp=sharing)
```
struct Test{
  char *ptr;
};
void shallow_copy(Test &src, Test &dest){
  dest.ptr = src.ptr;
}
void deep_copy(Test &src, Test &dest){
  dest.ptr = malloc(strlen(src.ptr) + 1);
  memcpy(dest.ptr, src.ptr);
}
```
## Name Hiding
* Name hiding occurs when we have overloaded functions and we try to override just one overloaded function.
```
class FirstClass{
  public:
  virtual void methodA(int);
  virtual void methodA(int, int);
};

class SecondClass : public FirstClass {
  public:
  void MethodA(int val){
    cout<<val;
  }
};

int main(){
  SecondClass obj;
  obj.MethodA(1);
  obj.MethodA(1,1); // This call will not work
  return 0;
}
```

## Virtual Functions
* A virtual function provides run time polymorphism and executes the function present in the object being referenced.
```
class Base{
  public:
  void display(){
    cout<<"Base class displayed\n";
  }
  virtual void show(){
    cout<<"Base class showed\n";
  }
};
class Derived : public Base{
  public:
  void display(){
    cout<<"Derived class displayed\n";
  }
  void show(){
    cout<<"Derived class showed\n";
  }
};

int main(){
  Base B;
  Derived D;
  Base *bptr;
  
  bptr = &B;
  bptr->display();    //Calls base version
  bptr->show();       //Calls base version
  
  bptr = &D;
  bptr->display();    //Calls base version
  bptr->show();       //Calls derived version
  
  return 0;
}
```
## Derived Destructors
* Derived destructors are called first, then their parents i.e opposite to what happening in constructors.
```
class Base{
  public:
  Base(){ cout<<"Constructor of Base\n"; }
  virtual ~Base(){ cout<<"Destructor of Base\n"; }
};
class Derived{
  public:
  Derived(){ cout<<"Constructor of Derived\n"; }
  ~Derived(){ cout<<"Destructor of Derived\n"; }
};

void main(){
  Base *bptr = new Derived();
  delete p;
}

### Output :
Constructor of Base
Constructor of Derived
Destructor of Derived
Destructor of Base
```

## GO LANG NOTES
```
Go's basic types are

bool

string

int  int8  int16  int32  int64
uint uint8 uint16 uint32 uint64 uintptr

byte // alias for uint8

rune // alias for int32
     // represents a Unicode code point

float32 float64

complex64 complex128
```

## Google Cloud Platform Components
* App Engine
* Compute Engine
* Cloud Data Storage
* Big Query
* Cloud Datastore


## Google Cloud Shell

* gcloud version

  *This will display a list of installed Cloud SDK components and their versions*
  
* gcloud app deploy ./index.yaml ./app.yaml

  *Deploy the app to App Engine*
  
* gcloud app browse 

  *To view your application in the web browser*
 
### Configure Your Cloud Shell Environment

* gcloud compute zones list

  *List available time zones*

* gcloud config set compute/zone asia-south1-a
 
  *Set a time zone example*


  
