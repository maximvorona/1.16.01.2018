# 1.16.01.2018


HI!


Выборка V1.

#include "stdafx.h"
#include <iostream>
#include <ctime>
#include <iomanip>
using namespace std;

void V1(int*, int); 

int main(int argc, char* argv[])
{
	srand(time(NULL)); 
	cout << "Size array: ";
	int size_array; cin >> size_array;

	int *sorted_array = new int[size_array]; 
	for (int counter = 0; counter < size_array; counter++)
	{
		sorted_array[counter] = rand() % 100; 
		cout << setw(2) << sorted_array[counter] << "  "; 
	}
	cout << "\n\n";

	V1(sorted_array, size_array); 

	for (int counter = 0; counter < size_array; counter++)
	{
		cout << setw(2) << sorted_array[counter] << "  "; 
	}
	cout << "\n";
	delete[] sorted_array; 
	system("pause");
	return 0;
}

void V1(int *ar, int size) {
	int i, j, mx, nmx;

	for (i = 0; i < size - 1; i++)
	{
		mx = ar[i];
		nmx = i;
		for (j = i + 1; j < size; j++)
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
