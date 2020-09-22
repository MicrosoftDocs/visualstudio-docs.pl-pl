---
title: Korzystanie z zestawu znaczniki wizualizatora współbieżności | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cf33ad094716ee0f8f4c8cc4bb06220db1237e5
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851583"
---
# <a name="how-to-use-the-concurrency-visualizer-markers-sdk"></a>Instrukcje: korzystanie z zestawu SDK znaczników Concurrency Visualizer
W tym temacie pokazano, jak używać zestawu SDK wizualizatora współbieżności do tworzenia zakresów i flag zapisu, komunikatów i alertów.

### <a name="to-use-c"></a>Aby użyć języka C++

1. Dodaj do aplikacji obsługę zestawu SDK wizualizatora współbieżności. Aby uzyskać więcej informacji, zobacz [zestaw SDK wizualizatora współbieżności](../profiling/concurrency-visualizer-sdk.md).

2. Dodaj `include` instrukcję i `using` instrukcję dla zestawu SDK.

    ```cpp
    #include <cvmarkersobj.h>
    using namespace Concurrency::diagnostic;
    ```

3. Dodaj kod, aby utworzyć trzy zakresy w domyślnej serii znaczników i napisać flagę, komunikat i alert, jeden do każdego zakresu. Metody zapisywania flag, komunikatów i alertów są elementami członkowskimi klasy [marker_series](../profiling/marker-series-class.md) . Konstruktor klasy [span](../profiling/span-class.md) wymaga `marker_series` obiektu, dzięki czemu każdy zakres jest skojarzony z konkretną serią znaczników. `span`Zostanie zakończona po usunięciu.

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

4. Na pasku menu wybierz kolejno opcje **Analizuj**, **Concurrency Visualizer**, **Rozpocznij od bieżącego projektu** , aby uruchomić aplikację i wyświetlić Wizualizator współbieżności. Na poniższej ilustracji przedstawiono trzy zakresy i trzy znaczniki w wizualizatorze współbieżności.

     ![Wizualizator współbieżności z 3 znacznikami i alertami](../profiling/media/cvmarkersnative.png "CvMarkersNative")

5. Dodaj kod, aby utworzyć dodatkową, niestandardową serię znaczników przez wywołanie konstruktora dla `marker_series` , który pobiera nazwę ciągu dla serii znaczników.

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

6. Uruchom bieżący projekt, aby wyświetlić Wizualizator współbieżności. Dwie serie znaczników pojawiają się w ich własnych tory w widoku wątki. Na poniższej ilustracji przedstawiono dwa nowe zakresy.

     ![Wizualizator współbieżności z 3 seriami niestandardowych znaczników](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNative")

### <a name="to-use-visual-basic-or-c"></a>Aby użyć Visual Basic lub C\#

1. Dodaj do aplikacji obsługę zestawu SDK wizualizatora współbieżności. Aby uzyskać więcej informacji, zobacz [zestaw SDK wizualizatora współbieżności](../profiling/concurrency-visualizer-sdk.md).

2. Dodaj `using` instrukcję or `Imports` dla zestawu SDK.

    ```vb
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

3. Dodaj kod, aby utworzyć trzy zakresy na domyślnej serii znaczników i napisać flagę, komunikat i alert, jeden do każdego zakresu. Tworzysz obiekt [span](/previous-versions/hh694189(v=vs.140)) przez wywołanie metody statycznej `EnterSpan` . Aby zapisać w serii domyślnej, należy użyć statycznych metod zapisu klasy [Marks](/previous-versions/hh694099(v=vs.140)) .

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

4. Na pasku menu wybierz kolejno opcje **Analizuj**, **Concurrency Visualizer**, **Rozpocznij od bieżącego projektu** , aby uruchomić aplikację i wyświetlić Wizualizator współbieżności. Na poniższej ilustracji przedstawiono trzy zakresy i trzy znaczniki w widoku wątki wizualizatora współbieżności.

     ![Wizualizator współbieżności ze znacznikami i alertami](../profiling/media/cvmarkersmanaged.png "CvMarkersManaged")

5. Dodaj kod, aby utworzyć serię znaczników klienta przy użyciu statycznej metody [CreateMarkerSeries](/previous-versions/hh694171(v=vs.140)) . Klasa [MarkerSeries](/previous-versions/hh694127(v=vs.140)) zawiera metody tworzenia zakresów i pisania flag, wiadomości i alertów.

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

6. Uruchom bieżący projekt, aby wyświetlić Wizualizator współbieżności. Trzy serie znaczników pojawiają się w swoich własnych tory w widoku wątki. Na poniższej ilustracji przedstawiono trzy nowe zakresy.

     ![Wizualizator współbieżności z 3 seriami niestandardowych znaczników](../profiling/media/cvmarkerseriesmanaged.png "CvMarkerSeriesManaged")

## <a name="see-also"></a>Zobacz także
- [Concurrency Visualizer SDK](../profiling/concurrency-visualizer-sdk.md)
