---
title: Widok wskaźników instrukcji (IP) - dane Kontencji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d41f48594e50e9d5ae0c6f67aabab673a9f112a3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618981"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Widok wskaźników instrukcji (IP) — dane rywalizacji
Adresy IP widok rywalizacji o zasoby danych zawierający dane, instrukcje zestawu, które zostały zablokowane wykonania podczas uruchomienia profilowania.

 W poniższej tabeli przedstawiono wartości w kolumnach w widok wskaźników instrukcji.

|Kolumna|Opis|
|------------|-----------------|
|**Wyłączny czas blokowania**|Czas blokowania w tej funkcji.|
|**% Własnego czasu blokowania**|Procent czasu blokowania, gdy została wykonana instrukcja.|
|**Rywalizacje wyłączne**|Liczba rywalizacji, które wystąpiły w trakcie instrukcji zostało wykonane.|
|**% Rywalizacji wyłącznych**|Procent wszystkich rywalizacji podczas uruchomienia profilowania, które wystąpiły w trakcie instrukcji zostało wykonane.|
|**Adres funkcji**|Początkowy adres pamięci funkcja w załadowano danych binarnych.|
|**Nazwa funkcji**|Nazwa funkcji, która zawiera instrukcję.|
|**Adres instrukcji**|Adres pamięci, instrukcja w załadowano danych binarnych.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera instrukcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) dla PROFILOWANEGO procesu.|
|**Nazwa procesu**|Nazwa procesu.|
|**Początkowy znak w źródle**|Przesunięcie znaku w wierszu pliku źródłowego, w którym rozpoczyna się tej instrukcji.|
|**Końcowy znak w źródle**|Przesunięcie znaku w wierszu pliku źródłowego, w którym kończy się w tej instrukcji.|
|**Plik źródłowy**|Plik źródłowy, który zawiera instrukcję.|
|**Początkowy wiersz w źródle**|Numer wiersza w pliku źródłowym, w którym rozpoczyna się tej instrukcji.|
|**Końcowy wiersz w źródle**|Numer wiersza w pliku źródłowym, w którym kończy się w tej instrukcji.|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view.md)
- [Wskaźników instrukcji (IP) View - próbkowanie](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
- [Widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)