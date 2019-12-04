---
title: Widok funkcji — dane próbkowania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 70fda712a29ff07ee34a4ac76a06198cb5ead8a5
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74780029"
---
# <a name="functions-view---sampling-data"></a>Widok funkcji — dane próbkowania
Widok raport funkcji dla metody profilu próbkowania zawiera listę funkcji, które były próbkowane podczas przebiegu profilowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Adres funkcji**|Adres funkcji.|
|**Próbki włączne**|Całkowita liczba próbek zebranych podczas wykonywania tej funkcji; oznacza to, że liczba próbek zebranych, gdy ta funkcja była w stosie wywołań. Liczba zawiera próbki, które zostały zebrane, gdy funkcje, które zostały wywołane przez tę funkcję, były wykonywane.|
|**Próbki włączne%**|Procent wszystkich próbek w przebiegu profilowania, który był włączonych próbek tej funkcji.|
|**Próbki wyłączne**|Całkowita liczba próbek zebranych podczas wykonywania kodu w treści tej funkcji; oznacza to, że gdy ta funkcja znajduje się w górnej części stosu wywołań. Próbki, które zostały zebrane w funkcjach, które zostały wywołane przez tę funkcję, nie są uwzględniane.|
|**Wyłącznych próbek%**|Procent wszystkich próbek w przebiegu profilowania, które były wyłącznymi próbkami tej funkcji.|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok funkcji-Instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Widok funkcji — próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Widok funkcji](../profiling/functions-view-instrumentation-data.md)
