---
title: Właściwości elementów Decorator
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3374c07cac01104354b2ce41abddbeabbec0a373
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566140"
---
# <a name="properties-of-decorators"></a>Właściwości elementów Decorator
Dekoratory to ikony, tekst lub Rozwijanie/zwijanie pagons, które mogą być wyświetlane na kształtach lub łącznikach na diagramie. W poniższych tabelach przedstawiono właściwości trzech rodzajów dekoratora. Niektóre właściwości są wyświetlane tylko na dekoratory kształtu lub tylko w łączniku dekoratory.

 Aby uzyskać więcej informacji, zobacz [jak zdefiniować język specyficzny dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o sposobach korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Rozwiń/Zwiń Dekoratora

|Właściwość|Opis|Domyślny|
|-|-|-|
|DisplayName|Nazwa dekoratora, która będzie wyświetlana w wygenerowanym projektancie.|Rozwiń pozycję Zwiń Dekoratora|
|Nazwa|Nazwa dekoratora.|ExpandCollapseDecorator|
|Uwagi|Nieformalne uwagi, które są skojarzone z tym dekoratoraem.|\<brak >|
|HorizontalOffset|Przesunięcie w poziomie względem domyślnej pozycji dekoratora, w calach. (Tylko w przypadku kształtów).|0|
|VerticalOffset|Przesunięcie w pionie względem domyślnej pozycji dekoratora, w calach. (Tylko w przypadku kształtów).|0|
|OffsetFromLine|Przesunięcie dekoratora od linii względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników)|0|
|OffsetFromShape|Przesunięcie dekoratora od kształtu względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników)|0|
|Pozycja|Domyślna pozycja dekoratora.|SourceTop|

## <a name="icon-decorator"></a>Ikona Dekoratora

|Właściwość|Opis|Domyślny|
|-|-|-|
|DefaultIcon|Ścieżka pliku ikony lub obrazu, który ma być wyświetlany.|\<brak >|
|DisplayName|Nazwa dekoratora, która ma być wyświetlana w wygenerowanym projektancie.|Ikona Dekoratora|
|Nazwa|Nazwa dekoratora.|IconDecorator|
|Uwagi|Nieformalne uwagi, które są skojarzone z dekoratora.|\<brak >|
|HorizontalOffset|Przesunięcie w poziomie względem domyślnej pozycji dekoratora, w calach. (Tylko w przypadku kształtów).|0|
|VerticalOffset|Przesunięcie w pionie względem domyślnej pozycji dekoratora, w calach. (Tylko w przypadku kształtów).|0|
|OffsetFromLine|Przesunięcie dekoratora od linii względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników)|0|
|OffsetFromShape|Przesunięcie dekoratora od kształtu względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników)|0|
|Pozycja|Domyślna pozycja dekoratora.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Właściwość|Opis|Domyślny|
|-|-|-|
|DefaultText|Domyślny tekst, który ma być wyświetlany.|Etykieta|
|DisplayName|Nazwa dekoratora, która ma być wyświetlana w wygenerowanym projektancie.|Etykieta|
|FontSize|Rozmiar czcionki dla tekstu wyświetlanego w dekoratora.|8|
|FontStyle|Styl czcionki dla tekstu wyświetlanego w dekoratora.|Regular|
|Nazwa|Nazwa dekoratora.|Etykieta|
|Uwagi|Nieformalne uwagi, które są skojarzone z dekoratora.|\<brak >|
|HorizontalOffset|Przesunięcie w poziomie względem domyślnej pozycji dekoratora, w calach. (Tylko w przypadku kształtów).|0|
|VerticalOffset|Przesunięcie w pionie względem domyślnej pozycji dekoratora, w calach. (Tylko w przypadku kształtów).|0|
|OffsetFromLine|Przesunięcie dekoratora od linii względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników)|0|
|OffsetFromShape|Przesunięcie dekoratora od kształtu względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników)|0|
|Pozycja|Domyślna pozycja dekoratora.|TargetBottom|

## <a name="see-also"></a>Zobacz także

- [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
