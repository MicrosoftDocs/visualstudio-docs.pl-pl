---
title: Wizualizator ciągu — okno dialogowe | Microsoft Docs
description: Wyświetlanie ciągów z wbudowanym Wizualizatorem ciągu w trakcie debugowania w programie Visual Studio.
ms.date: 10/10/2018
ms.custom: seoapril2019, SEO-VS-2020
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c33459312cb0c5c4dd4be3bc043956ccb33a6e1
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150278"
---
# <a name="string-visualizer-dialog-box"></a>String Visualizer — okno dialogowe

Podczas debugowania w programie Visual Studio, można wyświetlać ciągi z wbudowanym wizualizatorem ciągu. Wizualizator ciągu przedstawia ciągi, które są za długie dla okna etykietki danych lub debugera. Może również pomóc identyfikować źle sformułowane ciągi.

Wbudowany wizualizator ciągu zawiera opcje zwykłego tekstu, XML, HTML i JSON. Możesz również otwierać wbudowane Wizualizatory dla kilku innych typów, takich jak obiekty [DataSet, DataTable i DataView](../debugger/dataset-visualizer-dialog-box.md) , z okien **Autostart** lub innych debugerów.

> [!NOTE]
> Jeśli musisz sprawdzić elementy interfejsu użytkownika XAML lub WPF w wizualizatorze, zobacz lub [Sprawdź właściwości XAML podczas debugowania](../xaml-tools/inspect-xaml-properties-while-debugging.md) lub [Użyj wizualizatora drzewa WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

Aby otworzyć wizualizator ciągu, należy wstrzymać podczas debugowania. Umieść kursor nad zmienną, która ma wartość ciągu zwykłego tekstu, XML, HTML lub JSON, a następnie wybierz ikonę lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona wizualizatora").

## <a name="uielement-list"></a>Lista elementów UIElement

W polu **wyrażenie** jest wyświetlana zmienna lub wyrażenie, nad którym znajduje się kursor.

W polu **wartość** jest wyświetlana wartość ciągu. **Wartość** pusta oznacza, że wybrany wizualizator nie może rozpoznać ciągu. Na przykład **wizualizator XML** przedstawia pustą **wartość** dla ciągu tekstowego bez tagów XML lub ciąg JSON. Aby wyświetlić ciągi, które nie są rozpoznawane przez wybranego wizualizatora, wybierz zamiast tego **wizualizator tekstu** . **Wizualizator tekstu** wyświetla zwykły tekst.

### <a name="json-string-data"></a>Dane ciągu JSON

Poprawnie sformułowany ciąg JSON wygląda podobnie do poniższej ilustracji w wizualizatorze JSON. Źle sformułowany kod JSON może wyświetlić ikonę błędu (lub pustą, jeśli nie zostanie rozpoznany). Aby zidentyfikować błąd JSON, skopiuj i wklej ciąg w narzędziu Zaznaczanie błędów JSON, takim jak [JSLint](https://www.jslint.com/).

![Wizualizator ciągu JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Wizualizator ciągu JSON")

### <a name="xml-string-data"></a>Dane ciągu XML

Poprawnie sformułowany ciąg XML wygląda podobnie do poniższej ilustracji w wizualizatorze XML. Nieprawidłowo sformułowany kod XML może być wyświetlany bez tagów XML lub pusty, jeśli nie został rozpoznany.

![Wizualizator ciągu XML](../debugger/media/dbg-string-visualizers-xml.png "Wizualizator ciągu XML")

### <a name="html-string-data"></a>Dane ciągu HTML

Poprawnie sformułowany ciąg HTML wygląda tak, jakby był renderowany w przeglądarce, jak pokazano na poniższej ilustracji. Nieprawidłowo sformułowany kod HTML może być wyświetlany jako zwykły tekst.

![Wizualizator ciągu HTML](../debugger/media/dbg-string-visualizers-html.png "Wizualizator ciągu HTML")

## <a name="see-also"></a>Zobacz także

- [Tworzenie wizualizacji niestandardowych (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Wizualizacje danych w Visual Studio dla komputerów Mac](/visualstudio/mac/data-visualizations)