# Arrays and integer calculations
Омирбекова Дария БПИ-217

# На 4 балла:
#### - Приведено решение задачи на C.

#### - Из ассемблерной программы убраны лишние макросы за счет использования соответствующих аргументов командной строки:

# На 7 баллов:
#### - Скомпоновала программу, с помощью команд:
```s
gcc -masm=intel -fno-asynchronous-unwind-tables -fno-jump-tables -fno-stack-protector -fno-exceptions ./main.c -S -o ./main.s
gcc -masm=intel -fno-asynchronous-unwind-tables -fno-jump-tables -fno-stack-protector -fno-exceptions ./task.c -S -o ./task.s
gcc ./main.s -c -o main.o
gcc ./task.s -c -o task.o
gcc ./task.o main.o -o program.exe
```

# На 8 баллов:
#### - Добавлен генератор случайных наборов данных, расширяющих возможности тестирования:
```c
a_size = atoi(argv[1]);
input = fopen("input.txt", "r");
// Ввод длины массива
printf("Input length (0 < length <= %d): ", max_size);
a_size = atoi(argv[argc - 1]);
// Проверка длины массива на коррекность
if(a_size < 1 || a_size > max_size) {
      printf("Incorrect length = %d\n", a_size);
      return 1;
}
// Чтение с файла значение элементов массива А
for(i = 0; i < a_size; ++i) {
      fscanf(input,"%d", A + i);
}
printf("Length of array A: %d \n", a_size);
printf("Array A: ");
for(i = 0; i < a_size; ++i) {
      printf("%d ", A[i]);
}
printf("\n");
// Вызов метода для извлечения из А положительных элементов в B
b_size = Task(A, a_size, B);
// Запись в файл массива B
output = fopen("output.txt", "w");
for(i = 0; i < b_size; ++i) {
      fprintf(output, "%d", B[i]);
}
```
#### - Генератор подключен к программе с выбором в командной строке варианта ввода данных:<br>
Проверяю, что в консоль введен 1 аргумент, а далее значение этого аргумента.<br>
Если равен 1, то значит, что пользователь выбрал ввод с консоли.<br>
Если равен 2, то значит, что пользователь выбрал ввод с файла.<br>
Если равен 3, то значит, что пользователь выбрал ввод с помощью рандома.<br>

```c
        if (argc == 2 && atoi(argv[1]) == 1) {}
        else if (argc == 2 && atoi(argv[1]) == 2) {}
        else if (argc == 2 && atoi(argv[1]) == 3) {}
```
