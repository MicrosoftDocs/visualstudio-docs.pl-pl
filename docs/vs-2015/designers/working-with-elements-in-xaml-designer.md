---
title: Praca z elementami w projektant XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 483023fbd28da26d9967dd2d88bc37748d00f088
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663987"
---
# <a name="working-with-elements-in-xaml-designer"></a>Praca z elementami w projektancie XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz dodawać elementy — kontrolki, układy i kształty — do aplikacji w języku XAML, w kodzie lub przy użyciu projektant XAML. W tym temacie opisano sposób pracy z elementami w projektant XAML w programie Visual Studio lub Blend for Visual Studio.

## <a name="adding-an-element-to-a-layout"></a>Dodawanie elementu do układu
 *Układ* to proces ustalania rozmiarów i pozycjonowania elementów w interfejsie użytkownika. Aby ustawić położenie elementów wizualnych, należy umieścić je w [panelu](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.panel.aspx)układu. @No__t_0 ma właściwość podrzędną, która jest kolekcją typów [FrameworkElement](https://msdn.microsoft.com/library/windows/apps/br208706.aspx) . Możesz użyć różnych `Panel` elementów podrzędnych, takich jak [Kanwa](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.canvas.aspx), [StackPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.aspx)i [Siatka](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx), aby służyć jako kontenery układu oraz umieścić i rozmieścić elementy na stronie.

 Domyślnie panel `Grid` jest używany jako kontener układu najwyższego poziomu w obrębie strony lub formularza. Możesz dodać panele układu, kontrolki lub inne elementy w układzie strony najwyższego poziomu.

#### <a name="to-add-an-element-to-a-layout"></a>Aby dodać element do układu

- W projektant XAML wykonaj jedną z następujących czynności:

  - Kliknij dwukrotnie element w **przyborniku** (lub wybierz element w przyborniku, a następnie naciśnij klawisz ENTER).

  - Przeciągnij element z **przybornika** do obszaru kompozycji.

  - W **przyborniku**wybierz jeden z narzędzi do rysowania (na przykład [elipsę](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.ellipse.aspx) lub [prostokąt](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.aspx)), a następnie narysuj element w aktywnym panelu.

## <a name="changing-the-layering-order-of-elements"></a>Zmiana kolejności warstw elementów
 Gdy w projektant XAML znajdują się dwa elementy obszaru kompozycji, jeden element pojawi się przed drugim w kolejności warstw. W dolnej części listy elementów w oknie konspektu dokumentu znajduje się element (z wyjątkiem sytuacji, gdy ustawiona jest właściwość **ZIndex** elementu). Po wstawieniu elementu do strony, formularza lub kontenera układu element jest automatycznie umieszczany przed innymi elementami w aktywnym elemencie kontenera. Aby zmienić kolejność elementów, można użyć poleceń **Order** lub przeciągnąć elementy w drzewie obiektów w oknie konspektu dokumentu.

#### <a name="to-change-the-layering-order"></a>Aby zmienić kolejność warstw

- Wykonaj jedną z następujących czynności:

  - W oknie **Konspekt dokumentu** przeciągnij elementy w górę lub w dół, aby utworzyć żądaną kolejność warstw.

  - Kliknij prawym przyciskiem myszy element w oknie Konspekt dokumentu lub obszar kompozycji, dla którego chcesz zmienić kolejność warstwową, wskaż pozycję **kolejność**, a następnie kliknij jedną z następujących czynności:

    - **Przesuń na wierzch** , aby przenieść element do przodu w kolejności.

    - **Przesuń do przodu** , aby przenieść element do przodu o jeden poziom w kolejności.

    - **Wyślij do tyłu** , aby wysłać element do tyłu o jeden poziom w kolejności.

    - **Przesuń na spód** , aby wysłać element w sposób do tyłu zamówienia.

    Zmień właściwość **ZIndex** w sekcji **layout** w okno właściwości. Dla nakładających się elementów Właściwość **ZIndex** ma pierwszeństwo przed kolejnością elementów wyświetlanych w oknie konspektu dokumentu. Element o niższej wartości **ZIndex** pojawia się na początku, gdy elementy nakładają się na siebie.

## <a name="changing-the-alignment-of-an-element"></a>Zmiana wyrównania elementu
 Elementy w obszarze kompozycji można wyrównywać za pomocą poleceń menu lub przeciągając elementy do linii wyrównania.

 *Snapline* jest wizualną wizualizacją, która pomaga wyrównać element względem innych elementów w aplikacji.

#### <a name="to-align-two-or-more-elements-by-using-menu-commands"></a>Aby wyrównać dwa lub więcej elementów za pomocą poleceń menu

1. Wybierz elementy, które chcesz wyrównać. Możesz wybrać więcej niż jeden element, naciskając i przytrzymując klawisz CTRL podczas zaznaczania elementów.

2. Wybierz jedną z następujących właściwości w obszarze **HorizontalAlignment** w sekcji **layout** w okno właściwości: **Left**, **Center**, **Right**lub **Rozciągaj**.

3. Wybierz jedną z następujących właściwości w obszarze **VerticalAlignment** w sekcji **layout** w okno właściwości: **Top**, **Center**, **Bottom**lub **Rozciągaj**.

#### <a name="to-align-two-or-more-elements-by-using-snaplines"></a>Aby wyrównać dwa lub więcej elementów za pomocą linii wyrównania

- W projektant XAML w układzie, który zawiera co najmniej dwa elementy, przeciągnij lub Zmień rozmiar jednego z elementów tak, aby krawędź była wyrównana do innego elementu.

     Gdy krawędzie są wyrównane, zostanie wyświetlona *granica wyrównania* wskazująca wyrównanie. Granica wyrównania jest czerwoną linią kreskowaną. Granice wyrównania są wyświetlane tylko wtedy, gdy jest włączone **przyciąganie do linii wyrównania** . Ilustracja przedstawiająca obszar kompozycji, który pokazuje granicę wyrównania, znajduje się w temacie [Tworzenie interfejsu użytkownika przy użyciu Projektant XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="changing-the-an-elements-margins"></a>Zmiana marginesów elementu
 Marginesy w projektant XAML określają ilość pustego miejsca wokół elementu w obszarze kompozycji. Na przykład marginesy określają ilość miejsca między zewnętrznymi krawędziami elementu a granicami panelu `Grid`, który zawiera element. Marginesy określają również ilość miejsca między elementami zawartymi w `StackPanel`.

#### <a name="to-change-an-elements-margins-in-the-properties-window"></a>Aby zmienić marginesy elementu w okno Właściwości

1. Wybierz element, którego marginesy chcesz zmienić.

2. W **obszarze Układ** w okno właściwości Zmień wartość (w pikselach lub jednostkach niezależnych od urządzenia, które są w przybliżeniu 1/96 cala) dla dowolnej właściwości **marginesu** (**górny**, **lewy**, **prawy**lub **dolny**).

#### <a name="to-change-an-elements-margins-in-the-artboard"></a>Aby zmienić marginesy elementu w obszarze kompozycji

- Aby zmienić marginesy elementu względem jego kontenera układu, kliknij obszar *definiowania układu marginesu* , który pojawia się wokół elementu w obszarze kompozycji, gdy element jest zaznaczony i znajduje się w kontenerze układu. Ilustracja przedstawiająca moduł definiowania układu marginesów zawiera temat [Tworzenie interfejsu użytkownika przy użyciu Projektant XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

     Jeśli moduł definiowania układu marginesu jest otwarty, pionowo lub poziomo, margines nie jest ustawiony. Jeśli moduł definiowania układu marginesu jest zamknięty, ten margines jest ustawiany.

     Gdy otworzysz moduł definiowania układu marginesu i odwrotny margines nie jest ustawiony, odwrotny margines jest ustawiany na poprawną wartość zgodnie z lokalizacją elementu w obszarze kompozycji. W przypadku marginesów odwrotnych, takich jak **lewe** i **prawe** marginesy, zawsze jest ustawiana co najmniej jedna właściwość.

    > [!IMPORTANT]
    > Elementy umieszczane w niektórych kontenerach układów, takie jak <xref:Windows.UI.Xaml.Controls.Canvas>, nie mają modułu definiowania układu marginesów. Elementy umieszczane wewnątrz <xref:Windows.UI.Xaml.Controls.StackPanel> zawierają moduł definiowania układu marginesów dla lewego i prawego marginesu lub górnego i dolnego marginesu, w zależności od orientacji `StackPanel`.

## <a name="grouping-and-ungrouping-elements"></a>Grupowanie i rozgrupowywanie elementów
 Zgrupowanie co najmniej dwóch elementów w projektant XAML powoduje utworzenie nowego kontenera układu i umieszczenie tych elementów w tym kontenerze. Umieszczenie dwóch lub większej liczby elementów w kontenerze układu umożliwia łatwe wybieranie, przenoszenie i przekształcanie grupy tak, jakby elementy w tej grupie były jednym elementem. Grupowanie jest również przydatne w przypadku identyfikowania elementów, które są ze sobą powiązane w jakiś sposób, takich jak przyciski tworzące element nawigacji. Po rozdzieleniu elementów, wystarczy usunąć kontener układu, który zawiera elementy.

#### <a name="to-group-elements-into-a-new-layout-container"></a>Aby zgrupować elementy w nowym kontenerze układu

1. Wybierz elementy, które chcesz zgrupować. (Aby zaznaczyć wiele elementów, naciśnij i przytrzymaj klawisz CTRL podczas klikania.)

2. Kliknij prawym przyciskiem myszy wybrane elementy, wskaż polecenie **Grupuj do**, a następnie kliknij typ kontenera układu, w którym ma się znajdować Grupa.

    > [!TIP]
    > W przypadku wybrania opcji <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> lub <xref:Windows.UI.Xaml.Controls.ScrollViewer> w celu grupowania elementów elementy są umieszczane w nowym panelu <xref:Windows.UI.Xaml.Controls.Grid> w <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> lub <xref:Windows.UI.Xaml.Controls.ScrollViewer>. W przypadku rozgrupowania elementów w jednym z tych kontenerów układów zostanie usunięty tylko <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> lub <xref:Windows.UI.Xaml.Controls.ScrollViewer>, a panel <xref:Windows.UI.Xaml.Controls.Grid> pozostanie. Aby usunąć panel `Grid`, Rozgrupuj elementy ponownie.

#### <a name="to-ungroup-elements-and-delete-the-layout"></a>Aby rozgrupować elementy i usunąć układ

- Kliknij prawym przyciskiem myszy grupę, którą chcesz rozgrupować, a następnie kliknij polecenie **Rozgrupuj**.

  Można również grupować lub rozgrupować elementy, klikając prawym przyciskiem myszy wybrane elementy w oknie konspektu dokumentu i klikając pozycję **Grupuj do** lub **Rozgrupuj**.

## <a name="resetting-the-element-layout"></a>Resetowanie układu elementu
 Można przywrócić wartości domyślne dla określonych właściwości układu elementu przy użyciu poleceń resetowania układu. Za pomocą tego polecenia można zresetować margines, wyrównanie, Szerokość, Wysokość i rozmiar elementu, pojedynczo lub zbiorczo.

#### <a name="to-reset-the-element-layout"></a>Aby zresetować układ elementu

- W oknie Konspekt dokumentu lub obszarze kompozycji kliknij element prawym przyciskiem myszy, wybierz polecenie **Układ**, **Zresetuj** *PropertyName*, gdzie *PropertyName* jest właściwością, która ma zostać zresetowana (lub wybierz pozycję **Układ**, **Zresetuj wszystkie** do Zresetuj wszystkie właściwości układu elementu).

## <a name="see-also"></a>Zobacz też
 [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
