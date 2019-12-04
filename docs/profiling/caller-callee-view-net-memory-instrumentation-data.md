---
title: Widok wywołujący-wywoływany-Dane instrumentacji usługi NET Memory | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779730"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Widok elementu wywołującego/wywoływanego — dane Instrumentacji pamięci platformy .NET
Widok wywołujący/wywoływany pamięci platformy .NET, który został zebrany za pomocą metody instrumentacji, wyświetla dane alokacji i chronometraż dla wybranej funkcji oraz funkcje nadrzędne i podrzędne tej wybranej funkcji. Widok wywołujący/wywoływany zawiera trzy siatki.

 **Bieżąca funkcja** jest wyświetlana w środkowej siatce i zawiera informacje profilowania pamięci dotyczące wybranej funkcji. Wartości obejmują wszystkie przykładowe wywołania funkcji.

 **Funkcje, które wywołały bieżącą funkcję** , są wyświetlane w górnej siatce i pokazują ilość wartości wybranej (bieżącej) funkcji wygenerowanej przez wywołania z funkcji wywołującej (nadrzędnej).

 **Funkcje, które zostały wywołane przez bieżącą funkcję** , są wyświetlane w dolnej siatce i wyświetlają dane profilowania pamięci dla funkcji wywoływanych (podrzędnych) wybranej funkcji, gdy funkcja podrzędna została wywołana przez bieżącą funkcję.

 Kliknij dwukrotnie obiekt wywołujący lub element wywoływanej funkcji, aby uczynić ten wiersz bieżącą funkcją.

## <a name="general"></a>Ogólne

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa funkcji**|Nazwa funkcji.|
|**Adres funkcji**|Adres funkcji.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Liczba wywołań**|Całkowita liczba wywołań wykonanych dla tej funkcji.|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu uruchomienia profilowania.|
|**Nazwa procesu**|Nazwa, która jest przypisana do procesu.|
|**Obciążenie sondy czasu wyłącznego**|Narzut czasu dla tej funkcji ze względu na instrumentację. Narzuty sondowania zostały odjęte od wszystkich wyłączeń.|
|**Narzut sondy czasu włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych ze względu na instrumentację. Narzuty sondowania zostały odjęte od wszystkich czasów włączania.|
|**Wprowadź**|Kontekst funkcji:<br /><br /> **0** — bieżąca funkcja<br /><br /> **1** — funkcja, która wywołuje bieżącą funkcję<br /><br /> **2** — funkcja, która jest wywoływana przez bieżącą funkcję<br /><br /> Tylko w raportach wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) .|
|**Nazwa funkcji głównej**|Nazwa bieżącej funkcji. Tylko w raportach wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) .|

## <a name="net-memory-allocation-values"></a>Wartości przydziału pamięci platformy .NET

|Kolumna|Opis|
|------------|-----------------|
|**Alokacje wyłączne**|— Dla bieżącej funkcji — liczba obiektów, które zostały utworzone, gdy funkcja wykonywała kod w treści funkcji (to oznacza, gdy funkcja była w górnej części stosu wywołań). Liczba nie obejmuje obiektów, które zostały utworzone w funkcjach, które zostały wywołane przez tę funkcję.<br />— Dla funkcji wywołującej, liczba wyłącznych alokacji bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji wywołującej.<br />-Dla funkcji wywoływanej, liczba obiektów utworzonych przez wystąpienia tej funkcji, które zostały wywołane przez bieżącą funkcję. Ta liczba nie obejmuje obiektów, które zostały utworzone przez funkcje, które zostały wywołane przez wywoływaną funkcję.|
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały utworzone w ramach uruchomienia profilowania, które wystąpiły na wyłączność alokacji tej funkcji.|
|**Przydziały włączne**|— Dla bieżącej funkcji liczba obiektów, które zostały przydzielone przez funkcję w przebiegu profilowania. Liczba zawiera obiekty, które zostały utworzone w funkcjach wywoływanych przez funkcję.<br />-Dla funkcji wywołującej liczba przydziałów włącznie dla bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji wywołującej.<br />-Dla funkcji wywoływanej liczba obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba obejmuje alokacje wykonane przez funkcje, które zostały wywołane przez tę funkcję wywoływanej.|
|**% Przydziałów włącznych**|Procent wszystkich obiektów, które zostały utworzone w ramach uruchomienia profilowania, które były przydzielone do tej funkcji.|
|**Bajty wyłączne**|— Dla bieżącej funkcji — liczba bajtów pamięci przydzielonej przez funkcję w ramach uruchomienia profilowania. Liczba nie obejmuje pamięci, która została przypisana w funkcjach wywoływanych przez funkcję.<br />-Dla funkcji wywołującej liczba wyłącznych bajtów bieżącej funkcji, które zostały wygenerowane na podstawie wywołań przez tę funkcję wywołującego.<br />-Dla funkcji wywoływanej liczba bajtów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba nie obejmuje bajtów, które zostały przydzielone przez funkcje, które zostały wywołane przez wywoływaną funkcję.|
|**% Bajtów wyłącznych**|Wartość procentowa wszystkich bajtów pamięci przydzielonych w ramach uruchomienia profilowania, która wystąpiła na wyłączność alokacji tej funkcji.|
|**Bajty włączne**|— Dla bieżącej funkcji liczba bajtów w pamięci, które zostały przydzielone przez funkcję w przebiegu profilowania. Liczba zawiera pamięć przydzieloną w funkcjach wywoływanych, które zostały wywołane przez funkcję.<br />-Dla funkcji wywołującej liczba bajtów włącznie wystąpień bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji wywołującej.<br />-Dla funkcji wywoływanej liczba bajtów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba zawiera bajty, które zostały przydzielone przez funkcje, które zostały wywołane przez tę wbudowaną funkcję.|
|**% Bajtów włącznych**|Wartość procentowa wszystkich bajtów pamięci przydzielonych w ramach uruchomienia profilowania, która obejmuje przydziały tej funkcji.|

## <a name="elapsed-inclusive-values"></a>Wartości włączne, które upłynęły
 Wartości włączne (włącznie) wskazują czas, przez który funkcja była w stosie wywołań. Czas obejmuje czas spędzony w funkcjach podrzędnych i w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włączny, który upłynął**|— Dla bieżącej funkcji, czas spędzony w funkcji. Wartość obejmuje czas spędzony w funkcjach podrzędnych i w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.<br />— Dla funkcji wywołującej, ilość czasu włącznego dla bieżącej funkcji wygenerowanej przez wywołania z tej funkcji wywołującej.<br />-Dla funkcji wywoływanej, czas spędzony w tej funkcji, który został wygenerowany przez wywołania z bieżącej funkcji. Wartość obejmuje czas spędzony w funkcjach podrzędnych i w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.|
|**% Czasu włącznego, który upłynął**|Procent łącznego czasu trwania przebiegu profilowania, który był spędzony w czasie trwania tej funkcji w tym kontekście.|
|**Średni łączny czas, który upłynął**|Średni czas włączny, który upłynął w tym kontekście w przypadku wywołania tej funkcji.|
|**Maksymalny łączny czas, który upłynął**|Maksymalny łączny czas, który upłynął w przypadku wywołania tej funkcji w tym kontekście.|
|**Minimalny łączny czas, który upłynął**|Minimalny łączny czas, który upłynął w przypadku wywołania tej funkcji w tym kontekście.|

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęły
 Wartości wyłączne, które upłynęły, wskazują czas, przez który funkcja została bezpośrednio uruchomiona w górnej części stosu wywołań. Czas obejmuje czas wywołań systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czasu spędzonego w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|— Dla bieżącej funkcji czas spędzony w wykonywaniu treści funkcji. Wartość wyklucza czas spędzony w funkcjach podrzędnych, ale obejmuje wywołania systemu operacyjnego, takie jak operacje przełączania kontekstu i operacji wejścia/wyjścia.<br />— Dla funkcji wywołującej, ilość czasu wyłącznego bieżącej funkcji wygenerowanej przez wywołania z tej funkcji wywołującej.<br />-Dla funkcji wywoływanej, czas spędzony w tej funkcji, który został wygenerowany przez wywołania z bieżącej funkcji. Wartość wyklucza czas spędzony w funkcjach podrzędnych funkcji wywoływanej, ale obejmuje wywołania systemu operacyjnego, takie jak przełączniki kontekstu i operacje wejścia/wyjścia.|
|**% Czasu wyłącznego, który upłynął**|Wartość procentowa całkowitego czasu, który upłynął w przypadku uruchomienia profilowania w łącznym czasie trwania tej funkcji w tym kontekście.|
|**Średni czas wyłączny, który upłynął**|Średni czas wyłączny dla wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas wyłączny, który upłynął**|Maksymalny czas wyłączny w wywołaniu tej funkcji w tym kontekście.|
|**Minimalny czas, który upłynął**|Minimalny czas, który upłynął w przypadku wywołania tej funkcji w tym kontekście.|

## <a name="application-inclusive-values"></a>Wartości włączne aplikacji
 Wartości włącznie obejmują czas, przez który funkcja była w stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia, ale obejmuje czas spędzony w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włączny aplikacji**|— Dla bieżącej funkcji, czas spędzony w funkcji i jej funkcjach podrzędnych. Wartość wyklucza czas spędzony w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.<br />-Dla funkcji wywołującej, ilość łącznego czasu aplikacji wygenerowanej przez wywołania z tej funkcji wywołującej.<br />-Dla funkcji wywoływanej, czas spędzony w tej funkcji i jej funkcjach podrzędnych, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.|
|**% Włącznego czasu aplikacji**|Wartość procentowa łącznego czasu trwania przebiegu profilowania, która została wykorzystana w łącznym czasie włącznie aplikacji w tym kontekście.|
|**Średni czas włączny aplikacji**|Średni czas włączny aplikacji wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas włączny aplikacji**|Maksymalny czas włączny aplikacji wywołania tej funkcji w tym kontekście.|
|**Minimalny czas włączny aplikacji**|Minimalny czas włączny aplikacji w tym kontekście w przypadku wywołania tej funkcji.|

## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji
 Wartości wyłączne aplikacji wskazują czas spędzony w funkcji, z wyłączeniem czasu spędzonego w funkcjach podrzędnych. Określony czas również wyklucza czas spędzony na wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny aplikacji**|— Dla bieżącej funkcji czas spędzony w wykonywaniu treści funkcji. Wartość nie obejmuje czasu spędzonego w funkcjach podrzędnych ani nie obejmuje wywołań do systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.<br />— Dla funkcji wywołującej, ilość czasu wyłącznego aplikacji dla bieżącej funkcji wygenerowanej przez wywołania z tej funkcji wywołującej.<br />-Dla funkcji wywoływanej, czas spędzony w tej funkcji, który został wygenerowany przez wywołania z bieżącej funkcji. Wartość nie obejmuje czasu spędzonego w funkcjach podrzędnych funkcji wywoływanej ani nie obejmuje wywołań do systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.|
|**% Wyłącznego czasu aplikacji**|Wartość procentowa całkowitego czasu, który upłynął w przypadku uruchomienia profilowania, który został spędzony w łącznym czasie trwania tej funkcji aplikacji w tym kontekście.|
|**Średni czas wyłączny aplikacji**|Średni czas wyłączny aplikacji wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas wyłączny aplikacji**|Maksymalny czas wyłączny aplikacji wywołania tej funkcji w tym kontekście.|
|**Minimalny czas wyłączny aplikacji**|Minimalny czas wyłączny aplikacji w wywołaniu tej funkcji w tym kontekście.|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok wywołujący/wywoływany — Dane próbkowania pamięci platformy .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Widok wywołujący/wywoływany-Dane instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)
- [Widok wywołujący/wywoływany-Dane próbkowania](../profiling/caller-callee-view-sampling-data.md)
