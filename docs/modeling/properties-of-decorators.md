---
title: Właściwości elementów Decorator
description: Dowiedz się, że dekoratory to ikony, tekst lub Rozwijanie/zwijanie pagons, które mogą być wyświetlane na kształtach lub łącznikach na diagramie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e29dcda43fdbb7b60567ff0aa0627b41ca3ca299
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873791"
---
# <a name="properties-of-decorators"></a>Właściwości elementów Decorator
Dekoratory to ikony, tekst lub Rozwijanie/zwijanie pagons, które mogą być wyświetlane na kształtach lub łącznikach na diagramie. W poniższych tabelach przedstawiono właściwości trzech rodzajów dekoratora. Niektóre właściwości są wyświetlane tylko na dekoratory kształtu lub tylko w łączniku dekoratory.

 Aby uzyskać więcej informacji, zobacz [How to define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat sposobu korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Rozwiń/Zwiń Dekoratora

|Właściwość|Opis|Domyślne|
|-|-|-|
|Nazwa wyświetlana|Nazwa dekoratora, która będzie wyświetlana w wygenerowanym projektancie.|Rozwiń pozycję Zwiń Dekoratora|
|Nazwa|Nazwa dekoratora.|ExpandCollapseDecorator|
|Uwagi|Nieformalne uwagi, które są skojarzone z tym dekoratoraem.|\<none>|
|HorizontalOffset|Przesunięcie w poziomie względem domyślnej pozycji dekoratora, w calach. (Tylko w przypadku kształtów).|0|
|VerticalOffset|Przesunięcie w pionie względem domyślnej pozycji dekoratora, w calach. (Tylko w przypadku kształtów).|0|
|OffsetFromLine|Przesunięcie dekoratora od linii względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników)|0|
|OffsetFromShape|Przesunięcie dekoratora od kształtu względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników)|0|
|Położenie|Domyślna pozycja dekoratora.|SourceTop|

## <a name="icon-decorator"></a>Ikona Dekoratora

|Właściwość|Opis|Domyślne|
|-|-|-|
|DefaultIcon|Ścieżka pliku ikony lub obrazu, który ma być wyświetlany.|\<none>|
|Nazwa wyświetlana|Nazwa dekoratora, która ma być wyświetlana w wygenerowanym projektancie.|Ikona Dekoratora|
|Nazwa|Nazwa dekoratora.|IconDecorator|
|Uwagi|Nieformalne uwagi, które są skojarzone z dekoratora.|\<none>|
|HorizontalOffset|Przesunięcie w poziomie względem domyślnej pozycji dekoratora, w calach. (Tylko w przypadku kształtów).|0|
|VerticalOffset|Przesunięcie w pionie względem domyślnej pozycji dekoratora, w calach. (Tylko w przypadku kształtów).|0|
|OffsetFromLine|Przesunięcie dekoratora od linii względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników)|0|
|OffsetFromShape|Przesunięcie dekoratora od kształtu względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników)|0|
|Położenie|Domyślna pozycja dekoratora.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Właściwość|Opis|Domyślne|
|-|-|-|
|DefaultText|Domyślny tekst, który ma być wyświetlany.|Etykieta|
|Nazwa wyświetlana|Nazwa dekoratora, która ma być wyświetlana w wygenerowanym projektancie.|Etykieta|
|FontSize|Rozmiar czcionki dla tekstu wyświetlanego w dekoratora.|8|
|FontStyle|Styl czcionki dla tekstu wyświetlanego w dekoratora.|Zwykły|
|Nazwa|Nazwa dekoratora.|Etykieta|
|Uwagi|Nieformalne uwagi, które są skojarzone z dekoratora.|\<none>|
|HorizontalOffset|Przesunięcie w poziomie względem domyślnej pozycji dekoratora, w calach. (Tylko w przypadku kształtów).|0|
|VerticalOffset|Przesunięcie w pionie względem domyślnej pozycji dekoratora, w calach. (Tylko w przypadku kształtów).|0|
|OffsetFromLine|Przesunięcie dekoratora od linii względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników)|0|
|OffsetFromShape|Przesunięcie dekoratora od kształtu względem jego domyślnej pozycji w calach. (Tylko w przypadku łączników)|0|
|Położenie|Domyślna pozycja dekoratora.|TargetBottom|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownik](/previous-versions/bb126564(v=vs.100))