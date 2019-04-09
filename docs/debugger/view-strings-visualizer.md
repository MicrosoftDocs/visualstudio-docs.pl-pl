---
title: Wyświetl parametry w wizualizatorze ciąg | Dokumentacja firmy Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffd19dccb69d3ae05a84ae49a280ff49c14f2809
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59367367"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Wyświetl parametry w wizualizatorze ciągów w programie Visual Studio

Podczas debugowania w programie Visual Studio, można wyświetlić ciągów za pomocą wizualizatora wbudowanych ciągu. Wizualizator ciągu zawiera ciągi, które są zbyt długie okna porady lub debugera danych. Również może pomóc zidentyfikować ciągi źle sformułowane.

Wizualizator ciągu wbudowane zawiera zwykły tekst, XML, HTML i JSON opcji. Możesz również otworzyć wbudowanych wizualizatorów kilku innych typów takich jak [DataSet, DataTable i DataView](../debugger/dataset-visualizer-dialog-box.md) obiektów z **Autos** lub innych oknach debugera.

> [!NOTE]
> Jeśli trzeba sprawdzić XAML lub WPF UI elementów w wizualizatorze, zobacz lub [właściwości sprawdzić XAML podczas debugowania](../debugger/inspect-xaml-properties-while-debugging.md) lub [jak korzystanie z wizualizatora drzewa WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

## <a name="open-a-string-visualizer"></a>Otwórz Wizualizator ciągu

Aby otworzyć Wizualizator ciągu, zostanie wstrzymana podczas debugowania. Umieść kursor nad zmienną, która zawiera zwykły tekst, XML, HTML lub JSON wartość ciągu, a następnie wybierz ikonę lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ikonę Wizualizator").

![Otwórz Wizualizator ciągu](../debugger/media/dbg-tips-string-visualizers.png "Wizualizator ciągu Otwórz")

## <a name="view-string-visualizer-data"></a>Wyświetl dane Wizualizator ciągu

W oknie Wizualizator ciągu **wyrażenie** pole zawiera zmiennej lub wyrażenia są przenosząc kursor myszy nad, i **wartość** pole zawiera wartość ciągu.

Blank **wartość** oznacza, że wybrany visualizer nie może rozpoznać ciągu. Na przykład **Wizualizator XML** pokazuje pusty **wartość** ciąg tekstowy z żadnych znaczników XML lub ciąg JSON.

Aby wyświetlić ciągów, które nie może rozpoznać wybranego wizualizatora, wybierz **Wizualizator tekstu**. **Wizualizator tekstu** zawiera zwykły tekst.

### <a name="view-json-string-data"></a>Wyświetl dane ciągu JSON

Poprawnie sformułowany ciąg JSON wygląda podobnie jak na poniższej ilustracji w wizualizatorze JSON. Ikona błędu (lub pusty w przypadku nierozpoznany) mogą być wyświetlane nieprawidłowo sformatowany kod JSON. Aby zidentyfikować błąd danych JSON, skopiuj i Wklej parametry do narzędzia Zaznaczanie błędów JSON, takich jak [JSLint](https://www.jslint.com/).

![Wizualizator ciągu JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Wizualizator ciągu JSON")

### <a name="view-xml-string-data"></a>Wyświetl dane ciągu XML

Poprawnie sformułowany ciąg XML pojawia się podobnie jak na poniższej ilustracji w wizualizatorze XML. Nieprawidłowo sformułowany kod XML mogą być wyświetlane bez znaczników XML lub pusty Jeśli nierozpoznany.

![Wizualizator ciągu XML](../debugger/media/dbg-string-visualizers-xml.png "Wizualizator ciągu XML")

### <a name="view-html-string-data"></a>Dane ciągu widok HTML

Poprawnie sformułowany ciąg HTML pojawi się tak, jakby renderowane w przeglądarce, jak pokazano na poniższej ilustracji. Źle sformułowane HTML może być wyświetlany jako zwykły tekst.

![Wizualizator ciągu HTML](../debugger/media/dbg-string-visualizers-html.png "Wizualizator ciągu HTML")

## <a name="see-also"></a>Zobacz także

- [Tworzenie niestandardowych wizualizatorów (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Wizualizacje danych w programie Visual Studio dla komputerów Mac](/visualstudio/mac/data-visualizations)