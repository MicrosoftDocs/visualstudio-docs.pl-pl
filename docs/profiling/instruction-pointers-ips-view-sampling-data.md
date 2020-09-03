---
title: Widok wskaźników instrukcji (IP) — dane próbkowania | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74774259"
---
# <a name="instruction-pointers-ips-view---sampling-data"></a>Widok wskaźników instrukcji (IP) — dane próbkowania
Widok adresów IP danych próbkowania wyświetla listę danych wydajności dla instrukcji zestawu, które były wykonywane bezpośrednio, gdy próbki zostały zebrane w ramach uruchomienia profilowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera instrukcję.|
|**Plik źródłowy**|Plik źródłowy, który zawiera instrukcję.|
|**Nazwa funkcji**|Nazwa funkcji, która zawiera instrukcję.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Adres funkcji**|Adres pamięci początkowej funkcji w załadowanym pliku binarnym.|
|**Początek linii źródłowej**|Początkowy numer wiersza w pliku źródłowym, w którym zebrano ten przykład.|
|**Koniec linii źródłowej**|Końcowy numer wiersza w pliku źródłowym, w którym zebrano ten przykład.|
|**Początek znaku źródłowego**|Przesunięcie znaku początkowego w wierszu pliku źródłowego, w którym ten przykład został zebrany.|
|**Końcowy znak źródłowy**|Przesunięcie znaku końcowego w wierszu pliku źródłowego, w którym ten przykład został zebrany.|
|**Adres instrukcji**|Adres instrukcji w załadowanym pliku binarnym.|
|**Próbki wyłączne**|Całkowita liczba próbek zebranych podczas wykonywania instrukcji.|
|**Wyłącznych próbek%**|Procent wszystkich próbek w przebiegu profilowania, który został zebrany podczas wykonywania instrukcji.|

## <a name="see-also"></a>Zobacz też
- [Widok wskaźników instrukcji (IP) — próbkowanie](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
