# Anthony's Notes

## Data Structures

### Arrays

```
/* Created on the stack */
int arr[5];                    // {?, ?, ?, ?, ?}
int arr[5] = {1, 2, 3, 4, 5};  // {1, 2, 3, 4, 5}
int arr[5] = { };              // {0, 0, 0, 0, 0}

/* Accessing */
temp = arr[0];
temp = arr[1];

/* Created on the heap */
int* arr = new int[SIZE]  // delete with: delete [] arr;
double* arr = new double[SIZE];

/* Accessing */
temp = *arr;
temp = *(arr + 1);
```

### Character Arrays and Strings

```
char word[10];
char word[10] = {'H', 'e', 'l', 'l', 'o'};
char word[10] = "Hello";  // print with: printf("%c", word[i]) or printf("%c", *(word + i));
const char* word = "Hello"  // print with: printf("%s", word);
```

## Keywords

### Static
Static variables in a function
```
// Allocated for the lifetime of the program
// If function is called several times, the value of the variable carried through
void f() {
  static int count = 0;
  std::cout << count << std::endl;
  count++;
}

int main() {
  f();  // 0
  f();  // 1
}
```

### Virtual
A virtual function is declared within a base class and is re-defined (overriden) by a derived class. When you refer to a derived class object using a pointer or reference to the base class, you can call a virtual function for that object and execute the derived class' version of the function.

```
class base {
public:
  virtual void print() {
    cout << "print base" << endl;
   }
   
  void show() {
    cout << "show base" << endl;
  }
};

class derived : public base {
public:
  void print() {
    cout << "print derived" << endl;
  }
  
  void show() {
    cout << "show derived" << endl;
  }
};

int main() {
  base *bptr;
  derived d;
  bptr = &d;
  
  // virtual function, binded at runtime
  bptr->print();
  
  // non-virtual function, binded at compile time
  bptr->show();
}
```

output:

```
print derived
show base
```
Using the override keyword in the derived class' function will cause a compiler error if the two functions' signatures do not exactly match. Think of this keyword as saying "This function MUST override the base class' function".

```
class base {
public:
  virtual void func() {
    cout << "Hello" << endl;
  }
};

class derived : public base {
public:
  // Add override to the signature to throw an error
  void func(int a) {
    cout << "Hello, I'm derived" << endl;
  }
};

int main() {
  base b;
  derived d;
  cout << "Compiled successfully" << endl;
}
```

### Git

[Git Pro book](https://git-scm.com/book/en/v2)

Check which files are in which state. The right column indicates the status of the working tree and the left column indicates the status of the staging area. Add `-s` for less verbose output.
```
git status
```

Add files to staging area. The files are added in the state they were in when this command was executed. So you must run this after each change to the file.
```
git add [filename]
```

View exact lines that were changed but not staged. A more specific version of `git status`. Add `--staged` or `--cached` to see lines that were changed and staged.
```
git diff
```

Commit files. Add `-a` to add all tracked files for committing. Add `-m <message>` to add a commit messge and skip the text editor when the command is run.
```
git commit
```
