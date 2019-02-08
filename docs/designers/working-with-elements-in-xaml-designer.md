---
title: Praca z elementami w Projektancie XAML
ms.date: 05/14/2018
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 1fa232ccefed20608ec2391f591ac0a8a6f31fe2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931341"
---
# <a name="work-with-elements-in-xaml-designer"></a>Praca z elementami w projektancie XAML

Możesz dodawać elementy — kontrolki, układy i kształty — do aplikacji w XAML, w kodzie lub przy użyciu projektanta XAML. W tym temacie opisano sposób pracy z elementami w Projektancie XAML w programie Visual Studio lub Blend for Visual Studio.

## <a name="add-an-element-to-a-layout"></a>Dodaj element do układu

*Układ* polega na rozmiar i położenie elementów w interfejsie użytkownika. Aby zmienić położenie elementów wizualnych, możesz umieścić je w układzie [panelu](/uwp/api/Windows.UI.Xaml.Controls.Panel). A `Panel` ma właściwości elementu podrzędnego, który jest kolekcją z [FrameworkElement](/uwp/api/Windows.UI.Xaml.FrameworkElement) typów. Można użyć różnych `Panel` elementy podrzędne, takie jak [kanwy](/uwp/api/Windows.UI.Xaml.Controls.Canvas), [StackPanel](/uwp/api/Windows.UI.Xaml.Controls.StackPanel), i [siatki](/uwp/api/Windows.UI.Xaml.Controls.Grid), która będzie służyć jako kontenery i to pozycjonowania i rozmieszczania elementów na stronie.

Domyślnie `Grid` panelu służy jako kontener układu najwyższego poziomu w ramach strony lub formularza. Możesz dodać panele układów, formantów i innych elementów w obrębie układu strony najwyższego poziomu.

Aby dodać element do układu w Projektancie XAML, wykonaj jedną z następujących czynności:

- Kliknij dwukrotnie element **przybornika** (lub wybierz element w przyborniku, a następnie naciśnij klawisz **Enter**).

- Przeciągnij element z **przybornika** do obszaru kompozycji.

- W **przybornika**, wybierz jedno z narzędzi do rysowania (na przykład [elipsy](/uwp/api/Windows.UI.Xaml.Shapes.Ellipse) lub [prostokąt](/uwp/api/Windows.UI.Xaml.Shapes.Rectangle)), a następnie narysuj element aktywnego panelu.

## <a name="change-the-layering-order-of-elements"></a>Zmiana kolejności warstw elementów

Jeśli istnieją dwa elementy w obszarze kompozycji w Projektancie XAML, jeden element pojawi się przed innymi w kolejności warstw. W dolnej części listy elementów w konspekt dokumentu okna jest elementem najbardziej z przodu (z wyjątkiem kiedy **wyznacza indeks** ustawiono właściwość elementu). Po włożeniu element do strony, formularza lub kontener układu elementu automatycznie znajduje się przed inne elementy w elemencie aktywny kontener. Aby zmienić kolejność elementów, można użyć **kolejności** poleceń lub przeciągnąć elementy w drzewie obiektów w okno konspektu dokumentu.

Aby zmiana kolejności warstw, wykonaj jedną z następujących czynności:

- W **konspekt dokumentu** okna, przeciągnij elementy w górę lub dół tak, aby utworzyć kolejności warstw żądaną.

- Kliknij prawym przyciskiem myszy element w okno konspektu dokumentu lub obszaru kompozycji, dla którego chcesz zmienić kolejności warstw, wskaż **kolejności**, a następnie kliknij jedną z następujących czynności:

   - **Przesuń na wierzch** można przenieść elementu do przodu kolejności.

   - **Przesuń do przodu** można przenieść elementu do przodu o jeden poziom w kolejności.

   - **Wyślij do tyłu** wysyłać wstecz o jeden poziom elementów w kolejności.

   - **Przesuń na spód** do wysyłania elementu aż do tyłu kolejności.

   Zmiana **wyznacza indeks** właściwość **układ** sekcji w oknie dialogowym właściwości. Nakładających się elementów **wyznacza indeks** właściwości mają pierwszeństwo przed kolejność elementów wyświetlane w oknie konspekt dokumentu. Element, który ma wyższe **wyznacza indeks** wartość pojawia się na wierzchu, gdy nakładania się elementów.

## <a name="change-the-alignment-of-an-element"></a>Zmienianie wyrównania elementu

Elementy w obszarze kompozycji można wyrównać za pomocą poleceń menu lub poprzez przeciąganie elementów do linii wyrównania.

A *snapline —* jest wskazówką wizualną, która ułatwia wyrównywanie elementu względem innych elementów w aplikacji.

Aby wyrównać co najmniej dwa elementy za pomocą polecenia menu:

1.  Wybierz elementy, które mają zostać wyrównane. Można wybrać więcej niż jeden element przez naciśnięcie i przytrzymanie **Ctrl** klucza podczas wybierania elementów.

2.  Wybierz jedną z następujących właściwości w obszarze **HorizontalAlignment** w **układ** okna właściwości: **Po lewej stronie**, **Centrum**, **po prawej stronie**, lub **Stretch**.

3.  Wybierz jedną z następujących właściwości w obszarze **VerticalAlignment** w **układ** okna właściwości: **TOP**, **Centrum**, **dolnej**, lub **Stretch**.

Aby wyrównać co najmniej dwa elementy za pomocą linii przyciągania, w Projektancie XAML w układzie, który zawiera co najmniej dwa elementy, przeciągnij lub jeden z elementów zmiany rozmiaru, dzięki czemu krawędzi jest powiązana z innego elementu.

Gdy krawędzie są wyrównane, *granicy wyrównania* pojawia się w celu wskazania wyrównania. Granicy wyrównania jest czerwona linia przerywana. Wyrównanie granice są wyświetlane tylko wtedy, gdy **przyciąganie do linii wyrównania** jest włączona. Ilustracja przedstawiająca granicy wyrównania obszaru kompozycji, znajduje się [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="change-an-elements-margins"></a>Zmiana marginesów elementu

Marginesy w Projektancie XAML określają ilość pustej przestrzeni wokół elementu w obszarze kompozycji. Na przykład marginesy określają ilość miejsca między zewnętrznymi krawędziami elementu i granice `Grid` panel, który zawiera element. Marginesy określają również ilość miejsca między elementami, które są zawarte w `StackPanel`.

Aby zmienić marginesy elementu w oknie dialogowym właściwości:

1.  Wybierz element, którego marginesy chcesz zmienić.

2.  W obszarze **układ** w oknie Właściwości zmień wartość (w pikselach lub jednostek niezależnych od urządzenia, czyli około 1/96 cala) dla każdej z **margines** właściwości (**górnej**, **Po lewej stronie**, **po prawej stronie**, lub **dolnej**).

W obszarze kompozycji, aby zmienić marginesy elementu względem elementu kontener układu, kliknij przycisk *moduły definiowania układu marginesu* wyświetlanych wokół elementu, jeśli element jest zaznaczone i znajduje się w kontenerze układu. Ilustracja przedstawiająca moduły definiowania układu marginesu, znajduje się [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

Jeśli marginesu jest otwarty, w pionie lub poziomie, margines nie jest ustawiony. Jeśli moduł definiowania układu marginesu jest zamknięty, margines jest ustawiony.

Gdy otworzysz marginesu przeciwny margines nie jest ustawiony, przeciwny margines jest ustawiony na prawidłową wartość zgodnie z lokalizacją elementu w obszarze kompozycji. Marginesy przeciwnej takich jak **po lewej stronie** i **po prawej stronie** marginesy, co najmniej jedna właściwość ma zawsze wartość.

> [!IMPORTANT]
> Elementy umieszczone wewnątrz niektóre kontenery układów, takich jak <xref:Windows.UI.Xaml.Controls.Canvas>, nie masz moduły definiowania układu marginesu. Elementy są umieszczone wewnątrz <xref:Windows.UI.Xaml.Controls.StackPanel> ma moduły definiowania układu marginesu, jeden lewego i prawego marginesu lub marginesy górny i dolny, w zależności od orientację `StackPanel`.

## <a name="group-and-ungroup-elements"></a>Grupy i rozgrupowywanie elementów

Grupowanie dwóch lub więcej elementami w Projektancie XAML tworzy nowy kontener układu i umieszcza te elementy w tym kontenerze. Umieszczenie co najmniej dwa elementy razem w kontener układu umożliwia łatwe wybierz, przenoszenie i przekształcanie grupy jak elementy w tej grupie gdyby jeden element. Grupowanie jest również przydatny do identyfikowania elementów, które są ze sobą powiązane w jakiś sposób, takie jak przyciski, które tworzą element nawigacyjny. Podczas rozgrupowywania elementów po prostu usuwasz kontener układu, który zawiera elementy.

Do grupy elementów w kontenerze nowego układu:

1. Wybierz elementy, które mają zostać zgrupowane. (Aby zaznaczyć wiele elementów, naciśnij i przytrzymaj klawisz **Ctrl** klucza podczas klikania je.)

2. Kliknij prawym przyciskiem myszy wybranych elementów, wskaż opcję **Grupuj**, a następnie kliknij typ kontener układu, w którym chcesz umieścić grupę.

    > [!TIP]
    > Jeśli wybierzesz <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, lub <xref:Windows.UI.Xaml.Controls.ScrollViewer> do grupowania elementów, elementy są umieszczane w nowym <xref:Windows.UI.Xaml.Controls.Grid> panelu w ramach <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, lub <xref:Windows.UI.Xaml.Controls.ScrollViewer>. Jeśli użytkownik rozgrupuje elementów w jednym z tych kontenery układów tylko <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, lub <xref:Windows.UI.Xaml.Controls.ScrollViewer> zostanie usunięty, a <xref:Windows.UI.Xaml.Controls.Grid> panelu pozostaje. Aby usunąć `Grid` panelu, ponownie Rozgrupuj elementów.

Aby rozgrupować elementy i usunąć układ, kliknij prawym przyciskiem myszy grupę, którą chcesz rozgrupować, a następnie kliknij przycisk **Ungroup**. Można także grupować lub rozgrupować elementy, klikając prawym przyciskiem myszy wybranych elementów w okno konspektu dokumentu i klikając **Grupuj** lub **Ungroup**.

## <a name="reset-the-element-layout"></a>Resetuj układ elementów

Resetuj układ poleceń można przywrócić wartości domyślnych dla właściwości określonego układu elementu. Za pomocą tego polecenia, możesz zresetować margines, wyrównanie, szerokość, wysokość i rozmiar elementu, pojedynczo lub zbiorczo.

Aby zresetować układ elementów, kliknij prawym przyciskiem myszy element w okno konspektu dokumentu lub obszar roboczy, a następnie wybierz **układ** > **resetowania** *PropertyName* , gdzie *PropertyName* jest właściwością, który chcesz zresetować (lub wybierz **układ** > **Resetuj wszystko** do resetowania wszystkich właściwości element).

## <a name="see-also"></a>Zobacz także

- [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
