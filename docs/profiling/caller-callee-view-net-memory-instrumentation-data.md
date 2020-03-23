---
title: Caller-Callee View - Dane instrumentacji pamięci NET | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3c51f4bc1e823f565670bf1f6df77553ff4658d6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779730"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Widok wywołujący/wywoływany — dane instrumentacji pamięci .NET
Widok wywołujący/wywoływany danych profilowania pamięci .NET, który został zebrany przy użyciu metody instrumentacji wyświetla dane alokacji i chronometrażu dla wybranej funkcji oraz funkcji nadrzędnych i podrzędnych tej wybranej funkcji. Widok wywołujący/wywoływany zawiera trzy siatki.

 **Bieżąca funkcja** jest wyświetlana w środkowej siatce i pokazuje informacje profilowania pamięci o wybranej funkcji. Wartości obejmują wszystkie próbkowanie wywołań funkcji.

 **Funkcje, które wywołały bieżącą funkcję,** są wyświetlane w górnej siatce i pokazują wartość wybranej (bieżącej) funkcji wygenerowanej przez wywołania z funkcji wywołującego (nadrzędnego).

 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w dolnej siatce i pokazuje dane profilowania pamięci dla wywoływane (podrzędne) funkcje wybranej funkcji, gdy funkcja podrzędna została wywołana przez bieżącą funkcję.

 Kliknij dwukrotnie wiersz funkcji wywołującego lub wywoływanego, aby ten wiersz był bieżącą funkcją.

## <a name="general"></a>Ogólne

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa funkcji**|Nazwa funkcji.|
|**Adres funkcji**|Adres funkcji.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Liczba połączeń**|Całkowita liczba wywołań, które są wykonane do tej funkcji.|
|**Plik źródłowy**|Plik źródłowy zawierający definicję tej funkcji.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu przebiegu profilowania.|
|**Nazwa procesu**|Nazwa, która jest przypisana do procesu.|
|**Narzucie sondy na wyłączność czasu**|Obciążenie czasowe dla tej funkcji z powodu instrumentacji. Obciążenie sondy zostało odjęte od wszystkich czasów wyłączności.|
|**Narzucie sondy włącznie z czasem**|Obciążenie czasowe dla tej funkcji i jej funkcji podrzędnych z powodu instrumentacji. Obciążenie sondy zostało odjęte od czasów all inclusive.|
|**Typ**|Kontekst funkcji:<br /><br /> **0** - bieżąca funkcja<br /><br /> **1** - funkcja, która wywołuje bieżącą funkcję<br /><br /> **2** - funkcja wywoływana przez bieżącą funkcję<br /><br /> Tylko w raportach wiersza polecenia [VSPerfReport.](../profiling/vsperfreport.md)|
|**Nazwa funkcji głównej**|Nazwa bieżącej funkcji. Tylko w raportach wiersza polecenia [VSPerfReport.](../profiling/vsperfreport.md)|

## <a name="net-memory-allocation-values"></a>Wartości alokacji pamięci .NET

|Kolumna|Opis|
|------------|-----------------|
|**Alokacje wyłączne**|- Dla bieżącej funkcji liczba obiektów, które zostały utworzone, gdy funkcja była wykonywanie kodu w treści funkcji (czyli gdy funkcja była w górnej części stosu wywołań). Liczba nie obejmuje obiektów, które zostały utworzone w funkcjach, które były wywoływane przez tę funkcję.<br />- Dla funkcji wywołującego, numer wyłącznych alokacji bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji wywołującego.<br />- Dla funkcji wywoływanej liczba obiektów, które zostały utworzone przez wystąpienia tej funkcji, które zostały wywołane przez bieżącą funkcję. Ten numer nie obejmuje obiektów, które zostały utworzone przez funkcje, które zostały wywołane przez funkcję wywoływana.|
|**Alokacje wyłączne %**|Procent wszystkich obiektów, które zostały utworzone w przebiegu profilowania, które były wyłączne alokacje tej funkcji.|
|**Alokacje włącznie**|- Dla bieżącej funkcji liczba obiektów, które zostały przydzielone przez funkcję w przebiegu profilowania. Numer zawiera obiekty, które zostały utworzone w wywoływanych funkcji, które zostały wywołane przez funkcję.<br />- Dla funkcji wywołującego, numer alokacji włącznie bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji wywołującego.<br />- Dla funkcji wywoływanej liczba obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba ta obejmuje alokacje wykonane przez funkcje, które były wywoływane przez tę funkcję wywoływana.|
|**Alokacje włącznie %**|Procent wszystkich obiektów, które zostały utworzone w przebiegu profilowania, które były alokacje włącznie tej funkcji.|
|**Bajty wyłączne**|- Dla bieżącej funkcji liczba bajtów pamięci, które zostały przydzielone przez funkcję w przebiegu profilowania. Numer nie zawiera pamięci, która została przydzielona w wywoływanych funkcji, które zostały wywołane przez funkcję.<br />- Dla funkcji wywołującego, numer wyłącznych bajtów bieżącej funkcji, które zostały wygenerowane z wywołań przez tę funkcję wywołującego.<br />- Dla funkcji wywoływanej liczba bajtów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Numer nie zawiera bajtów, które zostały przydzielone przez funkcje, które zostały wywołane przez funkcję wywoływana.|
|**Bajty wyłączności %**|Procent wszystkich bajtów pamięci, które zostały przydzielone w przebiegu profilowania, które były wyłączne alokacje tej funkcji.|
|**Bajty włącznie**|- Dla bieżącej funkcji liczba bajtów w pamięci, które zostały przydzielone przez funkcję w przebiegu profilowania. Numer zawiera pamięć, która została przydzielona w wywoływanych funkcji, które zostały wywołane przez funkcję.<br />- Dla funkcji wywołującego, numer bajtów włącznie wystąpień bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji wywołującego.<br />- Dla funkcji wywoływanej liczba bajtów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba zawiera bajty, które zostały przydzielone przez funkcje, które były wywoływane przez tę funkcję wywoływana.|
|**Bajty włącznie %**|Procent wszystkich bajtów pamięci, które zostały przydzielone w przebiegu profilowania, które były alokacje włącznie tej funkcji.|

## <a name="elapsed-inclusive-values"></a>Wartości włącznie, które upłynęło
 Wartości włącznie, które upłynęło, wskazują czas, przez jaki funkcja znajdowała się na stosie wywołań. Czas obejmuje czas spędzony w funkcjach podrzędnych i wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie, który upłynął**|- Dla bieżącej funkcji, czas spędzony w funkcji. Wartość obejmuje czas spędzony w funkcjach podrzędnych i wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.<br />- Dla funkcji wywołującego, ilość czasu włącznie, który upłynął włącznie bieżącej funkcji, która została wygenerowana przez wywołania z tej funkcji wywołującego.<br />- Dla funkcji wywoływanego, czas spędzony w tej funkcji, który został wygenerowany przez wywołania z bieżącej funkcji. Wartość obejmuje czas spędzony w funkcjach podrzędnych i wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.|
|**Czas włącznie, który upłynął %**|Procent całkowitego czasu włącznie przebiegu profilowania, który został spędzony w czasie włącznie tej funkcji w tym kontekście.|
|**Średni czas włącznie, który upłynął**|Średni czas włącznie wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas włącznie, który upłynął**|Maksymalny czas włącznie wywołania tej funkcji w tym kontekście.|
|**Min. Czas włącznie, który upłynął**|Minimalny czas włącznie wywołania tej funkcji w tym kontekście.|

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęło
 Wartości wyłączne, które upłynęło, wskazują czas, przez który funkcja była wykonywana bezpośrednio u góry stosu wywołań. Czas obejmuje czas w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacji wejścia/wyjścia, ale nie obejmuje czasu spędzonego w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|- Dla bieżącej funkcji, czas spędzony na wykonywaniu treści funkcji. Wartość nie obejmuje czasu spędzonego w funkcjach podrzędnych, ale obejmuje wywołania systemu operacyjnego, takie jak przełączniki kontekstu i operacje wejścia/wyjścia.<br />- Dla funkcji wywołującego, ilość czasu wyłącznego, który upłynął bieżącej funkcji, która została wygenerowana przez wywołania z tej funkcji wywołującego.<br />- Dla funkcji wywoływanego, czas spędzony w tej funkcji, który został wygenerowany przez wywołania z bieżącej funkcji. Wartość nie obejmuje czasu spędzonego w funkcjach podrzędnych funkcji wywoływanego, ale obejmuje wywołania systemu operacyjnego, takie jak przełączniki kontekstu i operacje wejścia/wyjścia.|
|**Czas wyłączny, który upłynął %**|Procent całkowitego czasu wyłącznego przebiegu profilowania, który został wydany w całkowitym czasie wyłącznym tej funkcji w tym kontekście.|
|**Średni czas wyłączny, który upłynął**|Średni czas wyłączny wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas wyłączny**|Maksymalny czas wyłączny wywołania tej funkcji w tym kontekście.|
|**Min Upłynął czas wyłączny**|Minimalny czas wyłączny wywołania tej funkcji w tym kontekście.|

## <a name="application-inclusive-values"></a>Wartości włącznie aplikacji
 Wartości włącznie aplikacji wskazują czas, że funkcja była na stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia, ale obejmuje czas spędzony w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie aplikacji**|- Dla bieżącej funkcji, czas spędzony w funkcji i jej funkcji podrzędnych. Wartość nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.<br />- Dla funkcji wywołującego, ilość aplikacji włącznie czas bieżącej funkcji, która została wygenerowana przez wywołania z tej funkcji wywołującego.<br />- Dla funkcji wywoływanego, czas spędzony w tej funkcji i jego funkcji podrzędnych, który został wygenerowany przez wywołania z bieżącej funkcji. Wartość nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.|
|**Czas włącznie z aplikacją %**|Procent całkowitego czasu włącznie przebiegu profilowania, który został spędzony w całkowitym czasie włącznie aplikacji tej funkcji w tym kontekście.|
|**Średni czas włącznie aplikacji**|Średni czas włącznie aplikacji wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas włącznie aplikacji**|Maksymalny czas włącznie aplikacji wywołania tej funkcji w tym kontekście.|
|**Min. czas włącznie aplikacji**|Minimalny czas włącznie aplikacji wywołania tej funkcji w tym kontekście.|

## <a name="application-exclusive-values"></a>Wyłączne wartości aplikacji
 Wyłączne wartości aplikacji wskazują czas spędzony w funkcji, z wyłączeniem czasu spędzonego w funkcjach podrzędnych. Wskazany czas wyklucza również czas spędzony na zawołaniach do systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączności aplikacji**|- Dla bieżącej funkcji, czas spędzony na wykonywaniu treści funkcji. Wartość nie obejmuje czasu spędzonego w funkcjach podrzędnych ani nie obejmuje wywołań systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.<br />- Dla funkcji wywołującego, ilość wyłącznego czasu aplikacji bieżącej funkcji, która została wygenerowana przez wywołania z tej funkcji wywołującego.<br />- Dla funkcji wywoływanego, czas spędzony w tej funkcji, który został wygenerowany przez wywołania z bieżącej funkcji. Wartość nie obejmuje czasu spędzonego w funkcjach podrzędnych funkcji wywoływanego ani nie obejmuje wywołań systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.|
|**Ekskluzywny czas aplikacji %**|Procent całkowitego czasu wyłącznego przebiegu profilowania, który został spędzony w całkowitym czasie wyłączności aplikacji tej funkcji w tym kontekście.|
|**Średni czas wyłączny aplikacji**|Średni czas wyłączności aplikacji wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas wyłączności aplikacji**|Maksymalny czas wyłączności aplikacji wywołania tej funkcji w tym kontekście.|
|**Minimalny czas wyłączności aplikacji**|Minimalny czas wyłączności aplikacji wywołania tej funkcji w tym kontekście.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok wywołujący/wywoływany — dane próbkowania pamięci .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Widok rozmówcy/wywoływania — dane oprzyrządowania](../profiling/caller-callee-view-instrumentation-data.md)
- [Widok wywołujący/wywoływany — dane próbkowania](../profiling/caller-callee-view-sampling-data.md)
