# 1.16.01.2018

#include "stdafx.h"
#include <iostream>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>
#include <time.h>

void selection(int *ar)
{
	int i, j, mx, nmx;
	for (i = 0; i < 100000 - 1; i++)
	{
		mx = ar[i];
		nmx = i;
		for (j = i + 1; j < 100000; j++)
		{
			if (ar[j]<mx)
			{
				mx = ar[j];
				nmx = j;
			}
		}
		ar[nmx] = ar[i];
		ar[i] = mx;
	}
}

void radix(int *ar, int *br, int *cr) {
	int i, k = 100000, n = 100000;
	for (i = 0; i <= k; i++)
		 cr[i] = 0;
	for (i = 0; i < n; i++)
		 cr[ar[i]] += 1;
	for (i = 1; i < k + 1; i++)
	 cr[i] += cr[i - 1];
	for (i = n - 1; i >= 0; i--)
	 {
	br[cr[ar[i]] - 1] = ar[i];
	cr[ar[i]] -= 1;
	}
}

void arrOut(int *ar)
{
	printf("\n%s\n", "Array:");
	for (int i = 0; i < 100000; i++)
		printf("%d\t", ar[i]);
	printf("\n");
}

int main()
{
	setlocale(LC_ALL, "Russian");
	clock_t start1, start2, end1, end2;
	int i, s1, s2;
	int *m1 = new int[100000];
	int *m2 = new int[100000];
	int *cr = new int[100000];
	int *br = new int[100000];
	for (i = 0; i < 100000; i++)
	{
		m1[i] = rand() % 20; 	m2[i] = rand() % 20;
	}
	start1 = clock(); selection(m1);
	end1 = clock(); s1 = end1 - start1;
	printf("%s %d\t", "Время Selection:", s1);
	
	start2 = clock(); radix(m2, br, cr);
	end2 = clock(); s2 = end2 - start2;
	printf("%s %d\t\n", "Время Radix:", s2);

	system("pause");
	return 0;
}
