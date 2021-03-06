---
title: Widok linii — dane rywalizacji | Microsoft Docs
description: Dowiedz się, w jaki sposób widok wierszy danych rywalizacji zawiera dane dotyczące wydajności dla instrukcji, które były wykonywane, gdy próbki zostały zebrane w ramach uruchomienia profilowania.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 863cd741833082ddfac400d86edeba574b4dcb09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917887"
---
# <a name="lines-view---contention-data"></a>Widok linii — dane rywalizacji
Widok wiersze danych rywalizacji zawiera dane dotyczące wydajności dla instrukcji, które były wykonywane, gdy próbki zostały zebrane w ramach uruchomienia profilowania. W pliku źródłowym instrukcja może obejmować więcej niż jeden wiersz w pliku źródłowym, a pojedynczy wiersz może zawierać więcej niż jedną instrukcję.

 Instrukcja jest identyfikowana przez następujące dane:

- Plik źródłowy, który zawiera instrukcję Function.

- Funkcja, która zawiera instrukcję.

- Wiersz źródłowy, w którym rozpocznie się wykonywanie instrukcji.

- Znak w wierszu źródłowym, w którym rozpocznie się wykonywanie instrukcji.

- Wiersz źródłowy, w którym zostanie zakończona instrukcja.

- Znak w wierszu źródłowym, w którym następuje zakończenie instrukcji.

  Kolumna Nazwa wiersza zawiera konkatenację łączenia danych identyfikatora.

  W poniższej tabeli opisano kolumny raportu widok wierszy.

|Kolumna|Opis|
|------------|-----------------|
|**Wyłączny czas blokowania**|Czas, w którym ta instrukcja została zablokowana względem wykonywania kodu w instrukcji z powodu zdarzenia rywalizacji. Czas blokowania w funkcjach wywoływanych przez instrukcję nie jest uwzględniony.|
|**% Wyłącznego czasu blokowania**|Procent całego czasu blokowania w procesie, który miał wyłączny czas zablokowany w instrukcji.|
|**Rywalizacje wyłączne**|Liczba przypadków, w których ta instrukcja była blokowana względem wykonywania kodu w instrukcji z powodu zdarzenia rywalizacji. Zdarzenia rywalizacji w funkcjach, których wywołana została instrukcja, nie są uwzględniane.|
|**Zawartość wyłącznych%**|Procent wszystkich zdarzeń rywalizacji w procesie, które były wyłuskanymi wypełnień tej instrukcji.|
|**Adres funkcji**|Adres funkcji, która zawiera tę instrukcję.|
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji, która zawiera tę instrukcję.|
|**Włączny czas blokowania**|Czas blokowania w tej instrukcji i funkcjach wywoływanych w instrukcji.|
|**% Włącznego czasu blokowania**|Wartość procentowa wszystkich zablokowanych godzin w procesie, który był zablokowanym czasem blokowania instrukcji.|
|**Rywalizacje włączne**|Liczba przypadków, w których ta instrukcja i funkcje, które zostały wywołane w instrukcji zostały zablokowane.|
|**% Rywalizacji włącznych**|Wyrażona w procentach zawartość wszystkich zdarzeń związanych z rywalizacją w procesie, które były w tej instrukcji.|
|**Nazwa wiersza**|Wygenerowany przez profiler Identyfikator wiersza. Identyfikator używa następującej składni: `SourceFile` **; [** `LineNumberStart` **,**`CharacterStart` **]->; [**`LineNumberEnd`**,**`CharacterEnd`**]**|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera instrukcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) PROFILOWANEGO procesu.|
|**Nazwa procesu**|Nazwa procesu|
|**Początek znaku źródłowego**|Przesunięcie znaku początkowego w wierszu pliku źródłowego, w którym rozpoczyna się ta instrukcja.|
|**Końcowy znak źródłowy**|Przesunięcie znaku początkowego w wierszu pliku źródłowego, w którym ta instrukcja zostaje zakończona.|
|**Plik źródłowy**|Nazwa pliku źródłowego, który zawiera instrukcję Function.|
|**Początek linii źródłowej**|Numer wiersza w pliku źródłowym, w którym rozpocznie się wykonywanie instrukcji.|
|**Koniec linii źródłowej**|Numer wiersza w pliku źródłowym, w którym następuje zakończenie instrukcji.|

## <a name="see-also"></a>Zobacz też
- [Instrukcje: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok linii](../profiling/lines-view.md)
- [Widok linii — próbkowanie](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Widok linii](../profiling/lines-view-sampling-data.md)
