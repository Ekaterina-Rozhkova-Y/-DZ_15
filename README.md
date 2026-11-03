# Лабораторная работа 15
# Вариант 22. Обработка строк

## Постановка задачи
Написать программу на языке C, которая запрашивает у пользователя строку и заменяет в ней все последовательные (подряд идущие) пробелы на один одиночный пробел. 

**Требования:**
* Использовать массивы символов (`char`) для хранения строки.
* Для ввода строки с пробелами использовать функцию `fgets()`.
* Выполнить обработку строки «на месте», без создания второго массива.

---

## Алгоритм и блок-схема

### Алгоритм

1. Ввести строку с помощью `fgets`.
2. Установить два счетчика: `i = 0` (читаем) и `j = 0` (записываем).
3. Запустить цикл `while`, пока не встретим конец строки (`\0`):
   * Скопировать символ `str[i]` в `str[j]`. Увеличить `j`.
   * Если встретился пробел — пропустить все следующие за ним пробелы (увеличивая `i`).
   * Увеличить `i` на 1.
4. В конце добавить `\0` в позицию `j`, чтобы закрыть строку.
5. Вывести результат.

### Блок-схема

<img width="489" height="812" alt="Диаграмма без назвмымымцымыания drawio" src="https://github.com/user-attachments/assets/63f23df5-7f1a-49e3-bac4-ddb8f6975b3b" />

## Код программы

#define _CRT_SECURE_NO_WARNINGS
#include <windows.h>
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include <locale.h>

int z1() {
    setlocale(LC_CTYPE, "RUS");

    char name[50];
    char greeting[100];

    puts("Пожалуйста, введите имя: ");
    scanf("%49s", name);

    strcpy(greeting, "Привет, ");
    strcat(greeting, name);

    puts(greeting);

}

int z1_1() {
    setlocale(LC_CTYPE, "RUS");

    char name[50];
    char greeting[100];

    puts("Пожалуйста, введите имя: ");
    scanf("%49s", name);

    for (int i = 0; name[i] != '\0'; i++) {
        name[i] = toupper(name[i]);
    }
    

    strcpy(greeting, "Привет, ");
    strcat(greeting, name);

    puts(greeting);

    return 0;
}
int z1_2() {
    setlocale(LC_CTYPE, "RUS");

    char name[50];
    char greeting[100];

    puts("Пожалуйста, введите имя: ");
    scanf("%49s", name);
    strcpy(greeting, "Привет, ");
    strcat(greeting, name);

    while (strlen(greeting) < 40) {
        strcat(greeting, "!");
    }
   
    puts(greeting);

    return 0;
}


int z2() {
    
        setlocale(LC_CTYPE, "RUS");
        SetConsoleCP(1251);
        SetConsoleOutputCP(1251);

        char name[50];
        char r1[100], r2[100], r3[100], r4[100], r5[100], r6[100];
        char r7[100], r8[100], r9[100], r10[100], r11[100], r12[100];

        printf("ЗАДАНИЕ 2:\n");
        printf("Введите имя: ");
        fgets(name, sizeof(name), stdin);
        name[strcspn(name, "\n")] = '\0';

        int l = (int)strlen(name);
        int k = 0;

       
        strcpy(r1, name);
        if (l > 0) {
            r1[l] = name[l - 1];
            r1[l + 1] = '\0';
        }


        strcpy(r2, name);
        strcpy(r2, name);
        if (l > 0) {
          
            r2[0] = tolower(name[0]);

            for (int i = 1; i < l; i++) {
                r2[i] = toupper(name[i]);
            }
        }

        strcpy(r3, name);
        if (l >= 2) {
            char temp = r3[0];
            r3[0] = r3[1];
            r3[1] = temp;
        }

  
        k = 0;
        for (int i = 0; i < l; i++) {
            if (i == l - 1) r4[k++] = '_';
            r4[k++] = name[i];
        }
        r4[k] = '\0';


        k = 0;
        for (int i = l - 1; i >= 0; i--) {
            r5[k++] = name[i];
        }
        r5[k] = '\0';


        k = 0;
        for (int i = 0; i < l; i++) {
            if (i == 1) continue;
            r6[k++] = name[i];
        }
        r6[k] = '\0';


        strcpy(r7, name);
        int half = l / 2;
        for (int i = 0; i < l; i++) {
            if (i < half) r7[i] = toupper(name[i]);
            else r7[i] = tolower(name[i]);
        }

        k = 0;
        for (int i = 0; i < l; i++) {
            r8[k++] = name[i];
            if (i == 2) break;
        }
        r8[k] = '\0';
        strcat(r8, "...");


        k = 0;
        for (int i = 0; i < l; i++) {
            r9[k++] = name[i];
            r9[k++] = ' ';
        }
        r9[k] = '\0';


        strcpy(r10, name);
        for (int i = 0; i < l; i++) {
            if (name[i] == 'а' || name[i] == 'a') r10[i] = '@';
        }

        strcpy(r11, name);
        if (l >= 2) {
            r11[l - 2] = '-';
        }


        k = 0;
        if (l > 0) {
            char first = toupper(name[0]);
            r12[k++] = first;
            r12[k++] = first;
            r12[k++] = first;
            for (int i = 1; i < l; i++) {
                r12[k++] = name[i];
            }
        }
        r12[k] = '\0';

        printf("\nРЕЗУЛЬТАТЫ\n");
        printf("1.  Удвоение последней буквы:         %s\n", r1);
        printf("2.  Первая строчная, ост. заглавные:  %s\n", r2);
        printf("3.  Первые две местами:               %s\n", r3);
        printf("4.  Подчеркивание:                    %s\n", r4);
        printf("5.  Наоборот:                         %s\n", r5);
        printf("6.  Без второй буквы:                 %s\n", r6);
        printf("7.  Половина заглавных:               %s\n", r7);
        printf("8.  Три точки:                        %s\n", r8);
        printf("9.  Пробелы:                          %s\n", r9);
        printf("10. Замена 'а' на '@':                %s\n", r10);
        printf("11. Предпоследняя - тире:             %s\n", r11);
        printf("12. Утроение первой буквы:            %s\n", r12);


        return 0;
}

int DZ() {
    setlocale(LC_CTYPE, "RUS");
    printf("Вариант: 22\n\n");

    char str[1000];

    printf("Введите строку: ");
   
    fgets(str, sizeof(str), stdin);

    printf("\nИсходная строка: %s", str);

    int i = 0;
    int j = 0;

    while (str[i] != '\0') {
        str[j] = str[i];
        j++;
        if (str[i] == ' ') {
            while (str[i + 1] == ' ') {
                i++;
            }
        }
        i++;
    }
    str[j] = '\0';
    printf("Измененная строка: %s\n", str);

    return 0;
}

int main() {
    DZ();
    return 0;
}

## Пример работы

**Ввод:** `Привет,    мир!   Как    дела?`
**Вывод:** `Привет, мир! Как дела?`

## Разработчик
* Рожкова Екатерина Юрьевна
* бИЦТ-261
