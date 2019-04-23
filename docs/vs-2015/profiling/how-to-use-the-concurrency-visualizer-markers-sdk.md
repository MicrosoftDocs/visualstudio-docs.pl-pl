---
title: 'Instrukcje: Użyj znaczników wizualizatora współbieżności SDK | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 00957e742f5731d43881df4f0ff9e18bfd7cf773
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60085730"
---
# <a name="how-to-use-the-concurrency-visualizer-markers-sdk"></a>Instrukcje: Korzystanie ze znaczników zestawu SDK narzędzia Concurrency Visualizer

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie pokazano, jak za pomocą SDK narzędzia Concurrency Visualizer utworzyć zakresy i zapisać flagi, wiadomości i alerty.

### <a name="to-use-c"></a>Aby użyć języka C++

1. Dodanie obsługi SDK narzędzia Concurrency Visualizer do aplikacji. Aby uzyskać więcej informacji, zobacz [SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md).

2. Dodaj `include` instrukcji i `using` instrukcji dla zestawu SDK.

    ```cpp
    #include <cvmarkersobj.h>
    using namespace Concurrency::diagnostic;
    ```

3. Dodaj kod, aby utworzyć trzy zakresy w domyślnej znaczników serii i zapis flagi, wiadomości i alertu, jeden na każdy zakres. Metody, które można zapisać flagi, wiadomości i alerty są elementami członkowskimi [marker_series](../profiling/marker-series-class.md) klasy. Konstruktor [span](../profiling/span-class.md) klasa wymaga `marker_series` obiektu tak, aby każdy zakres jest skojarzony z serii określonego znacznika. A `span` kończy się, gdy zostanie usunięta.

    ```cpp
    marker_series series;
    span *flagSpan = new span(series, 1, _T("flag span"));
    series.write_flag(_T("Here is the flag."));
    delete flagSpan;

    span *messageSpan = new span(series, 2, _T("message span"));
    series.write_flag(_T("Here is the message."));
    delete messageSpan;

    span *alertSpan = new span(series, 3, _T("alert span"));
    series.write_flag(_T("Here is the alert."));
    delete alertSpan;
    ```

4. Na pasku menu wybierz **analizy**, **Concurrency Visualizer**, **Rozpocznij od bieżącego projektu** Aby uruchomić aplikację i wyświetlić wizualizatora współbieżności. Na poniższej ilustracji przedstawiono trzy znaczniki i trzy zakresy w Wizualizatorze współbieżności.

     ![Narzędzie CONCURRENCY Visualizer z 3 znaczniki i alertami](../profiling/media/cvmarkersnative.png "CvMarkersNative")

5. Dodaj kod, aby utworzyć dodatkowe, niestandardowych znaczników serii przez wywołanie konstruktora dla `marker_series` która pobiera nazwę ciągu dla serii znacznika.

    ```cpp
    marker_series flagSeries(_T("flag series"));
    span *flagSeriesSpan = new span(flagSeries, 1, _T("flag span"));
    flagSeries.write_flag(1, _T("flag"));
    // Sleep to even out the display in the Concurrency Visualizer.
    Sleep(50);
    delete flagSeriesSpan;

    marker_series messageSeries(_T("message series"));
    span *messageSeriesSpan = new span(messageSeries, 1, _T("message span"));
    messageSeries.write_message(1, _T("message"));
    // Sleep to even out the display in the Concurrency Visualizer.
    Sleep(50);
    delete messageSeriesSpan;
    ```

6. Uruchom bieżący projekt do wyświetlenia w Wizualizatorze współbieżności. Serii dwóch znacznika pojawiają się w ich własnych pasmach w widoku wątków. Poniższa ilustracja przedstawia dwa nowe zakresy.

     ![Narzędzie CONCURRENCY Visualizer 3 serii znacznika niestandardowego](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNative")

### <a name="to-use-visual-basic-or-c"></a>Aby użyć programu Visual Basic lub C\#

1. Dodanie obsługi SDK narzędzia Concurrency Visualizer do aplikacji. Aby uzyskać więcej informacji, zobacz [SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md).

2. Dodaj `using` lub `Imports` instrukcji dla zestawu SDK.

    ```vb
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

3. Dodaj kod, aby utworzyć trzy zakresy na domyślnej znaczników serii i wpisać flagi, wiadomości i alertu, jeden na każdy zakres. Możesz utworzyć <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Span> obiektu przez wywołanie metody statyczne ([EnterSpan]<!-- TODO: review code entity reference <xref:assetId:///EnterSpan?qualifyHint=False&amp;autoUpgrade=True>  -->) metody. Można zapisać do domyślnej serii, użyj metod statycznych zapisu <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers> klasy.

    ```vb
    Dim flagSpan As Span = Markers.EnterSpan("flag span")
    Markers.WriteFlag("Here is the flag.")
    flagSpan.Leave()

    Dim messageSpan As Span = Markers.EnterSpan("message span")
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1)
    Markers.WriteMessage("Here is a message")
    messageSpan.Leave()

    Dim alertSpan As Span = Markers.EnterSpan("alert span")
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1)
    Markers.WriteAlert("Here is an alert")
    alertSpan.Leave()
    ```

    ```csharp
    Span flagSpan = Markers.EnterSpan("flag span");
    Markers.WriteFlag("Here is the flag.");
    flagSpan.Leave();

    Span messageSpan = Markers.EnterSpan("message span");
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1);
    Markers.WriteMessage("Here is a message");
    messageSpan.Leave();

    Span alertSpan = Markers.EnterSpan("alert span");
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1);
    Markers.WriteAlert("Here is an alert");
    alertSpan.Leave();
    ```

4. Na pasku menu wybierz **analizy**, **Concurrency Visualizer**, **Rozpocznij od bieżącego projektu** Aby uruchomić aplikację i wyświetlić wizualizatora współbieżności. Na poniższej ilustracji przedstawiono trzy znaczniki i trzy zakresy w widoku wątków narzędzia Concurrency visualizer.

     ![Narzędzie CONCURRENCY Visualizer ze znacznikami i alerty](../profiling/media/cvmarkersmanaged.png "CvMarkersManaged")

5. Dodaj kod, aby utworzyć serii znacznika klienta przy użyciu statycznej <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.CreateMarkerSeries%2A> metody. <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries> Klasa zawiera metody służące do tworzenia zakresów i zapisywanie flagi, wiadomości i alerty.

    ```vb
    Dim flagSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series")
    Dim flagSeriesSpan As Span = flagSeries.EnterSpan("flag span")
    System.Threading.Thread.Sleep(1)
    flagSeries.WriteFlag(1, "flag")
    System.Threading.Thread.Sleep(1)
    flagSeriesSpan.Leave()

    Dim messageSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("message series")
    Dim messageSeriesSpan As Span = messageSeries.EnterSpan("message span")
    messageSeries.WriteMessage("message")
    System.Threading.Thread.Sleep(1)
    messageSeriesSpan.Leave()
    ```

    ```csharp
    MarkerSeries flagSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series");
    Span flagSeriesSpan = flagSeries.EnterSpan("flag span");
    System.Threading.Thread.Sleep(1);
    flagSeries.WriteFlag(1, "flag");
    System.Threading.Thread.Sleep(1);
    flagSeriesSpan.Leave();

    MarkerSeries messageSeries = Markers.DefaultWriter.CreateMarkerSeries("message series");
    Span messageSeriesSpan = messageSeries.EnterSpan("message span");
    messageSeries.WriteMessage("message");
    System.Threading.Thread.Sleep(1);
    messageSeriesSpan.Leave();
    ```

6. Uruchom bieżący projekt do wyświetlenia w Wizualizatorze współbieżności. Serii trzech znacznika pojawiają się w ich własnych pasmach w widoku wątków. Poniższa ilustracja przedstawia trzy nowe zakresy.

     ![Narzędzie CONCURRENCY Visualizer 3 serii znacznika niestandardowego](../profiling/media/cvmarkerseriesmanaged.png "CvMarkerSeriesManaged")

## <a name="see-also"></a>Zobacz też

- [Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)
