# C 语言基础

[c语言菜鸟教程](https://www.runoob.com/cprogramming/c-tutorial.html)

## <font class="text-color-13" color="#ffeb3b"> 数据类型</font>
* [C数据类型](https://www.runoob.com/cprogramming/c-data-types.html)
1. 基本数据类型：

   - **整型**：用于表示整数值。包括以下类型：
     - `char`：用于表示字符类型。大小为1字节。
     - `short`：短整型，一般为2字节。
     - `int`：整型，一般为4字节。
     - `long`：长整型，一般为4字节或8字节。
     - `long long`：长长整型，一般为8字节。

   - **浮点型**：用于表示带有小数部分的数值。包括以下类型：
     - `float`：单精度浮点型，一般为4字节。
     - `double`：双精度浮点型，一般为8字节。
     - `long double`：扩展精度浮点型，一般为10字节或12字节。

   - **布尔型**：用于表示逻辑值，只能取两个值：0（假）和非零（真）。C99标准及以后引入了布尔类型 `_Bool`，可以使用头文件 `<stdbool.h>` 中的 `true` 和 `false` 宏来表示逻辑值。

   - **空类型**：`void` 用于表示没有值的情况，常用于函数的返回类型或不带参数的函数声明。

2. 派生数据类型：

   - **指针类型**：指针是存储内存地址的变量，可以指向其他数据类型的对象。指针类型由基本数据类型加上 `*` 构成，例如 `int*` 表示指向整型的指针。

   - **数组类型**：数组是具有相同数据类型的元素的集合。可以通过指定元素类型和数组大小来声明数组，例如 `int numbers[10]` 表示包含10个整型元素的数组。

   - **结构体类型**：结构体是用户自定义的复合数据类型，可以包含多个不同类型的成员变量。使用 `struct` 关键字定义结构体类型，并在结构体中定义成员变量的类型和名称。

   - **联合体类型**：联合体是一种特殊的数据类型，允许在相同的内存空间中存储不同类型的数据。联合体使用 `union` 关键字定义，所有成员共享同一块内存。

   - **枚举类型**：枚举是一种用户自定义的数据类型，用于定义一组具名的常量值。枚举类型使用 `enum` 关键字定义，列出枚举常量的名称。

   - **函数类型**：函数类型由函数返回值的类型和参数的类型组合而成。可以声明函数指针变量，用于指向具有相同函数类型的函数。

类型修饰符：`signed`、`unsigned`、`const`、`volatile` 等，用于修改数据类型的行为和特性。

需要注意的是，不同的数据类型在不同的编译器和操作系统上可能会有不同的大小和范围。可以使用标准库头文件 `<limits.h>` 和 `<float.h>` 中的常量和宏来获取数据类型的特性信息，如最小值、最大值和精度等。

类型别名：使用 `typedef` 关键字为现有类型创建别名，以提高代码的可读性和可维护性。通过为类型定义别名，可以使用更具描述性的名称来表示数据类型，使代码更易于理解和维护。例如：`typedef int Age;` 可以为 `int` 类型创建别名 `Age`。



## <font class="text-color-13" color="#ffeb3b">字符串</font>
* [C字符串](https://www.runoob.com/cprogramming/c-strings.html)
### <font class="text-color-15" color="#ff9800"> 字符串操作函数</font>
在C语言中，有许多用于操作字符串的函数。

1. `strlen()`: 计算字符串的长度（不包括空字符）。
    ```c
    #include <string.h>

    int length = strlen("Hello"); // 返回 5
    ```

2. `strcpy()`: 将一个字符串复制到另一个字符串。
    ```c
    #include <string.h>

    char dest[20];
    strcpy(dest, "Hello"); // 将 "Hello" 复制到 dest
    ```

3. `strcat()`: 将一个字符串追加到另一个字符串的末尾。
    ```c
    #include <string.h>

    char str[20] = "Hello";
    strcat(str, " World"); // 将 " World" 追加到 str 的末尾
    ```

4. `strcmp()`: 比较两个字符串是否相等。
    ```c
    #include <string.h>

    int result = strcmp("Hello", "Hello"); // 返回 0，表示相等
    ```

5. `strchr()`: 在字符串中查找指定字符的第一次出现。 
    ```c
    #include <string.h>

    char* position = strchr("Hello", 'l'); // 返回指向第一个 'l' 的指针
    ```

6. `strstr()`: 在字符串中查找指定子字符串的第一次出现。
    ```c
    #include <string.h>

    char* position = strstr("Hello World", "World"); // 返回指向 "World" 的指针
    ```

 
 7.  `strtok()`: 将字符串拆分为多个子字符串，使用指定的分隔符进行分割。
	 ```c
	 #include <string.h> char str[20] = "Hello World";
	 char* token = strtok(str, " "); // 将字符串以空格为分隔符拆分成两个子字符串
	 while (token != NULL) {
	 printf("%s\n", token);
	 token = strtok(NULL, " ");
	 }
	 ```
	 `strtok()` 函数会修改传入的字符串。具体来说，`strtok()` 函数会将分隔符位置替换为空字符 (`'\0'`)，从而将原始字符串拆分为多个子字符串。
	 
这些函数只是 C 语言中操作字符串的一部分函数。C语言中还有许多其他的字符串函数，可以根据具体需求来选择合适的函数。请注意，在使用这些函数之前，应确保包含 `<string.h>` 头文件。


## <font class="text-color-13" color="#ffeb3b">数组</font>
* [c 数组](https://www.runoob.com/cprogramming/c-arrays.html)
1. 声明数组：要声明一个数组，需要指定元素的类型和数组的名称，并使用方括号 `[]` 指定数组的大小。例如：
```c
int numbers[5];  // 声明一个包含5个整数的数组
```
2. 初始化数组：可以在声明数组时初始化，或者使用赋值语句逐个赋值。例如：
```c
int numbers[5] = {1, 2, 3, 4, 5};  // 初始化数组
```
3. 访问数组元素：使用下标（索引）运算符 `[]` 可以访问数组中的特定元素。数组的下标从 0 开始，最大下标为数组大小减一。例如：
```c
int x = numbers[2];  // 访问数组中下标为2的元素，将其赋值给变量x
```
4. 数组长度：可以使用 `sizeof` 运算符获取数组的长度（字节数）。例如：
```c
int length = sizeof(numbers) / sizeof(numbers[0]);  // 计算数组numbers的长度
```
5. 多维数组：C语言支持多维数组，即数组的元素本身也可以是数组。例如：
```c
int matrix[3][3] = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};  // 声明一个3x3的矩阵
int value = matrix[1][2];  // 访问矩阵中第2行第3列的元素
```
6. 字符串数组：在C语言中，字符串通常用字符数组表示，以null字符 `\0` 结尾。例如：
```c
char name[10] = "John";  // 声明一个包含10个字符的字符串数组
```
### <font class="text-color-15" color="#ff9800">数组遍历</font>
- for 循环遍历
```c
int numbers[] = {1, 2, 3, 4, 5};

for (int i = 0; i < sizeof(numbers) / sizeof(numbers[0]); i++) {
    // 访问数组元素并执行操作
    printf("%d ", numbers[i]);  // 打印数组元素的值
}
```
- 可以利用C语言中数组以null字符 `\0` 结尾的特性，来进行数组遍历（字符串限定）
```c
char str[] = "Hello, World!";

for (int i = 0; str[i] != '\0'; i++) {
    // 访问数组元素并执行操作
    printf("%c ", str[i]);  // 打印字符数组元素的值
}
```
- while 循环遍历（字符串限定）
```c
char str[] = "Hello, World!";
int i = 0;

while (str[i] != '\0') {
    // 访问数组元素并执行操作
    printf("%c ", str[i]);  // 打印字符数组元素的值
    i++;
}
```

## <font class="text-color-13" color="#ffeb3b">内存分配函数</font>

* [c 内存管理](https://www.runoob.com/cprogramming/c-memory-management.html)

1.  `malloc`：用于动态分配内存空间。函数原型为：
```c
void *malloc(size_t size);
```
* 函数接受一个参数 `size`，表示要分配的内存空间的字节数。如果分配成功，返回一个指向分配内存的指针；如果分配失败，返回`NULL`。

2. `calloc`：用于动态分配并初始化内存空间。函数原型为：
```c
void *calloc(size_t num, size_t size);
```
* 函数接受两个参数 `num` 和 `size`，分别表示要分配的元素数量和每个元素的字节数。`calloc` 会分配一个大小为 `num * size` 的内存块，并将其所有位初始化为零。如果分配成功，返回一个指向分配内存的指针；如果分配失败，返回`NULL`。

3. `realloc`：用于重新分配已经分配的内存空间的大小。函数原型为：
```c
void *realloc(void *ptr, size_t size);
```
- 函数接受两个参数 `ptr` 和 `size`，其中 `ptr` 是一个指向之前由 `malloc`、`calloc` 或 `realloc` 返回的内存块的指针，`size` 表示要重新分配的内存块的大小。如果分配成功，返回一个指向重新分配内存的指针；如果分配失败，返回`NULL`。注意，`realloc` 可能会在原地扩展或收缩内存块，也可能会在新的位置上重新分配内存块。

4. `free`：用于释放之前分配的内存空间。函数原型为：
```c
void free(void *ptr);
```
- 函数接受一个参数 `ptr`，是之前由 `malloc`、`calloc` 或 `realloc` 返回的内存块的指针。调用 `free` 将释放该内存块，使其可供后续的内存分配使用。


## <font class="text-color-13" color="#ffeb3b">自定义类型</font>
- `typedef` 的基本语法如下：
```c
typedef <existing_type> <new_type_name>;
```
* 其中，`existing_type` 是已有的数据类型，可以是任何合法的C数据类型，包括基本类型、指针类型、数组类型、结构体类型、联合体类型等。`new_type_name` 是你为该已有类型定义的新名称，可以是任何合法的标识符。

* 通过使用 `typedef`，可以使代码更具可读性，减少代码中重复的类型声明，以及提高代码的可维护性和可重用性。

### <font class="text-color-15" color="#ff9800">自定义字符串类型 </font>
```c
typedef char String[100];
```

