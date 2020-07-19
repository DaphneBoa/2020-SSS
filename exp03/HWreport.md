# 二进制安全

## 实验目的

- [x] 一、读 VirtualAlloc、VirtualFree、VirtualProtect 等函数的官方文档；
- [ ] 二、编程使用 malloc 分配一段内存，测试是否这段内存所在的 4KB 全都可以写入读取；
- [ ] 三、使用 VirtualAlloc 分配一段**可读可写**的内存，然后写入内容，再改为只读状态，最后读数据、写数据，看看是否会有异常情况；然后 VirtualFree 这段内存，再测试对这段内存的读写释放是否正常。

## 实验步骤

### 一、读文档

`VirtualAlloc` 的官方文档链接：https://docs.microsoft.com/en-us/windows/win32/api/memoryapi/nf-memoryapi-virtualalloc

该函数用于分配虚拟地址空间，使用该函数分配出的内存默认初始化为0。

语法如下：

```c++
LPVOID VirtualAlloc(
  LPVOID lpAddress,
  SIZE_T dwSize,
  DWORD  flAllocationType,
  DWORD  flProtect
);
```

`VirtualFree` 的官方文档链接：https://docs.microsoft.com/en-us/windows/win32/api/memoryapi/nf-memoryapi-virtualfree

该函数用于释放虚拟地址空间。

语法如下：

```c++
BOOL VirtualFree(
  LPVOID lpAddress,
  SIZE_T dwSize,
  DWORD  dwFreeType
);
```

`VirtualProtect` 的官方文档链接：https://docs.microsoft.com/en-us/windows/win32/api/memoryapi/nf-memoryapi-virtualprotect

该函数用于更改对虚拟地址空间中已提交页面区域的保护。

语法如下：

```c++
BOOL VirtualProtect(
  LPVOID lpAddress,
  SIZE_T dwSize,
  DWORD  flNewProtect,
  PDWORD lpflOldProtect
);
```

### 二、编程使用 malloc

### 三、使用 VirtualAlloc