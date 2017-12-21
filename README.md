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

