---
title: Warunki MSBuild | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb0f29224bb87611f010421dd372832f2a014d7e
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59366487"
---
# <a name="msbuild-conditions"></a>Warunki MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] obsługuje określony zbiór warunków, które mogą być stosowane wszędzie tam, gdzie `Condition` atrybut jest dozwolony. W poniższej tabeli opisano te warunki.

|Warunek|Opis|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Daje w wyniku `true` Jeśli `stringA` jest równa `stringB`.<br /><br /> Na przykład:<br /><br /> `Condition="$(CONFIG)=='DEBUG'"`<br /><br /> Apostrofy nie są wymagane dla prostych ciągów znaków alfanumerycznych lub wartościami logicznymi. Jednakże apostrofy są wymagane do wartości puste.|
|'`stringA`' != '`stringB`'|Daje w wyniku `true` Jeśli `stringA` nie jest równa `stringB`.<br /><br /> Na przykład:<br /><br /> `Condition="$(CONFIG)!='DEBUG'"`<br /><br /> Apostrofy nie są wymagane dla prostych ciągów znaków alfanumerycznych lub wartościami logicznymi. Jednakże apostrofy są wymagane do wartości puste.|
|\<, >, \<=, >=|Oblicza wartości liczbowych operandu. Zwraca `true` Jeśli relacyjnych oceny ma wartość true. Argumenty operacji musi być liczbą dziesiętną lub szesnastkową. Liczby szesnastkowe musi zaczynać się od "0 x". **Uwaga:**  W pliku XML, znaki `<` i `>` muszą być poprzedzone znakiem zmiany znaczenia. Symbol `<` jest reprezentowany jako `&lt;`. Symbol `>` jest reprezentowany jako `&gt;`.|
|Istnieje ("`stringA`")|Daje w wyniku `true` Jeśli plik lub folder o nazwie `stringA` istnieje.<br /><br /> Na przykład:<br /><br /> `Condition="!Exists($(builtdir))"`<br /><br /> Apostrofy nie są wymagane dla prostych ciągów znaków alfanumerycznych lub wartościami logicznymi. Jednakże apostrofy są wymagane do wartości puste.|
|HasTrailingSlash ("`stringA`")|Daje w wyniku `true` czy określony ciąg zawiera albo końcowej kreski ułamkowej odwróconej (\\) lub przekazywania znaku ukośnika (/).<br /><br /> Na przykład:<br /><br /> `Condition="!HasTrailingSlash($(OutputPath))"`<br /><br /> Apostrofy nie są wymagane dla prostych ciągów znaków alfanumerycznych lub wartościami logicznymi. Jednakże apostrofy są wymagane do wartości puste.|
|!|Daje w wyniku `true` Jeśli argument daje w wyniku `false`.|
|Oraz|Daje w wyniku `true` Jeśli oba koniunkcję `true`.|
|Lub|Daje w wyniku `true` , gdy co najmniej jeden z operandów jest `true`.|
|()|Grupowanie mechanizm, który daje w wyniku `true` Jeśli zawarte wewnątrz wyrażenia mają `true`.|
|$if$ (% wyrażenie %) $else$, $endif$|Sprawdza, czy określony `%expression%` pasuje do wartości ciągu parametru przekazany szablon niestandardowy. Jeśli `$if$` warunek to `true`, a następnie jego instrukcje są wykonywania; w przeciwnym razie `$else$` warunek jest sprawdzany. Jeśli `$else$` warunek jest `true`, nie można jej instrukcje wykonywania; w przeciwnym razie `$endif$` warunku zakończenia Obliczanie wyrażenia.<br /><br /> Przykłady użycia, zobacz [logiki parametru szablonu projektu/elementu programu Visual Studio](http://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)
- [Konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md)
- [Przewodnik: Tworzenie pliku projektu MSBuild od zera](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
