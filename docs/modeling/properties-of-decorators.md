---
title: Właściwości elementów Decorator
description: Dowiedz się, że dekoratory to ikony, tekst lub chevrony rozwijania/zwijania, które mogą pojawiać się na kształtach lub łącznikach na diagramie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f3436bb800142e7c85594f4b05cef6fb45c4489
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390805"
---
# <a name="properties-of-decorators"></a>Właściwości elementów Decorator
Dekoratory to ikony, tekst lub rozwiń/zwiń chevrony, które mogą pojawiać się na kształtach lub łącznikach na diagramie. W poniższych tabelach przedstawiono właściwości trzech rodzajów dekoratora. Niektóre właściwości są wyświetlane tylko dla dekoratorów kształtów lub tylko dla dekoratorów łączników.

 Aby uzyskać więcej informacji, [zobacz How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz Dostosowywanie i [rozszerzanie Domain-Specific języku](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Rozwijanie/zwijanie dekoratora

|Właściwość|Opis|Domyślne|
|-|-|-|
|Nazwa wyświetlana|Nazwa dekoratora, która będzie wyświetlana w wygenerowanym projektancie.|Rozwijanie zwinięcia dekoratora|
|Nazwa|Nazwa dekoratora.|ExpandCollapseDecorator|
|Uwagi|Notatki nieformalne skojarzone z tym dekoratorem.|\<none>|
|Horizontaloffset|Przesunięcie w poziomie względem domyślnej pozycji dekoratora w calach. (Tylko kształty).|0|
|Verticaloffset|Przesunięcie w pionie względem domyślnej pozycji dekoratora w calach. (Tylko kształty).|0|
|OffsetFromLine|Przesunięcie dekoratora od linii względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników).|0|
|OffsetFromShape|Przesunięcie dekoratora od kształtu względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników).|0|
|Położenie|Domyślna pozycja dekoratora.|SourceTop|

## <a name="icon-decorator"></a>Icon Decorator

|Właściwość|Opis|Domyślne|
|-|-|-|
|DefaultIcon|Ścieżka ikony lub pliku obrazu do wyświetlania.|\<none>|
|Nazwa wyświetlana|Nazwa dekoratora do wyświetlania w wygenerowanym projektancie.|Icon Decorator|
|Nazwa|Nazwa dekoratora.|IkonaDecorator|
|Uwagi|Notatki nieformalne skojarzone z dekoratorem.|\<none>|
|Horizontaloffset|Przesunięcie w poziomie względem domyślnej pozycji dekoratora w calach. (Tylko kształty).|0|
|Verticaloffset|Przesunięcie w pionie względem domyślnej pozycji dekoratora w calach. (Tylko kształty).|0|
|OffsetFromLine|Przesunięcie dekoratora od linii względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników).|0|
|OffsetFromShape|Przesunięcie dekoratora od kształtu względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników).|0|
|Położenie|Domyślna pozycja dekoratora.|SourceTop|

## <a name="textdecorator"></a>Textdecorator

|Właściwość|Opis|Domyślne|
|-|-|-|
|DefaultText (Tekst domyślny)|Domyślny tekst do wyświetlania.|Etykieta|
|Nazwa wyświetlana|Nazwa dekoratora do wyświetlania w wygenerowanym projektancie.|Etykieta|
|Fontsize|Rozmiar czcionki tekstu wyświetlanego w dekoratorze.|8|
|Fontstyle|Styl czcionki tekstu wyświetlanego w dekoratorze.|Zwykły|
|Nazwa|Nazwa dekoratora.|Etykieta|
|Uwagi|Notatki nieformalne skojarzone z dekoratorem.|\<none>|
|Horizontaloffset|Przesunięcie w poziomie względem domyślnej pozycji dekoratora w calach. (Tylko kształty).|0|
|Verticaloffset|Przesunięcie w pionie względem domyślnej pozycji dekoratora w calach. (Tylko kształty).|0|
|OffsetFromLine|Przesunięcie dekoratora od linii względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników).|0|
|OffsetFromShape|Przesunięcie dekoratora od kształtu względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników).|0|
|Położenie|Domyślna pozycja dekoratora.|TargetBottom|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownika](/previous-versions/bb126564(v=vs.100))