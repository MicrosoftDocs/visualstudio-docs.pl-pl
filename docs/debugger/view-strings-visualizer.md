---
title: Wyświetlanie ciągów w wizualizatorze ciągu | Microsoft Docs
description: Użyj wizualizatora ciągów w debugerze programu Visual Studio, aby wyświetlić ciągi tekstowe, XML, HTML i JSON. Można wyświetlać inne typy obiektów, w tym zestawy danych i DataTable.
ms.custom: SEO-VS-2020
ms.date: 04/08/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 287b5e4546d720160c5e73d19cfeaee5bc0c59e1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933066"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Wyświetlanie ciągów w wizualizatorze ciągu w programie Visual Studio

Podczas debugowania w programie Visual Studio, można wyświetlać ciągi z wbudowanym wizualizatorem ciągu. Wizualizator ciągu przedstawia ciągi, które są za długie dla okna etykietki danych lub debugera. Może również pomóc identyfikować źle sformułowane ciągi.

Wbudowany wizualizator ciągu zawiera opcje zwykłego tekstu, XML, HTML i JSON. Możesz również otwierać wbudowane Wizualizatory dla kilku innych typów, takich jak obiekty [DataSet, DataTable i DataView](../debugger/dataset-visualizer-dialog-box.md) , z okien **Autostart** lub innych debugerów.

> [!NOTE]
> Jeśli musisz sprawdzić elementy interfejsu użytkownika XAML lub WPF w wizualizatorze, zobacz lub [Sprawdź właściwości XAML podczas debugowania](../xaml-tools/inspect-xaml-properties-while-debugging.md) lub [Użyj wizualizatora drzewa WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

## <a name="open-a-string-visualizer"></a>Otwórz wizualizator ciągu

Aby otworzyć wizualizator ciągu, należy wstrzymać podczas debugowania. Umieść kursor nad zmienną, która ma wartość ciągu zwykłego tekstu, XML, HTML lub JSON, a następnie wybierz ikonę lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona wizualizatora").

![Otwórz wizualizator ciągu](../debugger/media/dbg-tips-string-visualizers.png "Otwórz wizualizator ciągu")

## <a name="view-string-visualizer-data"></a>Wyświetl dane wizualizatora ciągu

W oknie wizualizator ciągu w polu **wyrażenie** jest wyświetlana zmienna lub wyrażenie, nad którym znajduje się kursor, a w polu **wartość** zostanie wyświetlona wartość ciągu.

**Wartość** pusta oznacza, że wybrany wizualizator nie może rozpoznać ciągu. Na przykład **wizualizator XML** przedstawia pustą **wartość** dla ciągu tekstowego bez tagów XML lub ciąg JSON.

Aby wyświetlić ciągi, które nie są rozpoznawane przez wybranego wizualizatora, wybierz **wizualizator tekstu**. **Wizualizator tekstu** wyświetla zwykły tekst.

### <a name="view-json-string-data"></a>Wyświetl dane ciągu JSON

Poprawnie sformułowany ciąg JSON wygląda podobnie do poniższej ilustracji w wizualizatorze JSON. Źle sformułowany kod JSON może wyświetlić ikonę błędu (lub pustą, jeśli nie zostanie rozpoznany). Aby zidentyfikować błąd JSON, skopiuj i wklej ciąg w narzędziu Zaznaczanie błędów JSON, takim jak [JSLint](https://www.jslint.com/).

![Wizualizator ciągu JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Wizualizator ciągu JSON")

### <a name="view-xml-string-data"></a>Wyświetl dane ciągu XML

Poprawnie sformułowany ciąg XML wygląda podobnie do poniższej ilustracji w wizualizatorze XML. Nieprawidłowo sformułowany kod XML może być wyświetlany bez tagów XML lub pusty, jeśli nie został rozpoznany.

![Wizualizator ciągu XML](../debugger/media/dbg-string-visualizers-xml.png "Wizualizator ciągu XML")

### <a name="view-html-string-data"></a>Wyświetl dane ciągu HTML

Poprawnie sformułowany ciąg HTML wygląda tak, jakby był renderowany w przeglądarce, jak pokazano na poniższej ilustracji. Nieprawidłowo sformułowany kod HTML może być wyświetlany jako zwykły tekst.

![Wizualizator ciągu HTML](../debugger/media/dbg-string-visualizers-html.png "Wizualizator ciągu HTML")

## <a name="see-also"></a>Zobacz też

- [Tworzenie wizualizacji niestandardowych (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Wizualizacje danych w Visual Studio dla komputerów Mac](/visualstudio/mac/data-visualizations)