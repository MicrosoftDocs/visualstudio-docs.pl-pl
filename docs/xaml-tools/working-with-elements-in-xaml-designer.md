---
title: Praca z elementami w projektancie XAML
ms.date: 05/14/2018
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 3f544501a7d8a792af9ddd89c682324a21002c4f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592925"
---
# <a name="work-with-elements-in-xaml-designer"></a>Praca z elementami w projektancie XAML

Możesz dodawać elementy — kontrolki, układy i kształty — do aplikacji w języku XAML, w kodzie lub przy użyciu projektant XAML. W tym temacie opisano sposób pracy z elementami w projektant XAML w programie Visual Studio lub Blend for Visual Studio.

## <a name="add-an-element-to-a-layout"></a>Dodawanie elementu do układu

*Układ* to proces ustalania rozmiarów i pozycjonowania elementów w interfejsie użytkownika. Aby ustawić położenie elementów wizualnych, należy umieścić je w [panelu](xref:Windows.UI.Xaml.Controls.Panel)układu. `Panel` ma właściwość podrzędną, która jest kolekcją typów [FrameworkElement](xref:Windows.UI.Xaml.FrameworkElement) . Możesz użyć różnych `Panel` elementów podrzędnych, takich jak [Kanwa](xref:Windows.UI.Xaml.Controls.Canvas), [StackPanel](xref:Windows.UI.Xaml.Controls.StackPanel)i [Siatka](xref:Windows.UI.Xaml.Controls.Grid), aby służyć jako kontenery układu oraz umieścić i rozmieścić elementy na stronie.

Domyślnie panel `Grid` jest używany jako kontener układu najwyższego poziomu w obrębie strony lub formularza. Możesz dodać panele układu, kontrolki lub inne elementy w układzie strony najwyższego poziomu.

Aby dodać element do układu w projektant XAML, wykonaj jedną z następujących czynności:

- Kliknij dwukrotnie element w **przyborniku** (lub wybierz element w przyborniku, a następnie naciśnij klawisz **Enter**).

- Przeciągnij element z **przybornika** do obszaru kompozycji.

- W **przyborniku**wybierz jeden z narzędzi do rysowania (na przykład [elipsę](xref:Windows.UI.Xaml.Shapes.Ellipse) lub [prostokąt](xref:Windows.UI.Xaml.Shapes.Rectangle)), a następnie narysuj element w aktywnym panelu.

## <a name="change-the-layering-order-of-elements"></a>Zmiana kolejności warstw elementów

Gdy w projektant XAML znajdują się dwa elementy obszaru kompozycji, jeden element pojawi się przed drugim w kolejności warstw. W dolnej części listy elementów w oknie Konspekt dokumentu znajduje się element (z wyjątkiem sytuacji, gdy ustawiona jest właściwość **ZIndex** elementu). Po wstawieniu elementu do strony, formularza lub kontenera układu element jest automatycznie umieszczany przed innymi elementami w aktywnym elemencie kontenera. Aby zmienić kolejność elementów, można użyć poleceń **Order** lub przeciągnąć elementy w drzewie obiektów w oknie konspektu dokumentu.

Aby zmienić kolejność warstw, wykonaj jedną z następujących czynności:

- W oknie **Konspekt dokumentu** przeciągnij elementy w górę lub w dół, aby utworzyć żądaną kolejność warstw.

- Kliknij prawym przyciskiem myszy element w oknie Konspekt dokumentu lub obszar kompozycji, dla którego chcesz zmienić kolejność warstwową, wskaż pozycję **kolejność**, a następnie kliknij jedną z następujących czynności:

  - **Przesuń na wierzch** , aby przenieść element do przodu w kolejności.

  - **Przesuń do przodu** , aby przenieść element do przodu o jeden poziom w kolejności.

  - **Wyślij do tyłu** , aby wysłać element do tyłu o jeden poziom w kolejności.

  - **Przesuń na spód** , aby wysłać element w sposób do tyłu zamówienia.

- Zmień właściwość **ZIndex** w sekcji **layout** w okno właściwości. Dla nakładających się elementów Właściwość **ZIndex** ma pierwszeństwo przed kolejnością elementów wyświetlanych w oknie konspektu dokumentu. Element o wyższej wartości **ZIndex** pojawia się na początku, gdy elementy nakładają się na siebie.

## <a name="change-the-alignment-of-an-element"></a>Zmień wyrównanie elementu

Elementy w obszarze kompozycji można wyrównywać za pomocą poleceń menu lub przeciągając elementy do linii wyrównania.

*Snapline* jest wizualną wizualizacją, która pomaga wyrównać element względem innych elementów w aplikacji.

Aby wyrównać dwa lub więcej elementów za pomocą poleceń menu:

1. Wybierz elementy, które chcesz wyrównać. Możesz wybrać więcej niż jeden element, naciskając i przytrzymując klawisz **Ctrl** podczas zaznaczania elementów.

2. Wybierz jedną z następujących właściwości w obszarze **HorizontalAlignment** w sekcji **layout** w okno właściwości: **Left**, **Center**, **Right**lub **Rozciągaj**.

3. Wybierz jedną z następujących właściwości w obszarze **VerticalAlignment** w sekcji **layout** w okno właściwości: **Top**, **Center**, **Bottom**lub **Rozciągaj**.

Aby wyrównać dwa lub więcej elementów za pomocą linii wyrównania, w projektant XAML, w układ, który zawiera co najmniej dwa elementy, przeciągnij lub Zmień rozmiar jednego z elementów, aby krawędź była wyrównana do innego elementu.

Gdy krawędzie są wyrównane, zostanie wyświetlona *granica wyrównania* wskazująca wyrównanie. Granica wyrównania jest czerwoną linią kreskowaną. Wyrównanie granice są wyświetlane tylko wtedy, gdy **przyciąganie do linii wyrównania** jest włączona. Ilustracja przedstawiająca obszar kompozycji, który pokazuje granicę wyrównania, znajduje się w temacie [Tworzenie interfejsu użytkownika przy użyciu Projektant XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="change-an-elements-margins"></a>Zmień marginesy elementu

Marginesy w projektant XAML określają ilość pustego miejsca wokół elementu w obszarze kompozycji. Na przykład marginesy określają ilość miejsca między zewnętrznymi krawędziami elementu a granicami panelu `Grid`, który zawiera element. Marginesy określają również ilość miejsca między elementami zawartymi w `StackPanel`.

Aby zmienić marginesy elementu w okno Właściwości:

1. Wybierz element, którego marginesy chcesz zmienić.

2. W **obszarze Układ** w okno właściwości Zmień wartość (w pikselach lub jednostkach niezależnych od urządzenia, które są w przybliżeniu 1/96 cala) dla dowolnej właściwości **marginesu** (**górny**, **lewy**, **prawy**lub **dolny**).

W obszarze kompozycji, aby zmienić marginesy elementu względem kontenera układu elementu, kliknij *marginesy* , które pojawiają się wokół elementu, gdy element jest zaznaczony i znajduje się w kontenerze układu. Ilustracja przedstawiająca moduł definiowania układu marginesów zawiera temat [Tworzenie interfejsu użytkownika przy użyciu Projektant XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

Jeśli moduł definiowania układu marginesu jest otwarty, pionowo lub poziomo, margines nie jest ustawiony. Jeśli moduł definiowania układu marginesu jest zamknięty, ten margines jest ustawiany.

Gdy otworzysz moduł definiowania układu marginesu i odwrotny margines nie jest ustawiony, odwrotny margines jest ustawiany na poprawną wartość zgodnie z lokalizacją elementu w obszarze kompozycji. W przypadku marginesów odwrotnych, takich jak **lewe** i **prawe** marginesy, zawsze jest ustawiana co najmniej jedna właściwość.

> [!IMPORTANT]
> Elementy umieszczane w niektórych kontenerach układów, takich jak [Kanwa](xref:Windows.UI.Xaml.Controls.Canvas), nie mają modułu definiowania układu marginesów. Elementy umieszczane wewnątrz elementu [StackPanel](xref:Windows.UI.Xaml.Controls.StackPanel) zawierają moduł definiowania układu marginesów dla lewego i prawego marginesu lub górnego i dolnego marginesu, w zależności od orientacji `StackPanel`.

## <a name="group-and-ungroup-elements"></a>Grupuj i Rozgrupuj elementy

Zgrupowanie co najmniej dwóch elementów w projektant XAML powoduje utworzenie nowego kontenera układu i umieszczenie tych elementów w tym kontenerze. Umieszczenie dwóch lub większej liczby elementów w kontenerze układu umożliwia łatwe wybieranie, przenoszenie i przekształcanie grupy tak, jakby elementy w tej grupie były jednym elementem. Grupowanie jest również przydatne w przypadku identyfikowania elementów, które są ze sobą powiązane w jakiś sposób, takich jak przyciski tworzące element nawigacji. Po rozdzieleniu elementów, wystarczy usunąć kontener układu, który zawiera elementy.

Aby zgrupować elementy w nowym kontenerze układu:

1. Wybierz elementy, które chcesz zgrupować. (Aby zaznaczyć wiele elementów, naciśnij i przytrzymaj klawisz **Ctrl** podczas klikania.)

2. Kliknij prawym przyciskiem myszy wybrane elementy, wskaż polecenie **Grupuj do**, a następnie kliknij typ kontenera układu, w którym ma się znajdować Grupa.

    > [!TIP]
    > W przypadku wybrania opcji [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [Border](xref:Windows.UI.Xaml.Controls.Border)lub [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer) w celu grupowania elementów elementy są umieszczane w nowym panelu [siatki](xref:Windows.UI.Xaml.Controls.Grid) w obrębie [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [Border](xref:Windows.UI.Xaml.Controls.Border)lub [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer). Jeśli rozgrupujesz elementy w jednym z tych kontenerów układu, zostanie usunięty tylko [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [Border](xref:Windows.UI.Xaml.Controls.Border)lub [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer) , a panel [Siatka](xref:Windows.UI.Xaml.Controls.Grid) pozostanie. Aby usunąć panel `Grid`, Rozgrupuj elementy ponownie.

Aby rozgrupować elementy i usunąć układ, kliknij prawym przyciskiem myszy grupę, którą chcesz rozgrupować, a następnie kliknij pozycję **Rozgrupuj**. Można również grupować lub rozgrupować elementy, klikając prawym przyciskiem myszy wybrane elementy w oknie konspektu dokumentu i klikając pozycję **Grupuj do** lub **Rozgrupuj**.

## <a name="reset-the-element-layout"></a>Zresetuj układ elementu

Można przywrócić wartości domyślne dla określonych właściwości układu elementu przy użyciu poleceń resetowania układu. Za pomocą tego polecenia można zresetować margines, wyrównanie, Szerokość, Wysokość i rozmiar elementu, pojedynczo lub zbiorczo.

Aby zresetować układ elementu, kliknij prawym przyciskiem myszy element w oknie konspektu dokumentu lub obszarze kompozycji, a następnie wybierz polecenie **układ** > **Zresetuj** *PropertyName*, gdzie *PropertyName* jest właściwością, którą chcesz zresetować (lub wybierz pozycję **Układ** > **Zresetuj wszystko** , aby zresetować wszystkie właściwości układu elementu).

## <a name="see-also"></a>Zobacz także

- [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
