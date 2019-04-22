---
title: Okno dialogowe Wizualizator ciągu | Dokumentacja firmy Microsoft
ms.date: 10/10/2018
ms.custom: seoapril2019
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
ms.openlocfilehash: 982db296fd17fb86b4a139e02a9418eeb507cd91
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59366786"
---
# <a name="string-visualizer-dialog-box"></a>String Visualizer — okno dialogowe

Podczas debugowania w programie Visual Studio, można wyświetlić ciągów za pomocą wizualizatora wbudowanych ciągu. Wizualizator ciągu zawiera ciągi, które są zbyt długie okna porady lub debugera danych. Również może pomóc zidentyfikować ciągi źle sformułowane.

Wizualizator ciągu wbudowane zawiera zwykły tekst, XML, HTML i JSON opcji. Możesz również otworzyć wbudowanych wizualizatorów kilku innych typów takich jak [DataSet, DataTable i DataView](../debugger/dataset-visualizer-dialog-box.md) obiektów z **Autos** lub innych oknach debugera.

> [!NOTE]
> Jeśli trzeba sprawdzić XAML lub WPF UI elementów w wizualizatorze, zobacz lub [właściwości sprawdzić XAML podczas debugowania](../debugger/inspect-xaml-properties-while-debugging.md) lub [jak korzystanie z wizualizatora drzewa WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

Aby otworzyć Wizualizator ciągu, zostanie wstrzymana podczas debugowania. Umieść kursor nad zmienną, która zawiera zwykły tekst, XML, HTML lub JSON wartość ciągu, a następnie wybierz ikonę lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ikonę Wizualizator").

## <a name="uielement-list"></a>Lista elementów interfejsu użytkownika

**Wyrażenie** pole zawiera zmiennej lub wyrażenia jest aktywowany.

**Wartość** pole zawiera wartość ciągu. Blank **wartość** oznacza, że wybrany visualizer nie może rozpoznać ciągu. Na przykład **Wizualizator XML** pokazuje pusty **wartość** ciąg tekstowy z żadnych znaczników XML lub ciąg JSON. Aby wyświetlić ciągów, które nie może rozpoznać wybranego wizualizatora, wybierz **Wizualizator tekstu** zamiast tego. **Wizualizator tekstu** zawiera zwykły tekst.

### <a name="json-string-data"></a>Dane ciągu JSON

Poprawnie sformułowany ciąg JSON wygląda podobnie jak na poniższej ilustracji w wizualizatorze JSON. Ikona błędu (lub pusty w przypadku nierozpoznany) mogą być wyświetlane nieprawidłowo sformatowany kod JSON. Aby zidentyfikować błąd danych JSON, skopiuj i Wklej parametry do narzędzia Zaznaczanie błędów JSON, takich jak [JSLint](https://www.jslint.com/).

![Wizualizator ciągu JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Wizualizator ciągu JSON")

### <a name="xml-string-data"></a>Dane ciągu XML

Poprawnie sformułowany ciąg XML pojawia się podobnie jak na poniższej ilustracji w wizualizatorze XML. Nieprawidłowo sformułowany kod XML mogą być wyświetlane bez znaczników XML lub pusty Jeśli nierozpoznany.

![Wizualizator ciągu XML](../debugger/media/dbg-string-visualizers-xml.png "Wizualizator ciągu XML")

### <a name="html-string-data"></a>Dane ciągu HTML

Poprawnie sformułowany ciąg HTML pojawi się tak, jakby renderowane w przeglądarce, jak pokazano na poniższej ilustracji. Źle sformułowane HTML może być wyświetlany jako zwykły tekst.

![Wizualizator ciągu HTML](../debugger/media/dbg-string-visualizers-html.png "Wizualizator ciągu HTML")

## <a name="see-also"></a>Zobacz także

- [Tworzenie niestandardowych wizualizatorów (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Wizualizacje danych w programie Visual Studio dla komputerów Mac](/visualstudio/mac/data-visualizations)