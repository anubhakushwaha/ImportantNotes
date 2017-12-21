# RandomNotes

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
