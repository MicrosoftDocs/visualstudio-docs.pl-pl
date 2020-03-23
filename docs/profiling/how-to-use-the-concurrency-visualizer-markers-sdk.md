---
title: 'Jak: Użyj sdk markerów wizualizatora współbieżności | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d97ea90963f70d3a06c669f08473bab27fa08bd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "68870332"
---
# <a name="how-to-use-the-concurrency-visualizer-markers-sdk"></a>Jak: Użyj sdk znaczników wizualizatora współbieżności
W tym temacie pokazano, jak używać SDK wizualizatora współbieżności do tworzenia zakresów i pisania flag, wiadomości i alertów.

### <a name="to-use-c"></a>Aby użyć języka C++

1. Dodaj obsługę SDK wizualizatora współbieżności do aplikacji. Aby uzyskać więcej informacji, zobacz [SDK wizualizatora współbieżności](../profiling/concurrency-visualizer-sdk.md).

2. Dodaj `include` instrukcję `using` i instrukcję dla SDK.

    ```cpp
    #include <cvmarkersobj.h>
    using namespace Concurrency::diagnostic;
    ```

3. Dodaj kod, aby utworzyć trzy zakresy w domyślnej serii znaczników i napisać flagę, wiadomość i alert, po jednym do każdego zakresu. Metody pisania flag, wiadomości i alerty są członkami [marker_series](../profiling/marker-series-class.md) klasy. Konstruktor dla [span](../profiling/span-class.md) klasy span `marker_series` wymaga obiektu, tak aby każdy zakres jest skojarzony z określoną serią znaczników. A `span` kończy się po usunięciu.

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

4. Na pasku menu wybierz pozycję **Analizuj**, **Wizualizujący współbieżność**, **Rozpocznij od bieżącego projektu,** aby uruchomić aplikację i wyświetlić wizualizator współbieżności. Na poniższej ilustracji przedstawiono trzy zakresy i trzy znaczniki w wizualizatorze współbieżności.

     ![Wizualizator współbieżności z 3 znacznikami i alertami](../profiling/media/cvmarkersnative.png "CvMarkersNarodowy")

5. Dodaj kod, aby utworzyć dodatkowe, niestandardowe `marker_series` serie znaczników, wywołując konstruktora, który przyjmuje nazwę ciągu dla serii znaczników.

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

6. Uruchom bieżący projekt, aby wyświetlić wizualizator współbieżności. Dwie serie znaczników są wyświetlane we własnych pasach ruchu w widoku wątków. Na poniższej ilustracji przedstawiono dwa nowe zakresy.

     ![Wizualizator współbieżności z 3 niestandardowymi seriami znaczników](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNatywny")

### <a name="to-use-visual-basic-or-c"></a>Aby użyć języka Visual Basic lub C\#

1. Dodaj obsługę SDK wizualizatora współbieżności do aplikacji. Aby uzyskać więcej informacji, zobacz [SDK wizualizatora współbieżności](../profiling/concurrency-visualizer-sdk.md).

2. Dodaj `using` lub `Imports` instrukcji dla SDK.

    ```vb
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

3. Dodaj kod, aby utworzyć trzy zakresy w domyślnej serii znaczników i napisać flagę, wiadomość i alert, po jednym do każdego zakresu. Możesz utworzyć [Span](/previous-versions/hh694189(v=vs.140)) obiektu wywołując `EnterSpan` metodę statyczną. Aby zapisać do serii domyślnej, należy użyć statycznych metod zapisu [markerów](/previous-versions/hh694099(v=vs.140)) klasy.

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

4. Na pasku menu wybierz pozycję **Analizuj**, **Wizualizujący współbieżność**, **Rozpocznij od bieżącego projektu,** aby uruchomić aplikację i wyświetlić wizualizator współbieżności. Na poniższej ilustracji przedstawiono trzy zakresy i trzy znaczniki w widoku wątków wizualizatora współbieżności.

     ![Wizualizator współbieżności ze znacznikami i alertami](../profiling/media/cvmarkersmanaged.png "CvMarkersZrządzony")

5. Dodaj kod, aby utworzyć serię znaczników klienta przy użyciu statycznej metody [CreateMarkerSeries.](/previous-versions/hh694171(v=vs.140)) [Klasa MarkerSeries](/previous-versions/hh694127(v=vs.140)) zawiera metody tworzenia zakresów i pisania flag, wiadomości i alertów.

    ```VB

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

6. Uruchom bieżący projekt, aby wyświetlić wizualizator współbieżności. Seria trzech znaczników jest wyświetlana we własnych pasach ruchu w widoku wątków. Na poniższej ilustracji przedstawiono trzy nowe zakresy.

     ![Wizualizator współbieżności z 3 niestandardowymi seriami znaczników](../profiling/media/cvmarkerseriesmanaged.png "CvMarkerSeriesManaged")

## <a name="see-also"></a>Zobacz też
- [Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)
