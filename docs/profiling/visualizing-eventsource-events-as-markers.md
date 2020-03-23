---
title: Wizualizacja zdarzeń eventsource jako znaczników | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd6339b3f55b4a4c9a1e2c90ff3183a36f16c178
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "64811548"
---
# <a name="visualize-eventsource-events-as-markers"></a>Wizualizuj zdarzenia EventSource jako znaczniki
Wizualizator współbieżności można wyświetlić EventSource zdarzenia jako znaczniki i można kontrolować sposób wyświetlania znaczników. Aby wyświetlić znaczniki EventSource, zarejestruj identyfikator GUID dostawcy ETW za pomocą okna dialogowego [Ustawienia zaawansowane.](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) Wizualizator współbieżności ma domyślne konwencje reprezentujące zdarzenia EventSource jako [znaczniki flag,](../profiling/flag-markers.md) [znaczniki zakresu](../profiling/span-markers.md)i [znaczniki wiadomości](../profiling/message-markers.md). Sposób wyświetlania zdarzeń EventSource można dostosować, dodając pola niestandardowe do zdarzeń. Aby uzyskać więcej informacji na temat znaczników, zobacz [Znaczniki wizualizatora współbieżności](../profiling/concurrency-visualizer-markers.md). Aby uzyskać więcej informacji o <xref:System.Diagnostics.Tracing>zdarzeniach EventSource, zobacz .

## <a name="default-visualization-of-eventsource-events"></a>Domyślna wizualizacja zdarzeń EventSource
 Domyślnie wizualizator współbieżności używa następujących konwencji do reprezentowania zdarzeń EventSource.

### <a name="marker-type"></a>Typ znacznika

1. Zdarzenia, które mają [Opcode](/windows/desktop/WES/eventmanifestschema-opcodetype-complextype) win:Start lub win:Stop są traktowane jako początek lub koniec zakresu, odpowiednio.  Nie można wyświetlić zagnieżdżonych lub nakładających się zakresów. Nie można wyświetlić par zdarzeń, które rozpoczynają się w jednym wątku i kończą na innym.

2. Zdarzenie, którego kod opcode nie jest win:Start ani win:Stop jest traktowane jako flaga znacznika, chyba że jego [poziom](/windows/desktop/WES/defining-severity-levels) (pole EVENT_RECORD. EVENT_HEADER. EVENT_DESCRIPTOR) jest win:Verbose lub wyższe.

3. We wszystkich innych przypadkach zdarzenie jest traktowane jako komunikat.

### <a name="importance"></a>Ważność
 W poniższej tabeli zdefiniowano sposób, w jaki poziom zdarzenia jest mapowy do ważności znacznika.

|Poziom ETW|Znaczenie wizualizatora współbieżności|
|---------------|---------------------------------------|
|wygrać:LogWszkejszy|Normalne|
|wygrana:Krytyczne|Krytyczny|
|wygrać:Błąd|Krytyczny|
|wygrać:Ostrzeżenie|Wysoka|
|wygrać:Informacje|Normalne|
|wygrana:Pełne|Małe|
|Większa niż wygrana:pełne|Małe|

### <a name="series-name"></a>Nazwa serii
 Nazwa zadania zdarzenia jest używana dla nazwy serii. Nazwa serii jest pusta, jeśli nie zdefiniowano żadnego zadania dla zdarzenia.

### <a name="category"></a>Kategoria
 Jeśli poziom jest win:Critical lub win:Error, a następnie kategorii alert (-1). W przeciwnym razie kategoria jest domyślna (0).

### <a name="text"></a>Tekst
 Jeśli dla zdarzenia zdefiniowano sformatowaną wiadomość tekstową typu printf, jest ona wyświetlana jako opis znacznika. W przeciwnym razie opis jest nazwą zdarzenia i wartością każdego pola ładunku.

## <a name="customize-visualization-of-eventsource-events"></a>Dostosowywanie wizualizacji zdarzeń EventSource
 Sposób wyświetlania zdarzeń EventSource można dostosować, dodając odpowiednie pola do zdarzenia, zgodnie z opisem w poniższych sekcjach.

### <a name="marker-type"></a>Typ znacznika
 Użyj `cvType` pola, bajtu, aby kontrolować rodzaj znacznika, który jest używany do reprezentowania zdarzenia. Oto dostępne wartości dla cvType:

|wartość cvType|Wynikowy typ znacznika|
|------------------|---------------------------|
|0|Komunikat|
|1|Początek rozszeł|
|2|Koniec rozsłości|
|3|Flaga|
|Wszystkie inne wartości|Komunikat|

### <a name="importance"></a>Ważność
 Można użyć `cvImportance` pola, bajt, aby kontrolować ustawienie ważności dla eventSource zdarzenia. Jednak zaleca się kontrolowanie wyświetlane znaczenie zdarzenia przy użyciu jego poziom.

|wartość cvImportance|Znaczenie wizualizatora współbieżności|
|------------------------|---------------------------------------|
|0|Normalne|
|1|Krytyczny|
|2|Wysoka|
|3|Wysoka|
|4|Normalne|
|5|Małe|
|Wszystkie inne wartości|Małe|

### <a name="series-name"></a>Nazwa serii
 Użyj `cvSeries` pola zdarzenia, ciąg, aby kontrolować nazwę serii, że wizualizator współbieżności daje eventSource zdarzenia.

### <a name="category"></a>Kategoria
 Użyj `cvCategory` pola, bajt, aby kontrolować kategorię, którą wizualizator współbieżności daje do zdarzenia EventSource.

### <a name="text"></a>Tekst
 Użyj `cvTextW` pola, ciąg, aby kontrolować opis, który wizualizator współbieżności daje eventSource zdarzenia.

### <a name="spanid"></a>SpanID
 Użyj pola cvSpanId, int, aby dopasować pary zdarzeń. Wartość dla każdej pary zdarzeń start/stop, które reprezentują zakres musi być unikatowa. Zazwyczaj dla równoczesnego kodu wymaga to użycia wierzchołków synchronizacji, takich jak <xref:System.Threading.Interlocked.Exchange%2A> zapewnienie, że klucz (wartość, która jest używana dla CvSpanID) jest poprawna.

> [!NOTE]
> Użycie SpanID do zagnieżdżania zakresów, zezwalaj im na częściowe nakładanie się na ten sam wątek lub zezwalanie im na uruchamianie na jednym wątku i na końcu na innym nie jest obsługiwane.

## <a name="see-also"></a>Zobacz też
- [Znaczniki wizualizatora współbieżności](../profiling/concurrency-visualizer-markers.md)