---
title: Narzędzie CONCURRENCY Visualizer zestawu SDK | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a9898037e7dc6beae5d984856ff5c12b74183049
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53884973"
---
# <a name="concurrency-visualizer-sdk"></a>Concurrency Visualizer SDK
Możliwe jest instrumentowanie kodu źródłowego za pomocą SDK narzędzia Concurrency Visualizer, aby wyświetlić dodatkowe informacje w Wizualizatorze współbieżności. Możesz skojarzyć dodatkowe dane przy użyciu etapy i zdarzenia w kodzie. Te dodatkowe wizualizacje, są znane jako *znaczniki*.  Aby uzyskać Przewodnik wprowadzający, zobacz [Przedstawiamy SDK narzędzia Concurrency Visualizer](http://go.microsoft.com/fwlink/?LinkId=235405).  
  
## <a name="properties"></a>Właściwości  
 Flagi, zakresy i komunikaty, każdy z nich ma dwie właściwości: Kategoria i ważność. W [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe, te właściwości można użyć do filtrowania zestawu znaczników, które są wyświetlane. Ponadto te właściwości mają wpływ na wizualnej reprezentacji znaczników. Na przykład rozmiar flagi jest używana do reprezentowania znaczenie. Ponadto kolor jest używany do wskazania kategorii.  
  
## <a name="basic-usage"></a>Podstawowe użycia  
 Wizualizator współbieżności przedstawia domyślnego dostawcę, który służy do generowania znaczników. Dostawca jest już zarejestrowany wraz z Concurrency Visualizer, i nie trzeba nic robić, aby znaczniki są wyświetlane w interfejsie użytkownika.  
  
### <a name="c-and-visual-basic"></a>C# i Visual Basic  
 W języku C#, Visual basic i innego kodu zarządzanego, należy użyć domyślnego dostawcy, wywołując <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>. Udostępnia ona czterech funkcji generowania znaczniki: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A>, i <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>. Istnieje wiele przeciążeń dla tych funkcji, w zależności od tego, czy chcesz użyć wartości domyślnych dla właściwości.  Najprostsza przeciążenia zajmuje tylko jako parametr ciągu, który określa opis zdarzenia. Opis jest wyświetlany w raportach narzędzia Concurrency Visualizer.  
  
##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Aby dodać obsługę zestawu SDK do projektu C# lub Visual Basic  
  
1.  Na pasku menu wybierz **analizy**, **Concurrency Visualizer**, **Dodawanie zestawu SDK do projektu**.  
  
2.  Wybierz projekt, w której ma dostęp do zestawu SDK, a następnie wybierz polecenie **Dodawanie zestawu SDK do projektu wybrano** przycisku.  
  
3.  Dodaj import lub przy użyciu instrukcji w kodzie.  
  
    ```csharp  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```VB  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### <a name="c"></a>C++  
 W języku C++, należy utworzyć [marker_series — klasa](../profiling/marker-series-class.md) obiektu i użyć go do wywołania funkcji.  `marker_series` Klasa udostępnia trzy funkcje generowania znaczników, [metoda marker_series::write_flag](../profiling/marker-series-write-flag-method.md), [metoda marker_series::write_message](../profiling/marker-series-write-message-method.md)i [znacznik_ Metoda Series::write_alert](../profiling/marker-series-write-alert-method.md).  
  
##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Aby dodać obsługę zestawu SDK do projektu C++ lub C  
  
1.  Na pasku menu wybierz **analizy**, **Concurrency Visualizer**, **Dodawanie zestawu SDK do projektu**.  
  
2.  Wybierz projekt, w której ma dostęp do zestawu SDK, a następnie wybierz polecenie **Dodawanie zestawu SDK do projektu wybrano** przycisku.  
  
3.  Dla języka C++, obejmują `cvmarkersobj.h`. Dla języka C zawierają `cvmarkers.h`.  
  
4.  Dodaj przy użyciu instrukcji w kodzie.  
  
    ```cpp  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  Tworzenie `marker_series` obiektu i przekazać ją do `span` konstruktora.  
  
    ```C++  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## <a name="custom-usage"></a>Niestandardowe użycie  
 W przypadku zaawansowanych scenariuszy SDK narzędzia Concurrency Visualizer udostępnia większą kontrolę.  Dwa główne pojęcia są skojarzone z bardziej zaawansowanych scenariuszy: dostawców znaczników i znaczników serii. Dostawców znaczników narzędzia są różnych dostawców ETW (każda ma inny identyfikator GUID). Serie znacznika są serial kanały zdarzeń, które są generowane przez jednego dostawcę. Można ich użyć do organizowania zdarzeń, które są generowane przez dostawcę znaczników.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Aby użyć nowego dostawcę znaczników w projekcie języka C# lub Visual Basic  
  
1.  Tworzy obiekt <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>.  Konstruktor przyjmuje postać identyfikatora GUID.  
  
2.  Aby zarejestrować dostawcę, Otwórz narzędzie Concurrency Visualizer [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe.  Wybierz **znaczniki** kartę, a następnie wybierz **Dodaj nowego dostawcę** przycisku. W [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okna dialogowego wprowadź identyfikator GUID, który został użyty do utworzenia dostawcy i opis dostawcy.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>Aby użyć nowego dostawcę znaczników w projekcie języka C++ lub C  
  
1.  Użyj `CvInitProvider` funkcji, aby zainicjować PCV_PROVIDER.  Konstruktor przyjmuje identyfikator GUID *, a PCV_PROVIDER\*.  
  
2.  Aby zarejestrować dostawcę, należy otworzyć [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe.  Wybierz **znaczniki** kartę, a następnie wybierz **Dodaj nowego dostawcę** przycisku. W tym oknie dialogowym Wprowadź identyfikator GUID, który został użyty do utworzenia dostawcy i opis dostawcy.  
  
#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Aby użyć znaczników serii w projekcie języka C# lub Visual Basic  
  
1.  Aby użyć nowego <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries>, najpierw utworzyć za pomocą <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> obiektu, a następnie wygeneruj znacznika zdarzenia bezpośrednio z poziomu nowej serii.  
  
    ```csharp  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries("Series 1");  
    series1.WriteFlag("My flag");  
    ```  
  
    ```VB  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries("Series 1")  
    series1.WriteFlag("My flag")  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Aby użyć serii znacznika w projekcie C++.  
  
1.  Tworzy obiekt `marker_series`.  Zdarzenia można wygenerować z tej nowej serii.  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Aby użyć znaczników serii w projekcie języka C  
  
1.  Użyj `CvCreateMarkerSeries` funkcji, aby utworzyć PCV_MARKERSERIES.  
  
    ```C++  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## <a name="see-also"></a>Zobacz także  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)|Opisuje interfejs API wizualizatora współbieżności dla języka C++.|  
|[Odwołanie do biblioteki C](../profiling/c-library-reference.md)|W tym artykule opisano interfejs API wizualizatora współbieżności dla języka C.|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|Opisuje interfejs API wizualizatora współbieżności dla kodu zarządzanego.|  
|[Concurrency Visualizer](../profiling/concurrency-visualizer.md)|Informacje referencyjne dotyczące widoków i raportów plików danych, które są generowane przy użyciu metody współbieżności i że profilowania obejmują danych wykonanie wątku.|