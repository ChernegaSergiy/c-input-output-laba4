# Lab Work 4: C Console Input/Output

This project is a laboratory work for the "Computer Technologies and Programming" course.

## Description

The program is a simple console application written in C. It prompts the user to enter data for three agricultural crops:
- Name
- Type (e.g., grain, bean)
- Sown area (in hectares)
- Yield (in centners per hectare)

After the data is entered, the program displays it in a formatted table.

## How to Compile and Run

You can compile and run the program using a C compiler like GCC:

```bash
# Compile the program
gcc main.c -o lab4

# Run the executable
./lab4
```

## Example Usage

Below is a sample terminal session demonstrating the program's usage.

```
$ gcc main.c -o lab4
$ ./lab4
Введення даних про культури
Культура 1:
Найменування: Соя
Тип (З-зернові, Би-боби): Би
Посівна площа (га): 13000
Врожайність (ц/га): 45

Культура 2:
Найменування: Чумиза
Тип (З-зернові, Би-боби): З
Посівна площа (га): 8000
Врожайність (ц/га): 24

Культура 3:
Найменування: Рис
Тип (З-зернові, Би-боби): З
Посівна площа (га): 25650
Врожайність (ц/га): 17

Введені дані:

+--------------------------------------------------------------+
|                Сільськогосподарські культури                 |
+--------------+-----+--------------------+--------------------+
| Найменування | Тип | Посівна площа (га) | Врожайність (ц/га) |
+--------------+-----+--------------------+--------------------+
| Соя          | Би  |              13000 |                 45 |
| Чумиза       | З   |               8000 |                 24 |
| Рис          | З   |              25650 |                 17 |
+--------------+-----+--------------------+--------------------+\
| Примітка: З - зернові, Би - боби                             |
+--------------------------------------------------------------+
```

## Known Issues: Text Alignment

As seen in the example above, there is a known alignment issue in the output table when using non-ASCII characters (e.g., Cyrillic names like "Соя" or "Чумиза").

This is a classic problem in standard C I/O. The `printf` function, when used with a width specifier like `%-12s`, calculates the width based on the number of **bytes** in the string, not the number of visual **characters**. Since characters in UTF-8 encoding can occupy multiple bytes (e.g., a Cyrillic letter often takes two bytes), the padding is calculated incorrectly, causing the table columns to become misaligned.

Resolving this issue requires more advanced C techniques, such as using wide characters (`wchar_t` and `wprintf`), manually calculating padding based on character counts, or using platform-specific libraries.
