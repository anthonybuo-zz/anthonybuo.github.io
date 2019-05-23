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

Static variables in a class
