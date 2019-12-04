---
title: Widok drzewa wywołań — dane Instrumentacji pamięci platformy .NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 2066959578987e358f8c1c91dcbda1eeb6f79f26
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74773600"
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Widok drzewa wywołań — dane Instrumentacji pamięci platformy .NET
Widok drzewa wywołań dla danych profilowania przydziału pamięci platformy .NET, który został zebrany przy użyciu metody instrumentacji, wyświetla ścieżki wykonywania funkcji, które zostały przesunięte w profilowanej aplikacji. Katalog główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera listę wszystkich wywoływanych funkcji oraz dane dotyczące pamięci i czasu .NET dla funkcji.

 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji z łączną liczbą lub rozmiarem alokacji w ramach uruchomienia profilowania.

## <a name="highlight-the-execution-hot-path"></a>Wyróżnij gorącą ścieżkę wykonywania
 Widok drzewa wywołań może rozwijać i wyróżniać ścieżkę wykonywania procesu lub funkcji, która utworzyła największe lub większość obiektów pamięci. Aby wyświetlić najbardziej aktywną ścieżkę, kliknij prawym przyciskiem myszy proces lub funkcję, a następnie kliknij przycisk **Rozwiń ścieżkę gorącą**.

## <a name="set-the-call-tree-root-node"></a>Ustaw węzeł główny drzewa wywołań
 Każdy proces w przebiegu profilowania jest wyświetlany jako węzeł główny. Węzeł początkowy widoku drzewa wywołań można ustawić, klikając prawym przyciskiem myszy węzeł, który ma zostać ustawiony jako węzeł początkowy, a następnie wybierając pozycję **Ustaw katalog główny**.

 Po ustawieniu węzła głównego można wyeliminować wszystkie inne wpisy z widoku, z wyjątkiem poddrzewa wybranego węzła. Możesz zresetować węzeł główny z powrotem do węzła, który był przeglądany; Kliknij prawym przyciskiem myszy w oknie widok drzewa wywołań i wybierz polecenie **Zresetuj katalog główny**.

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
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa, która jest przypisana do procesu.|
|**Obciążenie sondy czasu wyłącznego**|Narzut czasu dla tej funkcji, który jest spowodowany przez instrumentację. Narzuty sondowania zostały odjęte od wszystkich wyłączeń.|
|**Narzut sondy czasu włącznego**|Narzut czasu dla tej funkcji i jej funkcji podrzędnych, która jest spowodowana przez instrumentację. Narzuty sondowania zostały odjęte od wszystkich czasów włączania.|
|**Wprowadź**|Kontekst funkcji:<br /><br /> -   **0** — bieżąca funkcja<br />-   **1** — funkcja, która wywołuje bieżącą funkcję<br />-   **2** — funkcja, która jest wywoływana przez bieżącą funkcję<br /><br /> Tylko w raportach wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) .|
|**Nazwa funkcji głównej**|Nazwa bieżącej funkcji. Tylko w raportach wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) .|

## <a name="net-memory-values"></a>Wartości pamięci platformy .NET
 Wartości pamięci platformy .NET włącznie funkcji wskazują liczbę (alokacje) i rozmiar (w bajtach) obiektów, które zostały utworzone przez funkcję i funkcje, które zostały wywołane przez funkcję.

 Wartości pamięci wyłącznej wskazują liczbę i rozmiar obiektów, które zostały utworzone przez kod w treści funkcji, a nie przez funkcje, które zostały wywołane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Przydziały włączne**|Liczba obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Ta liczba obejmuje przydziały, które zostały wykonane przez funkcje podrzędne.|
|**% Przydziałów włącznych**|Procent wszystkich obiektów, które zostały utworzone w ramach uruchomienia profilowania, które były przydzielone do wystąpień funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań.|
|**Alokacje wyłączne**|Liczba obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Ta liczba nie obejmuje przydziałów, które zostały wykonane przez funkcje podrzędne.|
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały utworzone w ramach uruchomienia profilowania, które wystąpiły na wyłączność alokacji wystąpień funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań.|

## <a name="elapsed-inclusive-values"></a>Wartości włączne, które upłynęły
 Wartości włączne (włącznie) wskazują czas, przez który funkcja była w stosie wywołań. Czas obejmuje czas spędzony w funkcjach, które zostały wywołane przez funkcję i w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włączny, który upłynął**|Łączny czas, który upłynął, przez wszystkie wywołania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**% Czasu włącznego, który upłynął**|Wartość procentowa łącznego czasu trwania przebiegu profilowania, która nastąpiła w łącznym czasie, który upłynął, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Średni łączny czas, który upłynął**|Średni czas włączny, który upłynął w wywołaniu tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Maksymalny łączny czas, który upłynął**|Maksymalny łączny czas, który upłynął w wywołaniu tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Minimalny łączny czas, który upłynął**|Minimalny łączny czas, który upłynął w wywołaniu tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęły
 Wartości wyłączne, które upłynęły, wskazują czas, przez który funkcja została bezpośrednio uruchomiona w górnej części stosu wywołań. Czas obejmuje czas wywołań systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia. Jednak czas nie obejmuje czasu spędzonego w funkcjach, które zostały wywołane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|Łączny czas wyłączny wszystkich wywołań tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**% Czasu wyłącznego, który upłynął**|Wartość procentowa całkowitego czasu, który upłynął w przypadku uruchomienia profilowania w łącznym czasie, który upłynął, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Średni czas wyłączny, który upłynął**|Średni czas wyłączny, który upłynął w wywołaniu tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Maksymalny czas wyłączny, który upłynął**|Maksymalny czas wyłączny, który upłynął w wywołaniu tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Minimalny czas, który upłynął**|Minimalny czas wyłączny, który upłynął w przypadku wywołania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|

## <a name="application-inclusive-values"></a>Wartości włączne aplikacji
 Wartości włącznie obejmują czas, przez który funkcja była w stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączenia kontekstu i operacje wejścia/wyjścia. Czas jest uwzględniany czas spędzony w funkcjach podrzędnych, które zostały wywołane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włączny aplikacji**|Łączny czas, w którym wszystkie wywołania tej funkcji został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**% Włącznego czasu aplikacji**|Wartość procentowa całkowitego czasu, który upłynął w przypadku uruchomienia profilowania, który został wystawiony w łącznym czasie włącznie aplikacji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Średni czas włączny aplikacji**|Średni czas włączny aplikacji wywołania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Maksymalny czas włączny aplikacji**|Maksymalny czas włączny aplikacji wywołania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Minimalny czas włączny aplikacji**|Minimalny czas włączny aplikacji wywołania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|

## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji
 Wartości wyłączne aplikacji wskazują czas spędzony w funkcji, z wyłączeniem czasu spędzonego w funkcjach podrzędnych, które zostały wywołane przez funkcję. Czas ten wyklucza również wywołania systemu operacyjnego, takie jak przełączniki kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny aplikacji**|Łączny czas wyłączny aplikacji wszystkich wywołań tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**% Wyłącznego czasu aplikacji**|Wartość procentowa całkowitego czasu, który upłynął w przypadku uruchomienia profilowania, który został wykorzystany w łącznym czasie trwania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Średni czas wyłączny aplikacji**|Średni czas wyłączny aplikacji wywołania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Maksymalny czas wyłączny aplikacji**|Maksymalny czas wyłączny aplikacji wywołania tej funkcji, gdy została wywołana przez funkcję nadrzędną w drzewie wywołań.|
|**Minimalny czas wyłączny aplikacji**|Minimalny czas wyłączny aplikacji wywołania tej funkcji, gdy została wywołana przez funkcję nadrzędną w drzewie wywołań.|
