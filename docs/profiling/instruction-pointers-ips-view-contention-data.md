---
title: Widok wskaźników instrukcji (IP) — dane rywalizacji | Dokumenty firmy Microsoft
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
ms.openlocfilehash: f37fb451238ec7ce6f48d8a4d3b91efa9ce04db7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774315"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Widok wskaźników instrukcji ( IP) — dane rywalizacji
Widok usług IP danych rywalizacji zawiera listę danych dla instrukcji zestawu, które zostały zablokowane przed wykonywaniem w przebiegu profilowania.

 W poniższej tabeli wyjaśniono wartości kolumn w widoku Wskaźniki instrukcji.

|Kolumna|Opis|
|------------|-----------------|
|**Ekskluzywny zablokowany czas**|Zablokowany czas w tej funkcji.|
|**Ekskluzywny zablokowany czas %**|Procent zablokowanego czasu podczas wykonywania instrukcji.|
|**Ekskluzywne twierdzenia**|Liczba rywalizacji, które wystąpiły podczas wykonywania instrukcji.|
|**Ekskluzywne rywalizacje %**|Procent wszystkich rywalizacji w przebiegu profilowania, który wystąpił podczas wykonywania instrukcji.|
|**Adres funkcji**|Początkowy adres pamięci funkcji w załadowanym pliku binarnym.|
|**Nazwa funkcji**|Nazwa funkcji, która zawiera instrukcję.|
|**Adres instrukcji**|Adres pamięci instrukcji w załadowanym pliku binarnym.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera instrukcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) procesu profilowanego.|
|**Nazwa procesu**|Nazwa procesu|
|**Początek znaku źródłowego**|Przesunięcie znaku w wierszu pliku źródłowego, od którego rozpoczyna się ta instrukcja.|
|**Źródłowy koniec znaku**|Przesunięcie znaku w wierszu pliku źródłowego, w którym kończy się ta instrukcja.|
|**Plik źródłowy**|Plik źródłowy zawierający instrukcję.|
|**Początek wiersza źródłowego**|Numer wiersza w pliku źródłowym, od którego rozpoczyna się ta instrukcja.|
|**Koniec wiersza źródłowego**|Numer wiersza w pliku źródłowym, w którym kończy się ta instrukcja.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view.md)
- [Widok wskaźników instrukcji (IP) — próbkowanie](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
- [Widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)
