---
title: Znaczniki CONCURRENCY Visualizer | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 64b602b5c00380449eb1c296ccde98a88bdc1abc
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56600236"
---
# <a name="concurrency-visualizer-markers"></a>Znaczniki CONCURRENCY Visualizer
W Wizualizatorze współbieżności znaczniki są ikon reprezentujących zdarzenia w aplikacji.  Zazwyczaj aplikacja wygeneruje tych zdarzeń do wyznaczenia fazy lub wystąpień w aplikacji.  Zdarzenia mogą być generowane przez aplikację lub bibliotek i środowisk wykonawczych, przez aplikację.

## <a name="kinds-of-markers"></a>Rodzaje znaczników
 Narzędzie Concurrency Visualizer używa trzy rodzaje znaczników, który reprezentuje zdarzenia aplikacji: flaguje wiadomości i obejmuje.

1.  Użyj *flagi* do wskazania interesujące punktu w czasie w swojej aplikacji.  Na przykład może użyć flagi do reprezentowania, że wartość zmiennej osiągnęła określony próg lub został zgłoszony wyjątek.

2.  A *komunikat* również znaczniki punktu w czasie, ale możesz go używać stylu dziennika śledzenia.  Na przykład co może mieć zostały zrzucone do pliku dziennika, który teraz można opakować wywołanie wiadomości, aby można ją śledzić i wyświetlać go w Wizualizatorze współbieżności. Narzędzie Concurrency Visualizer umożliwia również wyeksportować te dane do pliku CSV.

3.  A *span* reprezentuje przedział czasu w swojej aplikacji, na przykład jeden z jego faz.

## <a name="marker-linkage-to-threads"></a>Powiązania znacznika dla wątków
 Każdy wątek, który generuje znaczniki ma kanału oddzielne osi czasu.  Identyfikator wątku, który jest odpowiedzialny za wygenerowanie zdarzenia znacznik jest wyświetlany obok opis kanału znacznika.  Identyfikator, który jest wyświetlany po lewej stronie kanału znaczników zgodny z Identyfikatorem inny wątek w bieżącym procesie.

## <a name="marker-importance"></a>Znaczenie znacznika
 Znaczniki może mieć jedną z czterech poziomów ważności: niska, normalna, wysokiej i krytyczne.  Można filtrować źródeł znaczników na podstawie poziomu ważności.  Na przykład, jeśli chcesz tylko zobaczyć znaczniki z określonego źródła, zawierającej normalnej lub krytyczne znaczenie, można skonfigurować filtr w [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe. Znaczenie znacznik jest wyświetlany w jego etykietki narzędzi i w [raport dotyczący znaczników](../profiling/markers-report.md).

## <a name="marker-category"></a>Kategoria znacznika
 Kategoria znacznika wskazuje grupę znacznika zdarzenia, które pochodzą z tego samego źródła.  Narzędzie Concurrency Visualizer używa kolorów do rozróżniania różne kategorie flag i zakresy. Można skonfigurować narzędzie Concurrency Visualizer można użyć kategorii do filtrowania zdarzeń znacznika od dostawcy określonego zdarzenia.  Użyj [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe, aby skonfigurować filtr.

## <a name="known-sources-of-markers"></a>Znanych źródeł znaczników
 Wszystkich dostawców ETW może generować znaczniki, tak długo, jak dostawca działa zgodnie z określonymi ograniczeniami. Można skonfigurować narzędzie Concurrency Visualizer do nasłuchiwania ze źródłami zdarzeń dodatkowe znaczniki. Domyślnie nasłuchuje on do tych źródeł zdarzeń:

- [Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)

- [Biblioteka zadań równoległych (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)

- [Przepływ danych](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)

- [Równoległe LINQ (PLINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)

- [Środowisko uruchomieniowe współbieżności](/cpp/parallel/concrt/concurrency-runtime)

- [Obsługa znaczników scenariusza](/previous-versions/visualstudio/visual-studio-2010/dd984115\(v\=vs.100\))

- [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)

  Można użyć karty znaczników w [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe, aby kontrolować, czy znaczniki z różnych źródeł, są wyświetlane w Wizualizatorze współbieżności i filtrować dla znaczników na podstawie ważności i kategorii.

## <a name="markers-from-eventsource"></a>Znaczniki z źródła zdarzeń
 Narzędzie Concurrency Visualizer można również wyświetlić zdarzeń EventSource.  Aby uzyskać więcej informacji, zobacz [zdarzeń EventSource wizualizacji jako znaczniki](../profiling/visualizing-eventsource-events-as-markers.md).

## <a name="see-also"></a>Zobacz także
- [Znaczniki typu Flaga](../profiling/flag-markers.md)
- [Znaczniki komunikatu](../profiling/message-markers.md)
- [Znaczniki zakresu](../profiling/span-markers.md)
- [Wizualizowanie zdarzeń EventSource w postaci znaczników](../profiling/visualizing-eventsource-events-as-markers.md)