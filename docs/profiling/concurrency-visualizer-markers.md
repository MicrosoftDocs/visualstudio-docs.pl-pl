---
title: Markery wizualizatora współbieżności | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab5e4b65db5c3d96b16a68a7b8e21a2786b9110b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "63001051"
---
# <a name="concurrency-visualizer-markers"></a>Znaczniki wizualizatora współbieżności
W wizualizatorze współbieżności znaczniki są ikonami reprezentującymi zdarzenia w aplikacji.  Zazwyczaj aplikacja generuje te zdarzenia, aby wyznaczyć fazy lub wystąpienia w aplikacji.  Zdarzenia mogą być generowane przez aplikację lub biblioteki i środowiska wykonawcze, których używa aplikacja.

## <a name="kinds-of-markers"></a>Rodzaje znaczników
 Wizualizator współbieżności używa trzech rodzajów znaczników do reprezentowania zdarzeń aplikacji: flagi, wiadomości i zakresy.

1. Użyj *flagi,* aby wskazać interesujący punkt w czasie w aplikacji.  Na przykład można użyć flagi do reprezentowania, że wartość zmiennej osiągnęła określony próg lub że został zgłoszony wyjątek.

2. *Komunikat* oznacza również punkt w czasie, ale można go używać do śledzenia w stylu dziennika.  Na przykład, co może być po cenach dumpingowych do pliku dziennika można teraz zawinąć w wywołaniu wiadomości, dzięki czemu można go śledzić i wyświetlić go w wizualizatora współbieżności. Można również użyć wizualizatora współbieżności, aby wyeksportować te dane do pliku CSV.

3. *Zakres* reprezentuje interwał czasu w aplikacji, na przykład jedną z jego faz.

## <a name="marker-linkage-to-threads"></a>Powiązanie znaczników z wątkami
 Każdy wątek, który generuje znaczniki ma oddzielny kanał osi czasu.  Identyfikator wątku, który jest odpowiedzialny za generowanie zdarzeń znacznika jest wyświetlany obok opisu kanału znacznika.  Identyfikator, który jest wyświetlany po lewej stronie kanału znacznika pasuje do identyfikatora innego wątku w bieżącym procesie.

## <a name="marker-importance"></a>Znaczenie znacznika
 Markery mogą mieć jeden z czterech poziomów ważności: niski, normalny, wysoki i krytyczny.  Źródła znaczników można filtrować na podstawie poziomu ważności.  Na przykład jeśli chcesz zobaczyć tylko znaczniki z określonego źródła, które ma normalne lub krytyczne znaczenie, możesz skonfigurować filtr w oknie dialogowym [Ustawienia zaawansowane.](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) Znaczenie znacznika jest wyświetlane w jego etykietce narzędzia i w [raporcie znaczników](../profiling/markers-report.md).

## <a name="marker-category"></a>Kategoria znaczników
 Kategoria znacznika wskazuje grupę zdarzeń znacznika, które pochodzą z tego samego źródła.  Wizualizator współbieżności używa koloru do rozróżniania różnych kategorii flag i zakresów. Wizualizator współbieżności można skonfigurować tak, aby używał kategorii do filtrowania zdarzeń znaczników od określonego dostawcy zdarzeń.  Aby skonfigurować filtr, użyj okna dialogowego [Ustawienia zaawansowane.](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md)

## <a name="known-sources-of-markers"></a>Znane źródła markerów
 Każdy dostawca ETW może generować znaczniki, o ile dostawca przestrzega pewnych ograniczeń. Wizualizator współbieżności można skonfigurować, aby nasłuchiwać dodatkowych źródeł zdarzeń dla znaczników. Domyślnie nasłuchuje tych źródeł zdarzeń:

- [Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)

- [Biblioteka zadań równoległych (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)

- [Przepływ danych](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)

- [Równoległe LINQ (PLINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)

- [Środowisko uruchomieniowe współbieżności](/cpp/parallel/concrt/concurrency-runtime)

- [Obsługa znaczników scenariuszy](/previous-versions/visualstudio/visual-studio-2010/dd984115\(v\=vs.100\))

- [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)

  Za pomocą karty Znaczniki w oknie dialogowym [Ustawienia zaawansowane](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) można kontrolować, czy znaczniki z różnych źródeł są wyświetlane w wizualizatorze współbieżności i można filtrować znaczniki na podstawie ważności i kategorii.

## <a name="markers-from-eventsource"></a>Znaczniki z eventsource
 Wizualizator współbieżności można również wyświetlać zdarzenia EventSource.  Aby uzyskać więcej informacji, zobacz [Wizualizacja zdarzeń EventSource jako znaczników](../profiling/visualizing-eventsource-events-as-markers.md).

## <a name="see-also"></a>Zobacz też
- [Znaczniki flagi](../profiling/flag-markers.md)
- [Znaczniki wiadomości](../profiling/message-markers.md)
- [Znaczniki zakresu](../profiling/span-markers.md)
- [Wizualizuj zdarzenia EventSource jako znaczniki](../profiling/visualizing-eventsource-events-as-markers.md)