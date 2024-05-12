# test_tasks
## Задача 1

```
function getComputerString(n) {
    let lastTwoDigits = n % 100;
    let lastDigit = n % 10;
    let form = (lastTwoDigits >= 11 && lastTwoDigits <= 19) ? 'компьютеров' :
               (lastDigit === 1) ? 'компьютер' :
               (lastDigit >= 2 && lastDigit <= 4) ? 'компьютера' :
               'компьютеров';
    return `${n} ${form}`;
}
```

## Задача 2
```
function findCommonDivisors(nums) {
    // Вспомогательная функция для нахождения наибольшего общего делителя (НОД) с использованием алгоритма Евклида
    function gcd(a, b) {
        while (b !== 0) {
            let t = b;
            b = a % b;
            a = t;
        }
        return a;
    }

    // Сокращение массива до одного НОД всех элементов
    let overallGcd = nums.reduce((a, b) => gcd(a, b));

    // Поиск делителей НОД
    let divisors = [];
    for (let i = 1; i <= Math.sqrt(overallGcd); i++) {
        if (overallGcd % i === 0) {
            divisors.push(i);
            if (i !== overallGcd / i) {
                divisors.push(overallGcd / i);
            }
        }
    }
    return divisors.sort((a, b) => a - b);
}

```

## Задача 3
```
function findPrimesInRange(min, max) {
    if (max < 2) return []; // Если максимальное значение меньше 2, нет простых чисел

    // Определение размера решета: массив для отметки составных чисел только в заданном диапазоне
    let rangeLength = max - min + 1;
    let isPrimeRange = new Array(rangeLength).fill(true);

    // Проверяем каждое число до √max на то, является ли оно делителем чисел в диапазоне
    for (let i = 2; i * i <= max; i++) {
        // Находим первое число в диапазоне, кратное i
        let start = Math.max(i*i, min + (i - min % i) % i); // Math.max(i*i, ...) учитывает, что начинать нужно минимум с i*i

        // Отмечаем кратные числа в диапазоне как составные
        for (let j = start; j <= max; j += i) {
            isPrimeRange[j - min] = false; // Сдвигаем индекс для соответствия началу диапазона
        }
    }

    // Собираем простые числа из диапазона
    let primes = [];
    for (let i = 0; i < rangeLength; i++) {
        if (isPrimeRange[i]) primes.push(i + min); // Возвращаем числа, соответствующие индексам
    }
    return primes;
}
```
## Задача 4
```
function printMultiplicationTable(n) {
    let table = "";
    for (let i = 1; i <= n; i++) {
        for (let j = 1; j <= n; j++) {
            table += (i * j).toString().padStart(3, ' ') + " ";
        }
        table += "\n";
    }
    console.log(table);
}
```
