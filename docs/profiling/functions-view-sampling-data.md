---
title: Widok funkcji — dane próbkowania | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780029"
---
# <a name="functions-view---sampling-data"></a>Widok funkcji — próbkowanie danych
Widok raportu Funkcje dla metody profilu próbkowania zawiera listę funkcji, które zostały pobrane podczas przebiegu profilowania.

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
|**Próbki włączające**|Całkowita liczba próbek, które zostały zebrane podczas wykonywania tej funkcji; oznacza to, że liczba próbek, które zostały zebrane, gdy ta funkcja była na stosie wywołań. Liczba ta zawiera przykłady, które zostały zebrane podczas wykonywania funkcji wywoływanych przez tę funkcję.|
|**Próbki włącznie %**|Procent wszystkich próbek w przebiegu profilowania, które były włącznie próbki tej funkcji.|
|**Ekskluzywne próbki**|Całkowita liczba próbek, które zostały zebrane podczas wykonywania kodu w treści tej funkcji; oznacza to, gdy ta funkcja była na górze stosu wywołań. Próbki, które zostały zebrane w funkcjach, które zostały wywołane przez tę funkcję nie są uwzględniane.|
|**Próbki na wyłączność %**|Procent wszystkich próbek w przebiegu profilowania, które były wyłącznymi próbkami tej funkcji.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok funkcji - instrumentacja](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Widok funkcji — próbkowanie](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Widok funkcji](../profiling/functions-view-instrumentation-data.md)
