---
title: Debugowanie — wizualizacje danych
description: Debugowanie jest wspólną i konieczną częścią programowania. Visual Studio dla komputerów Mac zawiera cały zestaw funkcji, aby debugowanie łatwe. W tym artykule omówiono różne wizualizacje danych, które można wyświetlać podczas sprawdzania obiektów w debugerze.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 14696040160dfc33f89b7647fb73b116b41afa16
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "67691733"
---
# <a name="data-visualizations"></a>Wizualizacja danych

Visual Studio dla komputerów Mac zawiera obsługę interfejsu użytkownika dla debugera, umożliwiając wizualizacje wartości zmiennej, pola lub właściwości podczas debugowania. Te wizualizatory danych pokazują rozszerzoną wersję danych i umożliwiają deweloperom sprawdzanie znanych struktur, na przykład pokazując kolor struktury kolorów.

Wizualizatory w konsoli **lokalnej** debugowania mogą być wyświetlane, klikając ikonę podglądu, która pojawia się po prawej stronie wartości, gdy użytkownik najedzie kursorem na wiersz:

![Podkładka lokalna](media/data-visualizations-image9.png)

Na poniższej liście znajduje się wiele nowych wizualizacji dostępnych podczas debugowania w programie Visual Studio dla komputerów Mac.

## <a name="point"></a>Punkt
Point/PointF lub CGPoint w systemach iOS i Mac będą renderowane jako krotka pokazująca wartości X i Y w konsoli debugowania:

![Wizualizacja punktów](media/data-visualizations-image10.png)

## <a name="size"></a>Rozmiar
A Size/SizeF lub CGSize w systemach iOS i Mac będzie renderowany jako prostokąt. Jest rysowany do skalowania, aż wymiar wzrośnie przeszłości 250 px, w którym to momencie będzie skalować prostokąt o największym wymiarze jako 250 px:

[Wizualizacja rozmiaru](media/data-visualizations-image11.png)

## <a name="rectangle"></a>Prostokąt
Prostokąt/RectangleF lub CGRect w systemach iOS i Mac wyświetli wymiary i początek. Podobnie jak rozmiar, jest rysowany na skali, aż wymiar wzrośnie przeszłości 250 px:

![Wizualizacja prostokąta](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Współrzędnych
Współrzędne są kreślone na mapie, a lokalizacja jest przypięta do środka:

[Wizualizacja współrzędnych](media/data-visualizations-image13.png)

## <a name="color"></a>Kolor
Spowoduje to wyświetlenie właściwości UIColor, CGColor i Color, przedstawiające podgląd kolorów, komponenty RGBA, wartości barwy-nasycenia-światłości oraz wartość szesnastkową koloru:

![Wizualizacja kolorów](media/data-visualizations-image14.png)

## <a name="images"></a>Obrazy

Nośnik będzie renderowany do skalowania do maksymalnego wymiaru 250 px i będzie skalowany w taki sposób, aby pasował, gdy obraz przekroczy 250 px:

![Wizualizacja obrazu](media/data-visualizations-image15.png)

## <a name="bezier-curves"></a>Krzywe Beziera

Wizualizator `NSBezierPath`wyświetli:

![Wizualizacja krzywej Beziera](media/data-visualizations-image16.png)

## <a name="string"></a>Ciąg

Ciąg mniej niż 100 znaków jest wyświetlany w całości, bez podglądu. Dłuższe ciągi są wyświetlane w całości w podglądzie. Ciągi są edytowalne, a wizualizatorowi towarzyszy przycisk edycji, umożliwiający edycję wartości ciągu w podglądzie lub w Edytorze wartości ciągu, pokazanym poniżej:

![Wizualizacja ciągów](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Małe struny:
![Wizualizacja małych ciągów](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Struny średniej długości:
![Wizualizacja średniego ciągu](media/data-visualizations-image19.png)

### <a name="editor"></a>Edytor:

![Wizualizacja edytora](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>Ienumerable

IEnumerable wylicza wszystkie wartości; wartości każdego z nich można wyświetlić, klikając przycisk **Pokaż** wartości. Opcja IEnumerable nie będzie wyświetlać `Array`wartości `ArrayList` `List<>`dla `Dictionary<,>` obiektów, takich jak , , ponieważ mają one własne wizualizatory debugera.

![Wizualizacja ienumerable](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Inne wizualizatory

Niektóre inne typy, które mają również własne wizualizatory wbudowane są wymienione poniżej:

![Inna wizualizacja](media/data-visualizations-image23.png)

* **Typy pierwotne**
  * Spowoduje to wyświetlenia nieprzetworzonej wartości typu pierwotnego.
* **Wyliczenie**
  * Spowoduje to wyświetlenie wartości pola bez kwalifikatora typu wyliczenia.
* **Krotki**
  * Wyświetlane w formacie (,)
* **Null**
  * Pokazuje wartość "null".
* **Adres URL**
  * Spowoduje to wyświetlenie klikliwego hiperłącza.
* **Intptr**
  * Spowoduje to wyświetlenie szesnastkowy reprezentacji IntPtr.

## <a name="see-also"></a>Zobacz też

- [Sprawdzanie zmiennych w oknach Autos i locals (Visual Studio w systemie Windows)](/visualstudio/debugger/autos-and-locals-windows)
- [Wyświetlanie ciągów w wizualizatorze (Visual Studio w systemie Windows)](/visualstudio/debugger/string-visualizer-dialog-box)