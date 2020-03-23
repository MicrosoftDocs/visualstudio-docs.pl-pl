---
title: Caller-Callee View - Dane instrumentacji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 551c183dd9c368b1af16c1fe52b36762f4e71504
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773299"
---
# <a name="callercallee-view---instrumentation-data"></a>Widok rozmówcy/wywoływania — dane oprzyrządowania
W widoku wywołujący/wywoływany są wyświetlane informacje profilowania wybranej funkcji oraz jej funkcji nadrzędnych i podrzędnych w drzewie wywołań. Widok wywołujący/wywoływany zawiera trzy siatki.

 **Bieżąca funkcja** jest wyświetlana w środkowej siatce i pokazuje informacje profilowania wybranej funkcji. Wartości obejmują wszystkie wywołania funkcji.

 **Funkcje, które wywoływały bieżącą funkcję,** są wyświetlane w górnej siatce i pokazują informacje profilowania o funkcjach wywołującego (nadrzędnego) wybranej funkcji. Wartości wskazują ilość wartości bieżącej funkcji, która została wygenerowana przez wywołania z tej funkcji wywołującego.

 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w dolnej siatce i pokazuje profilowanie informacji o wystąpieniach wywoływane (podrzędne) funkcje wybranej funkcji. Wartości wskazują tylko czas spędzony w funkcji podrzędnej, gdy został wywołany przez bieżącą funkcję.

## <a name="general"></a>Ogólne
 Kolumny ogólne identyfikują funkcję w wierszu widoku.

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
|**Nazwa procesu**|Nazwa procesu|
|**Narzucie sondy na wyłączność czasu**|Obciążenie czasowe dla tej funkcji, które było spowodowane przez instrumentację. Obciążenie sondy zostało odjęte od wszystkich czasów wyłączności.|
|**Narzucie sondy włącznie z czasem**|Obciążenie czasowe dla tej funkcji i jej funkcji podrzędnych, które zostały spowodowane przez instrumentację. Obciążenie sondy zostało odjęte od czasów all inclusive.|
|**Typ**|Kontekst funkcji:<br /><br /> **0** - bieżąca funkcja<br /><br /> **1** - funkcja, która wywołuje bieżącą funkcję<br /><br /> **2** - funkcja wywoływana przez bieżącą funkcję<br /><br /> Tylko w raportach wiersza polecenia [VSPerfReport.](../profiling/vsperfreport.md)|
|**Nazwa funkcji głównej**|Nazwa bieżącej funkcji. Tylko w raportach wiersza polecenia [VSPerfReport.](../profiling/vsperfreport.md)|

## <a name="elapsed-inclusive-values"></a>Wartości włącznie, które upłynęło
 Wartości włącznie, które upłynęło, wskazują czas, przez jaki funkcja znajdowała się na stosie wywołań. Czas obejmuje czas spędzony w funkcjach podrzędnych i czas spędzony w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie, który upłynął**|- Dla bieżącej funkcji, czas spędzony w funkcji. Wartość obejmuje czas spędzony w funkcjach podrzędnych i wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.<br />- Dla funkcji wywołującego, ilość czasu włącznie, który upłynął włącznie bieżącej funkcji, która została wygenerowana przez wywołania z tej funkcji wywołującego.<br />- Dla funkcji wywoływanej, czas spędzony w wystąpieniach tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość obejmuje czas spędzony w funkcjach podrzędnych wywoływanego i w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.|
|**Czas włącznie, który upłynął %**|Procent całkowitego czasu włącznie przebiegu profilowania, który został spędzony w czasie włącznie tej funkcji w tym kontekście.|
|**Średni czas włącznie, który upłynął**|Średni czas włącznie wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas włącznie, który upłynął**|Maksymalny czas włącznie wywołania tej funkcji w tym kontekście.|
|**Min. Czas włącznie, który upłynął**|Minimalny czas włącznie wywołania tej funkcji w tym kontekście.|

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęło
 Wartości wyłączne, które upłynęło, wskazują czas, przez który funkcja była wykonywana bezpośrednio u góry stosu wywołań. Czas obejmuje czas spędzony w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia, ale nie obejmuje czasu spędzonego w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączny, który upłynął**|- Dla bieżącej funkcji, czas spędzony na bezpośrednim wykonaniu funkcji. Wartość obejmuje czas spędzony w funkcjach podrzędnych i wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.<br />- Dla funkcji wywołującego, ilość czasu wyłącznego, który upłynął bieżącej funkcji, która została wygenerowana przez wywołania z tej funkcji wywołującego.<br />- Dla funkcji wywoływanej, czas spędzony w wystąpieniach tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość nie obejmuje czasu spędzonego w funkcjach podrzędnych funkcji wywoływanego, ale obejmuje wywołania systemu operacyjnego, takie jak przełączniki kontekstu i operacje wejścia/wyjścia.|
|**Czas wyłączny, który upłynął %**|Procent całkowitego czasu wyłącznego przebiegu profilowania, który został wydany w całkowitym czasie wyłącznym tej funkcji w tym kontekście.|
|**Średni czas wyłączny, który upłynął**|Średni czas wyłączny wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas wyłączny**|Maksymalny czas wyłączny wywołania tej funkcji w tym kontekście.|
|**Min Upłynął czas wyłączny**|Minimalny czas wyłączny wywołania tej funkcji w tym kontekście.|

## <a name="application-inclusive-values"></a>Wartości włącznie aplikacji
 Wartości włącznie aplikacji wskazują czas, że funkcja była na stosie wywołań. Czas nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia, ale obejmuje czas spędzony w funkcjach podrzędnych.

|Kolumna|Opis|
|------------|-----------------|
|**Czas włącznie aplikacji**|- Dla bieżącej funkcji, czas spędzony w funkcji i jej funkcji podrzędnych. Wartość nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.<br />- Dla funkcji wywołującego, ilość aplikacji włącznie czas bieżącej funkcji, która została wygenerowana przez wywołania z tej funkcji wywołującego.<br />- Dla funkcji wywoływanej, czas spędzony w wystąpieniach tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość obejmuje czas spędzony w funkcjach podrzędnych funkcji wywoływanej, ale nie obejmuje czasu spędzonego w wywołaniach systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.|
|**Czas włącznie z aplikacją %**|Procent całkowitego czasu włącznie przebiegu profilowania, który został spędzony w całkowitym czasie włącznie aplikacji tej funkcji w tym kontekście.|
|**Średni czas włącznie aplikacji**|Średni czas włącznie aplikacji wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas włącznie aplikacji**|Maksymalny czas włącznie aplikacji wywołania tej funkcji w tym kontekście.|
|**Min. czas włącznie aplikacji**|Minimalny czas włącznie aplikacji wywołania tej funkcji w tym kontekście.|

## <a name="application-exclusive-values"></a>Wyłączne wartości aplikacji
 Wyłączne wartości aplikacji wskazują czas spędzony w funkcji. Nie obejmuje to czasu spędzonego w funkcjach podrzędnych, a także wyklucza wywołania systemu operacyjnego, takie jak przełączniki kontekstu i operacje wejścia/wyjścia.

|Kolumna|Opis|
|------------|-----------------|
|**Czas wyłączności aplikacji**|- Dla bieżącej funkcji, czas spędzony na bezpośrednim wykonaniu funkcji. Wartość nie obejmuje czasu spędzonego w funkcjach podrzędnych ani nie obejmuje wywołań systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.<br />- Dla funkcji wywołującego, ilość wyłącznego czasu aplikacji bieżącej funkcji, która została wygenerowana przez wywołania z tej funkcji wywołującego.<br />- Dla funkcji wywoływanej, czas spędzony w wystąpieniach tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Wartość nie obejmuje czasu spędzonego w funkcjach podrzędnych funkcji wywoływanego ani nie obejmuje wywołań systemu operacyjnego, takich jak przełączniki kontekstu i operacje wejścia/wyjścia.|
|**Ekskluzywny czas aplikacji %**|Procent całkowitego czasu wyłącznego przebiegu profilowania, który został spędzony w całkowitym czasie wyłączności aplikacji tej funkcji w tym kontekście.|
|**Średni czas wyłączny aplikacji**|Średni czas wyłączności aplikacji wywołania tej funkcji w tym kontekście.|
|**Maksymalny czas wyłączności aplikacji**|Maksymalny czas wyłączności aplikacji wywołania tej funkcji w tym kontekście.|
|**Minimalny czas wyłączności aplikacji**|Minimalny czas wyłączności aplikacji wywołania tej funkcji w tym kontekście.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok wywołujący/wywoływany — dane próbkowania](../profiling/caller-callee-view-sampling-data.md)
- [Widok wywołujący/wywoływany — dane próbkowania pamięci .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Widok wywołujący/wywoływany — dane instrumentacji pamięci .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
