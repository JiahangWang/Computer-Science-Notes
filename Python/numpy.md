# <center>numpy</center>

## <font class="text-color-13" color="#ffeb3b">介绍</font>
- NumPy（Numerical Python）是Python的一种开源的数值计算扩展1。它是一个Python库，提供多维数组对象，各种派生对象（如掩码数组和矩阵），以及用于数组快速操作的各种API，有包括数学、逻辑、形状操作、排序、选择、输入输出、离散傅立叶变换、基本线性代数，基本统计运算和随机模拟等等2。

- NumPy的前身Numeric最早是由Jim Hugunin与其它协作者共同开发，2005年，Travis Oliphant在Numeric中结合了另一个同性质的程序库Numarray的特色，并加入了其它扩展而开发了NumPy3。NumPy为开放源代码并且由许多协作者共同维护开发3。

- NumPy是一个运行速度非常快的数学库，主要用于数组计算，包含：
    - 一个强大的N维数组对象ndarray
    - 广播功能函数
    - 整合C/C++/Fortran代码的工具
    - 线性代数、傅里叶变换、随机数生成等功能3
- NumPy通常与SciPy（Scientific Python）和Matplotlib（绘图库）一起使用，这种组合广泛用于替代MatLab，是一个强大的科学计算环境，有助于我们通过Python学习数据科学或者机器学习3。SciPy是一个开源的Python算法库和数学工具包。SciPy包含的模块有最优化、线性代数、积分、插值、特殊函数、快速傅里叶变换、信号处理和图像处理、常微分方程求解和其他科学与工程中常用的计算3。Matplotlib是Python编程语言及其数值数学扩展包NumPy的可视化操作界面3。

- 总的来说，NumPy是Python中科学计算的基础包，提供了许多高级的数值编程工具，如：矩阵数据类型、矢量处理，以及精密的运算库。专为进行严格的数字处理而产生4。

## <font class="text-color-121" color="#ffeb3b">ndarray</font>
* NumPy 的 `ndarray`（n-dimensional array）是其最重要的对象之一，它是用于存储和操作多维数据的核心数据结构。以下是关于 NumPy 的 `ndarray` 对象的详细解释：

1. **多维数组**：
  
  - `ndarray` 是一个多维数组，它可以包含任意维度的数据。一维数组类似于列表，二维数组类似于矩阵，更高维度的数组可以看作是多个嵌套的数组。
2. **数据类型**：
  
  - `ndarray` 中的所有元素都具有相同的数据类型，这使得它非常适合进行数值计算。NumPy 提供了各种数据类型，包括整数、浮点数、复数、布尔值等，以及不同精度的数据类型。
3. **形状**：
  
  - `ndarray` 具有形状（shape），形状是一个元组，用于描述数组的维度和每个维度的大小。例如，二维数组的形状可以是 `(rows, columns)`。
4. **元素访问**：
  
  - 可以使用索引来访问 `ndarray` 中的元素，其中索引从0开始。可以使用单个整数索引访问一维数组，使用多个整数索引访问多维数组的元素。
5. **切片操作**：
  
  - 可以使用切片操作来访问 `ndarray` 中的子数组。切片允许您选择数组的一部分，创建一个新的数组视图，而不需要复制数据。
6. **广播**：
  
  - NumPy 具有强大的广播机制，允许对具有不同形状的数组执行元素级操作，以便它们具有兼容的形状。这使得处理不同形状的数组变得更加方便。
7. **矢量化操作**：
  
  - NumPy 鼓励使用矢量化操作，这意味着可以在整个数组上执行操作，而不需要显式编写循环。这可以提高代码的效率和可读性。
8. **数学和统计函数**：
  
  - NumPy 提供了丰富的数学和统计函数，用于对数组执行各种操作，如求和、平均值、标准差、最小值、最大值等。
9. **数组操作**：
  
  - `ndarray` 支持各种数组操作，包括转置、形状调整、连接、分割、堆叠等，这些操作可以用于改变数组的形状和结构。
10. **高性能计算**：
  
  - NumPy 的 `ndarray` 通过底层的 C 或 Fortran 代码实现，因此具有出色的性能，特别适用于大规模数据处理和科学计算。
11. **广泛的应用**：
  
  - NumPy 的 `ndarray` 在科学、工程、数据分析、机器学习等领域中被广泛应用，它是许多 Python 数据科学库的基础，如 SciPy、pandas、scikit-learn 等。

创建 `ndarray` 对象通常通过 `numpy.array()` 函数或其他函数（如 `numpy.zeros()`、`numpy.ones()`、`numpy.arange()` 等）来实现。一旦创建了 `ndarray`，就可以使用 NumPy 提供的各种函数和方法对其进行操作和分析。

### <font class="text-color-15" color="#ff9800">创建</font>
1.  **使用 `numpy.array` 函数**：
- 最常见的方法是使用 `numpy.array()` 函数，它接受一个序列（如列表或元组）作为输入，并返回一个 ndarray。创建的数组的数据类型会自动推断，也可以显式指定。
```python
import numpy as np
arr = np.array([1, 2, 3, 4, 5])
```
* `numpy.array` 函数用于创建 ndarray（多维数组），它有多个参数，以下是这些参数的详细说明：
```python
numpy.array(object, dtype=None, copy=True, order='K', subok=False, ndmin=0)
```
    1. `object`：必需，用于创建 ndarray 的输入对象。可以是以下之一：

      - 列表、元组或其他类数组的可迭代对象。
      - 一个已存在的 ndarray。
      - 一个字符串，表示一个已存在的文件名，用于从文件中读取数据。
      - 一个缓冲区对象（buffer），用于从原始数据创建数组。
    2. `dtype`：可选，指定创建的数组的数据类型。默认情况下，数据类型会自动推断，但您可以显式指定，如 `'int32'`、`numpy.int32` 等。

    3. `copy`：可选，一个布尔值，用于指定是否复制输入对象的数据。如果为 True（默认值），则创建一个副本，否则直接引用输入对象的数据。

    4. `order`：可选，用于指定多维数据的存储顺序。可以是以下值之一：

      - `'C'`：按行主序（行优先，C风格）存储多维数据。
      - `'F'`：按列主序（列优先，Fortran风格）存储多维数据。
      - `'A'`：自动选择存储顺序（默认值）。
      - `'K'`：保留输入数据的存储顺序。
    5. `subok`：可选，一个布尔值，用于指定是否返回子类的 ndarray。如果为 True，返回一个子类的 ndarray；如果为 False（默认值），返回一个普通的 ndarray。

    6. `ndmin`：可选，一个整数，用于指定创建的数组的最小维数。默认值为 0。如果设置为 1 或更大，将创建一个具有指定维数的数组。
  

这些参数使得 `numpy.array` 函数非常灵活，可以根据需要创建不同形状、数据类型和存储顺序的数组。通常情况下，最常用的参数是 `object` 和 `dtype`，其他参数在特殊情况下才会用到。例如，`copy` 参数用于控制是否复制输入对象的数据，`ndmin` 参数用于创建具有最小维数的数组，`order` 参数用于控制多维数组的存储顺序。

以下是一些示例，演示如何使用 `numpy.array` 函数的不同参数：
```python
import numpy as np

# 创建一个整数数组
arr1 = np.array([1, 2, 3])

# 创建一个浮点数数组，并指定数据类型
arr2 = np.array([4.0, 5.0, 6.0], dtype='float32')

# 创建一个二维数组
arr3 = np.array([[1, 2, 3], [4, 5, 6]])

# 创建一个具有最小维数的数组
arr4 = np.array([1, 2, 3], ndmin=2)

# 创建一个复数数组
arr5 = np.array([1 + 2j, 3 + 4j])

# 创建一个数组，不复制输入对象的数据
arr6 = np.array(arr1, copy=False)
```


2. **使用 `numpy.zeros` 和 `numpy.ones` 函数**：

- `numpy.zeros(shape)` 和 `numpy.ones(shape)` 函数用于创建指定形状的全零数组和全一数组。
```python
import numpy as np
zeros_arr = np.zeros((3, 4))  # 创建一个3x4的全零数组
ones_arr = np.ones((2, 2), dtype=int)  # 创建一个2x2的全一整数数组
```
3. **使用 `numpy.empty` 函数**：

- `numpy.empty(shape)` 函数创建一个指定形状的数组，但不会初始化数组的元素值。它通常比 `numpy.zeros` 和 `numpy.ones` 快，但数组的元素值是未定义的。
```python
import numpy as np
empty_arr = np.empty((2, 3))  # 创建一个2x3的未初始化数组
```
4. **使用 `numpy.arange` 函数**：

- `numpy.arange(start, stop, step)` 函数用于创建一个等差数列数组，其中 `start` 是起始值，`stop` 是终止值（不包含在内），`step` 是步长。
```python
import numpy as np
arange_arr = np.arange(0, 10, 2)  # 创建一个从0到10，步长为2的数组
```
5. **使用 `numpy.linspace` 函数**：

- `numpy.linspace(start, stop, num)` 函数用于创建一个等间隔的数组，其中 `start` 是起始值，`stop` 是终止值（包含在内），`num` 是生成的元素数量。
```python
import numpy as np
linspace_arr = np.linspace(0, 1, 5)  # 创建一个从0到1的5个元素的等间隔数组
```
6. **使用随机数生成函数**：

- NumPy 还提供了一系列用于生成随机数的函数，如 `numpy.random.rand`、`numpy.random.randn`、`numpy.random.randint` 等，这些函数可用于创建包含随机数的 ndarray。

7. **从现有数据结构或文件中创建**：

- 您可以从现有的数据结构（如 Python 列表、元组、其他数组）或文件中读取数据，然后使用 `numpy.array` 函数创建 ndarray。

#### <font class="text-color-7" color="#03a9f4">从已有的数组创建数组</font>
1. **`numpy.zeros_like(a, dtype=None, order='K', subok=True)`**：

- 该函数接受一个输入数组 `a`，然后返回一个与 `a` 具有相同形状和数据类型的全零数组。
- 参数 `dtype` 允许您指定新创建数组的数据类型，如果不指定，则默认使用与输入数组 `a` 相同的数据类型。
- 参数 `order` 允许您指定新数组的存储顺序（'C' 或 'F'），如果不指定，则默认使用 'K'（保留输入数组的存储顺序）。
- 参数 `subok` 控制返回的数组是否是输入数组的子类。如果为 True（默认值），返回一个与输入数组具有相同数据类型的子类数组；如果为 False，返回一个普通的 ndarray。
```python
import numpy as np

arr = np.array([[1, 2, 3], [4, 5, 6]])
zeros_arr = np.zeros_like(arr)

# zeros_arr 是与 arr 具有相同形状和数据类型的全零数组
```
2. **`numpy.ones_like(a, dtype=None, order='K', subok=True)`**：

- 与 `numpy.zeros_like` 类似，`numpy.ones_like` 接受一个输入数组 `a`，并返回一个与 `a` 具有相同形状和数据类型的全一数组。
- 参数 `dtype` 允许您指定新创建数组的数据类型，如果不指定，则默认使用与输入数组 `a` 相同的数据类型。
- 参数 `order` 允许您指定新数组的存储顺序（'C' 或 'F'），如果不指定，则默认使用 'K'（保留输入数组的存储顺序）。
- 参数 `subok` 控制返回的数组是否是输入数组的子类。如果为 True（默认值），返回一个与输入数组具有相同数据类型的子类数组；如果为 False，返回一个普通的 ndarray。
```python
import numpy as np

arr = np.array([[1, 2, 3], [4, 5, 6]])
ones_arr = np.ones_like(arr)

# ones_arr 是与 arr 具有相同形状和数据类型的全一数组
```

3. **`numpy.asarray`**：

- `numpy.asarray(a, dtype=None, order=None)` 函数用于将输入转换为 NumPy 数组。它接受以下参数：
  - `a`：输入数据，可以是 Python 列表、元组、其他数组或任何类数组对象。
  - `dtype`：可选，用于指定新数组的数据类型。默认情况下，将尝试推断数据类型。
  - `order`：可选，用于指定新数组的存储顺序，可以是 `'C'`（C 风格连续）或 `'F'`（Fortran 风格连续）。
```python
import numpy as np

# 从 Python 列表创建数组
arr1 = np.asarray([1, 2, 3])

# 指定数据类型创建数组
arr2 = np.asarray([1.0, 2.0, 3.0], dtype=int)
```

4. **`numpy.frombuffer`**：

- `numpy.frombuffer(buffer, dtype=float, count=-1, offset=0)` 函数从一个缓冲区对象中创建一个数组。它接受以下参数：
  - `buffer`：缓冲区对象，通常是一个字节对象。
  - `dtype`：可选，用于指定新数组的数据类型。默认是 `float`。
  - `count`：可选，用于指定要从缓冲区中读取的元素数量。默认为 -1，表示读取尽可能多的元素。
  - `offset`：可选，用于指定从缓冲区的哪个偏移量开始读取数据。默认为 0。
```python
import numpy as np

buffer = b'\x01\x02\x03\x04\x05'  # 字节对象
arr = np.frombuffer(buffer, dtype=int, count=3)

# 创建一个包含 [1, 2, 3] 的数组
```

5. **`numpy.fromiter`**：

- `numpy.fromiter(iterable, dtype, count=-1)` 函数从可迭代对象中创建一个数组。它接受以下参数：
  - `iterable`：可迭代对象，通常是 Python 迭代器或生成器。
  - `dtype`：用于指定新数组的数据类型。
  - `count`：可选，用于指定要从可迭代对象中读取的元素数量。默认为 -1，表示读取尽可能多的元素。
```python
import numpy as np

iterable = range(5)  # Python 迭代器
arr = np.fromiter(iterable, dtype=int, count=3)

# 创建一个包含 [0, 1, 2] 的数组
```


### <font class="text-color-141" color="#ff9800">数据类型</font>
NumPy 提供了多种数据类型，用于表示不同类型的数据。以下是 NumPy 支持的常见数据类型的列表：

1. **整数类型**：
  
  - `int8`、`int16`、`int32`、`int64`：有符号整数，表示8、16、32、64位整数。
  - `uint8`、`uint16`、`uint32`、`uint64`：无符号整数，表示8、16、32、64位整数。
2. **浮点数类型**：
  
  - `float16`、`float32`、`float64`、`float128`：浮点数，表示16、32、64、128位浮点数。
  - `half`：等同于 `float16`。
  - `single`：等同于 `float32`。
  - `double`：等同于 `float64`。
3. **复数类型**：
  
  - `complex64`、`complex128`、`complex256`：复数，表示64、128、256位复数。
4. **布尔类型**：
  
  - `bool`：布尔值，表示 True 或 False。
5. **字符串类型**：
  
  - `str_`：字符串类型，用于存储字符串数据。
  - `unicode_`：Unicode 字符串类型，用于存储 Unicode 字符串数据。
6. **对象类型**：
  
  - `object`：通用对象类型，可以用于存储任意 Python 对象，但会降低数组的性能。
7. **日期和时间类型**：
  
  - `datetime64`：日期和时间类型，用于存储日期和时间信息。
8. **虚数类型**：
  
  - `bool8`：布尔类型，用于存储 True 或 False。
  - `intc`：与 C 语言中的 `int` 类型等效。
  - `uintc`：与 C 语言中的无符号 `int` 类型等效。
  - `intp`：用于索引的整数类型。
  - `uintp`：用于索引的无符号整数类型。
9. **其他特殊类型**：
  
  - `void`：用于表示不定类型的数据。
  - `bytes_`：字节类型，用于存储字节数据。
  - `str_`：字符串类型，用于存储字符串数据。
  - `unicode_`：Unicode 字符串类型，用于存储 Unicode 字符串数据。
10. **特殊类型**：
  
  - `float16` 和 `complex32`：这些类型在硬件上可能不受支持，但在某些情况下可以用于降低内存占用。

### <font class="text-color-141" color="#ff9800">属性</font>
NumPy 的 `ndarray` 对象具有许多属性，这些属性提供有关数组的信息。以下是 `ndarray` 的一些常见属性：

| 属性          | 描述                                                           |
|---------------|----------------------------------------------------------------|
| shape         | 返回一个元组，表示数组的维度。例如，对于一个形状为 (3, 4, 2) 的数组，shape 属性将返回 (3, 4, 2)。       |
| ndim          | 返回一个整数，表示数组的维度数量。例如，对于一个三维数组，ndim 属性将返回 3。                          |
| size          | 返回一个整数，表示数组中的总元素数量。对于形状为 (3, 4, 2) 的数组，size 属性将返回 24。               |
| dtype         | 返回一个描述数组数据类型的对象。例如，对于一个包含整数的数组，dtype 属性将返回 int64。                 |
| itemsize      | 返回一个整数，表示数组中每个元素的字节大小。例如，对于 int64 类型的数组，itemsize 属性将返回 8。     |
| nbytes        | 返回一个整数，表示数组中的数据占用的总字节数。计算方法是 size * itemsize。                               |
| strides       | 返回一个元组，表示在每个维度上移动一个元素需要的字节数。这是一个高级属性，用于控制数组的内存布局。   |
| data          | 返回一个指向数组数据的缓冲区的 Python 缓冲区对象。                                                      |
| flags         | 返回一个描述数组内存布局和其他属性的字典。                                                            |
| real 和 imag | 对于复数数组，这些属性返回实部和虚部。                                                                 |
| flat          | 返回一个数组的一维迭代器，用于按照 C 风格的顺序迭代数组元素。                                           |
| T             | 返回数组的转置视图，交换维度。                                                                      |
| base          | 如果数组是一个视图，返回底层数据的原始数组。                                                            |

`flags` 是 NumPy `ndarray` 对象的一个属性，它是一个包含有关数组内存布局和其他属性的字典。`flags` 属性提供了关于数组的各种信息，帮助用户了解数组的特性。以下是 `flags` 属性的一些常见标志和其解释：

| 属性                  | 描述                                                                       |
|-----------------------|----------------------------------------------------------------------------|
| C_CONTIGUOUS          | 表示数组在内存中是否是 C 风格连续存储的（按行主序）。如果为 True，则数组是 C 风格连续的；如果为 False，则不是。        |
| F_CONTIGUOUS          | 表示数组在内存中是否是 Fortran 风格连续存储的（按列主序）。如果为 True，则数组是 Fortran 风格连续的；如果为 False，则不是。  |
| OWNDATA               | 表示数组是否拥有它所引用的数据的所有权。如果为 True，则数组拥有数据的所有权；如果为 False，则不拥有。当数组是其他数组的视图时，通常 OWNDATA 为 False。 |
| WRITEABLE             | 表示数组是否可写。如果为 True，则数组是可写的；如果为 False，则为只读数组。                                              |
| ALIGNED               | 表示数组数据是否按照硬件的要求进行字节对齐。如果为 True，则数组数据是按照字节对齐的；如果为 False，则不一定按照字节对齐。    |
| WRITEBACKIFCOPY       | 表示当数组是其他数组的拷贝时，是否允许写回原始数据。如果为 True，则允许写回；如果为 False，则不允许写回。                   |

### <font class="text-color-141" color="#ff9800">切片和索引</font>

基本切片：
1. **一维数组切片**：

对于一维数组，切片操作与 Python 列表非常相似，使用 `start:stop:step` 格式。这允许您选择数组的一部分。
```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])

# 基本切片示例
subset = arr[1:4]  # 获取索引 1 到 3 的元素，结果为 [2, 3, 4]
```
2. **多维数组切片**：

对于多维数组，您可以在每个维度上使用切片。每个维度都可以具有不同的切片范围。
```python
import numpy as np

arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])

# 多维数组切片示例
subset = arr[0:2, 1:3]  # 获取第一行和第二行的第二列和第三列元素，结果为 [[2, 3], [5, 6]]
```
高级切片：
1. **布尔索引**：

使用布尔数组作为索引，可以根据条件选择数组中的元素。
```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])
mask = arr > 2

# 使用布尔索引选择满足条件的元素
selected = arr[mask]  # 结果为 [3, 4, 5]
```
2. **整数数组索引**：

使用整数数组作为索引，可以选择数组中指定位置的元素。
```python
import numpy as np

arr = np.array([10, 20, 30, 40, 50])
indices = np.array([1, 3])

# 使用整数数组索引选择指定位置的元素
selected = arr[indices]  # 结果为 [20, 40]
```
3. **省略号（Ellipsis）**：

当处理高维数组时，省略号 `...` 可以用来代替多个冒号 `:`，以简化切片操作。
```python
import numpy as np

arr = np.random.rand(3, 4, 5)

# 使用省略号选择多维数组的子集
subset = arr[..., 2]  # 获取所有行和所有列的第三个维度的元素
```
#### <font class="text-color-7" color="#03a9f4">切片指定行或列</font>
- **切片指定行：**
```python
import numpy as np

# 创建一个示例的二维数组
arr = np.array([[1, 2, 3],
                [4, 5, 6],
                [7, 8, 9]])

# 使用切片选择特定行
selected_rows = arr[1:3, :]  # 选择第 2 行到最后一行，所有列
print(selected_rows)
# 输出：
# [[4 5 6]
#  [7 8 9]]
```

- **切片指定列：**
```python
import numpy as np

# 创建一个示例的二维数组
arr = np.array([[1, 2, 3],
                [4, 5, 6],
                [7, 8, 9]])

# 使用切片选择特定列
selected_cols = arr[:, 1:3]  # 选择所有行，第 2 列到最后一列
print(selected_cols)
# 输出：
# [[2 3]
#  [5 6]
#  [8 9]]
```

## <font class="text-color-13" color="#ffeb3b">广播</font>

NumPy 广播（broadcasting）是一种强大的机制，允许 NumPy 在不同形状的数组之间执行元素级操作，而无需显式地扩展数组的形状。这使得在处理不同形状的数组时变得非常方便，而不需要显式循环或复制数据。广播的核心思想是 NumPy 尝试使输入数组的形状相容，以便进行元素级操作。

广播规则如下：

1. 当操作的两个数组具有不同的维度时，将在维度较小的数组的前面（左侧）补齐一个或多个维度，直到两个数组的维度相同。这样，较小的数组会被“扩展”以匹配较大数组的形状。
  
2. 数组的维度在某个轴上必须匹配或其中一个维度为 1。
  
3. 如果两个输入数组的形状在任何维度上都不匹配，并且没有一个维度为 1，则广播操作将失败，抛出 ValueError。
  

下面是一些示例，说明了广播是如何工作的：
```python
import numpy as np

# 示例 1: 一个数组和一个标量的广播
arr = np.array([1, 2, 3, 4])
result = arr + 10  # 将标量 10 广播到 arr 中的每个元素
# 结果为 [11, 12, 13, 14]

# 示例 2: 两个数组的广播
arr1 = np.array([1, 2, 3])
arr2 = np.array([10, 20, 30])
result = arr1 + arr2  # arr1 和 arr2 形状不同，但可以广播进行元素级操作
# 结果为 [11, 22, 33]

# 示例 3: 更复杂的广播，将一个列向量广播到一个矩阵
arr1 = np.array([[1, 2, 3], [4, 5, 6]])
arr2 = np.array([10, 20, 30])
result = arr1 + arr2  # arr2 被广播为 [[10, 20, 30], [10, 20, 30]]
# 结果为 [[11, 22, 33], [14, 25, 36]]

# 示例 4: 广播失败，形状不兼容
arr1 = np.array([[1, 2, 3], [4, 5, 6]])
arr2 = np.array([10, 20])
# 尝试执行 arr1 + arr2 会引发 ValueError，因为形状不兼容
```

## <font class="text-color-13" color="#ffeb3b">迭代器</font>
`nditer` 是 NumPy 中的一个迭代器对象，用于在多维数组上进行迭代，同时允许您以不同的方式控制和定制迭代过程。`nditer` 的主要用途是在数组的元素级上执行操作，例如遍历、修改或收集数组的值。

### 特点和用途：

1. **多维数组迭代：** `nditer` 允许您在多维数组上进行迭代，包括一维、二维、三维或更高维度的数组。
  
2. **控制迭代顺序：** 您可以控制迭代元素的顺序，包括正向、逆向、多维坐标的不同排列等。
  
3. **自定义迭代操作：** 您可以在迭代过程中执行自定义的操作，例如修改数组元素、进行条件筛选等。
  
4. **数据类型转换：** `nditer` 支持数据类型转换，允许您将元素的数据类型从一种类型转换为另一种类型。

#### 示例

1. **基本迭代**
```python
import numpy as np

arr = np.array([[1, 2], [3, 4]])

# 创建 nditer 迭代器
it = np.nditer(arr)

# 使用迭代器遍历数组
for x in it:
    print(x)
# 输出：
# 1
# 2
# 3
# 4
```
2. **控制迭代顺序**
```python
import numpy as np

arr = np.array([[1, 2], [3, 4]])

# 创建逆向迭代器
it = np.nditer(arr, flags=['multi_index'], op_flags=['readwrite'], order='F')

# 使用迭代器遍历数组
for x in it:
    print(x, it.multi_index)
# 输出：
# 4 (1, 1)
# 3 (1, 0)
# 2 (0, 1)
# 1 (0, 0)
```
3. **自定义迭代操作**
```python
import numpy as np

arr = np.array([[1, 2], [3, 4]])

# 创建迭代器并修改数组元素
it = np.nditer(arr, flags=['multi_index'], op_flags=['readwrite'])

for x in it:
    arr[it.multi_index] = x * 2

print(arr)
# 输出：
# [[2 4]
#  [6 8]]
```

### 属性
| 属性         | 描述                                                                                                      |
|--------------|-----------------------------------------------------------------------------------------------------------|
| iternext()   | 这是一个方法，用于移动迭代器到下一个元素。它返回 True 表示成功移动到下一个元素，返回 False 表示迭代结束。         |
| finished     | 一个布尔属性，指示迭代是否已经完成。通常在迭代结束后，iternext() 方法将设置 finished 为 True。               |
| index        | 当前迭代元素的索引，这个属性只在迭代过程中有效。                                                         |
| multi_index  | 当前迭代元素的多维索引，这个属性只在迭代过程中有效。如果在构造 nditer 对象时启用了 flags=['multi_index']，则可以使用此属性来获取多维索引。 |
| operands     | 返回一个元组，其中包含 nditer 对象所迭代的操作数（通常是一个或多个数组）。这对于处理多个数组的元素级操作非常有用。   |
| shape        | 返回被迭代数组的形状，这是一个只读属性。                                                                 |
| flags        | 返回 nditer 对象的标志，表示迭代器的行为和属性。                                                          |
| order        | 返回迭代器的索引顺序，可以是 'C'（C 风格，行优先）或 'F'（Fortran 风格，列优先）。                         |

## <font class="text-color-121" color="#ffeb3b">数组操作</font>

### <font class="text-color-15" color="#ff9800">修改数组形状</font>

#### <font class="text-color-101" color="#8bc34a">reshape(newshape)</font>

- **参数：** `newshape` 是一个表示新的形状的整数元组或整数列表。它指定了要将数组重新排列成的新形状。
- **返回值：** 返回一个具有新形状的数组，但不更改原始数组的数据。如果无法创建具有指定形状的新数组，则会引发错误。

- `reshape` 函数用于将数组重新排列为指定的新形状，但要注意，新形状的元素总数必须与原始数组的元素总数相同。例如：
```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5, 6])
new_shape = (2, 3)
reshaped_arr = arr.reshape(new_shape)
```
- 在这个示例中，`arr` 是一个一维数组，通过 `reshape` 可以将其转换为一个二维数组 `reshaped_arr`，新形状为 (2, 3)。

#### <font class="text-color-101" color="#8bc34a">flat 属性</font>

- **返回值：** `flat` 是一个属性，返回一个扁平化迭代器（iterator），可以用于遍历多维数组的所有元素，返回的元素是按照内存中的顺序排列的。

- `flat` 属性返回一个迭代器，使得可以轻松地遍历多维数组的所有元素，而无需关心其维度结构。例如：
```python
import numpy as np

arr = np.array([[1, 2], [3, 4]])
for element in arr.flat:
    print(element)
```
```
1
2
3
4
```
- 这段代码将打印出数组 `arr` 中的所有元素。

#### <font class="text-color-101" color="#8bc34a">flatten()</font>

- **返回值：** `flatten` 函数返回一个新的一维数组，其中包含了原始多维数组的所有元素的拷贝。如果原始数组的形状发生变化，不会影响 `flatten` 返回的数组。

- `flatten` 函数用于将多维数组转换为一维数组。与 `reshape` 不同，`flatten` 总是返回一个新的一维数组，而不是一个视图。例如：
```python
import numpy as np

arr = np.array([[1, 2], [3, 4]])
flattened_arr = arr.flatten()
```
- 在这个示例中，`flattened_arr` 是一个新的一维数组，包含了原始数组 `arr` 中的所有元素。

#### <font class="text-color-101" color="#8bc34a">ravel()</font>

- **返回值：** `ravel` 函数与 `flatten` 类似，返回一个新的一维数组，包含了原始多维数组的所有元素。但不同之处在于，`ravel` 尝试返回一个视图（视图是原始数据的引用），而不是拷贝。

`ravel` 函数用于将多维数组转换为一维数组，但与 `flatten` 不同，它尝试返回视图，这意味着在某些情况下，对返回的数组进行修改会影响原始数组。例如：
```python
import numpy as np

arr = np.array([[1, 2], [3, 4]])
raveled_arr = arr.ravel()
```
- 在这个示例中，`raveled_arr` 是一个新的一维数组，但它可能会是原始数组 `arr` 的视图，这意味着对 `raveled_arr` 的修改可能会反映到 `arr` 中。

### <font class="text-color-15" color="#ff9800">翻转数组</font>
#### <font class="text-color-101" color="#8bc34a">transpose()</font>

- **参数：** `axes`，一个整数元组或整数列表，用于指定轴的新顺序。默认值是 `None`，表示按照原始数组的轴顺序进行转置。
- **返回值：** 返回一个新的数组，其轴的顺序根据指定的 `axes` 参数重新排列。

`transpose` 函数用于重新排列多维数组的轴，可以实现矩阵的转置或者改变数组的维度。例如：
```python
import numpy as np

arr = np.array([[1, 2], [3, 4]])
transposed_arr = arr.transpose()
```
- 在这个示例中，`transposed_arr` 是数组 `arr` 的转置，结果为 `[[1, 3], [2, 4]]`。

#### <font class="text-color-101" color="#8bc34a">ndarray.T 属性</font>

- **返回值：** `T` 是一个属性，用于返回数组的转置。它与 `transpose()` 函数的效果相同，但使用更加简便。

`ndarray.T` 属性用于获取数组的转置。例如：
```python
import numpy as np

arr = np.array([[1, 2], [3, 4]])
transposed_arr = arr.T
```
- 在这个示例中，`transposed_arr` 是数组 `arr` 的转置。

#### <font class="text-color-101" color="#8bc34a">rollaxis()</font>

- **参数：** `axis`，一个整数，表示要滚动到的位置。
- **返回值：** 返回一个新的数组，其中指定轴被滚动到指定位置。

`rollaxis` 函数用于将指定的轴滚动到新的位置，以改变数组的维度。例如：
```python
import numpy as np

arr = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])
rolled_arr = np.rollaxis(arr, axis=2, start=0)
```
- 在这个示例中，`rolled_arr` 将原始数组 `arr` 的第三个轴（axis=2）滚动到了第一个位置（start=0），结果是一个新的数组，其维度顺序发生了变化。

#### <font class="text-color-101" color="#8bc34a">swapaxes()</font>

- **参数：** `axis1` 和 `axis2`，两个整数，表示要交换位置的轴。
- **返回值：** 返回一个新的数组，其中指定的两个轴的顺序交换。

`swapaxes` 函数用于交换数组的两个指定轴的位置。例如：
```python
import numpy as np

arr = np.array([[1, 2], [3, 4]])
swapped_arr = np.swapaxes(arr, axis1=0, axis2=1)
```
- 在这个示例中，`swapped_arr` 是数组 `arr` 的一个新的版本，其中第一个轴和第二个轴的位置被交换了。

### <font class="text-color-15" color="#ff9800">修改数组维度</font>
#### <font class="text-color-101" color="#8bc34a">broadcast_to</font>

`broadcast_to` 是一个函数，用于将一个数组广播到指定的新形状，返回一个新的数组。这个函数用于显式地改变数组的形状，使其匹配广播的需求。这可以是有用的，特别是当你需要将一个数组广播到与另一个数组具有相同形状的情况下。

示例：
```python
import numpy as np

a = np.array([1, 2, 3])
b = np.broadcast_to(a, (3, 3))

# b 是 a 广播到 (3, 3) 形状的结果
# b 的值是：
# array([[1, 2, 3],
#        [1, 2, 3],
#        [1, 2, 3]])
```
#### <font class="text-color-101" color="#8bc34a">expand_dims</font>

`expand_dims` 是一个函数，用于在数组中插入新的维度。它接受一个数组和一个轴的索引作为参数，并在指定轴上插入一个新的维度。这对于改变数组的形状或准备进行广播操作时非常有用。

示例：
```python
import numpy as np

a = np.array([1, 2, 3])
b = np.expand_dims(a, axis=0)

# b 是在原数组 a 上插入新维度的结果
# b 的形状是 (1, 3)
```
#### <font class="text-color-101" color="#8bc34a">squeeze</font>

`squeeze` 是一个函数，用于删除数组中维度为1的轴。它返回一个新的数组，其中已经删除了所有维度为1的轴。这对于降低数组的维度或消除不必要的维度非常有用。

示例:
```python
import numpy as np

a = np.array([[[1, 2, 3]]])
b = np.squeeze(a)

# b 是去除了所有维度为1的轴后的结果
# b 的形状是 (3,)
```

### <font class="text-color-15" color="#ff9800">连接数组</font>
#### <font class="text-color-101" color="#8bc34a">concatenate</font>

`concatenate` 函数用于连接沿着现有轴的数组序列，返回一个新的数组。你需要提供一个包含要连接数组的序列（通常是元组或列表）以及要连接的轴。默认情况下，它在现有轴上连接数组。

示例：
```python
import numpy as np

a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
c = np.concatenate((a, b))

# c 是 a 和 b 连接在一起的结果
# c 的值是 [1, 2, 3, 4, 5, 6]
```
#### <font class="text-color-101" color="#8bc34a">stack</font>

`stack` 函数用于沿新的轴将一系列数组堆叠在一起。你需要提供一个包含要堆叠的数组的序列（通常是元组或列表）以及要堆叠的轴。新的轴将在指定位置插入。

示例：
```python
import numpy as np

a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
c = np.stack((a, b), axis=0)

# c 是将 a 和 b 沿新的轴（axis=0）堆叠在一起的结果
# c 的形状是 (2, 3)
# c 的值是:
# array([[1, 2, 3],
#        [4, 5, 6]])
```
#### <font class="text-color-101" color="#8bc34a">hstack</font>

`hstack` 函数用于水平堆叠序列中的数组，也就是按列方向连接数组。它相当于 `concatenate` 函数在轴1上的操作。

示例：
```python
import numpy as np

a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
c = np.hstack((a, b))

# c 是 a 和 b 在水平方向堆叠的结果
# c 的形状是 (6,)
# c 的值是 [1, 2, 3, 4, 5, 6]
```
#### <font class="text-color-101" color="#8bc34a">vstack</font>

`vstack` 函数用于竖直堆叠序列中的数组，也就是按行方向连接数组。它相当于 `concatenate` 函数在轴0上的操作。

示例：
```python
import numpy as np

a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
c = np.vstack((a, b))

# c 是 a 和 b 在竖直方向堆叠的结果
# c 的形状是 (2, 3)
# c 的值是:
# array([[1, 2, 3],
#        [4, 5, 6]])
```
### <font class="text-color-15" color="#ff9800">分割数组</font>
#### <font class="text-color-101" color="#8bc34a">split</font>

`split` 函数用于将一个数组沿指定的轴分割成多个子数组。你需要提供要分割的数组、分割的位置或索引以及分割的轴。该函数返回分割后的子数组列表。

示例：
```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5, 6])
sub_arrays = np.split(arr, [2, 4])

# sub_arrays 包含三个子数组，分割点是索引2和4
# sub_arrays 的值分别是 [1, 2], [3, 4], [5, 6]
```
#### <font class="text-color-101" color="#8bc34a">hsplit</font>

`hsplit` 函数用于将一个数组水平分割成多个子数组，按列进行分割。你可以指定分割的位置或子数组的数量。它通常用于将多列数据拆分为单独的列。

示例：
```python
import numpy as np

arr = np.array([[1, 2, 3],
                [4, 5, 6]])
sub_arrays = np.hsplit(arr, 3)

# sub_arrays 包含三个子数组，每个子数组包含一列
# sub_arrays 的值分别是:
[[1]
 [4]]

[[2]
 [5]]

[[3]
 [6]]
```
#### <font class="text-color-101" color="#8bc34a">vsplit</font>

`vsplit` 函数用于将一个数组垂直分割成多个子数组，按行进行分割。你可以指定分割的位置或子数组的数量。它通常用于将多行数据拆分为单独的行。

示例：
```python
import numpy as np

arr = np.array([[1, 2, 3],
                [4, 5, 6]])
sub_arrays = np.vsplit(arr, 2)

# sub_arrays 包含两个子数组，每个子数组包含一行
# sub_arrays 的值分别是:
# [[1, 2, 3]],
# [[4, 5, 6]]
```

### <font class="text-color-15" color="#ff9800">数组元素的添加与删除</font>
#### <font class="text-color-101" color="#8bc34a">resize</font>

`resize` 函数用于返回一个指定形状的新数组，可以用于改变数组的形状。如果新形状大于原始数组的大小，将会在新数组中填充重复的数据；如果新形状小于原始数组的大小，将会截断数组的元素。

示例：
```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])
new_arr = np.resize(arr, (3, 2))

# new_arr 是一个 (3, 2) 形状的新数组
# new_arr 的值是:
# array([[1, 2],
#        [3, 4],
#        [5, 1]])
```
#### <font class="text-color-101" color="#8bc34a">append</font>

`append` 函数用于将值添加到数组的末尾，创建一个新数组。你需要提供要添加的值和要添加的轴（如果未指定轴，默认为展平数组）。

示例：
```python
import numpy as np

arr = np.array([1, 2, 3])
new_arr = np.append(arr, [4, 5])

# new_arr 是一个包含添加值的新数组
# new_arr 的值是 [1, 2, 3, 4, 5]
```
#### <font class="text-color-101" color="#8bc34a">insert</font>

`insert` 函数用于沿指定轴将值插入到指定下标之前，创建一个新数组。你需要提供要插入的数组、要插入的位置、要插入的值以及要插入的轴。

示例：
```python
import numpy as np

arr = np.array([1, 2, 3, 4])
new_arr = np.insert(arr, 2, [0.5, 0.6])

# new_arr 是在索引2之前插入值的新数组
# new_arr 的值是 [1.  2.  0.5 0.6 3.  4. ]
```
#### <font class="text-color-101" color="#8bc34a">delete</font>

`delete` 函数用于删除数组中某个轴的子数组，并返回删除后的新数组。你需要提供要删除的数组、要删除的位置以及要删除的轴。

示例：
```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])
new_arr = np.delete(arr, 2)

# new_arr 是删除索引2处的值后的新数组
# new_arr 的值是 [1, 2, 4, 5]
```
#### <font class="text-color-101" color="#8bc34a">unique</font>

`unique` 函数用于查找数组内的唯一元素，并返回按升序排列的唯一元素数组。这个函数常用于查找数组中的不重复值。

示例：
```python
import numpy as np

arr = np.array([3, 1, 2, 2, 3, 1, 4])
unique_values = np.unique(arr)

# unique_values 是按升序排列的唯一元素数组
# unique_values 的值是 [1, 2, 3, 4]
```
## <font class="text-color-13" color="#ffeb3b">位运算</font>
#### <font class="text-color-11" color="#8bc34a">bitwise_and</font>

`bitwise_and` 函数对数组元素执行位与操作，即对数组的每个元素执行按位与运算。这意味着它将数组中的每个元素的二进制表示的对应位进行与操作。

示例：
```python
import numpy as np

arr1 = np.array([2, 5, 7])
arr2 = np.array([4, 4, 1])
result = np.bitwise_and(arr1, arr2)

# result 是数组 arr1 和 arr2 对应元素的位与操作结果
# result 的值是 [0, 4, 1]
```
#### <font class="text-color-101" color="#8bc34a">bitwise_or</font>

`bitwise_or` 函数对数组元素执行位或操作，即对数组的每个元素执行按位或运算。这意味着它将数组中的每个元素的二进制表示的对应位进行或操作。

示例：
```python
import numpy as np

arr1 = np.array([2, 5, 7])
arr2 = np.array([4, 4, 1])
result = np.bitwise_or(arr1, arr2)

# result 是数组 arr1 和 arr2 对应元素的位或操作结果
# result 的值是 [6, 5, 7]
```
#### <font class="text-color-101" color="#8bc34a">invert</font>

`invert` 函数对数组中的元素执行按位取反操作，即对数组的每个元素执行位非运算。这意味着它将数组中的每个元素的二进制表示的对应位进行取反操作。

示例：
```python
import numpy as np

arr = np.array([2, 5, 7])
result = np.invert(arr)

# result 是数组 arr 中元素的按位取反结果
# result 的值是 [-3, -6, -8]
```
#### <font class="text-color-101" color="#8bc34a">left_shift</font>

`left_shift` 函数将数组中的元素向左移动指定的位数，即对数组的每个元素执行左移操作。这意味着它将数组中的每个元素的二进制表示的位向左移动。

示例：
```python
import numpy as np

arr = np.array([2, 5, 7])
result = np.left_shift(arr, 2)

# result 是数组 arr 中元素向左移动2位后的结果
# result 的值是 [ 8, 20, 28]
```

#### <font class="text-color-101" color="#8bc34a">right_shift</font>

`right_shift` 函数将数组中的元素向右移动指定的位数，即对数组的每个元素执行右移操作。这意味着它将数组中的每个元素的二进制表示的位向右移动。

示例：
```python
import numpy as np

arr = np.array([16, 8, 4])
result = np.right_shift(arr, 2)

# result 是数组 arr 中元素向右移动2位后的结果
# result 的值是 [4, 2, 1]
```

## <font class="text-color-13" color="#ffeb3b">字符串函数</font>
- 以下函数用于对 dtype 为 numpy.string_ 或 numpy.unicode_ 的数组执行向量化字符串操作。 它们基于 Python 内置库中的标准字符串函数。

- 这些函数在字符数组类（numpy.char）中定义。

| 方法          | 描述                                       |
|--------------|--------------------------------------------|
| add()        | 对两个数组的逐个字符串元素进行连接        |
| multiply()   | 返回按元素多重连接后的字符串              |
| center()     | 居中字符串                                |
| capitalize() | 将字符串第一个字母转换为大写              |
| title()      | 将字符串的每个单词的第一个字母转换为大写  |
| lower()      | 数组元素转换为小写                         |
| upper()      | 数组元素转换为大写                         |
| split()      | 指定分隔符对字符串进行分割，并返回数组列表 |
| splitlines() | 返回元素中的行列表，以换行符分割           |
| strip()      | 移除元素开头或者结尾处的特定字符           |
| join()       | 通过指定分隔符来连接数组中的元素           |
| replace()    | 使用新字符串替换字符串中的所有子字符串    |
| decode()     | 数组元素依次调用str.decode                |
| encode()     | 数组元素依次调用str.encode                |

## <font class="text-color-13" color="#ffeb3b">数学函数</font>

### <font class="text-color-15" color="#ff9800">三角函数</font>
- NumPy 提供了标准的三角函数：sin()、cos()、tan()
```python
import numpy as np

# 输入角度（以弧度表示）
angle = np.array([0, np.pi/4, np.pi/2, np.pi])

# 计算正弦值
sine_values = np.sin(angle)

# 计算余弦值
cosine_values = np.cos(angle)

# 计算正切值
tangent_values = np.tan(angle)

# 输出结果
print("输入角度（弧度）:", angle)
print("正弦值:", sine_values)
print("余弦值:", cosine_values)
print("正切值:", tangent_values)
```
```
输入角度（弧度）: [0.         0.78539816 1.57079633 3.14159265]
正弦值: [0.0000000e+00 7.0710678e-01 1.0000000e+00 1.2246468e-16]
余弦值: [ 1.000000e+00  7.071068e-01  6.123234e-17 -1.000000e+00]
正切值: [ 0.00000000e+00  1.00000000e+00  1.63312394e+16 -1.22464680e-16]
```
* `numpy.degrees()` 函数用于将弧度转换为角度。它接受一个包含弧度值的 NumPy 数组作为输入，并返回一个包含对应角度值的新数组。这对于将弧度表示的角度转换为度数表示的角度非常有用。
```python
import numpy as np

# 输入弧度值
radians = np.array([0, np.pi/2, np.pi, 2*np.pi])

# 将弧度转换为角度
degrees = np.degrees(radians)

# 输出结果
print("输入弧度:", radians)
print("对应角度（度数表示）:", degrees)
```
```
输入弧度: [0.         1.57079633 3.14159265 6.28318531]
对应角度（度数表示）: [  0.  90. 180. 360.]
```

### <font class="text-color-15" color="#ff9800">舍入函数</font>
- `numpy.around()`, `numpy.floor()`, 和 `numpy.ceil()` 是 NumPy 中用于处理浮点数的舍入和取整操作的函数。
```python
import numpy as np

# 输入浮点数数组
arr = np.array([1.25, 2.75, 3.5, 4.6])

# 使用 numpy.around() 进行四舍五入
rounded_arr = np.around(arr, decimals=1)

# 使用 numpy.floor() 进行向下取整
floor_arr = np.floor(arr)

# 使用 numpy.ceil() 进行向上取整
ceil_arr = np.ceil(arr)

# 输出结果
print("原始数组:", arr)
print("四舍五入结果:", rounded_arr)
print("向下取整结果:", floor_arr)
print("向上取整结果:", ceil_arr)
```
```
原始数组: [1.25 2.75 3.5  4.6 ]
四舍五入结果: [1.2 2.8 3.5 4.6]
向下取整结果: [1. 2. 3. 4.]
向上取整结果: [2. 3. 4. 5.]
```

### <font class="text-color-15" color="#ff9800">算数函数</font>
- NumPy 算术函数包含简单的加减乘除: **add()**，**subtract()**，**multiply()** 和 **divide()**。

- 需要注意的是数组必须具有相同的形状或符合数组广播规则。
```python
import numpy as np

# 输入两个数组
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])

# 使用 add() 进行加法操作
add_result = np.add(arr1, arr2)

# 使用 subtract() 进行减法操作
subtract_result = np.subtract(arr1, arr2)

# 使用 multiply() 进行乘法操作
multiply_result = np.multiply(arr1, arr2)

# 使用 divide() 进行除法操作
divide_result = np.divide(arr1, arr2)

# 输出结果
print("arr1:", arr1)
print("arr2:", arr2)
print("加法结果:", add_result)
print("减法结果:", subtract_result)
print("乘法结果:", multiply_result)
print("除法结果:", divide_result)
```
```
arr1: [1 2 3]
arr2: [4 5 6]
加法结果: [5 7 9]
减法结果: [-3 -3 -3]
乘法结果: [ 4 10 18]
除法结果: [0.25 0.4  0.5 ]
```
- `numpy.reciprocal()`, `numpy.power()`, 和 `numpy.mod()` 是 NumPy 中用于执行不同数学运算的函数，分别用于计算倒数、幂次方和取模运算。
```python
import numpy as np

# 输入数组
arr = np.array([2, 4, 8])
base = np.array([2, 3, 4])
exponent = np.array([2, 3, 2])
dividend = np.array([10, 15, 20])
divisor = np.array([3, 4, 7])

# 使用 numpy.reciprocal() 计算倒数
reciprocal_arr = np.reciprocal(arr)

# 使用 numpy.power() 计算幂次方
power_result = np.power(base, exponent)

# 使用 numpy.mod() 计算取模运算
mod_result = np.mod(dividend, divisor)

# 输出结果
print("原始数组 arr:", arr)
print("倒数结果 reciprocal_arr:", reciprocal_arr)
print("底数数组 base:", base)
print("指数数组 exponent:", exponent)
print("幂次方结果 power_result:", power_result)
print("被除数数组 dividend:", dividend)
print("除数数组 divisor:", divisor)
print("取模运算结果 mod_result:", mod_result)
```
```
原始数组 arr: [2 4 8]
倒数结果 reciprocal_arr: [0.5   0.25  0.125]
底数数组 base: [2 3 4]
指数数组 exponent: [2 3 2]
幂次方结果 power_result: [ 4 27 16]
被除数数组 dividend: [10 15 20]
除数数组 divisor: [3 4 7]
取模运算结果 mod_result: [1 3 6]
```

### <font class="text-color-15" color="#ff9800">统计函数</font>
- `numpy.amin()` 和 `numpy.amax()` 是 NumPy 中用于计算数组中最小值和最大值的函数。它们可以用于在数组中查找最小和最大的元素，并提供了参数来指定轴的操作。
```python
import numpy as np

# 示例使用的数组
arr = np.array([3, 7, 1, 9, 2])
matrix = np.array([[3, 7, 1], [9, 2, 6]])

# 使用 numpy.amin() 计算最小值
min_value = np.amin(arr)

# 使用 numpy.amin() 沿指定轴计算最小值
min_values_by_column = np.amin(matrix, axis=0)

# 使用 numpy.amax() 计算最大值
max_value = np.amax(arr)

# 使用 numpy.amax() 沿指定轴计算最大值
max_values_by_row = np.amax(matrix, axis=1)

# 输出结果
print("原始数组 arr:", arr)
print("最小值 min_value:", min_value)
print("每列的最小值 min_values_by_column:", min_values_by_column)
print("\n原始数组 arr:", arr)
print("最大值 max_value:", max_value)
print("每行的最大值 max_values_by_row:", max_values_by_row)
```
```
原始数组 arr: [3 7 1 9 2]
最小值 min_value: 1
每列的最小值 min_values_by_column: [3 1 1]

原始数组 arr: [3 7 1 9 2]
最大值 max_value: 9
每行的最大值 max_values_by_row: [7 9]
```

- `numpy.ptp()`, `numpy.percentile()`, `numpy.median()`, `numpy.mean()`, 和 `numpy.average()` 是 NumPy 中用于统计和描述数组数据的函数。它们分别用于计算数据的范围、百分位数、中位数、平均值和加权平均值。
```python
import numpy as np

# 示例使用的数组和权重数组
arr = np.array([3, 7, 1, 9, 2])
weights = np.array([0.1, 0.2, 0.3, 0.2, 0.2])

# 使用 numpy.ptp() 计算数据范围
data_range = np.ptp(arr)

# 使用 numpy.percentile() 计算中位数
percentile_50 = np.percentile(arr, 50)

# 使用 numpy.median() 计算中位数
median_value = np.median(arr)

# 使用 numpy.mean() 计算平均值
mean_value = np.mean(arr)

# 使用 numpy.average() 计算加权平均值
weighted_mean = np.average(arr, weights=weights)

# 输出结果
print("原始数组 arr:", arr)
print("数据范围 data_range:", data_range)
print("中位数 percentile_50:", percentile_50)
print("中位数 median_value:", median_value)
print("平均值 mean_value:", mean_value)
print("加权平均值 weighted_mean:", weighted_mean)
```
```
原始数组 arr: [3 7 1 9 2]
数据范围 data_range: 8
中位数 percentile_50: 3.0
中位数 median_value: 3.0
平均值 mean_value: 4.4
加权平均值 weighted_mean: 4.2
```

### <font class="text-color-15" color="#ff9800">排序函数</font>
#### <font class="text-color-101" color="#8bc34a">numpy.sort()</font>

`numpy.sort()` 函数用于对数组进行排序。它接受一个数组作为输入，并返回一个新的数组，其中的元素按升序排列。

示例：
```python
import numpy as np

arr = np.array([3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5])
sorted_arr = np.sort(arr)

# sorted_arr 包含了 arr 中的元素按升序排列的结果
# sorted_arr 的值是 [1 1 2 3 3 4 5 5 5 6 9]
```
- 你也可以使用 `axis` 参数来指定排序的轴，以便在多维数组中排序。

#### <font class="text-color-101" color="#8bc34a">numpy.argsort()</font>

`numpy.argsort()` 函数用于返回数组中元素的索引，这些索引表示在排序后的顺序中元素的位置。它接受一个数组作为输入，并返回一个新的数组，其中的元素是原始数组中元素的索引。

示例：
```python
import numpy as np

arr = np.array([3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5])
indices = np.argsort(arr)

# indices 包含了原始数组 arr 中元素的索引，按升序排列
# indices 的值是 [1 3 6 0 9 2 4 8 10 7 5]
```
#### <font class="text-color-101" color="#8bc34a">numpy.lexsort()</font>

`numpy.lexsort()` 函数用于对多个键（数组）进行间接排序。它接受一个或多个数组作为输入，并返回一个排序后的索引数组，该数组表示了如何对输入数组进行排序，以便按照键的优先级进行排序。

示例：
```python
import numpy as np

last_names = np.array(['Smith', 'Johnson', 'Brown', 'Taylor', 'Clark'])
first_names = np.array(['John', 'Jane', 'Bob', 'Sarah', 'David'])
indices = np.lexsort((last_names, first_names))

# indices 包含了对 last_names 和 first_names 进行排序的索引
# indices 的值是 [2 4 0 3 1]
```
- 在这个示例中，`numpy.lexsort()` 按照姓氏（`last_names`）的字母顺序对数据进行排序，然后在姓氏相同的情况下按照名字（`first_names`）的字母顺序进行排序。

#### <font class="text-color-101" color="#8bc34a">numpy.msort()</font>

`numpy.msort()` 函数用于对多维数组进行排序。它接受一个数组作为输入，并返回一个新的数组，其中的元素按升序排列。

示例：
```python
import numpy as np

arr = np.array([[3, 1, 4], [1, 5, 2]])
sorted_arr = np.msort(arr)

# sorted_arr 包含了 arr 中的元素按升序排列的结果
# sorted_arr 的值是 [[1 1 2]
#                   [3 4 5]]
```
- 与 `numpy.sort()` 不同，`numpy.msort()` 可以对多维数组按照所有元素进行排序。

#### <font class="text-color-101" color="#8bc34a">numpy.sort_complex()</font>

`numpy.sort_complex()` 函数用于对复数数组进行排序。它接受一个复数数组作为输入，并返回一个新的复数数组，其中的复数按升序排列，首先按实部排序，然后按虚部排序。

示例：
```python
import numpy as np

complex_arr = np.array([2 + 1j, 1 + 3j, 4 - 2j, 3 + 2j])
sorted_complex_arr = np.sort_complex(complex_arr)

# sorted_complex_arr 包含了 complex_arr 中的复数按升序排列的结果
# sorted_complex_arr 的值是 [1.+3.j 2.+1.j 3.+2.j 4.-2.j]
```
#### <font class="text-color-101" color="#8bc34a">numpy.partition()</font>

`numpy.partition()` 函数用于在数组中分割数据，使得分割点左边的元素小于等于分割点右边的元素。它接受一个数组和分割点的索引作为输入，并返回一个新的数组，其中分割点左边的元素是最小的，分割点右边的元素是最大的。

示例：
```python
import numpy as np

arr = np.array([3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5])
partitioned_arr = np.partition(arr, 4)

# partitioned_arr 包含了 arr 中的元素，其中分割点左边的元素是最小的，分割点右边的元素是最大的
# partitioned_arr 的值是 [1 1 2 3 3 4 5 5 6 9 5]
```

#### <font class="text-color-101" color="#8bc34a">numpy.argpartition()</font>

`numpy.argpartition()` 函数用于返回数组中元素的索引，这些索引表示在分割后的顺序中元素的位置。它接受一个数组和分割点的索引作为输入，并返回一个新的数组，其中的元素是原始数组中元素的索引。

示例：
```python
import numpy as np

arr = np.array([3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5])
indices = np.argpartition(arr, 4)

# indices 包含了原始数组 arr 中元素的索引，按分割后的顺序排列
# indices 的值是 [3 1 6 0 9 2 4 8 7 5 10]
```


### <font class="text-color-15" color="#ff9800">条件筛选函数</font>
#### <font class="text-color-101" color="#8bc34a">numpy.nonzero()</font>

`numpy.nonzero()` 函数用于查找数组中非零元素的索引位置。它返回一个元组，其中包含了非零元素的索引，每个元素都是一个数组，对应于一个轴。
```python
import numpy as np

arr = np.array([3, 0, 0, 1, 0, 2])
nonzero_indices = np.nonzero(arr)

# nonzero_indices 包含了数组 arr 中非零元素的索引
# nonzero_indices 的值是 (array([0, 3, 5]),)
```
* 在多维数组中，`nonzero()` 返回的元组包含了每个轴上非零元素的索引。

#### <font class="text-color-101" color="#8bc34a">numpy.extract() </font>

`numpy.extract()` 函数用于从数组中提取满足条件的元素。它接受一个条件数组和一个待操作的数组作为输入，然后返回一个新的数组，其中包含满足条件的元素。

示例：
```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5, 6])
condition = (arr % 2 == 0)
extracted_values = np.extract(condition, arr)

# extracted_values 包含了数组 arr 中满足条件 (偶数) 的元素
# extracted_values 的值是 [2 4 6]
```

#### <font class="text-color-101" color="#8bc34a">numpy.where()</font>

`numpy.where()` 函数用于根据条件选择元素。它接受一个条件数组和两个待选择的数组作为输入，然后返回一个新的数组，其中包含根据条件选择的元素。

示例：
```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5, 6])
condition = (arr % 2 == 0)
selected_values = np.where(condition, arr, 0)

# selected_values 包含了根据条件选择的元素，偶数元素保留，奇数元素用 0 填充
# selected_values 的值是 [0 2 0 4 0 6]
```
- 你还可以使用 `numpy.where()` 来根据条件创建新的数组。

### <font class="text-color-15" color="#ff9800">字节交换函数</font>
* `numpy.ndarray.byteswap()` 方法用于在数组元素的字节表示中切换字节顺序。它可以将大端字节顺序（Big-Endian）切换为小端字节顺序（Little-Endian），或者反之。

- 字节顺序通常在处理二进制数据时很重要，特别是在不同的计算机体系结构之间传递数据时。例如，x86 架构的计算机通常使用小端字节顺序，而其他体系结构（如 SPARC 或 PowerPC）可能使用大端字节顺序。如果你需要在不同体系结构之间交换数据，可能需要使用 `byteswap()` 方法。
```python
import numpy as np

# 创建一个包含整数的数组，并显示它的字节表示
arr = np.array([1, 2, 3, 4], dtype=np.int32)
print("原始数组的字节表示：")
print(arr.tobytes())

# 使用 byteswap() 切换字节顺序
arr.byteswap(True)  # 将大端字节顺序切换为小端字节顺序

# 显示切换后的字节表示
print("切换字节顺序后的字节表示：")
print(arr.tobytes())
```
## <font class="text-color-13" color="#ffeb3b">副本和视图</font>
- 在 NumPy 中，数组的副本和视图是两种不同的概念，它们影响着数据的复制和共享。理解这两者之间的区别对于有效地处理大型数据集和节省内存非常重要。

### <font class="text-color-15" color="#ff9800">**副本（Copy)**</font>

副本是一个完全独立于原始数组的新数组。当你创建一个数组的副本时，它将复制原始数组的数据和结构，这意味着对副本的任何操作都不会影响原始数组。

副本可以通过以下方式创建：

- 使用 `copy()` 方法或 `numpy.copy()` 函数。
- 使用切片操作，如 `arr.copy()`。
```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])
arr_copy = arr.copy()

# 修改副本的值不会影响原始数组
arr_copy[0] = 0
print("原始数组：", arr)
print("副本：", arr_copy)
```

### <font class="text-color-141" color="#ff9800">2. 视图（View）</font>

视图是一个共享原始数组数据的新数组，它与原始数组具有不同的数据结构或元数据。当你创建一个数组的视图时，它不会复制数据，而是与原始数据共享相同的数据缓冲区。因此，对视图的操作也会影响原始数组。

视图可以通过以下方式创建：

- 使用切片操作，如 `arr[1:4]`。
- 使用 `view()` 方法或 `numpy.ndarray.view()` 函数。

示例：
```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])
arr_view = arr[1:4]

# 修改视图的值会影响原始数组
arr_view[0] = 0
print("原始数组：", arr)
print("视图：", arr_view)
```

### **区别和注意事项：**
- 副本是独立的，对副本的操作不会影响原始数组。视图是原始数组的一部分，对视图的操作会反映在原始数组上。
  
- 副本需要额外的内存空间，因为它复制了整个数组的数据。视图共享内存，因此节省内存空间，但可能导致原始数据被修改。
  
- 在某些情况下，NumPy 可能会自动选择是创建副本还是视图。例如，在切片操作中，如果切片是连续的，NumPy 通常会创建视图，而如果切片不连续，它可能会创建副本。
  
- 如果你想确保创建副本而不是视图，可以使用 `copy()` 方法或 `numpy.copy()` 函数。
  
- 如果你想检查数组是否是视图，可以使用 `base` 属性。如果数组是视图，则 `base` 属性将指向原始数组；如果数组是副本，则 `base` 属性为 `None`。


## <font class="text-color-13" color="#ffeb3b">matlib库</font>
`matlib` 是 NumPy 库的一个子模块，提供了一些用于创建矩阵的工具函数。这些函数可以帮助你创建、操作和处理矩阵，尤其适用于线性代数和科学计算任务。

- 以下是一些创建自定义矩阵的方法：
```python
import numpy as np

# 方法1: 手动指定元素值创建矩阵
matrix1 = np.array([[1, 2, 3],
                    [4, 5, 6]])

# 方法2: 从嵌套列表创建矩阵
data = [[1, 2, 3],
        [4, 5, 6]]
matrix2 = np.array(data)

# 方法3: 生成单位矩阵
identity_matrix = np.eye(3)

# 方法4: 生成对角矩阵
diagonal_matrix = np.diag([1, 2, 3])

# 方法5: 使用随机数创建矩阵
random_matrix = np.random.rand(3, 3)

# 打印创建的矩阵
print("手动指定元素值创建的矩阵：")
print(matrix1)

print("从嵌套列表创建的矩阵：")
print(matrix2)

print("单位矩阵：")
print(identity_matrix)

print("对角矩阵：")
print(diagonal_matrix)

print("随机矩阵：")
print(random_matrix)
```

## <font class="text-color-13" color="#ffeb3b">linalg 库</font>
- `numpy.linalg` 是 NumPy 库中的线性代数模块，提供了许多用于线性代数运算的函数和工具，包括矩阵分解、求逆、行列式计算、特征值和特征向量计算等。这些函数对于科学计算、工程、机器学习等领域的任务非常有用。

### <font class="text-color-11" color="#8bc34a">numpy.linalg.dot(a, b)</font>
- 功能：计算两个数组的点积，即元素对应相乘，并将结果相加。如果输入是一维数组，这相当于标量积。对于多维数组，它执行通常的矩阵乘法。
  
- 示例：
```python
import numpy as np

a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
result = np.dot(a, b)  # 结果是 1*4 + 2*5 + 3*6 = 32
```

### <font class="text-color-101" color="#8bc34a">numpy.linalg.vdot(a, b)</font>
- 功能：计算两个向量的点积，这与 `numpy.dot(a, b.conjugate())` 相等。
  
- 示例：
```python
import numpy as np

a = np.array([1 + 2j, 3 + 4j])
b = np.array([5 + 6j, 7 + 8j])
result = np.vdot(a, b)  # 结果是 (1*5 - 2*6) + (2*5 + 1*6) + (3*7 - 4*8) + (4*7 + 3*8) = (-8 + 17j)
```

### <font class="text-color-101" color="#8bc34a">numpy.linalg.inner(a, b)</font>
- 功能：计算两个数组的内积，对于一维数组，这相当于点积；对于多维数组，有所不同
  
- 示例：
```python
import numpy as np

a = np.array([[1, 2],
              [3, 4]])
b = np.array([[5, 6],
              [7, 8]])
result = np.inner(a, b)  # 结果是 [[17, 23], [39, 53]]
```
### <font class="text-color-101" color="#8bc34a">numpy.linalg.determinant(a)</font>
- 功能：计算矩阵的行列式，返回一个标量值。
  
- 示例：
```python
import numpy as np

A = np.array([[1, 2],
              [3, 4]])
det_A = np.linalg.determinant(A)  # 结果是 -2.0
```

### <font class="text-color-101" color="#8bc34a">numpy.linalg.solve(a, b)</font>
- 功能：解线性矩阵方程 Ax = b，其中 A 是系数矩阵，b 是常数向量。返回解向量 x。
  
- 示例：
```python
import numpy as np

A = np.array([[2, 3],
              [1, -2]])
b = np.array([7, 1])
x = np.linalg.solve(A, b)  # 结果是 [3. 1.]
```

### <font class="text-color-101" color="#8bc34a">numpy.linalg.inv(a)</font>
- 功能：计算矩阵的乘法逆矩阵。如果矩阵不可逆或奇异，将引发 `LinAlgError`。
  
- 示例：
```python
import numpy as np

A = np.array([[1, 2],
              [3, 4]])
A_inv = np.linalg.inv(A)
```

## <font class="text-color-13" color="#ffeb3b">常用函数</font>

### <font class="text-color-15" color="#ff9800">np.prod()</font>
- `np.prod` 是 NumPy（Python 中用于科学计算的库）中的一个函数，用于计算给定数组中所有元素的乘积。该函数的语法如下：
```python
numpy.prod(a, axis=None, dtype=None, out=None, keepdims=<no value>, initial=<no value>, where=<no value>)
```
参数说明：

- `a`：要计算乘积的输入数组。
- `axis`：指定沿着哪个轴计算乘积。默认情况下（`axis=None`），将对整个数组的所有元素进行乘积计算。你也可以指定轴，以便在指定轴上计算乘积。例如，如果你有一个二维数组，可以指定 `axis=0` 来计算每列的乘积，或指定 `axis=1` 来计算每行的乘积。
- `dtype`：指定返回数组的数据类型。默认情况下，结果的数据类型与输入数组的数据类型相同。
- `out`：可选参数，用于指定输出数组，计算结果将存储在这个数组中。
- `keepdims`：如果设置为 `True`，则在计算乘积时保持输入数组的维度。默认情况下，`keepdims` 为 `False`，结果将是一个具有减少维度的数组。
- `initial`：可选参数，指定初始累积值。如果不指定，初始累积值将根据数据类型的特定规则进行选择。
- `where`：可选参数，用于指定一个条件数组，只有满足条件的元素才会参与乘积计算。如果不指定，所有元素都会参与计算。

示例：
```python
import numpy as np

arr = np.array([1, 2, 3, 4])
result = np.prod(arr)  # 计算数组中所有元素的乘积，结果为 24
```
```python
matrix = np.array([[1, 2], [3, 4]])
column_product = np.prod(matrix, axis=0)  # 计算每列的乘积，结果为 [3 8]
row_product = np.prod(matrix, axis=1)     # 计算每行的乘积，结果为 [ 2 12]
```

### <font class="text-color-15" color="#ff9800">np.random.rand(n) 小于 p</font>
- `np.random.rand(n) < p` 的结果是一个布尔值数组，该数组的长度与 `n` 相同，表示了在生成的 `n` 个随机数中，哪些小于概率 `p`，哪些不小于 `p`。
- 示例
```python
import numpy as np

# 模拟投掷硬币
n = 10  # 试验次数
p = 0.5  # 正面朝上的概率

# 生成布尔值数组，表示每次试验是否正面朝上
outcomes = np.random.rand(n) < p
# [ True  True False False  True  True  True False  True  True]

# 统计正面朝上的次数
num_heads = np.sum(outcomes)

print("投掷硬币正面朝上的次数:", num_heads)
```

### <font class="text-color-15" color="#ff9800">np.sum()</font>
- `np.sum` 是 NumPy 中用于计算数组元素之和的函数。它的语法如下：
```python
numpy.sum(a, axis=None, dtype=None, out=None, keepdims=<no value>, initial=<no value>, where=<no value>)
```
参数说明：

- `a`：要计算元素之和的输入数组。
- `axis`：指定沿着哪个轴计算和。默认情况下（`axis=None`），将对整个数组的所有元素进行求和。你也可以指定轴，以便在指定轴上计算和。例如，如果你有一个二维数组，可以指定 `axis=0` 来计算每列的和，或指定 `axis=1` 来计算每行的和。
- `dtype`：指定返回数组的数据类型。默认情况下，结果的数据类型与输入数组的数据类型相同。
- `out`：可选参数，用于指定输出数组，计算结果将存储在这个数组中。
- `keepdims`：如果设置为 `True`，则保持输入数组的维度。默认情况下，`keepdims` 为 `False`，结果将是一个降低维度的数组。
- `initial`：可选参数，指定初始累积值。如果不指定，初始累积值将根据数据类型的特定规则进行选择。
- `where`：可选参数，用于指定一个条件数组，只有满足条件的元素才会参与求和计算。如果不指定，所有元素都会参与计算。

示例：
```python
import numpy as np

arr = np.array([1, 2, 3, 4])
result = np.sum(arr)  # 计算数组中所有元素的和，结果为 10
```
```python
matrix = np.array([[1, 2], [3, 4]])
column_sum = np.sum(matrix, axis=0)  # 计算每列的和，结果为 [4 6]
row_sum = np.sum(matrix, axis=1)     # 计算每行的和，结果为 [3 7]
```

### <font class="text-color-141" color="#ff9800">argmax()</font>

`numpy.argmax()` 函数用于查找数组中的最大值，并返回最大值的索引位置。如果数组是多维的，你可以使用 `axis` 参数来指定沿某个轴查找最大值的索引。
```python
import numpy as np

matrix = np.array([[3, 7, 1], [9, 2, 6]])
max_indices_by_column = np.argmax(matrix, axis=0)

# max_indices_by_column 包含了每列中最大值的索引
# max_indices_by_column 的值是 [1 0 1]
```


### <font class="text-color-141" color="#ff9800">argmin()</font>
`numpy.argmin()` 函数用于查找数组中的最小值，并返回最小值的索引位置。同样，如果数组是多维的，你可以使用 `axis` 参数来指定沿某个轴查找最小值的索引。
```python
import numpy as np

matrix = np.array([[3, 7, 1], [9, 2, 6]])
min_indices_by_row = np.argmin(matrix, axis=1)

# min_indices_by_row 包含了每行中最小值的索引
# min_indices_by_row 的值是 [2 1]
```

### <font class="text-color-141" color="#ff9800">column_stack()</font>
- `np.column_stack` 是 NumPy 中的一个函数，用于将多个一维数组按列堆叠成一个二维数组。这个函数通常用于将多个一维数组合并成一个矩阵，其中每个一维数组成为矩阵的一列。下面是 `np.column_stack` 的详细说明：
```python
numpy.column_stack(tup)
```
- 示例：
```python
import numpy as np

# 创建两个一维数组
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])

# 使用 np.column_stack 将它们按列堆叠成一个二维数组
result = np.column_stack((arr1, arr2))

print(result)
```
```
[[1 4]
 [2 5]
 [3 6]]
```

### <font class="text-color-141" color="#ff9800">row_stack()</font>
- `np.row_stack` 是 NumPy 中的一个函数，用于将多个一维数组按行堆叠成一个二维数组。这个函数通常用于将多个一维数组合并成一个矩阵，其中每个一维数组成为矩阵的一行。下面是 `np.row_stack` 的详细说明：
```
numpy.row_stack(tup)
```
- 示例：
```python
import numpy as np

# 创建两个一维数组
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])

# 使用 np.row_stack 将它们按行堆叠成一个二维数组
result = np.row_stack((arr1, arr2))

print(result)
```
```
[[1 2 3]
 [4 5 6]]
```

### <font class="text-color-141" color="#ff9800">np.linalg.lstsq()</font>
- `np.linalg.lstsq` 是 NumPy 中的一个函数，用于执行最小二乘线性回归。最小二乘线性回归是一种用于拟合线性模型的方法，它试图找到一组系数，使得线性模型的预测值与实际观测值的残差平方和最小化。这个函数的详细说明如下：
```python
numpy.linalg.lstsq(a, b, rcond='warn')
```
参数说明：

- `a`：形状为 `(M, N)` 的二维数组，其中 `M` 表示观测数据的数量，`N` 表示自变量的数量（特征的数量）。
- `b`：形状为 `(M,)` 或 `(M, K)` 的一维或二维数组，其中 `M` 表示观测数据的数量，`K` 表示因变量的数量。通常情况下，`b` 是目标值，也就是实际观测到的因变量值。
- `rcond`：可选参数，表示奇异值分解（SVD）的截断值。默认值是 `'warn'`，表示如果计算中遇到奇异矩阵，则会发出警告。如果设置为一个浮点数值，它将用于控制奇异值的截断，过小的值可能会导致矩阵近似问题。

返回值：

`numpy.linalg.lstsq` 返回一个包含以下内容的元组 `(x, residuals, rank, s)`：

- `x`：包含线性回归系数的一维数组，即拟合的线性模型的权重。
- `residuals`：一个一维数组，表示残差（预测值与实际值的差异）。
- `rank`：矩阵 `a` 的秩。
- `s`：奇异值数组。

示例：
```python
import numpy as np

# 创建观测数据和目标值
X = np.array([[1, 1], [1, 2], [1, 3]])
y = np.array([2, 2.5, 3.5])

# 使用 np.linalg.lstsq 进行线性回归拟合
coefficients, residuals, rank, singular_values = np.linalg.lstsq(X, y, rcond=None)

print("拟合的系数（权重）:", coefficients)
print("残差:", residuals)
print("矩阵的秩:", rank)
print("奇异值数组:", singular_values)
```
```
拟合的系数（权重）: [1.16666667 0.75      ]
残差: [0.04166667]
矩阵的秩: 2
奇异值数组: [4.07914333 0.60049122]
```

### <font class="text-color-141" color="#ff9800">np.mean()</font>
- `np.mean` 是 NumPy 库中的一个函数，用于计算数组中元素的平均值。以下是关于 `np.mean` 函数的详细解释：
```python
numpy.mean(a, axis=None, dtype=None, out=None, keepdims=<no value>)
```
参数说明：

- `a`: 输入的数组，可以是一个一维或多维数组。
- `axis`: 沿着哪个轴计算平均值。默认情况下，计算整个数组的平均值。如果指定了轴，将沿着该轴计算平均值，得到一个新的数组，包含了沿着指定轴的平均值。轴的值可以是整数，也可以是元组，以计算多个轴的平均值。
- `dtype`: 指定结果的数据类型。默认为 None，表示结果的数据类型由输入数组的数据类型决定。
- `out`: 可选参数，用于指定计算结果存储的位置。如果提供了该参数，计算结果将保存在这个数组中，而不是创建一个新的数组。
- `keepdims`: 布尔值，指定是否保持结果的维度与输入数组相同。如果为 True，结果将具有与输入数组相同的维度，但维度大小为 1 的维度将保留。如果为 False（默认值），结果将是一个降维后的数组，即去掉维度大小为 1 的维度。

返回值

- `np.mean` 函数返回计算得到的平均值。

示例
- 对一维数组计算平均值
```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])
mean_value = np.mean(arr)
print(mean_value)  # 输出结果为 3.0
```





