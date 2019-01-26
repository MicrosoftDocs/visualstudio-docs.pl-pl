---
title: Wizualizowanie zdarzeń EventSource w postaci znaczników | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8db20a51872af37ce9f7ee655a365efb98d2f687
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938623"
---
# <a name="visualize-eventsource-events-as-markers"></a>Wizualizowanie zdarzeń EventSource w postaci znaczników
Narzędzie Concurrency Visualizer można wyświetlać zdarzeń EventSource w postaci znaczników i możesz kontrolować sposób wyświetlania znaczników. Aby wyświetlić znaczników EventSource, należy zarejestrować identyfikator GUID dostawcy ETW za pomocą [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe. Narzędzie Concurrency Visualizer zawiera domyślnych Konwencji do reprezentowania zdarzeń EventSource jako [znaczniki typu Flaga](../profiling/flag-markers.md), [znaczniki zakresu](../profiling/span-markers.md), i [znaczniki komunikatu](../profiling/message-markers.md). Można dostosować sposób wyświetlania zdarzeń EventSource, dodając pola niestandardowe do zdarzenia. Aby uzyskać więcej informacji na temat znaczników, zobacz [znaczniki Concurrency Visualizer](../profiling/concurrency-visualizer-markers.md). Aby uzyskać więcej informacji na temat zdarzeń EventSource, zobacz <xref:System.Diagnostics.Tracing>.  
  
## <a name="default-visualization-of-eventsource-events"></a>Wizualizacji domyślnej wpisania zdarzeń EventSource  
 Domyślnie narzędzie Concurrency Visualizer używa następujących konwencji, który reprezentuje zdarzeń EventSource.  
  
### <a name="marker-type"></a>Typ znacznika  
  
1.  Zdarzenia, które mają [Opcode](/windows/desktop/WES/eventmanifestschema-opcodetype-complextype) win: uruchamianie lub win: zatrzymywanie są traktowane jako początek lub koniec zakresu, odpowiednio.  Zagnieżdżone lub nakładające się zakresy nie mogą być wyświetlane. Nie można wyświetlić pary zdarzeń, które zaczynają się w jednym wątku i kończyć się na innym.  
  
2.  Zdarzenie, którego kod operacji nie jest win: Start ani win: Stop jest traktowany jako flagi znacznika, chyba że jego [poziom](/windows/desktop/WES/defining-severity-levels) (pole EVENT_RECORD. EVENT_HEADER. EVENT_DESCRIPTOR) jest win: pełne lub nowszej.  
  
3.  We wszystkich innych przypadkach zdarzenia jest traktowany jak jeden komunikat.  
  
### <a name="importance"></a>Znaczenie  
 W poniższej tabeli opisano, jak poziom zdarzenia mapuje znaczenie znacznika.  
  
|Poziom funkcji ETW|Znaczenie wizualizatora współbieżności|  
|---------------|---------------------------------------|  
|win: LogAlways|Normalne|  
|Wygraj: krytyczne|Krytyczny|  
|win: błąd|Krytyczny|  
|win: ostrzeżenie|Wysoka|  
|Wygraj: informacyjne|Normalne|  
|Wygraj: pełne|Małe|  
|Większa niż win: pełne|Małe|  
  
### <a name="series-name"></a>Nazwa serii  
 Nazwa zadania zdarzenia jest używany dla nazwy serii. Nazwa serii jest pusta, jeśli zadanie nie został zdefiniowany dla tego zdarzenia.  
  
### <a name="category"></a>Kategoria  
 Jeśli jest na poziomie systemu Windows: krytyczne lub win: błąd, a następnie kategorię alertu (-1). W przeciwnym razie kategoria jest wartość domyślna (0).  
  
### <a name="text"></a>Tekst  
 Jeśli komunikat tekstu sformatowanego typu printf został zdefiniowany dla zdarzenia, jest on wyświetlany jako opis znacznika. W przeciwnym razie długość opisu jest nazwa zdarzenia i wartości poszczególnych pól ładunku.  
  
## <a name="customize-visualization-of-eventsource-events"></a>Dostosowywanie wizualizacji zdarzeń EventSource  
 Można dostosować sposób wyświetlania zdarzeń EventSource, dodając odpowiednie pola do zdarzenia, zgodnie z opisem w poniższych sekcjach.  
  
### <a name="marker-type"></a>Typ znacznika  
 Użyj `cvType` pola typu byte, do kontroli rodzaju znacznik, który jest używany do reprezentowania zdarzenia. Poniżej przedstawiono dostępne wartości dla cvType:  
  
|wartość cvType|Wynikowy typ znacznika|  
|------------------|---------------------------|  
|0|Komunikat|  
|1|Początek zakresu|  
|2|Koniec zakresu|  
|3|Flaga|  
|Wszystkie inne wartości|Komunikat|  
  
### <a name="importance"></a>Znaczenie  
 Możesz użyć `cvImportance` pola typu byte, aby kontrolować ustawienia ważności zdarzeń EventSource. Firma Microsoft zaleca jednak sterować wyświetlanych ważność zdarzenia przy użyciu jego poziom.  
  
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
 Użyj `cvSeries` pole zdarzenia, ciąg, aby kontrolować nazwę serii, zapewniająca przez narzędzie Concurrency Visualizer do zdarzeń EventSource.  
  
### <a name="category"></a>Kategoria  
 Użyj `cvCategory` pola typu byte do kontrolowania kategorię, która Concurrency Visualizer zapewnia na zdarzenie źródła zdarzeń.  
  
### <a name="text"></a>Tekst  
 Użyj `cvTextW` pola ciągu, do kontrolowania opis, zapewniająca Concurrency Visualizer na zdarzenie źródła zdarzeń.  
  
### <a name="spanid"></a>SpanID  
 Używają pola cvSpanId, int, aby dopasować pary zdarzeń. Wartość dla każdej pary uruchamianie i zatrzymywanie wydarzeń, które reprezentują zakres musi być unikatowa. Zazwyczaj współbieżnych kodu to wymaga użycia elementów podstawowych synchronizacji takich jak <xref:System.Threading.Interlocked.Exchange%2A> aby upewnić się, że klucz (wartość jest używana do CvSpanID) jest poprawny.  
  
> [!NOTE]
>  Użycie SpanID Aby zagnieździć zakresy, zezwolić im na częściowo nakładają się na tym samym wątku, lub zezwolić im na uruchomienie na jeden wątek i zakończenia od innego nie jest obsługiwane.  
  
## <a name="see-also"></a>Zobacz także  
 [Znaczniki CONCURRENCY visualizer](../profiling/concurrency-visualizer-markers.md)