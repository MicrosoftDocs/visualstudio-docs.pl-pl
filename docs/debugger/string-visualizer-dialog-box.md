---
title: Okno dialogowe wizualizatora ciągów | Microsoft Docs
description: Wyświetlaj ciągi za pomocą wbudowanego okna dialogowego wizualizatora ciągów podczas debugowania w Visual Studio.
ms.date: 10/10/2018
ms.custom: contperf-fy21q4
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85092f6a339fdaaa3ddaa56112cc351d8b8e9bdc
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108640855"
---
# <a name="string-visualizer-dialog-box"></a>String Visualizer — okno dialogowe

Podczas debugowania w Visual Studio można wyświetlać ciągi za pomocą wbudowanego wizualizatora ciągów. Wizualizator ciągów pokazuje ciągi, które są zbyt długie dla porady danych lub okna debugera. Może również ułatwić identyfikację źle sformułowanych ciągów.

Wbudowane wizualizatory ciągów obejmują [opcje Text](#text-string-data), [XML,](#xml-string-data) [HTML](#html-string-data)i [JSON.](#json-string-data) Możesz również otwierać wbudowane wizualizatory dla kilku innych typów, takich jak obiekty  [DataSet, DataTable i DataView,](../debugger/dataset-visualizer-dialog-box.md) z automatycznych lub innych okien debugera.

> [!NOTE]
> Jeśli musisz sprawdzić elementy interfejsu użytkownika XAML lub WPF w wizualizatorze, zobacz lub sprawdź właściwości [XAML](../xaml-tools/inspect-xaml-properties-while-debugging.md) podczas debugowania lub Jak używać wizualizatora drzewa [WPF.](../debugger/how-to-use-the-wpf-tree-visualizer.md)

Aby otworzyć wizualizator ciągów, musisz być wstrzymany podczas debugowania. Umieść kursor nad zmienną, która ma zwykły tekst, wartość ciągu XML, HTML lub JSON, a następnie wybierz ikonę lupy ![VisualizerIcon.](../debugger/media/dbg-tips-visualizer-icon.png "Ikona wizualizatora")

## <a name="uielement-list"></a>Lista UIElement

**Pole** wyrażenia zawiera zmienną lub wyrażenie, na których umieszczasz wskaźnik myszy.

**Pole** Wartość zawiera wartość ciągu. Wartość pusta **oznacza,** że wybrany wizualizator nie może rozpoznać ciągu. Na przykład **wizualizator XML** pokazuje pustą **wartość** dla ciągu tekstowego bez tagów XML lub ciągu JSON. Aby wyświetlić ciągi, których wybrany wizualizator nie może rozpoznać, wybierz zamiast tego **wizualizator** tekstu. **Wizualizator tekstu wyświetla** zwykły tekst.

### <a name="text-string-data"></a>Dane ciągu tekstowego

**Wizualizator tekstu wyświetla** zwykły tekst. Jeśli potrzebujesz niestandardowego formatowania dla ciągu C++, utwórz [wizualizację Natvis](../debugger/create-custom-views-of-native-objects.md).

![Wizualizator ciągów tekstowych](../debugger/media/dbg-string-visualizer-text.png "Wizualizator ciągów tekstowych")

### <a name="json-string-data"></a>Dane ciągu JSON

Dobrze uformowany ciąg JSON wygląda podobnie do poniższej ilustracji w wizualizatorze JSON. Źle sformułowany kod JSON może wyświetlać ikonę błędu (lub wartość pustą, jeśli jest nierozpoznana). Aby zidentyfikować błąd JSON, skopiuj i wklej ciąg do narzędzia do linowania JSON, takiego [jak JSLint.](https://www.jslint.com/)

![Wizualizator ciągów JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Wizualizator ciągów JSON")

### <a name="xml-string-data"></a>Dane ciągu XML

Dobrze uformowany ciąg XML jest podobny do poniższej ilustracji w wizualizatorze XML. Źle sformułowany kod XML może być wyświetlany bez tagów XML lub pusty, jeśli jest nierozpoznany.

![Wizualizator ciągów XML](../debugger/media/dbg-string-visualizers-xml.png "Wizualizator ciągów XML")

### <a name="html-string-data"></a>Dane ciągu HTML

Dobrze uformowany ciąg HTML wygląda tak, jakby był renderowany w przeglądarce, jak pokazano na poniższej ilustracji. Źle sformułowany kod HTML może być wyświetlany jako zwykły tekst.

![Wizualizator ciągów HTML](../debugger/media/dbg-string-visualizers-html.png "Wizualizator ciągów HTML")

## <a name="see-also"></a>Zobacz też

- [Tworzenie niestandardowych wizualizatorów (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Wizualizacje danych w Visual Studio dla komputerów Mac](/visualstudio/mac/data-visualizations)