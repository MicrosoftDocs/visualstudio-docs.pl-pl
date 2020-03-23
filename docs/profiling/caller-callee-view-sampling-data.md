---
title: Rozmówca - Widok wywoływania - Dane próbkowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 008aa6bd9402cde760ffc61a613aba778c8ec96f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773273"
---
# <a name="callercallee-view---sampling-data"></a>Widok wywołujący/wywoływany — dane próbkowania
W widoku Wywołujący/Wywoływany są wyświetlane informacje profilowania wybranej funkcji oraz jej funkcji nadrzędnych i podrzędnych. Widok wywołujący/wywoływany zawiera trzy siatki.

 **Bieżąca funkcja** jest wyświetlana w środkowej siatce i pokazuje informacje profilowania dla wybranej funkcji. Wartości obejmują wszystkie próbkowanie wywołań funkcji.

 **Funkcje, które wywoływały bieżącą funkcję,** są wyświetlane w górnej siatce i pokazują poszczególne wkłady funkcji wywołującego (nadrzędnego) do wartości wybranej (bieżącej) funkcji.

 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w dolnej siatce i pokazuje informacje profilowania dla wywoływane (podrzędne) funkcje wybranej funkcji, gdy funkcja podrzędna została wywołana przez bieżącą funkcję.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Plik źródłowy**|Plik źródłowy zawierający definicję tej funkcji.|
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Adres funkcji**|Adres funkcji.|
|**Typ**|Kontekst funkcji:<br /><br /> -   **0** - bieżąca funkcja<br />-   **1** - funkcja, która wywołuje bieżącą funkcję<br />-   **2** - funkcja wywoływana przez bieżącą funkcję|
|**Nazwa funkcji głównej**|Nazwa bieżącej funkcji.|
|**Próbki włączające**|- Dla bieżącej funkcji, liczba próbek, które zostały zebrane, mimo tej funkcji lub jednej z jej funkcji podrzędnych był wykonywany.<br />- Dla funkcji wywołującego liczba przykładów włącznie bieżącej funkcji, które zostały zebrane, gdy ta funkcja nazywa się bieżącą funkcję.<br />- Dla funkcji wywoływanej liczba przykładów włącznie tej funkcji, które zostały zebrane, gdy bieżąca funkcja wywoływała tę funkcję.|
|**Próbki włącznie %**|Procent wszystkich próbek w przebiegu profilowania, które były włącznie próbki tej funkcji.|
|**Ekskluzywne próbki**|- Dla bieżącej funkcji liczba próbek w przebiegu profilowania, które zostały zebrane podczas bezpośredniego wykonywania tej funkcji; oznacza to, gdy ta funkcja była w górnej części stosu wywołań. Przykłady, które są zbierane podczas wykonywania funkcji podrzędnych tej funkcji nie są liczone w liczbach wyłącznych.<br />- Dla funkcji wywołującego liczba wyłącznych próbek bieżącej funkcji, które zostały zebrane, gdy ta funkcja nazywa się bieżącą funkcją.<br />- Dla funkcji wywoływanej liczba wyłącznych próbek tej funkcji, które zostały zebrane, gdy bieżąca funkcja wywoływała tę funkcję.|
|**Próbki na wyłączność %**|Procent wszystkich próbek w przebiegu profilowania, które były wyłącznymi próbkami tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Widok wywołujący/wywoływany — dane próbkowania pamięci .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Widok wywołujący/wywoływany — dane instrumentacji pamięci .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Widok rozmówcy/wywoływania — dane oprzyrządowania](../profiling/caller-callee-view-instrumentation-data.md)
