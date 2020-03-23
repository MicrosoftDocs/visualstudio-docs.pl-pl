---
title: Warunki msbuild | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633372"
---
# <a name="msbuild-conditions"></a>Warunki MSBuild

MSBuild obsługuje określony zestaw warunków, które mogą `Condition` być stosowane wszędzie tam, gdzie atrybut jest dozwolony. W poniższej tabeli wyjaśniono te warunki.

|Warunek|Opis|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Ocenia, `true` czy `stringA` jest `stringB`równa .<br /><br /> Przykład:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane dla prostych ciągów alfanumeryczne lub wartości logiczne. Jednak pojedyncze cudzysłowy są wymagane dla pustych wartości.|
|'`stringA`' != '`stringB`'|Ocenia, `true` czy `stringA` nie jest `stringB`równa .<br /><br /> Przykład:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane dla prostych ciągów alfanumeryczne lub wartości logiczne. Jednak pojedyncze cudzysłowy są wymagane dla pustych wartości.|
|\<, >, \<=, >=|Ocenia wartości liczbowe argumentów. Zwraca, `true` jeśli ocena relacyjna jest spełniony. Operandy muszą oszacować liczbę dziesiętną lub szesnastkową. Liczby szesnastkowe muszą zaczynać się od "0x". **Uwaga:**  W języku XML `<` `>` znaki i musi być zmienione. Symbol `<` jest reprezentowany `&lt;`jako . Symbol `>` jest reprezentowany `&gt;`jako .|
|Istnieje('`stringA`')|Ocenia, `true` czy istnieje plik lub `stringA` folder o nazwie.<br /><br /> Przykład:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane dla prostych ciągów alfanumeryczne lub wartości logiczne. Jednak pojedyncze cudzysłowy są wymagane dla pustych wartości.|
|HasTrailingSlash('`stringA`')|Ocenia, `true` czy określony ciąg zawiera znak końcowego ukośnika wstecznego (\\) lub ukośnika do przodu (/).<br /><br /> Przykład:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane dla prostych ciągów alfanumeryczne lub wartości logiczne. Jednak pojedyncze cudzysłowy są wymagane dla pustych wartości.|
|!|Ocenia, `true` czy operand ocenia `false`.|
|And|Ocenia, `true` czy oba argumenty oceniają na `true`.|
|Lub|Ocenia, `true` czy co najmniej jeden z argumentów `true`ocenia .|
|()|Mechanizm grupowania, który `true` ocenia, czy wyrażenia `true`zawarte wewnątrz oceniają do .|
|$if$ ( %expression% ), $else$, $endif$|Sprawdza, czy `%expression%` określony odpowiada wartości ciągu przekazanego parametru szablonu niestandardowego. Jeśli `$if$` warunek ocenia `true`, a następnie jego instrukcje są uruchamiane; w przeciwnym `$else$` razie warunek jest sprawdzany. Jeśli `$else$` warunek `true`jest , a następnie jego instrukcje są uruchamiane; w przeciwnym `$endif$` razie warunek kończy ocenę wyrażenia.<br /><br /> Aby zapoznać się z przykładami użycia, zobacz [logika parametru projektu/elementu programu Visual Studio](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

## <a name="see-also"></a>Zobacz też

- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md)
- [Przewodnik: Tworzenie pliku projektu MSBuild od podstaw](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
