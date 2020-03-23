---
title: Współrzędność wizualizująca SDK | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb48733f84dcf484d2c2d7ffb18e838faae07ab0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72911195"
---
# <a name="concurrency-visualizer-sdk"></a>Concurrency Visualizer SDK
Kod źródłowy można przyrządzać za pomocą zestawu SDK wizualizatora współbieżności w celu wyświetlenia dodatkowych informacji w wizualizatorze współbieżności. Dodatkowe dane można skojarzyć z fazami i zdarzeniami w kodzie. Te dodatkowe wizualizacje są znane jako *znaczniki*.  Aby zapoznać się z wprowadzeniem przewodnika, zobacz [Przedstawianie SDK wizualizatora współbieżności](https://blogs.msdn.microsoft.com/visualizeparallel/2011/10/17/introducing-the-concurrency-visualizer-sdk/).

## <a name="properties"></a>Właściwości
 Flagi, zakresy i wiadomości mają dwie właściwości: kategoria i ważność. W oknie dialogowym [Ustawienia zaawansowane](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) można użyć tych właściwości do filtrowania zestawu wyświetlanych znaczników. Ponadto te właściwości wpływają na wizualną reprezentację znaczników. Na przykład rozmiar flagi jest używany do reprezentowania ważność. Ponadto kolor służy do wskazywania kategorii.

## <a name="basic-usage"></a>Podstawowy sposób użycia
 Wizualizator współbieżności udostępnia domyślnego dostawcy, którego można użyć do generowania znaczników. Dostawca jest już zarejestrowany razem z wizualizatorem współbieżności i nie trzeba nic więcej robić, aby znaczniki były wyświetlane w interfejsie użytkownika.

### <a name="c-and-visual-basic"></a>C# i Visual Basic
 W języku C#, Visual basic i innym kodzie zarządzanym użyj domyślnego dostawcy, wywołując metody w klasie [Markery.](/previous-versions/hh694099(v=vs.140)) Udostępnia cztery metody generowania znaczników: [WriteFlag](/previous-versions/hh694185%28v%3dvs.140%29), [EnterSpan](/previous-versions/hh694205(v=vs.140)), [WriteMessage](/previous-versions/hh694161(v=vs.140))i [WriteAlert](/previous-versions/hh694180(v=vs.140)). Istnieje wiele przeciążeń dla tych funkcji, w zależności od tego, czy chcesz użyć ustawień domyślnych dla właściwości.  Najprostsze przeciążenie trwa tylko parametr ciąg, który określa opis zdarzenia. Opis jest wyświetlany w raportach wizualizatora współbieżności.

##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Aby dodać obsługę SDK do projektu języka C# lub Visual Basic

1. Na pasku menu wybierz pozycję **Analizuj**, **Wizualizujący współbieżność**, **Dodaj zestaw SDK do projektu**.

2. Wybierz projekt, w którym chcesz uzyskać dostęp do SDK, a następnie wybierz przycisk **Dodaj zestaw SDK do wybranego projektu.**

3. Dodaj importowanie lub używanie instrukcji do kodu.

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

    ```VB
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

### <a name="c"></a>C++
 W języku C++ utwórz obiekt [marker_series Class](../profiling/marker-series-class.md) i użyj go do wywoływania funkcji.  Klasa `marker_series` udostępnia trzy funkcje generowania znaczników: [marker_series::write_flag Method](../profiling/marker-series-write-flag-method.md), [marker_series::write_message Method](../profiling/marker-series-write-message-method.md)oraz [marker_series::write_alert Method](../profiling/marker-series-write-alert-method.md).

##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Aby dodać obsługę SDK do projektu C++ lub C

1. Na pasku menu wybierz pozycję **Analizuj**, **Wizualizujący współbieżność**, **Dodaj zestaw SDK do projektu**.

2. Wybierz projekt, w którym chcesz uzyskać dostęp do SDK, a następnie wybierz przycisk **Dodaj zestaw SDK do wybranego projektu.**

3. W przypadku języka `cvmarkersobj.h`C++, dołącz . Dla C, `cvmarkers.h`to .

4. Dodaj instrukcję using do kodu.

    ```cpp
    using namespace Concurrency::diagnostic;
    ```

5. Utwórz `marker_series` obiekt i przekaż `span` go konstruktorowi.

    ```C++

    marker_series mySeries;
    span s(mySeries, _T("Span description"));

    ```

## <a name="custom-usage"></a>Niestandardowe użycie
 W przypadku zaawansowanych scenariuszy SDK wizualizatora współbieżności udostępnia większą kontrolę.  Dwa główne pojęcia są skojarzone z bardziej zaawansowanych scenariuszy: dostawców znaczników i serii znaczników. Dostawcy znaczników są różnymi dostawcami ETW (każdy ma inny identyfikator GUID). Seria znaczników to szeregowe kanały zdarzeń generowanych przez jednego dostawcę. Można ich używać do organizowania zdarzeń, które są generowane przez dostawcę znaczników.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Aby użyć nowego dostawcy znaczników w projekcie języka C# lub Visual Basic

1. Utwórz obiekt [MarkerWriter.](/previous-versions/hh694138(v=vs.140))  Konstruktor przyjmuje identyfikator GUID.

2. Aby zarejestrować dostawcę, otwórz okno dialogowe [Ustawienia zaawansowane](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) wizualizatora współbieżności.  Wybierz kartę **Znaczniki,** a następnie wybierz przycisk **Dodaj nowego dostawcę.** W oknie dialogowym [Ustawienia zaawansowane](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) wprowadź identyfikator GUID użyty do utworzenia dostawcy i opis dostawcy.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>Aby użyć nowego dostawcy znaczników w projekcie języka C++ lub C

1. Za `CvInitProvider` pomocą funkcji należy zainicjować PCV_PROVIDER.  Konstruktor przyjmuje identyfikator GUID* i\*PCV_PROVIDER .

2. Aby zarejestrować dostawcę, otwórz okno dialogowe [Ustawienia zaawansowane.](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md)  Wybierz kartę **Znaczniki,** a następnie wybierz przycisk **Dodaj nowego dostawcę.** W tym oknie dialogowym wprowadź identyfikator GUID, który został użyty do utworzenia dostawcy i opis dostawcy.

#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Aby użyć serii znaczników w projekcie języka C# lub Visual Basic

1. Aby użyć nowego [markeraSeries,](/previous-versions/hh694127(v=vs.140))najpierw utwórz go za pomocą [obiektu MarkerWriter,](/previous-versions/hh694138(v=vs.140)) a następnie wygeneruj zdarzenia znaczników bezpośrednio z nowej serii.

    ```csharp
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries("Series 1");
    series1.WriteFlag("My flag");
    ```

    ```VB
    Dim series1 As New myMarkerWriter.CreateMarkerSeries("Series 1")
    series1.WriteFlag("My flag")
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>Aby użyć serii znaczników w projekcie języka C++

1. Utwórz `marker_series` obiekt.  Można generować zdarzenia z tej nowej serii.

    ```scr
    marker_series series;
    series.write_flag(_T("Hello world!"));
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>Aby użyć serii znaczników w projekcie C

1. Funkcja `CvCreateMarkerSeries` służy do tworzenia PCV_MARKERSERIES.

    ```C++
    PCV_MARKERSERIES series;
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);
    CvWriteFlag(series, _T("Writing a flag"));
    ```

## <a name="see-also"></a>Zobacz też

|Tytuł|Opis|
|-----------|-----------------|
|[Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)|W tym artykule opisano interfejs API wizualizatora współbieżności dla języka C++.|
|[Odwołanie do biblioteki C](../profiling/c-library-reference.md)|W tym artykule opisano interfejs API wizualizatora współbieżności dla języka C.|
|[Instrumentacji](/previous-versions/hh694104(v=vs.140))|W tym artykule opisano interfejs API wizualizatora współbieżności dla kodu zarządzanego.|
|[Concurrency Visualizer](../profiling/concurrency-visualizer.md)|Informacje referencyjne dla widoków i raportów profilowania plików danych, które są generowane przy użyciu metody współbieżności i które obejmują dane wykonywania wątku.|