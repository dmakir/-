# -#include <iostream>
#include <algorithm>
#include <string> 
using namespace std;

struct Student
{
	string surname;
	int number;
	int progress[5];
};

int main()
{
	setlocale(LC_ALL, "ru");
	const int mas = 5;
	Student student[mas];
	int i, j;
	int summa = 0;
	int count = 0;

	for (i = 0; i < mas; i++)
	{
		cout << "Введите фамилию студента " << endl;
		cin >> student[i].surname;
		cout << "Введите номер группы " << endl;
		cin >> student[i].number;
		cout << "Введите 5 оценок " << endl;
		for (j = 0; j < 5; j++)
		{
			cout << j + 1 << ") ";
			cin >> student[i].progress[j];
		}
	}
	cout << endl << endl;

	for (i = 0; i < mas - 1; i++)
		for (j = 0; j < mas - 1; j++)
			if (student[j].number > student[j + 1].number)
			{
				Student temp;
				swap(temp, student[j]);
				swap(student[j], student[j + 1]);
				swap(student[j + 1], temp);
			}

	cout << "Список студентов " << endl;

	for (i = 0; i < mas; i++)
		cout << "Фамилия " << student[i].surname << " " << student[i].number << endl;

	cout << endl << endl;


	for (i = 0; i < mas; i++)
	{
		for (j = 0; j < 5; j++)
			summa += student[i].progress[j];
		if (summa / 5 >= 4)
		{
			cout << "Студенты у которых оценка выше 4 " << endl;
			cout << "Фамилия " << student[i].surname << " " << student[i].number << endl;
			count++;
		}

		summa = 0;
	}

	if (count == 0)
		cout << "Нет хорошистов " << endl;
}
