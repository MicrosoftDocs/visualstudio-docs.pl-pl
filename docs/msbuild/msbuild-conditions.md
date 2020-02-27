---
title: Warunki MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e69e5c8fc7404c0c313774271fd07b6315e5270
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633372"
---
# <a name="msbuild-conditions"></a>Warunki MSBuild

Program MSBuild obsługuje określony zestaw warunków, które mogą być stosowane wszędzie tam, gdzie jest dozwolony atrybut `Condition`. W poniższej tabeli opisano te warunki.

|Warunek|Opis|
|---------------|-----------------|
|"`stringA`" = = "`stringB`"|Oblicza `true`, jeśli `stringA` jest równa `stringB`.<br /><br /> Na przykład:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy.|
|"`stringA`"! = "`stringB`"|Oblicza wartość `true`, jeśli `stringA` nie jest równa `stringB`.<br /><br /> Na przykład:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy.|
|\<, >, \<=, > =|Oblicza wartości liczbowe argumentów operacji. Zwraca `true`, jeśli szacowanie relacyjne ma wartość true. Operandy muszą mieć wartość dziesiętną lub szesnastkową. Liczby szesnastkowe muszą zaczynać się od ciągu "0x". **Uwaga:**  W kodzie XML znaki `<` i `>` muszą być zmienione. Symbol `<` jest reprezentowany jako `&lt;`. Symbol `>` jest reprezentowany jako `&gt;`.|
|Istnieje ("`stringA`")|Oblicza `true`, jeśli istnieje plik lub folder o nazwie `stringA`.<br /><br /> Na przykład:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy.|
|HasTrailingSlash ("`stringA`")|Oblicza `true`, jeśli określony ciąg zawiera znak ukośnika odwrotnego (\\) lub ukośnika (/).<br /><br /> Na przykład:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy.|
|!|Oblicza `true`, jeśli operand zostanie obliczony na `false`.|
|And|Oblicza `true`, jeśli oba operandy są szacowane do `true`.|
|Lub|Oblicza `true`, jeśli co najmniej jeden z operandów zwróci `true`.|
|()|Mechanizm grupowania, który jest obliczany do `true`, jeśli wyrażenia zawarte w obliczaniu do `true`.|
|$if $ (% Expression%), $else $, $endif $|Sprawdza, czy określony `%expression%` jest zgodny z wartością ciągu podanego parametru szablonu niestandardowego. Jeśli warunek `$if$` zostanie oszacowany na `true`, jego instrukcje są uruchamiane; w przeciwnym razie warunek `$else$` jest zaznaczone. Jeśli warunek `$else$` jest `true`, jego instrukcje są uruchamiane; w przeciwnym razie warunek `$endif$` spowoduje zakończenie obliczania wyrażenia.<br /><br /> Przykłady użycia można znaleźć w temacie [logika parametrów projektu/elementu programu Visual Studio](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

## <a name="see-also"></a>Zobacz też

- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md)
- [Przewodnik: Tworzenie pliku projektu MSBuild od podstaw](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
