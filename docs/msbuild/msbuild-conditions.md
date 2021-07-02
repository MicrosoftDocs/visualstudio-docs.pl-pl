---
title: MSBuild Warunki | Microsoft Docs
description: Dowiedz się, MSBuild obsługuje określony zestaw warunków, które mogą być stosowane wszędzie tam, gdzie atrybut Warunek jest dozwolony.
ms.custom: SEO-VS-2020
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
- Exists, MSBuild condition function
- HasTrailingSlash, MSBuild condition function
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d72b69b2c80c4e20b5a4dadae18764a138210295
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222711"
---
# <a name="msbuild-conditions"></a>Warunki programu MSBuild

MSBuild obsługuje określony zestaw warunków, które mogą być stosowane wszędzie tam, gdzie `Condition` atrybut jest dozwolony. W poniższej tabeli wyjaśniono te warunki.

|Warunek|Opis|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Oblicza wartość , `true` jeśli wartość jest równa `stringA` `stringB` .<br /><br /> Na przykład:<br /><br /> `Condition="'$(Configuration)'=='DEBUG'"`<br /><br /> A cudzysłowy pojedyncze nie są wymagane w przypadku prostych ciągów alfanumerycznych ani wartości logicznych. Jednak w przypadku pustych wartości wymagane są pojedyncze cudzysłowy. To sprawdzenie nie ma uwzględniania liter.|
|'`stringA`' != '`stringB`'|Oblicza wartość , `true` jeśli wartość nie jest równa `stringA` `stringB` .<br /><br /> Na przykład:<br /><br /> `Condition="'$(Configuration)'!='DEBUG'"`<br /><br /> A cudzysłowy pojedyncze nie są wymagane w przypadku prostych ciągów alfanumerycznych ani wartości logicznych. Jednak w przypadku pustych wartości wymagane są pojedyncze cudzysłowy. To sprawdzenie nie ma uwzględniania liter.|
|\<, >, \<=, >=|Oblicza wartości liczbowe operandów. Zwraca `true` wartość , jeśli ocena relacyjnych ma wartość true. Operandy muszą być obliczane jako liczba dziesiętna lub szesnastkowa albo cztero częściowa wersja kropkowana. Liczby szesnastkowe muszą zaczynać się od "0x". **Uwaga:**  W języku XML znaki `<` i `>` muszą być znakami ucieczki. Symbol `<` jest reprezentowany jako `&lt;` . Symbol `>` jest reprezentowany jako `&gt;` .|
|Exists(' `stringA` ')|Oblicza wartość , `true` jeśli istnieje plik lub folder o nazwie `stringA` .<br /><br /> Na przykład:<br /><br /> `Condition="!Exists('$(Folder)')"`<br /><br /> A cudzysłowy pojedyncze nie są wymagane w przypadku prostych ciągów alfanumerycznych ani wartości logicznych. Jednak w przypadku pustych wartości wymagane są pojedyncze cudzysłowy.|
|HasTrailingSlash(' `stringA` ')|Oblicza wartość , jeśli określony ciąg zawiera ukośnik odwrotny () lub ukośnik `true` \\ (/).<br /><br /> Na przykład:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> A cudzysłowy pojedyncze nie są wymagane w przypadku prostych ciągów alfanumerycznych ani wartości logicznych. Jednak w przypadku pustych wartości wymagane są pojedyncze cudzysłowy.|
|!|Oblicza wartość , `true` jeśli argument operand ma wartość `false` .|
|`And`|Oblicza wartość , `true` jeśli oba operandy mają wartość `true` .|
|`Or`|Oblicza wartość , `true` jeśli co najmniej jeden z operandów ma wartość `true` .|
|()|Mechanizm grupowania, który ocenia wartość , jeśli `true` wyrażenia zawarte w wyrażeń wewnątrz oceniają wartość `true` .|
|$if$ ( %expression% ), $else$, $endif$|Sprawdza, czy `%expression%` określona wartość odpowiada wartości ciągu przekazanego parametru szablonu niestandardowego. Jeśli warunek ma wartość , jego instrukcje są uruchamiane. W przeciwnym razie `$if$` `true` `$else$` warunek jest sprawdzany. Jeśli warunek to , zostaną uruchomione jego instrukcje. W przeciwnym razie `$else$` `true` `$endif$` warunek kończy się oceną wyrażenia.<br /><br /> Aby uzyskać przykłady użycia, zobacz [Visual Studio logiki parametrów szablonu projektu/elementu](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

Metod ciągów można używać w warunkach, jak pokazano w poniższym przykładzie, w którym funkcja [TrimEnd()](/dotnet/api/system.string.trimend) jest używana do porównywania tylko odpowiedniej części ciągu w celu rozróżnienia między platformami docelowymi .NET Framework i .NET Core.

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd(`0123456789`))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

W MSBuild projektu nie ma prawdziwego typu logicznych. Dane logiczne są reprezentowane we właściwościach, które mogą być puste lub ustawione na dowolną wartość. W związku `'$(Prop)' == 'true'` z tym, oznacza "jeśli Prop jest `true` ,", ale oznacza "jeśli Prop jest lub `'$(Prop)' != 'false'` `true` unset lub ustawione na coś innego".

Logika logiczna jest oceniana tylko w kontekście warunków, więc ustawienia właściwości, takie jak , są reprezentowane jako ciąg (po rozwinięciu zmiennej), a nie jako `<Prop2>'$(Prop1)' == 'true'</Prop>` wartości logiczne.  

MSBuild implementuje kilka specjalnych reguł przetwarzania, aby ułatwić pracę z właściwościami ciągów, które są używane jako wartości logiczne. Literały logiczne są akceptowane, więc `Condition="true"` działają `Condition="false"` zgodnie z oczekiwaniami. MSBuild zawiera również specjalne reguły do obsługi operatora negacji logicznych. Tak więc, jeśli wartość jest równa "true", wartość rozwija się do , a wartość jest porównywana z wartością `$(Prop)` `!$(Prop)` `!true` `false` równą , jak można by się było spodziewać.

## <a name="comparing-versions"></a>Porównywanie wersji

Operatory relacyjne , , i obsługują wersje analizowane przez element , dzięki czemu można porównać wersje, które mają cztery części `<` `>` `<=` `>=` <xref:System.Version?displayProperty=fullName> liczbowe. Na przykład `'1.2.3.4' < '1.10.0.0'` to `true` .

> [!CAUTION]
> `System.Version` Porównania mogą dawać zaskakujące wyniki, gdy jedna lub obie wersje nie określają wszystkich czterech części. Na przykład wersja 1.1 jest starsza niż 1.1.0.

MSBuild funkcje [właściwości do porównywania](property-functions.md#msbuild-version-comparison-functions) wersji, które mają inny zestaw reguł zgodny z semantyczną wersją (semver).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md)
- [Przewodnik: Tworzenie pliku projektu MSBuild od zera](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
