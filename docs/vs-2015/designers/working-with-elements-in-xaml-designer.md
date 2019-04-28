---
title: Praca z elementami w Projektancie XAML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1063a94ad2ff08942ec191e9162b4b2d506bb048
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63403458"
---
# <a name="working-with-elements-in-xaml-designer"></a>Praca z elementami w Projektancie XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz dodawać elementy — kontrolki, układy i kształty — do aplikacji w XAML, w kodzie lub przy użyciu projektanta XAML. W tym temacie opisano sposób pracy z elementami w Projektancie XAML w programie Visual Studio lub Blend for Visual Studio.  
  
## <a name="adding-an-element-to-a-layout"></a>Dodanie elementu do układu  
 *Układ* polega na rozmiar i położenie elementów w interfejsie użytkownika. Aby zmienić położenie elementów wizualnych, możesz umieścić je w układzie [panelu](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.panel.aspx). A `Panel` ma właściwości elementu podrzędnego, który jest kolekcją z [FrameworkElement](http://msdn.microsoft.com/library/windows/apps/br208706.aspx) typów. Można użyć różnych `Panel` elementy podrzędne, takie jak [kanwy](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.canvas.aspx), [StackPanel](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.aspx), i [siatki](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx), która będzie służyć jako kontenery i to pozycjonowania i rozmieszczania elementów na stronie.  
  
 Domyślnie `Grid` panelu służy jako kontener układu najwyższego poziomu w ramach strony lub formularza. Możesz dodać panele układów, formantów i innych elementów w obrębie układu strony najwyższego poziomu.  
  
#### <a name="to-add-an-element-to-a-layout"></a>Aby dodać element do układu  
  
- W Projektancie XAML wykonaj jedną z następujących czynności:  
  
    - Kliknij dwukrotnie element **przybornika** (lub w przyborniku wybierz element i naciśnij klawisz Enter).  
  
    - Przeciągnij element z **przybornika** do obszaru kompozycji.  
  
    - W **przybornika**, wybierz jedno z narzędzi do rysowania (na przykład [elipsy](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.ellipse.aspx) lub [prostokąt](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.aspx)), a następnie narysuj element aktywnego panelu.  
  
## <a name="changing-the-layering-order-of-elements"></a>Zmiana kolejności warstw elementów  
 Jeśli istnieją dwa elementy w obszarze kompozycji w Projektancie XAML, jeden element pojawi się przed innymi w kolejności warstw. W dolnej części listy elementów w konspekt dokumentu okna jest elementem najbardziej z przodu (z wyjątkiem kiedy **wyznacza indeks** ustawiono właściwość elementu). Po włożeniu element do strony, formularza lub kontener układu elementu automatycznie znajduje się przed inne elementy w elemencie aktywny kontener. Aby zmienić kolejność elementów, można użyć **kolejności** poleceń lub przeciągnąć elementy w drzewie obiektów w okno konspektu dokumentu.  
  
#### <a name="to-change-the-layering-order"></a>Aby zmienić kolejność warstw  
  
- Wykonaj jedną z następujących czynności:  
  
  - W **konspekt dokumentu** okna, przeciągnij elementy w górę lub dół tak, aby utworzyć kolejności warstw żądaną.  
  
  - Kliknij prawym przyciskiem myszy element w okno konspektu dokumentu lub obszaru kompozycji, dla którego chcesz zmienić kolejności warstw, wskaż **kolejności**, a następnie kliknij jedną z następujących czynności:  
  
    - **Przesuń na wierzch** można przenieść elementu do przodu kolejności.  
  
    - **Przesuń do przodu** można przenieść elementu do przodu o jeden poziom w kolejności.  
  
    - **Wyślij do tyłu** wysyłać wstecz o jeden poziom elementów w kolejności.  
  
    - **Przesuń na spód** do wysyłania elementu aż do tyłu kolejności.  
  
    Zmiana **wyznacza indeks** właściwość **układ** sekcji w oknie dialogowym właściwości. Nakładających się elementów **wyznacza indeks** właściwości mają pierwszeństwo przed kolejność elementów wyświetlane w oknie konspekt dokumentu. Element, który ma mniejszy **wyznacza indeks** wartość pojawia się na wierzchu, gdy nakładania się elementów.  
  
## <a name="changing-the-alignment-of-an-element"></a>Zmiana wyrównania elementu  
 Elementy w obszarze kompozycji można wyrównać za pomocą poleceń menu lub poprzez przeciąganie elementów do linii wyrównania.  
  
 A *snapline —* jest wskazówką wizualną, która ułatwia wyrównywanie elementu względem innych elementów w aplikacji.  
  
#### <a name="to-align-two-or-more-elements-by-using-menu-commands"></a>Aby wyrównać co najmniej dwa elementy za pomocą poleceń menu  
  
1. Wybierz elementy, które mają zostać wyrównane. Można wybrać więcej niż jeden element, naciskając i przytrzymując klawisz Ctrl podczas zaznaczania elementów.  
  
2. Wybierz jedną z następujących właściwości w obszarze **HorizontalAlignment** w **układ** okna właściwości: **Po lewej stronie**, **Centrum**, **po prawej stronie**, lub **Stretch**.  
  
3. Wybierz jedną z następujących właściwości w obszarze **VerticalAlignment** w **układ** okna właściwości: **TOP**, **Centrum**, **dolnej**, lub **Stretch**.  
  
#### <a name="to-align-two-or-more-elements-by-using-snaplines"></a>Aby wyrównać co najmniej dwa elementy za pomocą linii przyciągania  
  
- W Projektancie XAML w układzie, który zawiera co najmniej dwa elementy przeciągnij lub jeden z elementów zmiany rozmiaru, dzięki czemu krawędzi jest powiązana z innego elementu.  
  
     Gdy krawędzie są wyrównane, *granicy wyrównania* pojawia się w celu wskazania wyrównania. Granicy wyrównania jest czerwona linia przerywana. Wyrównanie granice są wyświetlane tylko wtedy, gdy **przyciąganie do linii wyrównania** jest włączona. Ilustracja przedstawiająca granicy wyrównania obszaru kompozycji, znajduje się [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
## <a name="changing-the-an-elements-margins"></a>Zmiana marginesów elementu  
 Marginesy w Projektancie XAML określają ilość pustej przestrzeni wokół elementu w obszarze kompozycji. Na przykład marginesy określają ilość miejsca między zewnętrznymi krawędziami elementu i granice `Grid` panel, który zawiera element. Marginesy określają również ilość miejsca między elementami, które są zawarte w `StackPanel`.  
  
#### <a name="to-change-an-elements-margins-in-the-properties-window"></a>Aby zmienić marginesy elementu w oknie dialogowym właściwości  
  
1. Wybierz element, którego marginesy chcesz zmienić.  
  
2. W obszarze **układ** w oknie Właściwości zmień wartość (w pikselach lub jednostek niezależnych od urządzenia, czyli około 1/96 cala) dla każdej z **margines** właściwości (**górnej**, **Po lewej stronie**, **po prawej stronie**, lub **dolnej**).  
  
#### <a name="to-change-an-elements-margins-in-the-artboard"></a>Aby zmienić marginesy elementu w obszarze kompozycji  
  
- Aby zmienić marginesy elementu względem jego kontener układu, kliknij przycisk *moduły definiowania układu marginesu* wyświetlanych wokół elementu w obszarze kompozycji, gdy element jest zaznaczone i znajduje się w kontenerze układu. Ilustracja przedstawiająca moduły definiowania układu marginesu, znajduje się [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
     Jeśli marginesu jest otwarty, w pionie lub poziomie, margines nie jest ustawiony. Jeśli moduł definiowania układu marginesu jest zamknięty, margines jest ustawiony.  
  
     Gdy otworzysz marginesu przeciwny margines nie jest ustawiony, przeciwny margines jest ustawiony na prawidłową wartość zgodnie z lokalizacją elementu w obszarze kompozycji. Marginesy przeciwnej takich jak **po lewej stronie** i **po prawej stronie** marginesy, co najmniej jedna właściwość ma zawsze wartość.  
  
    > [!IMPORTANT]
    > Elementy umieszczone wewnątrz niektóre kontenery układów, takich jak <xref:Windows.UI.Xaml.Controls.Canvas>, nie masz moduły definiowania układu marginesu. Elementy są umieszczone wewnątrz <xref:Windows.UI.Xaml.Controls.StackPanel> ma moduły definiowania układu marginesu, jeden lewego i prawego marginesu lub marginesy górny i dolny, w zależności od orientację `StackPanel`.  
  
## <a name="grouping-and-ungrouping-elements"></a>Grupowanie i rozgrupowywanie elementów  
 Grupowanie dwóch lub więcej elementami w Projektancie XAML tworzy nowy kontener układu i umieszcza te elementy w tym kontenerze. Umieszczenie co najmniej dwa elementy razem w kontener układu umożliwia łatwe wybierz, przenoszenie i przekształcanie grupy jak elementy w tej grupie gdyby jeden element. Grupowanie jest również przydatny do identyfikowania elementów, które są ze sobą powiązane w jakiś sposób, takie jak przyciski, które tworzą element nawigacyjny. Podczas rozgrupowywania elementów po prostu usuwasz kontener układu, który zawiera elementy.  
  
#### <a name="to-group-elements-into-a-new-layout-container"></a>Celu zgrupowania elementów w kontenerze nowy układ  
  
1. Wybierz elementy, które mają zostać zgrupowane. (Aby zaznaczyć wiele elementów, naciśnij i przytrzymaj klawisz Ctrl podczas klikania ich).  
  
2. Kliknij prawym przyciskiem myszy wybranych elementów, wskaż opcję **Grupuj**, a następnie kliknij typ kontener układu, w którym chcesz umieścić grupę.  
  
    > [!TIP]
    > Jeśli wybierzesz <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, lub <xref:Windows.UI.Xaml.Controls.ScrollViewer> do grupowania elementów, elementy są umieszczane w nowym <xref:Windows.UI.Xaml.Controls.Grid> panelu w ramach <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, lub <xref:Windows.UI.Xaml.Controls.ScrollViewer>. Jeśli użytkownik rozgrupuje elementów w jednym z tych kontenery układów tylko <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, lub <xref:Windows.UI.Xaml.Controls.ScrollViewer> zostanie usunięty, a <xref:Windows.UI.Xaml.Controls.Grid> panelu pozostaje. Aby usunąć `Grid` panelu, ponownie Rozgrupuj elementów.  
  
#### <a name="to-ungroup-elements-and-delete-the-layout"></a>Aby rozgrupować elementy i usunąć układ  
  
- Kliknij prawym przyciskiem myszy grupę, którą chcesz rozgrupować, a następnie kliknij przycisk **Ungroup**.  
  
  Można także grupować lub rozgrupować elementy, klikając prawym przyciskiem myszy wybranych elementów w okno konspektu dokumentu i klikając **Grupuj** lub **Ungroup**.  
  
## <a name="resetting-the-element-layout"></a>Resetowanie układu elementu  
 Resetuj układ poleceń można przywrócić wartości domyślnych dla właściwości określonego układu elementu. Za pomocą tego polecenia, możesz zresetować margines, wyrównanie, szerokość, wysokość i rozmiar elementu, pojedynczo lub zbiorczo.  
  
#### <a name="to-reset-the-element-layout"></a>Aby zresetować układ elementów  
  
- Wybierz pozycję w okno konspektu dokumentu lub w obszarze kompozycji kliknij prawym przyciskiem myszy element **układ**, **resetowania** *PropertyName*, gdzie *PropertyName*jest właściwością, który chcesz zresetować (lub wybierz **układ**, **Resetuj wszystko** resetowania wszystkich właściwości układu dla elementu).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
