---
title: Wyświetl parametry w wizualizatorze ciąg | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/11/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2204f10711db96033976cf7b4f7bd3639daf422
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349091"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Wyświetl parametry w wizualizatorze ciągów w programie Visual Studio

Podczas debugowania w programie Visual Studio, można wyświetlić ciągów za pomocą wizualizatora wbudowanych ciągu. Wizualizator ciągu zawiera ciągi, które są zbyt długie okna porady lub debugera danych. Również może pomóc zidentyfikować ciągi źle sformułowane.

Wizualizator ciągu wbudowane zawiera zwykły tekst, XML, HTML i JSON opcji. Można również otworzyć wizualizatorów dla kilku innych typów, takich jak obiekty WPF z **Autos** lub innych oknach debugera.

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