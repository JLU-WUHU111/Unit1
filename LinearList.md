# **Introduction**
**This file is about linear list.**

**If you want to go back to the content ,please click the link below.**


**[Back to content](README.md)**



# **Linear List**

↓I prepared a image below. But I can't show it after I try each way.
<!-- structure chart of linear list-->
![](https://raw.githubusercontent.com/JLU-WUHU111/Unit1/master/linearlist.jpg)
1. Basic operations for linear list
2. Sequence list
	1. Definition of sequence list
	2. Implementation of basic operations on sequence list
3. Compare


## **Basic operations for linear list**

```cpp
//Without the type of functions
InitList(&L);//Initialize
Length(L);//Length of list
LocateElem(L,e);//Locate element by value
GetElem(L,i);//Locate element by order
ListInsert(&L,i,e);//Insert element
ListDelete(&L,i,&e);//Delete element
PrintList(L);//Print the List
Empty(L);//Judge if empty
DestroyList(L);//Destroy the list
```

## **Sequence list**

### ***Definition of sequence list***

#### Static allocation

```cpp
//static allocation
#define MaxSize 50			//maxsize of list
typedef struct{
	ElemType data[MaxSize];	//element of list 
	int length;				//current length of list
}SqList;					//define type of list(static)  
```

#### Dynamic allocation 

```cpp
//dynamic allocation 
#define InitSize 100		//maxsize of list
typedef struct{
	ElemType *data;			//pointer to dynamically allocated arrays
	int MaxSize,length;		//maxsize of array && current length(number of element) of list
}SeqList;					//define type of list(dynamic)
```
If we use C to programming, we use 
```c
L.data = (ElemType*)malloc(sizeof(ElemType) * InitSize);
// don't forget to include<stdlib.h> to ensure the use of malloc and sizeof 
```

If we use C++ to programming, we use 
```cpp
L.data = new ElemType[InitSize];
```
### ***Implementation of basic operations on sequence list***

#### **1.Insert**

```cpp
//Insert element
bool ListInsert(SqList& L, int i, ElemType e) {
	if (i<1 || i>L.length + 1)				//determine whether the range of i is valid
		return false;
	if (L.length >= MaxSize)				//the current storage space is full and cannot be inserted
		return false;
	for (int j = L.length; j >= 1; j--)		//move the ith element and subsequent elements back
		L.data[j] = L.data[j - 1];			
	L.data[i - 1] = e;						//put e at position i
	L.length++;								//length of list add 1
	return true;
}
```
#### **2.Delete**

```cpp
//Delete element
bool ListDelete(SqList& L, int i, ElemType& e) {
	if (i<1 || i>L.length)					//determine whether the range of i is valid
		return false;
	e = L.data[i - 1];						//assign the deleted element to e
	for (int j = 1; j < L.length; j++)		//move the ith element and subsequent elements foeward
		L.data[j - 1] = L.data[j];
	L.length--;								//length of list minus 1
	return true;
}
```

#### **3.LocateElem**

```cpp
//Locate element by value
int LocateElem(SqList L, ElemType e) {
	int i;
	for (i = 0; i < L.length; i++)
		if (L.data[i] == e)					//return the  order i +1 for the element i in the following table whose value is e
			return i + 1;					//if the loop exits, the search fails
	return 0;
}
```

## **Compare**

<!-- Tables -->
using pointers | using arrays 
-------------- | ---------------
single linked list  | static linked list |
double linked list 
circular linked list









