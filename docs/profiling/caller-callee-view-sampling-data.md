---
title: Widok wywołujący-wywoływany — Dane próbkowania | Microsoft Docs
description: Przeczytaj, jak widok wywołujący/wywoływany wyświetla informacje profilowania dla wybranej funkcji i jej funkcji nadrzędnych i podrzędnych w Eksplorator wydajności.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 376475d2a392b86b14a73ba45c5669eaaf338898
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886408"
---
# <a name="callercallee-view---sampling-data"></a>Widok wywołujący/wywoływany-Dane próbkowania
Widok wywołujący/wywoływany wyświetla informacje profilowania dla wybranej funkcji i jej funkcji nadrzędnych i podrzędnych. Widok wywołujący/wywoływany zawiera trzy siatki.

 **Bieżąca funkcja** jest wyświetlana w środkowej siatce i zawiera informacje profilowania dla wybranej funkcji. Wartości obejmują wszystkie przykładowe wywołania funkcji.

 **Funkcje, które wywołały bieżącą funkcję** , są wyświetlane w górnej siatce i pokazują indywidualne udziały funkcji wywołujących (nadrzędnych) do wartości wybranej (bieżącej) funkcji.

 **Funkcje, które zostały wywołane przez bieżącą funkcję** , są wyświetlane w dolnej siatce i pokazują informacje profilowania dla funkcji wywoływanych (podrzędnych) wybranej funkcji, gdy funkcja podrzędna została wywołana przez bieżącą funkcję.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Adres funkcji**|Adres funkcji.|
|**Typ**|Kontekst funkcji:<br /><br /> -   **0** — bieżąca funkcja<br />-   **1** — funkcja, która wywołuje bieżącą funkcję<br />-   **2** — funkcja, która jest wywoływana przez bieżącą funkcję|
|**Nazwa funkcji głównej**|Nazwa bieżącej funkcji.|
|**Próbki włączne**|— Dla bieżącej funkcji, liczbę próbek, które zostały zebrane pomimo wykonywania tej funkcji lub jednej z jej funkcji podrzędnych.<br />-Dla funkcji wywołującej liczba próbek włącznie bieżącej funkcji, które zostały zebrane, gdy ta funkcja nazywa bieżącą funkcję.<br />-Dla funkcji wywoływanej, liczba włączonych próbek tej funkcji, które zostały zebrane podczas bieżącej funkcji zwanej tą funkcją.|
|**Próbki włączne%**|Procent wszystkich próbek w przebiegu profilowania, który był włączonych próbek tej funkcji.|
|**Próbki wyłączne**|— Dla bieżącej funkcji liczba próbek w przebiegu profilowania, które zostały zebrane podczas bezpośredniego wykonywania tej funkcji; oznacza to, że w przypadku tej funkcji w górnej części stosu wywołań. Próbki, które są zbierane, gdy funkcje podrzędne tej funkcji są wykonywane, nie są zliczane jako liczby wyłączne.<br />— Dla funkcji wywołującej, liczba wyłącznych próbek bieżącej funkcji, które zostały zebrane, gdy ta funkcja nazywa bieżącą funkcję.<br />-Dla funkcji wywoływanej, liczba wyłącznych próbek tej funkcji, które zostały zebrane podczas bieżącej funkcji zwanej tą funkcją.|
|**Wyłącznych próbek%**|Procent wszystkich próbek w przebiegu profilowania, które były wyłącznymi próbkami tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Widok wywołujący/wywoływany — Dane próbkowania pamięci platformy .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Widok elementu wywołującego/wywoływanego — dane Instrumentacji pamięci platformy .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Widok wywołujący/wywoływany-Dane instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)
