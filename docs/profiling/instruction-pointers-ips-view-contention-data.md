---
title: Widok wskaźników instrukcji (IP) — dane rywalizacji | Microsoft Docs
description: Dowiedz się, w jaki sposób widok adresów IP dla danych rywalizacji zawiera dane dotyczące instrukcji zestawu, które zostały zablokowane w przebiegu profilowania.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d3877afb4beb48259d737112d61a36edc7a4fd4d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721596"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Widok wskaźników instrukcji (IP) — dane rywalizacji
Widok adresy IP danych rywalizacji zawiera dane dotyczące instrukcji zestawu, które zostały zablokowane w przebiegu profilowania.

 W poniższej tabeli objaśniono wartości kolumn w widoku wskaźników instrukcji.

|Kolumna|Opis|
|------------|-----------------|
|**Wyłączny czas blokowania**|Czas blokowania w tej funkcji.|
|**% Wyłącznego czasu blokowania**|Wartość procentowa czasu blokowania podczas wykonywania instrukcji.|
|**Rywalizacje wyłączne**|Liczba rywalizacji, które wystąpiły podczas wykonywania instrukcji.|
|**Zawartość wyłącznych%**|Wartość procentowa wszystkich rywalizacji w przebiegu profilowania, które wystąpiły podczas wykonywania instrukcji.|
|**Adres funkcji**|Adres pamięci początkowej funkcji w załadowanym pliku binarnym.|
|**Nazwa funkcji**|Nazwa funkcji, która zawiera instrukcję.|
|**Adres instrukcji**|Adres pamięci instrukcji w załadowanym pliku binarnym.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera instrukcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) PROFILOWANEGO procesu.|
|**Nazwa procesu**|Nazwa procesu|
|**Początek znaku źródłowego**|Przesunięcie znaku w wierszu pliku źródłowego, w którym rozpocznie się ta instrukcja.|
|**Końcowy znak źródłowy**|Przesunięcie znaku w wierszu pliku źródłowego, w którym ta instrukcja zostanie zakończona.|
|**Plik źródłowy**|Plik źródłowy, który zawiera instrukcję.|
|**Początek linii źródłowej**|Numer wiersza w pliku źródłowym, w którym rozpocznie się ta instrukcja.|
|**Koniec linii źródłowej**|Numer wiersza w pliku źródłowym, w którym zostanie zakończona ta instrukcja.|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view.md)
- [Widok wskaźników instrukcji (IP) — próbkowanie](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
- [Widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)
