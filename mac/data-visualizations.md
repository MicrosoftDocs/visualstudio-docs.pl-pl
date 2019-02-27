---
title: Debugowanie — wizualizacje danych
description: Debugowanie jest typowe i jest to konieczne, część programowania. Program Visual Studio dla komputerów Mac zawiera cały zestaw funkcji Łatwe debugowanie. W tym artykule patrzy na wizualizacje danych, które mogą być wyświetlane podczas sprawdzania obiektów w debugerze.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 0b9ec63855eff0b69f5523b1905b79d360509e67
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2019
ms.locfileid: "56953450"
---
# <a name="data-visualizations"></a>Wizualizacje danych

Program Visual Studio for Mac obsługuje interfejs użytkownika debugera, dzięki czemu wizualizacje wartości zmiennej, pole lub właściwość podczas debugowania. Wizualizatory te dane pokazują rozszerzoną wersję danych i umożliwić programistom sprawdzianie znanych struktur, na przykład wyświetlanie koloru struktury kolorów.

Wizualizatory podczas debugowania **lokalnego** konsoli można wyświetlić, klikając ikonę (wersja zapoznawcza), która pojawia się po prawej stronie wartości, gdy użytkownik zatrzyma na wiersz:

![Konsola lokalne](media/data-visualizations-image9.png)

Na poniższej liście sprawdza wiele nowych wizualizacji, dostępne podczas debugowania w programie Visual Studio dla komputerów Mac.

## <a name="point"></a>Punkt
Punkt/przedstawiającą lub CGPoint w systemie iOS i Mac, będą renderowane jako krotki zawierające wartości X i Y w konsoli debugowania:

![Punkt wizualizacji](media/data-visualizations-image10.png)

## <a name="size"></a>Rozmiar
Rozmiar/SizeF lub CGSize w systemie iOS i Mac, będą renderowane jako prostokąt. Jej rysowania skalowanie do momentu wymiaru rozwoju ostatnie 250 pikseli, w tym momencie zostanie przeprowadzone skalowanie prostokąt z największych wymiaru jako 250 pikseli:

[Rozmiar wizualizacji](media/data-visualizations-image11.png)

## <a name="rectangle"></a>Prostokąt
Prostokąt/RectangleF lub CGRect w systemie iOS i Mac, zostanie wyświetlona, wymiary i pochodzenia. Podobnie jak rozmiar, jej rysowania do skali, do momentu wymiaru rozwoju ostatnie 250 pikseli:

![Prostokąt wizualizacji](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Współrzędna
Współrzędne wykreślać na mapie, lokalizację przypiętą do Centrum usługi:

[Współrzędna wizualizacji](media/data-visualizations-image13.png)

## <a name="color"></a>Kolor
Spowoduje to wyświetlenie właściwości UIColor CGColor i kolorów przedstawiające Podgląd koloru, składniki RGBA, Hue-nasycenie-jasności i szesnastkowa wartość koloru:

![Kolor wizualizacji](media/data-visualizations-image14.png)

## <a name="images"></a>Obrazy

Będzie renderowany multimediów do skalowania, aby maksymalny rozmiar 250 pikseli i zostaną odpowiednio dopasowane, gdy obrazu przekracza 250 pikseli:

![Obraz wizualizacji](media/data-visualizations-image15.png)

## <a name="bezier-curves"></a>Krzywe Beziera

Wyświetli wizualizatora `NSBezierPath`:

![Wizualizacja krzywą Beziera](media/data-visualizations-image16.png)

## <a name="string"></a>String

Ciąg mniej niż 100 znaków jest wyświetlany w całości, bez wersji zapoznawczej. Dłużej ciągi są wyświetlane w całości w wersji zapoznawczej. Ciągi są edytowalne i wizualizatora towarzyszy przycisk edycji, pozwalając na wartość ciągu można edytować w wersji zapoznawczej albo w ciągu wartości edytorze, pokazano poniżej:

![Ciąg wizualizacji](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Małe ciągów:
![Ciąg małych wizualizacji](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Średnia długość ciągów:
![Średnie ciągu wizualizacji](media/data-visualizations-image19.png)

### <a name="editor"></a>Edytor:

![Edytor wizualizacji](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>Interfejs IEnumerable

Interfejs IEnumerable wylicza wszystkie wartości. wartości każdego z nich można wyświetlić, klikając pozycję **Pokaż** przycisku wartości. Opcja IEnumerable nie będą wyświetlane wartości dla obiektów takich jak `Array`, `ArrayList`, `List<>`, `Dictionary<,>` te są dostępne dla ich własnych wizualizatory debugera.

![Wizualizacja interfejsu IEnumerable](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Inne Wizualizatorów

Poniżej wymieniono niektóre typy, które również mają własne wizualizatorów wbudowany:

![Inne wizualizacje](media/data-visualizations-image23.png)

* **Typy pierwotne**
  * Spowoduje to wyświetlenie nieprzetworzonej wartości typu pierwotnego.
* **Enum**
  * Spowoduje to wyświetlenie wartości pola bez kwalifikatora typu wyliczenia.
* **Krotki**
  * Wyświetlane w formacie ()
* **Null**
  * Pokazuje wartość "null".
* **Adres URL**
  * Spowoduje to wyświetlenie możesz klikać hiperłącza.
* **IntPtr**
  * Spowoduje to wyświetlenie reprezentacji szesnastkowej elementu IntPtr.

## <a name="see-also"></a>Zobacz także

- [Sprawdzanie zmiennych w oknach zmiennych automatycznych i zmiennych lokalnych (Visual Studio Windows)](/visualstudio/debugger/autos-and-locals-windows)
- [Wyświetl parametry w wizualizatorze (Visual Studio Windows)](/visualstudio/debugger/string-visualizer-dialog-box)