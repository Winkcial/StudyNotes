
struct _finddata_t 是用来存储文件各种信息的结构体，用到头文件为 io.h ，具体的定义如下：

```
struct _finddata_t
        {
             unsigned attrib;
             time_t time_create;
             time_t time_access;
             time_t time_write;
             _fsize_t size;
             char name[_MAX_FNAME];
        };
```

## **结构体各变量的含义**

**unsigned atrrib：** 表示文件的属性，是一个文件还是一个文件夹，文件属性是用位表示的，主要有以下一些：

```
_A_ARCH（存档）
_A_HIDDEN（隐藏）
_A_NORMAL（正常）
_A_RDONLY（只读）
_A_SUBDIR（文件夹）
_A_SYSTEM（系统）
```

这些都是宏，当一个文件有多个属性时，往往通过位或的方式，来得到几个属性的综合。

例如只读+隐藏+系统属性，应该为：_A_HIDDEN | _A_RDONLY | _A_SYSTEM 。

**time_t time_create：**这里的 time_t 是一个变量类型，实际上就是长整形变量 long int，用来保存从1970年1月1日0时0分0秒到现在时刻的秒数

**time_t time_access：**文件最后一次被访问的时间。

**time_t time_write：**文件最后一次被修改的时间。

**_fsize_t size：**文件的大小（字节数表示）。

**char name[_MAX_FNAME]**：文件的文件名。这里的_MAX_FNAME是一个常量宏，它在头文件中被定义，表示的是文件名的最大长度。

## 三个常用函数

如何使用这个结构体才能够将文件的信息存储到该结构体的内存空间呢，这就需要_findfirst（）、_findnext（）和_fineclose（）三个函数的搭配使用，下面介绍这三个函数：

`long _findfirst( char *filespec, struct _finddata_t *fileinfo )；`

- **返回值**：如果查找成功的话，将返回一个long型的唯一的查找用的句柄。这个句柄将会在_findnext函数中被使用。失败返回0.**

- **参数：**
  - filespec：标明文件的字符串，可支持通配符。比如：*.c，则表示当前文件夹下的所有后缀为C的文件。
  - fileinfo ：这里就是用来存放文件信息的结构体的指针。这个结构体必须在调用此函数前声明，不过不用初始化，只要分配了内存空间就可以了。函数成功后，函数会把找到的文件的信息放入这个结构体所分配的内存空间中。

 

`int _findnext( long handle, struct _finddata_t *fileinfo );`

- **返回值：**若成功返回0，否则返回-1。

## 一个应用的例子：遍历文件夹

### 遍历当前文件夹

### 遍历当前文件夹及其子目录

