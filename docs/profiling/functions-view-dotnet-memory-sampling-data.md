---
title: Widok funkcji — dane próbkowania pamięci .NET | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: cce13da0c2dfee61d70da8bc288d1f0ff4690deb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780042"
---
# <a name="functions-view---net-memory-sampling-data"></a>Widok funkcji — dane próbkowania pamięci .NET
Widok Funkcje alokacji pamięci .NET profilowania danych, które zostały zebrane przy użyciu metody próbkowania wyświetla funkcje, które przydzielone pamięci podczas przebiegu profilowania i raportuje rozmiar i liczbę alokacji.

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
|**Alokacje włącznie**|Całkowita liczba obiektów, które zostały przydzielone w tej funkcji i jej funkcji podrzędnych.|
|**Alokacje włącznie %**|Procent wszystkich obiektów, które zostały przydzielone w przebiegu profilowania, które były alokacje włącznie tej funkcji.|
|**Alokacje wyłączne**|Liczba obiektów, które zostały utworzone, gdy funkcja była bezpośrednio wykonywania w górnej części stosu wywołań. Liczba ta nie obejmuje obiektów, które zostały utworzone w funkcjach podrzędnych.|
|**Alokacje wyłączne %**|Procent wszystkich obiektów, które zostały przydzielone w przebiegu profilowania, które były wyłączne alokacje tej funkcji.|
|**Bajty włącznie**|Liczba bajtów pamięci, które zostały przydzielone przez tę funkcję i jej funkcji podrzędnych.|
|**Bajty włącznie %**|Procent wszystkich bajtów pamięci, które zostały przydzielone w przebiegu profilowania, które były włącznie bajtów tej funkcji.|
|**Bajty wyłączne**|Liczba bajtów pamięci, które zostały przydzielone przez tę funkcję, ale nie przez jej funkcje podrzędne.|
|**Bajty wyłączności %**|Procent wszystkich bajtów pamięci, które zostały przydzielone w przebiegu profilowania, które były wyłączne bajty tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Widok funkcji - instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Widok funkcji](../profiling/functions-view-sampling-data.md)
- [Widok funkcji](../profiling/functions-view-instrumentation-data.md)
