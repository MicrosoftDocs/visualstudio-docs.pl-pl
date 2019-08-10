---
title: Zestaw SDK wizualizatora współbieżności | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eaaaacdcc5cf7e3044505f7cdb7aeb2e7e3e7078
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871965"
---
# <a name="concurrency-visualizer-sdk"></a>Concurrency Visualizer SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz instrumentować kod źródłowy przy użyciu zestawu SDK wizualizatora współbieżności, aby wyświetlić dodatkowe informacje w wizualizatorze współbieżności. Możesz skojarzyć dodatkowe dane z fazami i zdarzeniami w kodzie. Te dodatkowe wizualizacje są znane jako *znaczniki*.  Aby zapoznać się z przewodnikiem wprowadzającym, zobacz [wprowadzenie do zestawu SDK wizualizatora współbieżności](http://go.microsoft.com/fwlink/?LinkId=235405).

## <a name="properties"></a>Właściwości
 Flagi, zakresy i komunikaty mają dwie właściwości: Category i ważności. W oknie dialogowym [Ustawienia zaawansowane](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) można użyć tych właściwości do filtrowania zestawu znaczników, które są wyświetlane. Ponadto te właściwości wpływają na wizualną reprezentację znaczników. Na przykład rozmiar flag jest używany do reprezentowania znaczenia. Dodatkowo kolor jest używany do wskazania kategorii.

## <a name="basic-usage"></a>Podstawowe użycie
 Wizualizator współbieżności uwidacznia domyślnego dostawcę, którego można użyć do generowania znaczników. Dostawca jest już zarejestrowany razem ze Wizualizatorem współbieżności i nie trzeba wykonywać żadnych innych czynności, aby znaczniki były wyświetlane w interfejsie użytkownika.

### <a name="c-and-visual-basic"></a>C# i Visual Basic

W C#języku Visual Basic i innym zarządzanym kodzie Użyj domyślnego dostawcy, wywołując metody w klasie Markers [](/previous-versions/hh694099(v=vs.140)) . Udostępnia cztery metody generowania znaczników: [WriteFlag](/previous-versions/hh694185(v=vs.140)), [EnterSpan](/previous-versions/hh694205(v=vs.140)), [WriteMessage](/previous-versions/hh694161(v=vs.140))i [WriteAlert](/previous-versions/hh694180(v=vs.140)). Dla tych funkcji istnieje wiele przeciążeń, w zależności od tego, czy chcesz użyć wartości domyślnych dla właściwości.  Najprostszy Przeciążenie pobiera tylko parametr ciągu, który określa opis zdarzenia. Opis jest wyświetlany w raportach wizualizatora współbieżności.

#### <a name="add-sdk-support-to-a-c-or-visual-basic-project"></a>Dodawanie obsługi zestawu SDK do C# projektu lub Visual Basic

1. Na pasku menu wybierz polecenie **Analizuj**, **Concurrency Visualizer**, **Dodaj zestaw SDK do projektu**.

2. Wybierz projekt, do którego chcesz uzyskać dostęp do zestawu SDK, a następnie wybierz przycisk **Dodaj zestaw SDK do wybranego projektu** .

3. Dodaj instrukcję Imports lub using do kodu.

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

    ```vb
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

### <a name="c"></a>C++
 W C++programie Utwórz obiekt [klasy marker_series](../profiling/marker-series-class.md) i użyj go do wywołania funkcji.  Klasa uwidacznia trzy funkcje do generowania znaczników, Metoda [marker_series:: write_flag](../profiling/marker-series-write-flag-method.md), Metoda [marker_series:: write_message](../profiling/marker-series-write-message-method.md)oraz [Metoda marker_series:: write_alert.](../profiling/marker-series-write-alert-method.md) `marker_series`

##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Aby dodać obsługę zestawu SDK do C++ projektu C lub

1. Na pasku menu wybierz polecenie **Analizuj**, **Concurrency Visualizer**, **Dodaj zestaw SDK do projektu**.

2. Wybierz projekt, do którego chcesz uzyskać dostęp do zestawu SDK, a następnie wybierz przycisk **Dodaj zestaw SDK do wybranego projektu** .

3. Dla C++elementu, `cvmarkersobj.h`include. Dla języka C należy `cvmarkers.h`uwzględnić.

4. Dodaj instrukcję using do kodu.

    ```cpp
    using namespace Concurrency::diagnostic;
    ```

5. Utwórz obiekt i przekaż go `span` do konstruktora. `marker_series`

    ```cpp
    marker_series mySeries;
    span s(mySeries, _T("Span description"));
    ```

## <a name="custom-usage"></a>Niestandardowe użycie
 W przypadku zaawansowanych scenariuszy zestaw SDK wizualizatora współbieżności ujawnia więcej kontroli. Dwa główne koncepcje są powiązane z bardziej zaawansowanymi scenariuszami: dostawcami znaczników i seriami znaczników. Dostawcy znaczników są różnymi dostawcami ETW (każdy z nich ma inny identyfikator GUID). Seria znaczników to szereg kanałów zdarzeń, które są generowane przez jednego dostawcę. Można ich użyć do organizowania zdarzeń generowanych przez dostawcę znaczników.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Aby użyć nowego dostawcy znaczników w projekcie C# lub Visual Basic

1. Utwórz obiekt [MarkerWriter](/previous-versions/hh694138(v=vs.140)) . Konstruktor przyjmuje identyfikator GUID.

2. Aby zarejestrować dostawcę, Otwórz okno dialogowe [Ustawienia zaawansowanego](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) wizualizatora współbieżności.  Wybierz kartę **znaczniki** , a następnie wybierz przycisk **Dodaj nowy dostawca** . W oknie dialogowym [Ustawienia zaawansowane](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) wprowadź identyfikator GUID, który został użyty do utworzenia dostawcy i opis dostawcy.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>Aby użyć nowego dostawcy znaczników w projekcie C++ lub C

1. Użyj funkcji `CvInitProvider` , aby zainicjować PCV_PROVIDER. Konstruktor przyjmuje identyfikatory GUID * i PCV_PROVIDER\*.

2. Aby zarejestrować dostawcę, Otwórz okno dialogowe [Ustawienia zaawansowane](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) . Wybierz kartę **znaczniki** , a następnie wybierz przycisk **Dodaj nowy dostawca** . W tym oknie dialogowym wprowadź identyfikator GUID, który został użyty do utworzenia dostawcy i opis dostawcy.

#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Aby użyć serii znaczników w projekcie C# lub Visual Basic

1. Aby użyć nowego [MarkerSeries](/previous-versions/hh694127(v=vs.140)), należy najpierw utworzyć go przy użyciu obiektu [MarkerWriter](/previous-versions/hh694138(v=vs.140)) , a następnie wygenerować zdarzenia znacznika bezpośrednio z nowej serii.

    ```csharp
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries(″Series 1″);
    series1.WriteFlag(″My flag″);
    ```

    ```vb
    Dim series1 As New myMarkerWriter.CreateMarkerSeries(″Series 1″)
    series1.WriteFlag(″My flag″)
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>Aby użyć serii znaczników w C++ projekcie

1. Tworzy obiekt `marker_series`.  Można generować zdarzenia z tej nowej serii.

    ```scr
    marker_series series;
    series.write_flag(_T("Hello world!"));
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>Aby użyć serii znaczników w projekcie C

1. Użyj funkcji `CvCreateMarkerSeries` , aby utworzyć PCV_MARKERSERIES.

    ```cpp
    PCV_MARKERSERIES series;
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);
    CvWriteFlag(series, _T("Writing a flag"));
    ```

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)|Opisuje interfejs API wizualizatora współbieżności C++dla programu.|
|[Odwołanie do biblioteki języka C](../profiling/c-library-reference.md)|Opisuje interfejs API wizualizatora współbieżności dla języka C.|
|[WMI](/previous-versions/hh694104(v=vs.140))|Opisuje interfejs API wizualizatora współbieżności dla kodu zarządzanego.|
|[Concurrency Visualizer](../profiling/concurrency-visualizer.md)|Informacje referencyjne dotyczące widoków i raportów plików danych profilowania, które są generowane przy użyciu metody współbieżności, które obejmują dane wykonania wątku.|
