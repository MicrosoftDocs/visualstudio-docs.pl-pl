---
title: Widok funkcji — dane próbkowania pamięci platformy .NET | Microsoft Docs
description: Uzyskaj informacje o widoku funkcji dla danych profilowania przydziału pamięci platformy .NET, które zostały zebrane przy użyciu metody próbkowania.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 2fe4f011a88ab4cf293626fe01f708b3cf5bc68f
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801527"
---
# <a name="functions-view---net-memory-sampling-data"></a>Widok funkcji — dane próbkowania pamięci platformy .NET
Widok funkcji w obszarze Alokacja pamięci platformy .NET dane, które zostały zebrane przy użyciu metody próbkowania, zawierają listę funkcji, które przydzieliły pamięć podczas przebiegu profilowania i raportuje rozmiar i liczbę alokacji.

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
|**Przydziały włączne**|Całkowita liczba obiektów, które zostały przydzieloną w tej funkcji i jej funkcjach podrzędnych.|
|**% Przydziałów włącznych**|Wartość procentowa wszystkich obiektów, które zostały przydzielone w ramach uruchomienia profilowania, które były przydzielane przez tę funkcję.|
|**Alokacje wyłączne**|Liczba obiektów, które zostały utworzone podczas bezpośredniego wykonywania funkcji w górnej części stosu wywołań. Ta liczba nie obejmuje obiektów, które zostały utworzone w funkcjach podrzędnych.|
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały przydzielone w ramach uruchomienia profilowania, które wystąpiły wyłączne alokacje tej funkcji.|
|**Bajty włączne**|Liczba bajtów pamięci przydzielonej przez tę funkcję i jej funkcje podrzędne.|
|**% Bajtów włącznych**|Procent wszystkich bajtów pamięci, które zostały przydzieloną w przebiegu profilowania, które były w bajtach tej funkcji.|
|**Bajty wyłączne**|Liczba bajtów pamięci przydzielonej przez tę funkcję, ale nie przez jej funkcje podrzędne.|
|**% Bajtów wyłącznych**|Procent wszystkich bajtów pamięci, które zostały przydzieloną w ramach uruchomienia profilowania, które były wyłącznych bajtów tej funkcji.|

## <a name="see-also"></a>Zobacz także
- [Widok funkcji-Instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Widok funkcji](../profiling/functions-view-sampling-data.md)
- [Widok funkcji](../profiling/functions-view-instrumentation-data.md)
