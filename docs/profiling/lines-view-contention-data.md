---
title: Widok linii — dane rywalizacji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1dfcdf67c897c0c1565e536a69cc940b9df83390
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778599"
---
# <a name="lines-view---contention-data"></a>Widok linii — dane rywalizacji
Widok Lines danych rywalizacji zawiera listę danych wydajności dla instrukcji, które były wykonywane, gdy próbki zostały zebrane w przebiegu profilowania. W pliku źródłowym instrukcja może obejmować więcej niż jeden wiersz w pliku źródłowym, a pojedynczy wiersz może zawierać więcej niż jedną instrukcję.

 Oświadczenie jest identyfikowane na podstawie następujących danych:

- Plik źródłowy zawierający instrukcję funkcji.

- Funkcja, która zawiera instrukcję.

- Wiersz źródłowy, od którego rozpoczyna się instrukcja.

- Znak w wierszu źródłowym, od którego rozpoczyna się instrukcja.

- Wiersz źródłowy, w którym kończy się instrukcja.

- Znak w wierszu źródłowym, w którym kończy się instrukcja.

  Kolumna Nazwa wiersza zawiera sortowalne łączenia danych identyfikatorów.

  W poniższej tabeli opisano kolumny raportu Widok wierszy.

|Kolumna|Opis|
|------------|-----------------|
|**Ekskluzywny zablokowany czas**|Czas, w którym ta instrukcja została zablokowana od wykonywania kodu w instrukcji z powodu zdarzenia rywalizacji. Zablokowany czas w funkcjach, które wywoływana instrukcja nie jest uwzględniony.|
|**Ekskluzywny zablokowany czas %**|Procent wszystkich zablokowanych czasów w procesie, który był wyłącznym zablokowanym czasem instrukcji.|
|**Ekskluzywne twierdzenia**|Liczba razy, że ta instrukcja została zablokowana wykonywanie kodu w instrukcji z powodu zdarzenia rywalizacji. Zdarzenia rywalizacji w funkcjach, które wywoływana instrukcja nie są uwzględniane.|
|**Ekskluzywne rywalizacje %**|Procent wszystkich zdarzeń rywalizacji w procesie, które były wyłączne twierdzenia tej instrukcji.|
|**Adres funkcji**|Adres funkcji, która zawiera tę instrukcję.|
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji, która zawiera tę instrukcję.|
|**Włącznie zablokowany czas**|Zablokowany czas w tej instrukcji i funkcje wywoływane w instrukcji.|
|**Włącznie zablokowany czas %**|Procent wszystkich zablokowanych czasów w procesie, który był włącznie zablokowany czas instrukcji.|
|**Rywalizacje włączające**|Liczba razy, że ta instrukcja i funkcje, które zostały wywołane w instrukcji zostały zablokowane do wykonywania.|
|**Rywalizacja włączająca %**|Procent wszystkich zdarzeń rywalizacji w procesie, które były włącznie rywalizacji tej instrukcji.|
|**Nazwa wiersza**|Identyfikator linii generowany przez profiler. Identyfikator używa następującej składni:`SourceFile`**;[** `LineNumberStart` **,**,`CharacterStart`**]->; [**`LineNumberEnd`**,**`CharacterEnd`**]**|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera instrukcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) procesu profilowanego.|
|**Nazwa procesu**|Nazwa procesu|
|**Początek znaku źródłowego**|Przesunięcie znaku początkowego w wierszu pliku źródłowego, od którego rozpoczyna się ta instrukcja.|
|**Źródłowy koniec znaku**|Przesunięcie znaku początkowego w wierszu pliku źródłowego, w którym kończy się ta instrukcja.|
|**Plik źródłowy**|Nazwa pliku źródłowego zawierającego instrukcję funkcji.|
|**Początek wiersza źródłowego**|Numer wiersza w pliku źródłowym, od którego rozpoczyna się instrukcja.|
|**Koniec wiersza źródłowego**|Numer wiersza w pliku źródłowym, w którym kończy się instrukcja.|

## <a name="see-also"></a>Zobacz też
- [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok linii](../profiling/lines-view.md)
- [Widok linii — próbkowanie](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Widok linii](../profiling/lines-view-sampling-data.md)
