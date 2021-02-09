---
title: Wizualizowanie zdarzeń EventSource jako znaczników | Microsoft Docs
description: Informacje o tym, że Wizualizator współbieżności może wyświetlać zdarzenia EventSource jako znaczniki i można kontrolować sposób wyświetlania znaczników.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8c919c72cbf06faccf5bb39b0753533f2b2a441f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890529"
---
# <a name="visualize-eventsource-events-as-markers"></a>Wizualizuj zdarzenia EventSource jako znaczniki
Wizualizator współbieżności może wyświetlać zdarzenia EventSource jako znaczniki i można kontrolować sposób wyświetlania znaczników. Aby wyświetlić znaczniki EventSource, zarejestruj identyfikator GUID dostawcy ETW przy użyciu okna dialogowego [Ustawienia zaawansowane](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) . Wizualizator współbieżności ma konwencje domyślne do reprezentowania zdarzeń EventSource jako [znaczników flagi](../profiling/flag-markers.md), [znaczników zakresu](../profiling/span-markers.md)i [znaczników komunikatów](../profiling/message-markers.md). Możesz dostosować sposób wyświetlania zdarzeń EventSource, dodając pola niestandardowe do zdarzeń. Aby uzyskać więcej informacji na temat znaczników, zobacz [znaczniki Concurrency Visualizer](../profiling/concurrency-visualizer-markers.md). Aby uzyskać więcej informacji na temat zdarzeń EventSource, zobacz <xref:System.Diagnostics.Tracing> .

## <a name="default-visualization-of-eventsource-events"></a>Domyślna wizualizacja zdarzeń EventSource
 Domyślnie Wizualizator współbieżności używa następujących konwencji do reprezentowania zdarzeń EventSource.

### <a name="marker-type"></a>Typ znacznika

1. Zdarzenia, które mają [kod operacji](/windows/desktop/WES/eventmanifestschema-opcodetype-complextype) "Start" i "win: Stop", są traktowane odpowiednio jako początku lub na końcu zakresu.  Nie można wyświetlić zagnieżdżonych lub nakładających się zakresów. Nie można wyświetlić par zdarzeń, które zaczynają się na jednym wątku i kończą na drugim.

2. Zdarzenie, którego opcode nie jest ani win: Start ani win: Stop jest traktowany jako flaga znacznika, chyba że jego [poziom](/windows/desktop/WES/defining-severity-levels) (pole EVENT_RECORD. EVENT_HEADER. EVENT_DESCRIPTOR) to win: verbose lub wyższej.

3. We wszystkich innych przypadkach zdarzenie jest traktowane jako komunikat.

### <a name="importance"></a>Ważność
 W poniższej tabeli zdefiniowano sposób mapowania poziomu zdarzeń na ważność znacznika.

|Poziom ETW|Ważność wizualizatora współbieżności|
|---------------|---------------------------------------|
|win: LogAlways|Normalne|
|win: krytyczne|Krytyczne|
|win: błąd|Krytyczne|
|win: Warning|Wys.|
|win: informacyjne|Normalne|
|win: verbose|Niski|
|Większe niż win: verbose|Niski|

### <a name="series-name"></a>Nazwa serii
 Nazwa zadania jest używana dla nazwy serii. Nazwa serii jest pusta, jeśli żadne zadanie nie zostało zdefiniowane dla zdarzenia.

### <a name="category"></a>Kategoria
 Jeśli poziom to win: krytyczny lub win: Error, kategoria to alert (-1). W przeciwnym razie kategoria jest wartością domyślną (0).

### <a name="text"></a>Tekst
 Jeśli dla zdarzenia zdefiniowano printfą wiadomość tekstową, jest on wyświetlany jako opis znacznika. W przeciwnym razie opis jest nazwą zdarzenia i wartością każdego pola ładunku.

## <a name="customize-visualization-of-eventsource-events"></a>Dostosowywanie wizualizacji zdarzeń EventSource
 Możesz dostosować sposób wyświetlania zdarzeń EventSource, dodając odpowiednie pola do zdarzenia, zgodnie z opisem w poniższych sekcjach.

### <a name="marker-type"></a>Typ znacznika
 Użyj `cvType` pola, bajtu, aby kontrolować rodzaj znacznika, który jest używany do reprezentowania zdarzenia. Oto dostępne wartości cvType:

|cvType wartość|Typ wynikającego znacznika|
|------------------|---------------------------|
|0|Komunikat|
|1|Początek zakresu|
|2|Koniec zakresu|
|3|Flaga|
|Wszystkie inne wartości|Komunikat|

### <a name="importance"></a>Ważność
 Możesz użyć `cvImportance` pola, bajtu, aby kontrolować ustawienie ważności dla zdarzenia EventSource. Zaleca się jednak, aby kontrolować wyświetlane znaczenie zdarzenia przy użyciu jego poziomu.

|cvImportance wartość|Ważność wizualizatora współbieżności|
|------------------------|---------------------------------------|
|0|Normalne|
|1|Krytyczne|
|2|Wys.|
|3|Wys.|
|4|Normalne|
|5|Niski|
|Wszystkie inne wartości|Niski|

### <a name="series-name"></a>Nazwa serii
 Użyj `cvSeries` pola zdarzenie, ciągu, aby kontrolować nazwę serii, którą Wizualizator współbieżności ma dla zdarzenia EventSource.

### <a name="category"></a>Kategoria
 Użyj `cvCategory` pola, bajtu, aby kontrolować kategorię, którą Wizualizator współbieżności ma dla zdarzenia EventSource.

### <a name="text"></a>Tekst
 Użyj `cvTextW` pola, ciągu, aby kontrolować opis, który Wizualizator współbieżności przekazuje zdarzenia EventSource.

### <a name="spanid"></a>SpanID
 Użyj pola cvSpanId, int, aby dopasować pary zdarzeń. Wartość każdej pary zdarzeń uruchomienia/zatrzymania reprezentująca zakres musi być unikatowa. Zwykle w przypadku kodu współbieżnego wymaga to użycia pierwotnych synchronizacji, takich jak <xref:System.Threading.Interlocked.Exchange%2A> Aby upewnić się, że klucz (wartość użyta do CvSpanID) jest poprawny.

> [!NOTE]
> Użycie SpanID do zagnieżdżenia zakresów umożliwia im częściowo nakładanie się na ten sam wątek lub zezwalanie na ich uruchamianie w jednym wątku i zakończenie na drugim nie jest obsługiwane.

## <a name="see-also"></a>Zobacz też
- [Znaczniki wizualizatora współbieżności](../profiling/concurrency-visualizer-markers.md)