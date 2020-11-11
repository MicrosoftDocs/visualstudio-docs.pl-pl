---
title: Debugowanie — wizualizacje danych
description: Debugowanie jest powszechną i niezbędną częścią programowania. Visual Studio dla komputerów Mac zawiera cały zestaw funkcji, które ułatwiają debugowanie. Ten artykuł przegląda różne wizualizacje danych, które mogą być wyświetlane podczas przeprowadzania inspekcji obiektów w debugerze.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 838762435268ea06c09392475f294dbb22c3038d
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493247"
---
# <a name="data-visualizations"></a>Wizualizacja danych

Visual Studio dla komputerów Mac obejmuje obsługę interfejsu użytkownika dla debugera, umożliwiając wizualizacje wartości zmiennych, pól lub właściwości podczas debugowania. Te Wizualizatory danych pokazują rozszerzoną wersję danych i umożliwiają deweloperom inspekcję znanych struktur, na przykład pokazując Kolor struktury koloru.

Wizualizatory w oknie  **Ustawienia regionalne** debugowania można wyświetlić, klikając ikonę podglądu wyświetlaną po prawej stronie wartości, gdy użytkownik umieści wskaźnik myszy nad wierszem:

![Okno zmiennych lokalnych](media/data-visualizations-image9.png)

Poniższa lista szuka wielu nowych wizualizacji dostępnych podczas debugowania w Visual Studio dla komputerów Mac.

## <a name="point"></a>Moment
Punkt/przedstawiającą punkt, lub CGPoint w systemach iOS i Mac, będzie renderowany jako krotka pokazująca wartości X i Y w oknach debugowania:

![Wizualizacja punktu](media/data-visualizations-image10.png)

## <a name="size"></a>Rozmiar
Wartość Size/SizeF lub CGSize w systemach iOS i Mac będzie renderowana jako prostokąt. Jest on rysowany do skalowania do momentu, aż wymiar osiągnie 250 pikseli, a następnie skaluje prostokąt o największym wymiarze 250 px:

[Wizualizacja rozmiaru](media/data-visualizations-image11.png)

## <a name="rectangle"></a>Prostokąt
Prostokąty/RectangleF lub CGRect w systemach iOS i Mac będą wyświetlać wymiary i źródło. Podobnie jak w przypadku rozmiaru, jest rysowany do skalowania do momentu, aż rozmiar osiągnie poprzedni 250 pikseli:

![Wizualizacja prostokąta](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Środka
Współrzędne są kreślone na mapie, z lokalizacją przypiętą do centrum:

[Wizualizacja współrzędnej](media/data-visualizations-image13.png)

## <a name="color"></a>Color (Kolor)
Spowoduje to wyświetlenie właściwości UIColor, CGColor i Color, przedstawiających Podgląd kolorów, składniki RGBA, wartości jasności i nasycenie oraz wartość szesnastkową koloru:

![Wizualizacja kolorów](media/data-visualizations-image14.png)

## <a name="images"></a>Obrazy

Multimedia będą renderowane do skalowania, maksymalnie do maksymalnego wymiaru 250 pikseli i będą skalowane w celu dopasowania, gdy obraz przekroczy 250 pikseli:

![Wizualizacja obrazu](media/data-visualizations-image15.png)

## <a name="bezier-curves"></a>Krzywe Beziera

Wizualizator wyświetli `NSBezierPath` :

![Wizualizacja krzywej Beziera](media/data-visualizations-image16.png)

## <a name="string"></a>Ciąg

Ciąg krótszy niż 100 znaków jest wyświetlany w całości bez podglądu. Dłuższe ciągi są wyświetlane w pełnej wersji zapoznawczej. Ciągi można edytować, a wizualizator towarzyszy przyciskowi edycji, co pozwala na edytowanie wartości ciągu w podglądzie lub w edytorze wartości ciągów, jak pokazano poniżej:

![Wizualizacja ciągów](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Małe ciągi:
![Wizualizacja małych ciągów](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Ciągi o średniej długości:
![Wizualizacja średniej długooci](media/data-visualizations-image19.png)

### <a name="editor"></a>Edytora

![Wizualizacja edytora](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>IEnumerable

Interfejs IEnumerable wylicza wszystkie wartości; wartości każdego z nich można wyświetlić, klikając przycisk **Pokaż** wartości. Opcja IEnumerable nie będzie wyświetlać wartości dla obiektów, takich jak `Array` , `ArrayList` , `List<>` `Dictionary<,>` ponieważ mają własne Wizualizatory debugera.

![Wizualizacja IEnumerable](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Inne Wizualizatory

Poniżej znajdują się inne typy, które mają również własne Wizualizatory wbudowane:

![Inna Wizualizacja](media/data-visualizations-image23.png)

* **Typy pierwotne**
  * Spowoduje to wyświetlenie nieprzetworzonej wartości typu pierwotnego.
* **Wyliczenie**
  * Spowoduje to wyświetlenie wartości pola bez kwalifikatora typu wyliczeniowego.
* **Spoin**
  * Wyświetlane w formacie (,)
* **Null**
  * Wyświetla wartość "null".
* **Adres URL**
  * Spowoduje to wyświetlenie hiperlinku do kliknięcia.
* **IntPtr**
  * Spowoduje to wyświetlenie szesnastkowej reprezentacji elementu IntPtr.

## <a name="see-also"></a>Zobacz też

- [Sprawdź zmienne w oknach Autostart i lokalne (Visual Studio w systemie Windows)](/visualstudio/debugger/autos-and-locals-windows)
- [Wyświetlanie ciągów w wizualizatorze (Visual Studio w systemie Windows)](/visualstudio/debugger/string-visualizer-dialog-box)