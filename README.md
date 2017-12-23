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

* Go's basic types are

```
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

### Curl Commands

* Sometimes, you may want to debug a problem because the curl command hasn't returned what it was supposed to or just hasn't worked at all. In such cases, you can use the verbose mode using -v or **--verbose** to get more output from curl. Let's modify the previous HTTP request to become verbose.

```
curl -Iv  www.httpbin.org
* Rebuilt URL to: www.httpbin.org/
*   Trying 54.243.173.79...
* Connected to www.httpbin.org (54.243.173.79) port 80 (#0)
> HEAD / HTTP/1.1
> Host: www.httpbin.org
> User-Agent: curl/7.47.0
> Accept: */*
> 
< HTTP/1.1 200 OK
HTTP/1.1 200 OK
< Connection: keep-alive
Connection: keep-alive
< Server: meinheld/0.6.1
Server: meinheld/0.6.1
< Date: Sat, 23 Dec 2017 11:35:29 GMT
Date: Sat, 23 Dec 2017 11:35:29 GMT
< Content-Type: text/html; charset=utf-8
Content-Type: text/html; charset=utf-8
< Content-Length: 13011
Content-Length: 13011
< Access-Control-Allow-Origin: *
Access-Control-Allow-Origin: *
< Access-Control-Allow-Credentials: true
Access-Control-Allow-Credentials: true
< X-Powered-By: Flask
X-Powered-By: Flask
< X-Processed-Time: 0.00564694404602
X-Processed-Time: 0.00564694404602
< Via: 1.1 vegur
Via: 1.1 vegur

< 
* Connection #0 to host www.httpbin.org left intact
```
**Lines prefixed with a greater-than (>) sign show the data curl has sent to the server.**
**Lines prefixed with a less-than (<) sign show the data curl has received from the server.**

### POST request

You can send a POST request by using the -d (or --data) flag. It͛s up to you to properly URL encode the data or specify it as JSON. We'll see the examples for both of those. Here's how you'd send URL encoded data as a part of the POST body

```
me@home:~$ curl -d 'name=john+doe&course=linux' httpbin.org/post
```

The response sent by HTTPBin will simply echo what you͛ve sent.

To send JSON:

```
me@home:~$ curl -d '{"name":"John Doe","course":"Linux"}' httpbin.org/post
```

Notice that in both the examples, the data is enclosed in single quotes. Using double quotes is okay but it may cause problems if the body also contains double quotes like JSON. Using single quotes is the safer approach.
  
### PUT request

ReST APIs use the PUT request to **update an existing resource** that the server manages. Making a PUT request with curl is similar to making a POST request. Here’s how you’d make a PUT request:

```
me@home:~$ curl -X PUT -d '{"name":"Jane Doe"}' httpbin.org/put
```
