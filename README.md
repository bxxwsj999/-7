# 实验七指针
##一、实验目的
1.熟练掌握指针、地址、指针类型、void 指针、空指针等概念。
2、熟练掌握指针变量的定义和初始化、指针的间接访问、指针的加减运算和指针表达式。
3、会使用数组的指针和指向数组的指针变量。
4、会使用字符串的指针和指向字符串的指针变量。
##二、实验准备
1、复习变量、变量的地址、指针变量的概念并明确区分这三个不同的概念，
2、复习指针和数组的结合应用。
3、复习指针的其他理论知识。
##三、实验内容
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *ptr;
    int size = 5;

    // 使用malloc动态分配内存，返回的指针赋值给ptr
    ptr = (int *)malloc(size * sizeof(int));
    if (ptr == NULL) {
        printf("内存分配失败！\n");
        return -1;
    }

    // 使用指针访问分配的内存空间，进行赋值操作
    for (int i = 0; i < size; i++) {
        ptr[i] = i + 1;
    }

    printf("动态分配内存中存储的元素：\n");
    for (int i = 0; i < size; i++) {
        printf("%d ", ptr[i]);
    }
    printf("\n");

    // 使用完后释放内存
    free(ptr);

    return 0;
}
这个示例展示了动态内存分配的过程。首先通过 malloc 函数申请了一段连续的整型内存空间，将返回的指针赋值给 ptr，然后可以像使用数组一样通过指针来访问这块内存空间进行赋值等操作，最后使用完内存后通过 free 函数释放所分配的内存，防止内存泄漏。
#include <stdio.h>

// 函数声明，参数为指针类型
void swap(int *a, int *b) {
    int temp;
    temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int num1 = 5, num2 = 10;
    printf("交换前：num1 = %d, num2 = %d\n", num1, num2);

    // 调用swap函数，传递变量的地址（即指针）
    swap(&num1, &num2);

    printf("交换后：num1 = %d, num2 = %d\n", num1, num2);

    return 0;
}
此代码定义了一个 swap 函数，其参数为两个指向整型的指针。在函数内部通过指针操作来交换所指向的两个变量的值。在 main 函数中，定义了两个整型变量，然后调用 swap 函数，传递变量的地址，实现两个变量值的交换.
