---
title: Widok drzewa wywołań — dane instrumentacji pamięci .NET | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773600"
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Widok drzewa wywołań — dane instrumentacji pamięci .NET
Widok drzewa wywołań danych profilowania alokacji pamięci .NET, który został zebrany przy użyciu metody instrumentacji wyświetla ścieżki wykonywania funkcji, które były przenoszone w profilowanej aplikacji. Katalog główny drzewa jest punktem wejścia do aplikacji lub składnika. Każdy węzeł funkcji zawiera listę wszystkich funkcji, które wywoływał, oraz dane pamięci i chronometrażu .NET dla tej funkcji.

 Wartości w widoku drzewa wywołań są dla wystąpień funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Wartości procentowe są obliczane przez porównanie wartości wystąpienia funkcji z całkowitą liczbą lub rozmiarem alokacji w przebiegu profilowania.

## <a name="highlight-the-execution-hot-path"></a>Wyróżnianie ścieżki aktywnej wykonania
 Widok drzewa wywołań można rozwinąć i wyróżnić ścieżkę wykonywania procesu lub funkcji, która utworzyła największe lub większość obiektów pamięci. Aby wyświetlić najbardziej aktywną ścieżkę, kliknij prawym przyciskiem myszy proces lub funkcję, a następnie kliknij polecenie **Rozwiń ścieżkę gorącą**.

## <a name="set-the-call-tree-root-node"></a>Ustawianie węzła głównego drzewa wywołań
 Każdy proces w przebiegu profilowania jest wyświetlany jako węzeł główny. Węzeł początkowy widoku Drzewo wywołań można ustawić, klikając prawym przyciskiem myszy węzeł, który chcesz ustawić jako węzeł początkowy, a następnie wybierając **pozycję Ustaw katalog główny**.

 Po ustawieniu węzła głównego można wyeliminować wszystkie inne wpisy z widoku z wyjątkiem poddrzewa wybranego węzła. Węzeł główny można zresetować z powrotem do węźle, który był oglądany; kliknij prawym przyciskiem myszy okno Widok drzewa wywołań i wybierz polecenie **Resetuj katalog główny**.

## <a name="general"></a>Ogólne

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa funkcji**|Nazwa funkcji.|
|**Adres funkcji**|Adres funkcji.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Liczba połączeń**|Całkowita liczba wywołań tej funkcji.|
|**Plik źródłowy**|Plik źródłowy zawierający definicję tej funkcji.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa, która jest przypisana do procesu.|
|**Narzucie sondy na wyłączność czasu**|Obciążenie czasowe dla tej funkcji, które jest spowodowane przez instrumentację. Obciążenie sondy zostało odjęte od wszystkich czasów wyłączności.|
|**Narzucie sondy włącznie z czasem**|Obciążenie czasowe dla tej funkcji i jej funkcji podrzędnych, które są spowodowane przez instrumentację. Obciążenie sondy zostało odjęte od czasów all inclusive.|
|**Typ**|Kontekst funkcji:<br /><br /> -   **0** - bieżąca funkcja<br />-   **1** - funkcja, która wywołuje bieżącą funkcję<br />-   **2** - funkcja wywoływana przez bieżącą funkcję<br /><br /> Tylko w raportach wiersza polecenia [VSPerfReport.](../profiling/vsperfreport.md)|
|**Nazwa funkcji głównej**|Nazwa bieżącej funkcji. Tylko w raportach wiersza polecenia [VSPerfReport.](../profiling/vsperfreport.md)|

## <a name="net-memory-values"></a>Wartości pamięci .NET
 Wartości pamięci .NET włącznie funkcji wskazują liczbę (alokacje) i rozmiar (bajty) obiektów, które zostały utworzone przez funkcję i funkcje, które zostały wywołane przez funkcję.

 Wartości pamięci wyłączności wskazują liczbę i rozmiar obiektów, które zostały utworzone przez kod w treści funkcji, a nie przez funkcje, które były wywoływane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Alokacje włącznie**|Liczba obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Liczba ta obejmuje alokacje, które zostały wykonane przez funkcje podrzędne.|
|**Alokacje włącznie %**|Procent wszystkich obiektów, które zostały utworzone w przebiegu profilowania, które były włącznie alokacje wystąpień funkcji, które były wywoływane przez funkcję nadrzędną w drzewie wywołań.|
|**Alokacje wyłączne**|Liczba obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań. Liczba ta nie obejmuje alokacji, które zostały wykonane przez funkcje podrzędne.|
|**Alokacje wyłączne %**|Procent wszystkich obiektów, które zostały utworzone w przebiegu profilowania, które były wyłączne alokacje wystąpień funkcji, które były wywoływane przez funkcję nadrzędną w drzewie wywołań.|

## <a name="elapsed-inclusive-values"></a>Wartości włącznie, które upłynęło
 Wartości włącznie, które upłynęło, wskazują czas, przez jaki funkcja znajdowała się na stosie wywołań. Czas obejmuje czas spędzony w funkcjach, które były wywoływane przez funkcję i w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie, który upłynął**|Całkowity czas włącznie wszystkich wywołań tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Czas włącznie, który upłynął %**|Procent całkowitego czasu włącznie, jaki upłynął w przebiegu profilowania, który został spędzony w całkowitym czasie włącznie tej funkcji, gdy została wywołana przez funkcję nadrzędną w drzewie wywołań.|
|**Średni czas włącznie, który upłynął**|Średni czas włącznie wywołania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Maksymalny czas włącznie, który upłynął**|Maksymalny czas włącznie wywołania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Min. Czas włącznie, który upłynął**|Minimalny czas włącznie wywołania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęło
 Wartości wyłączne, które upłynęło, wskazują czas, przez który funkcja była wykonywana bezpośrednio u góry stosu wywołań. Czas obejmuje czas w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia. Jednak czas nie obejmuje czasu spędzonego w funkcjach, które były wywoływane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|Całkowity czas wyłączny wszystkich wywołań tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Czas wyłączny, który upłynął %**|Procent całkowitego czasu wyłącznego uruchomienia profilowania, który został wydany w całkowitym czasie wyłączności tej funkcji, gdy została wywołana przez funkcję nadrzędną w drzewie wywołań.|
|**Średni czas wyłączny, który upłynął**|Średni czas wyłączności wywołania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Maksymalny czas wyłączny**|Maksymalny czas wyłączny wywołania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Min Upłynął czas wyłączny**|Minimalny czas wyłączny wywołania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|

## <a name="application-inclusive-values"></a>Wartości włącznie aplikacji
 Wartości włącznie aplikacji wskazują czas, że funkcja była na stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia. Czas obejmuje czas spędzony w funkcjach podrzędnych, które były wywoływane przez funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie aplikacji**|Całkowita aplikacja włącznie czas wszystkich wywołań tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Czas włącznie z aplikacją %**|Procent całkowitego czasu włącznie, który został spędzony w całkowitym czasie włączania aplikacji tej funkcji, gdy została wywołana przez funkcję nadrzędną w drzewie wywołań.|
|**Średni czas włącznie aplikacji**|Średni czas włącznie aplikacji wywołanie tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Maksymalny czas włącznie aplikacji**|Maksymalny czas włącznie aplikacji wywołanie tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Min. czas włącznie aplikacji**|Minimalny czas włącznie aplikacji wywołanie tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|

## <a name="application-exclusive-values"></a>Wyłączne wartości aplikacji
 Wyłączne wartości aplikacji wskazują czas spędzony w funkcji, z wyłączeniem czasu spędzonego w funkcjach podrzędnych, które były wywoływane przez funkcję. Czas wyklucza również wywołania systemu operacyjnego, takie jak przełączniki kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączności aplikacji**|Całkowity czas wyłączności aplikacji wszystkich wywołań tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Ekskluzywny czas aplikacji %**|Procent całkowitego czasu wyłącznego uruchomienia profilowania, który został spędzony w całkowitym czasie wyłączności aplikacji tej funkcji, gdy została wywołana przez funkcję nadrzędną w drzewie wywołań.|
|**Średni czas wyłączny aplikacji**|Średni czas wyłączności aplikacji wywołania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Maksymalny czas wyłączności aplikacji**|Maksymalny czas wyłączności aplikacji wywołania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
|**Minimalny czas wyłączności aplikacji**|Minimalny czas wyłączności aplikacji wywołania tej funkcji, gdy został wywołany przez funkcję nadrzędną w drzewie wywołań.|
