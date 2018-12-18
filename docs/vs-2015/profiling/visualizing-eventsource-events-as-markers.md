---
title: Wizualizowanie zdarzeń EventSource w postaci znaczników | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c39f137299c1f229de8c3c6dc8d7329cba6033cb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742556"
---
# <a name="visualizing-eventsource-events-as-markers"></a>Wizualizowanie zdarzeń i znaczników EventSource
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzie Concurrency Visualizer można wyświetlać zdarzeń EventSource w postaci znaczników i możesz kontrolować sposób wyświetlania znaczników. Aby wyświetlić znaczników EventSource, należy zarejestrować identyfikator GUID dostawcy ETW za pomocą [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe. Narzędzie Concurrency Visualizer zawiera domyślnych Konwencji do reprezentowania zdarzeń EventSource jako [znaczniki typu Flaga](../profiling/flag-markers.md), [znaczniki zakresu](../profiling/span-markers.md), i [znaczniki komunikatu](../profiling/message-markers.md). Można dostosować sposób wyświetlania zdarzeń EventSource, dodając pola niestandardowe do zdarzenia. Aby uzyskać więcej informacji na temat znaczników, zobacz [znaczniki Concurrency Visualizer](../profiling/concurrency-visualizer-markers.md). Aby uzyskać więcej informacji na temat zdarzeń EventSource, zobacz <xref:System.Diagnostics.Tracing>.  
  
## <a name="default-visualization-of-eventsource-events"></a>Wizualizacji domyślnej wpisania zdarzeń EventSource  
 Domyślnie narzędzie Concurrency Visualizer używa następujących konwencji, który reprezentuje zdarzeń EventSource.  
  
### <a name="marker-type"></a>Typ znacznika  
  
1.  Zdarzenia, które mają [Opcode](http://msdn.microsoft.com/en-us/d97953df-669b-4c55-b1a8-925022b339b7) win: uruchamianie lub win: zatrzymywanie są traktowane jako początek lub koniec zakresu, odpowiednio.  Zagnieżdżone lub nakładające się zakresy nie mogą być wyświetlane. Nie można wyświetlić pary zdarzeń, które zaczynają się w jednym wątku i kończyć się na innym.  
  
2.  Zdarzenie, którego kod operacji nie jest win: Start ani win: Stop jest traktowany jako flagi znacznika, chyba że jego [poziom](http://msdn.microsoft.com/en-us/dfa4e0a9-4d89-4f50-aef9-1dae0dc11726) (pole EVENT_RECORD. EVENT_HEADER. EVENT_DESCRIPTOR) jest win: pełne lub nowszej.  
  
3.  We wszystkich innych przypadkach zdarzenia jest traktowany jak jeden komunikat.  
  
### <a name="importance"></a>Znaczenie  
 W poniższej tabeli opisano, jak poziom zdarzenia mapuje znaczenie znacznika.  
  
|Poziom funkcji ETW|Znaczenie wizualizatora współbieżności|  
|---------------|---------------------------------------|  
|win: LogAlways|Normalny|  
|Wygraj: krytyczne|Krytyczny|  
|win: błąd|Krytyczny|  
|win: ostrzeżenie|Wysoka|  
|Wygraj: informacyjne|Normalny|  
|Wygraj: pełne|Niska|  
|Większa niż win: pełne|Niska|  
  
### <a name="series-name"></a>Nazwa serii  
 Nazwa zadania zdarzenia jest używany dla nazwy serii. Nazwa serii jest pusta, jeśli zadanie nie został zdefiniowany dla tego zdarzenia.  
  
### <a name="category"></a>Kategoria  
 Jeśli jest na poziomie systemu Windows: krytyczne lub win: błąd, a następnie kategorię alertu (-1). W przeciwnym razie kategoria jest wartość domyślna (0).  
  
### <a name="text"></a>Tekst  
 Jeśli komunikat tekstu sformatowanego typu printf został zdefiniowany dla zdarzenia, jest on wyświetlany jako opis znacznika. W przeciwnym razie długość opisu jest nazwa zdarzenia i wartości poszczególnych pól ładunku.  
  
## <a name="customizing-visualization-of-eventsource-events"></a>Dostosowywanie wizualizacji zdarzeń EventSource  
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
|0|Normalny|  
|1|Krytyczny|  
|2|Wysoka|  
|3|Wysoka|  
|4|Normalny|  
|5|Niska|  
|Wszystkie inne wartości|Niska|  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Znaczniki Concurrency Visualizer](../profiling/concurrency-visualizer-markers.md)



