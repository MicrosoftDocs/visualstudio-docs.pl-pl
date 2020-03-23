---
title: Widok wskaźników instrukcji (IP) — dane próbkowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: c7f647bb-c5a3-4708-9f9d-33c0fd6e2e96
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 42398e044bfc06e41249b15ac9baeebcaebd19f6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774259"
---
# <a name="instruction-pointers-ips-view---sampling-data"></a>Widok wskaźników instrukcji ( IP) — dane próbkowania
Widok adresów IP próbkowania danych zawiera listę danych wydajności dla instrukcji zestawu, które były wykonywane bezpośrednio, gdy próbki zostały zebrane w przebiegu profilowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera instrukcję.|
|**Plik źródłowy**|Plik źródłowy zawierający instrukcję.|
|**Nazwa funkcji**|Nazwa funkcji, która zawiera instrukcję.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Adres funkcji**|Początkowy adres pamięci funkcji w załadowanym pliku binarnym.|
|**Początek wiersza źródłowego**|Numer wiersza początkowego w pliku źródłowym, w którym pobrano ten przykład.|
|**Koniec wiersza źródłowego**|Numer wiersza końcowego w pliku źródłowym, w którym pobrano tę próbkę.|
|**Początek znaku źródłowego**|Przesunięcie znaku początkowego w wierszu pliku źródłowego, w którym pobrano ten przykład.|
|**Źródłowy koniec znaku**|Przesunięcie znaku końcowego w wierszu pliku źródłowego, w którym pobrano ten przykład.|
|**Adres instrukcji**|Adres instrukcji w załadowanym pliku binarnym.|
|**Ekskluzywne próbki**|Całkowita liczba próbek, które zostały zebrane podczas wykonywania instrukcji.|
|**Próbki na wyłączność %**|Procent wszystkich próbek w przebiegu profilowania, które zostały zebrane podczas wykonywania instrukcji.|

## <a name="see-also"></a>Zobacz też
- [Widok wskaźników instrukcji (IP) — próbkowanie](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
