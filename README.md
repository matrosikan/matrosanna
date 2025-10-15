#include <iostream>
#include <vector>

using namespace std;

// Функция сортировки выбором
void selectionSort(vector<int>& arr) {
    int n = arr.size();
    
    // Проходим по всем элементам массива
    for (int i = 0; i < n - 1; i++) {
        // Предполагаем, что минимальный элемент находится на текущей позиции i
        int minIndex = i;
        
        // Ищем минимальный элемент в оставшейся части массива
        // (от i+1 до конца)
        for (int j = i + 1; j < n; j++) {
            // Если находим элемент меньше текущего минимального,
            // обновляем индекс минимального элемента
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        
        // Меняем местами найденный минимальный элемент с текущим элементом i
        // Используем временную переменную для обмена значений
        int temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }
}

// Функция для вывода массива
void printArray(const vector<int>& arr, const string& message = "") {
    if (!message.empty()) {
        cout << message;
    }
    for (int num : arr) {
        cout << num << " ";
    }
    cout << endl;
}

// Функция с подробным выводом процесса сортировки
void selectionSortDetailed(vector<int>& arr) {
    int n = arr.size();
    cout << "\n=== ПОДРОБНЫЙ ПРОЦЕСС СОРТИРОВКИ ===" << endl;
    
    for (int i = 0; i < n - 1; i++) {
        cout << "\n--- Итерация " << i + 1 << " ---" << endl;
        cout << "Текущий массив: ";
        printArray(arr);
        cout << "Ищем минимальный элемент в диапазоне [" << i << "..." << n-1 << "]" << endl;
        
        int minIndex = i;
        
        for (int j = i + 1; j < n; j++) {
            cout << "  Сравниваем arr[" << j << "]=" << arr[j] 
                 << " с текущим минимумом arr[" << minIndex << "]=" << arr[minIndex];
            
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
                cout << " -> НОВЫЙ МИНИМУМ! minIndex = " << minIndex << endl;
            } else {
                cout << " -> минимум не изменился" << endl;
            }
        }
        
        cout << "Найден минимальный элемент: arr[" << minIndex << "] = " << arr[minIndex] << endl;
        
        if (minIndex != i) {
            cout << "Меняем местами arr[" << i << "]=" << arr[i] 
                 << " и arr[" << minIndex << "]=" << arr[minIndex] << endl;
            
            // Обмен значений
            int temp = arr[i];
            arr[i] = arr[minIndex];
            arr[minIndex] = temp;
        } else {
            cout << "Элемент уже на своем месте, обмен не требуется" << endl;
        }
    }
    
    cout << "\n=== СОРТИРОВКА ЗАВЕРШЕНА ===" << endl;
}

int main() {
    // Тест 1: Простая сортировка
    cout << "ТЕСТ 1: Простая сортировка" << endl;
    vector<int> arr1 = {64, 25, 12, 22, 11};
    
    printArray(arr1, "Исходный массив: ");
    
    selectionSort(arr1);
    
    printArray(arr1, "Отсортированный массив: ");
    
    // Тест 2: Подробный процесс сортировки
    cout << "\n" << string(50, '=') << endl;
    cout << "ТЕСТ 2: Подробный процесс сортировки" << endl;
    vector<int> arr2 = {64, 25, 12, 22, 11};
    
    printArray(arr2, "Исходный массив: ");
    
    selectionSortDetailed(arr2);
    
    printArray(arr2, "Итоговый отсортированный массив: ");
    
    // Тест 3: Массив уже отсортирован
    cout << "\n" << string(50, '=') << endl;
    cout << "ТЕСТ 3: Уже отсортированный массив" << endl;
    vector<int> arr3 = {1, 2, 3, 4, 5};
    
    printArray(arr3, "Исходный массив: ");
    selectionSort(arr3);
    printArray(arr3, "После сортировки: ");
    
    // Тест 4: Массив в обратном порядке
    cout << "\n" << string(50, '=') << endl;
    cout << "ТЕСТ 4: Массив в обратном порядке" << endl;
    vector<int> arr4 = {5, 4, 3, 2, 1};
    
    printArray(arr4, "Исходный массив: ");
    selectionSort(arr4);
    printArray(arr4, "После сортировки: ");
    
    return 0;
}
