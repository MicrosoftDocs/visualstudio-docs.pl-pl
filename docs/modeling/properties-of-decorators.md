---
title: Właściwości elementów Decorator
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76129141ed293281eeb3179a654f470bcf608bdf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996799"
---
# <a name="properties-of-decorators"></a>Właściwości elementów Decorator
Dekoratory są ikony, tekst lub cudzysłów ostrokątny rozwijania/zwijania, które mogą być wyświetlane na kształtów i łączników na diagramie. W poniższej tabeli przedstawiono właściwości dla trzy rodzaje dekoratora. Niektóre właściwości są wyświetlane tylko dekoratory kształtu lub tylko dekoratory łącznika.

 Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o tym, jak korzystać z tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Rozwiń/Zwiń Dekoratora

|Właściwość|Opis|Domyślny|
|-|-|-|
|Nazwa wyświetlana|Nazwa dekoratora, która będzie wyświetlana w wygenerowanym projektancie.|Rozwiń Zwiń Dekoratora|
|Nazwa|Nazwa dekoratora.|ExpandCollapseDecorator|
|Uwagi|Uwagi informacyjne, które są skojarzone z tego dekoratora.|\<Brak >|
|HorizontalOffset|Przesunięcie w poziomie, względem domyślnej pozycji dekoratora, w calach. (Na tylko kształty.)|0|
|VerticalOffset|Przesunięcie w pionie, względem domyślnej pozycji dekoratora, w calach. (Na tylko kształty.)|0|
|OffsetFromLine|Przesunięcie dekoratora od linii, względem jego bieżącej pozycji (w calach). (W łącznikach jedynie.)|0|
|OffsetFromShape|Przesunięcie dekoratora od kształtu względem jego bieżącej pozycji (w calach). (W łącznikach jedynie.)|0|
|Pozycja|Domyślnej pozycji dekoratora.|SourceTop|

## <a name="icon-decorator"></a>Ikona Dekoratora

|Właściwość|Opis|Domyślny|
|-|-|-|
|DefaultIcon|Ścieżka pliku ikony lub obrazu do wyświetlenia.|\<Brak >|
|Nazwa wyświetlana|Nazwa dekoratora, który ma być wyświetlana w wygenerowanym projektancie.|Ikona Dekoratora|
|Nazwa|Nazwa dekoratora.|IconDecorator|
|Uwagi|Uwagi informacyjne, które są skojarzone z dekoratora.|\<Brak >|
|HorizontalOffset|Przesunięcie w poziomie, względem domyślnej pozycji dekoratora, w calach. (Na tylko kształty.)|0|
|VerticalOffset|Przesunięcie w pionie, względem domyślnej pozycji dekoratora, w calach. (Na tylko kształty.)|0|
|OffsetFromLine|Przesunięcie dekoratora od linii, względem jego bieżącej pozycji (w calach). (W łącznikach jedynie.)|0|
|OffsetFromShape|Przesunięcie dekoratora od kształtu względem jego bieżącej pozycji (w calach). (W łącznikach jedynie.)|0|
|Pozycja|Domyślnej pozycji dekoratora.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Właściwość|Opis|Domyślny|
|-|-|-|
|DefaultText|Domyślny tekst, który ma być wyświetlany.|Etykieta|
|Nazwa wyświetlana|Nazwa dekoratora, który ma być wyświetlana w wygenerowanym projektancie.|Etykieta|
|FontSize|Rozmiar czcionki dla tekstu wyświetlanego w dekoratorze.|8|
|FontStyle|Styl czcionki dla tekstu wyświetlanego w dekoratorze.|Regularne|
|Nazwa|Nazwa dekoratora.|Etykieta|
|Uwagi|Uwagi informacyjne, które są skojarzone z dekoratora.|\<Brak >|
|HorizontalOffset|Przesunięcie w poziomie, względem domyślnej pozycji dekoratora, w calach. (Na tylko kształty.)|0|
|VerticalOffset|Przesunięcie w pionie, względem domyślnej pozycji dekoratora, w calach. (Na tylko kształty.)|0|
|OffsetFromLine|Przesunięcie dekoratora od linii, względem jego bieżącej pozycji (w calach). (W łącznikach jedynie.)|0|
|OffsetFromShape|Przesunięcie dekoratora od kształtu względem jego bieżącej pozycji (w calach). (W łącznikach jedynie.)|0|
|Pozycja|Domyślnej pozycji dekoratora.|TargetBottom|

## <a name="see-also"></a>Zobacz też

- [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)