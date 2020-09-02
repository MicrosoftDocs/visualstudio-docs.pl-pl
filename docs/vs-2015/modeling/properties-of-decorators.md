---
title: Właściwości dekoratory | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb837c9b3d465d229f64fac08dac02af8d50f5fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652019"
---
# <a name="properties-of-decorators"></a>Właściwości elementów Decorator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dekoratory to ikony, tekst lub Rozwijanie/zwijanie pagons, które mogą być wyświetlane na kształtach lub łącznikach na diagramie. W poniższych tabelach przedstawiono właściwości trzech rodzajów dekoratora. Niektóre właściwości są wyświetlane tylko na dekoratory kształtu lub tylko w łączniku dekoratory.

 Aby uzyskać więcej informacji, zobacz [jak zdefiniować język specyficzny dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o sposobach korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Rozwiń/Zwiń Dekoratora

|Właściwość|Opis|Domyślne|
|--------------|-----------------|-------------|
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
|--------------|-----------------|-------------|
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
|--------------|-----------------|-------------|
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
 [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
