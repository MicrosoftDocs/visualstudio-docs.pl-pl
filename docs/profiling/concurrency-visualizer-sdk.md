---
title: Wizualizatora współbieżności SDK | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c02959f30f89b8f7c79527026404099a4452a827
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34691189"
---
# <a name="concurrency-visualizer-sdk"></a>Concurrency Visualizer SDK
Przy użyciu zestawu SDK wizualizatora współbieżności, aby wyświetlić dodatkowe informacje w Concurrency Visualizer, mogą dodawać kod źródłowy. Dodatkowe dane można skojarzyć z fazy i zdarzeń w kodzie. Te dodatkowe wizualizacje są określane jako *znaczniki*.  Przewodnik wprowadzający dla [wprowadzenie do zestawu SDK wizualizatora współbieżności](http://go.microsoft.com/fwlink/?LinkId=235405).  
  
## <a name="properties"></a>Właściwości  
 Flagi, zakresy i mieć dwie właściwości wiadomości: kategorii i ważności. W [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe, te właściwości można użyć do filtrowania zestawu znaczników, które są wyświetlane. Ponadto te właściwości mają wpływ na wizualną reprezentację znaczników. Na przykład rozmiar flag jest używana do reprezentowania znaczenie. Ponadto kolor jest służy do wskazania kategorii.  
  
## <a name="basic-usage"></a>Podstawowe sposoby użycia  
 Narzędzia Concurrency Visualizer przedstawia domyślnego dostawcę, który służy do generowania znaczników. Dostawca jest już zarejestrowany wraz z narzędzia Concurrency Visualizer i nie trzeba nic robić, aby znaczniki są wyświetlane w interfejsie użytkownika.  
  
### <a name="c-and-visual-basic"></a>C# i Visual Basic  
 W języku C#, Visual basic i innych kodu zarządzanego, należy użyć domyślnego dostawcy przez wywołanie metody <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>. Udostępnia ona czterech funkcji generowania znaczniki: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A>, i <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>. Istnieje wiele przeciążenia dla tych funkcji, w zależności od tego, czy chcesz użyć wartości domyślnych dla właściwości.  Najprostsza przeciążenia przyjmuje tylko parametr ciąg, który określa opis zdarzenia. Opis jest wyświetlany w raportach wizualizatora współbieżności.  
  
##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Aby dodać obsługę zestawu SDK do projektu C# lub Visual Basic  
  
1.  Na pasku menu wybierz **Analizuj**, **Concurrency Visualizer**, **dodać zestawu SDK do projektu**.  
  
2.  Wybierz projekt, w której ma dostęp do zestawu SDK, a następnie wybierz pozycję **Dodaj zestaw SDK, aby wybrać projekt** przycisku.  
  
3.  Dodaj importów lub przy użyciu instrukcji w kodzie.  
  
    ```csharp  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```VB  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### <a name="c"></a>C++  
 W języku C++, Utwórz [marker_series — klasa](../profiling/marker-series-class.md) obiektu i użyć go do wywołania funkcji.  `marker_series` Klasy udostępnia trzy funkcje generowania znaczników, [marker_series::write_flag — metoda](../profiling/marker-series-write-flag-method.md), [marker_series::write_message — metoda](../profiling/marker-series-write-message-method.md)i [znacznik_ Metoda Series::write_alert](../profiling/marker-series-write-alert-method.md).  
  
##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Aby dodać obsługę zestawu SDK do projektu C++ lub C  
  
1.  Na pasku menu wybierz **Analizuj**, **Concurrency Visualizer**, **dodać zestawu SDK do projektu**.  
  
2.  Wybierz projekt, w której ma dostęp do zestawu SDK, a następnie wybierz pozycję **Dodaj zestaw SDK, aby wybrać projekt** przycisku.  
  
3.  Dla języka C++, obejmują `cvmarkersobj.h`. W przypadku C, zawiera `cvmarkers.h`.  
  
4.  Dodawanie przy użyciu instrukcji w kodzie.  
  
    ```cpp  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  Utwórz `marker_series` obiektu i przekaż go do `span` konstruktora.  
  
    ```C++  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## <a name="custom-usage"></a>Użycie niestandardowej  
 W zaawansowanych scenariuszach SDK wizualizatora współbieżności przedstawia większą kontrolę.  Dwie główne pojęcia są skojarzone z bardziej zaawansowanych scenariuszy: znacznik dostawców i serii znacznika. Znacznik dostawcy są innego dostawcy ETW (każda ma inny identyfikator GUID). Znacznik serii są serial kanały zdarzeń, które są generowane przez jednego dostawcę. Można używać ich do organizowania zdarzeń, które są generowane przez dostawcę znacznika.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Aby użyć nowego dostawcę znacznika w projekcie języka C# lub Visual Basic  
  
1.  Tworzy obiekt <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>.  Konstruktor ma identyfikator GUID.  
  
2.  Aby zarejestrować dostawcę, należy otworzyć narzędzia Concurrency Visualizer [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe.  Wybierz **znaczniki** karcie, a następnie wybierz pozycję **Dodaj nowego dostawcę** przycisku. W [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okna dialogowego wprowadź identyfikator GUID, który został użyty do utworzenia dostawcy i opis dostawcy.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>Aby użyć nowego dostawcę znacznika w projektach C++ lub C  
  
1.  Użyj `CvInitProvider` funkcji, aby zainicjować PCV_PROVIDER.  Konstruktor ma identyfikator GUID * i PCV_PROVIDER\*.  
  
2.  Aby zarejestrować dostawcę, należy otworzyć [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe.  Wybierz **znaczniki** karcie, a następnie wybierz pozycję **Dodaj nowego dostawcę** przycisku. W tym oknie wprowadź identyfikator GUID, który został użyty do utworzenia dostawcy i opis dostawcy.  
  
#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Aby użyć serii znacznika w projekcie języka C# lub Visual Basic  
  
1.  Aby użyć nowego <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries>, najpierw utworzyć przy użyciu <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> obiekt, a następnie wygeneruj znacznika zdarzenia bezpośrednio z nowej serii.  
  
    ```csharp  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries("Series 1");  
    series1.WriteFlag("My flag");  
    ```  
  
    ```VB  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries("Series 1")  
    series1.WriteFlag("My flag")  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Aby użyć serii znacznika w projektach C++  
  
1.  Tworzy obiekt `marker_series`.  Można generować zdarzenia z tej nowej serii.  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Aby użyć serii znacznika w projekcie C  
  
1.  Użyj `CvCreateMarkerSeries` funkcja służąca do tworzenia PCV_MARKERSERIES.  
  
    ```C++  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## <a name="see-also"></a>Zobacz także  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Odwołanie do biblioteki C++](../profiling/cpp-library-reference.md)|Opisuje narzędzia Concurrency Visualizer interfejsu API dla języka C++.|  
|[Odwołanie do biblioteki C](../profiling/c-library-reference.md)|Opisuje narzędzia Concurrency Visualizer interfejsu API dla C.|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|Opisuje interfejs API wizualizatora współbieżności dla kodu zarządzanego.|  
|[Concurrency Visualizer](../profiling/concurrency-visualizer.md)|Informacje referencyjne dotyczące widoków i raportów profilowania pliki danych, które są generowane przy użyciu metody współbieżności i czy obejmują dane wykonanie wątku.|