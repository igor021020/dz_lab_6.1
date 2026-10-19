# #1. Алгоритм

1. Начало
2. Задать исходные данные: total_seconds (время в секундах, вводится пользователем).
3. Вычислить значение времени в часах, минутах и секундах (если значение часов равно 0, то слово «час» не выводится).
4. Вывести результат.
5. Конец
# #Блок-схема
<img width="411" height="782" alt="лаба 6 drawio" src="https://github.com/user-attachments/assets/c44be6b2-6bec-4e53-ab83-d90c91369f69" />

# #2. Реализация программы

```c
#include <stdio.h>
#include <locale.h>

const char* get_form(int n, const char* f1, const char* f2, const char* f5) {
    int n100 = n % 100;
    if (n100 >= 11 && n100 <= 14) return f5;
    int n10 = n % 10;
    if (n10 == 1) return f1;
    if (n10 >= 2 && n10 <= 4) return f2;
    return f5;
}

int main() {
    setlocale(LC_ALL, "Russian");

    int total_seconds;
    int hours, minutes, seconds;

    printf("Введите время в секундах: ");
    if (scanf("%d", &total_seconds) != 1 || total_seconds < 0) {
        printf("Ошибка ввода\n");
        return 1;
    }

    hours = total_seconds / 3600;
    minutes = (total_seconds % 3600) / 60;
    seconds = total_seconds % 60;

    if (hours > 0) {
        printf("%d %s ", hours, get_form(hours, "час", "часа", "часов"));
    }

    printf("%d %s %d %s\n", 
           minutes, get_form(minutes, "минута", "минуты", "минут"),
           seconds, get_form(seconds, "секунда", "секунды", "секунд"));

    return 0;
}
```
# #3. Результаты работы программы
Ниже представлены примеры работы программы (с учетом условия, что при 0 часов слово «час» не выводится).

Пример 1. Часы, минуты и секунды (с проверкой склонения)

Введите время в секундах: 3665
1 час 1 минута 5 секунд

Пример 2. Без часов (условие выполнено)

Введите время в секундах: 125
2 минуты 5 секунд

Пример 3. Круглое время

Введите время в секундах: 7200
2 часа 0 минут 0 секунд

Пример 4. Только секунды

Введите время в секундах: 45
0 минут 45 секунд

# #4. Информация о разработчике
Бакулин Игорь, БИЦТ-261
