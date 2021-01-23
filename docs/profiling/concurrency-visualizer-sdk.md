---
title: Zestaw SDK wizualizatora współbieżności | Microsoft Docs
description: Dowiedz się, jak używać zestawu SDK narzędzia Concurrency Visualizer do Instrumentacji kodu do wyświetlania znaczników. Znaczniki są ikonami wyświetlanymi w wizualizatorze współbieżności, aby oznaczyć zdarzenia.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f07dbfb0ca193f7bacbf2408fc26e622ffb037e1
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720985"
---
# <a name="concurrency-visualizer-sdk"></a>Concurrency Visualizer SDK
Możesz instrumentować kod źródłowy przy użyciu zestawu SDK wizualizatora współbieżności, aby wyświetlić dodatkowe informacje w wizualizatorze współbieżności. Możesz skojarzyć dodatkowe dane z fazami i zdarzeniami w kodzie. Te dodatkowe wizualizacje są znane jako *znaczniki*.  Aby zapoznać się z przewodnikiem wprowadzającym, zobacz [wprowadzenie do zestawu SDK wizualizatora współbieżności](/archive/blogs/visualizeparallel/introducing-the-concurrency-visualizer-sdk).

## <a name="properties"></a>Właściwości
 Flagi, zakresy i komunikaty mają dwie właściwości: Category i ważności. W oknie dialogowym [Ustawienia zaawansowane](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) można użyć tych właściwości do filtrowania zestawu znaczników, które są wyświetlane. Ponadto te właściwości wpływają na wizualną reprezentację znaczników. Na przykład rozmiar flag jest używany do reprezentowania znaczenia. Dodatkowo kolor jest używany do wskazania kategorii.

## <a name="basic-usage"></a>Podstawowy sposób użycia
 Wizualizator współbieżności uwidacznia domyślnego dostawcę, którego można użyć do generowania znaczników. Dostawca jest już zarejestrowany razem ze Wizualizatorem współbieżności i nie trzeba wykonywać żadnych innych czynności, aby znaczniki były wyświetlane w interfejsie użytkownika.

### <a name="c-and-visual-basic"></a>C# i Visual Basic
 W języku C#, Visual Basic i innym zarządzanym kodzie Użyj domyślnego dostawcy, wywołując metody w klasie [Marks](/previous-versions/hh694099(v=vs.140)) . Udostępnia cztery metody generowania znaczników: [WriteFlag](/previous-versions/hh694185%28v%3dvs.140%29), [EnterSpan](/previous-versions/hh694205(v=vs.140)), [WriteMessage](/previous-versions/hh694161(v=vs.140))i [WriteAlert](/previous-versions/hh694180(v=vs.140)). Dla tych funkcji istnieje wiele przeciążeń, w zależności od tego, czy chcesz użyć wartości domyślnych dla właściwości.  Najprostszy Przeciążenie pobiera tylko parametr ciągu, który określa opis zdarzenia. Opis jest wyświetlany w raportach wizualizatora współbieżności.

##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Aby dodać obsługę zestawu SDK do projektu C# lub Visual Basic

1. Na pasku menu wybierz polecenie **Analizuj**, **Concurrency Visualizer**, **Dodaj zestaw SDK do projektu**.

2. Wybierz projekt, do którego chcesz uzyskać dostęp do zestawu SDK, a następnie wybierz przycisk **Dodaj zestaw SDK do wybranego projektu** .

3. Dodaj instrukcję Imports lub using do kodu.

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

    ```VB
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

### <a name="c"></a>C++
 W języku C++ Utwórz obiekt [klasy marker_series](../profiling/marker-series-class.md) i użyj go do wywołania funkcji.  `marker_series`Klasa uwidacznia trzy funkcje do generowania znaczników, metody [marker_series:: write_flag](../profiling/marker-series-write-flag-method.md), [marker_series:: write_message](../profiling/marker-series-write-message-method.md)i [marker_series:: write_alert metody](../profiling/marker-series-write-alert-method.md).

##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Aby dodać obsługę zestawu SDK do projektu C++ lub C

1. Na pasku menu wybierz polecenie **Analizuj**, **Concurrency Visualizer**, **Dodaj zestaw SDK do projektu**.

2. Wybierz projekt, do którego chcesz uzyskać dostęp do zestawu SDK, a następnie wybierz przycisk **Dodaj zestaw SDK do wybranego projektu** .

3. W przypadku języka C++ Uwzględnij `cvmarkersobj.h` . Dla języka C należy uwzględnić `cvmarkers.h` .

4. Dodaj instrukcję using do kodu.

    ```cpp
    using namespace Concurrency::diagnostic;
    ```

5. Utwórz `marker_series` obiekt i przekaż go do `span` konstruktora.

    ```C++

    marker_series mySeries;
    span s(mySeries, _T("Span description"));

    ```

## <a name="custom-usage"></a>Niestandardowe użycie
 W przypadku zaawansowanych scenariuszy zestaw SDK wizualizatora współbieżności ujawnia więcej kontroli.  Dwa główne koncepcje są powiązane z bardziej zaawansowanymi scenariuszami: dostawcami znaczników i seriami znaczników. Dostawcy znaczników są różnymi dostawcami ETW (każdy z nich ma inny identyfikator GUID). Seria znaczników to szereg kanałów zdarzeń, które są generowane przez jednego dostawcę. Można ich użyć do organizowania zdarzeń generowanych przez dostawcę znaczników.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Aby użyć nowego dostawcy znaczników w projekcie C# lub Visual Basic

1. Utwórz obiekt [MarkerWriter](/previous-versions/hh694138(v=vs.140)) .  Konstruktor przyjmuje identyfikator GUID.

2. Aby zarejestrować dostawcę, Otwórz okno dialogowe [Ustawienia zaawansowanego](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) wizualizatora współbieżności.  Wybierz kartę **znaczniki** , a następnie wybierz przycisk **Dodaj nowy dostawca** . W oknie dialogowym [Ustawienia zaawansowane](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) wprowadź identyfikator GUID, który został użyty do utworzenia dostawcy i opis dostawcy.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>Aby użyć nowego dostawcy znaczników w projekcie C++ lub C

1. Użyj `CvInitProvider` funkcji, aby zainicjować PCV_PROVIDER.  Konstruktor przyjmuje identyfikatory GUID * i PCV_PROVIDER \* .

2. Aby zarejestrować dostawcę, Otwórz okno dialogowe [Ustawienia zaawansowane](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) .  Wybierz kartę **znaczniki** , a następnie wybierz przycisk **Dodaj nowy dostawca** . W tym oknie dialogowym wprowadź identyfikator GUID, który został użyty do utworzenia dostawcy i opis dostawcy.

#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Aby użyć serii znaczników w projekcie C# lub Visual Basic

1. Aby użyć nowego [MarkerSeries](/previous-versions/hh694127(v=vs.140)), należy najpierw utworzyć go przy użyciu obiektu [MarkerWriter](/previous-versions/hh694138(v=vs.140)) , a następnie wygenerować zdarzenia znacznika bezpośrednio z nowej serii.

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

1. Użyj `CvCreateMarkerSeries` funkcji, aby utworzyć PCV_MARKERSERIES.

    ```C++
    PCV_MARKERSERIES series;
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);
    CvWriteFlag(series, _T("Writing a flag"));
    ```

## <a name="see-also"></a>Zobacz także

|Tytuł|Opis|
|-----------|-----------------|
|[Dokumentacja biblioteki C++](../profiling/cpp-library-reference.md)|Opisuje interfejs API wizualizatora współbieżności dla języka C++.|
|[Dokumentacja biblioteki języka C](../profiling/c-library-reference.md)|Opisuje interfejs API wizualizatora współbieżności dla języka C.|
|[WMI](/previous-versions/hh694104(v=vs.140))|Opisuje interfejs API wizualizatora współbieżności dla kodu zarządzanego.|
|[Concurrency Visualizer](../profiling/concurrency-visualizer.md)|Informacje referencyjne dotyczące widoków i raportów plików danych profilowania, które są generowane przy użyciu metody współbieżności, które obejmują dane wykonania wątku.|