---
title: Warunki MSBuild | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild obsługuje określony zestaw warunków, które mogą być stosowane wszędzie tam, gdzie atrybut Condition jest dozwolony.
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
ms.openlocfilehash: a480c539fc178e5ae672427fe32e9fd34728dc79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919163"
---
# <a name="msbuild-conditions"></a>Warunki programu MSBuild

Program MSBuild obsługuje określony zestaw warunków, które mogą być stosowane wszędzie tam, gdzie `Condition` atrybut jest dozwolony. W poniższej tabeli opisano te warunki.

|Warunek|Opis|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Zwraca wartość, `true` Jeśli `stringA` jest równa `stringB` .<br /><br /> Na przykład:<br /><br /> `Condition="'$(Configuration)'=='DEBUG'"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy. W tym sprawdzaniu nie jest rozróżniana wielkość liter.|
|'`stringA`' != '`stringB`'|Daje w `true` przypadku, gdy `stringA` nie jest równe `stringB` .<br /><br /> Na przykład:<br /><br /> `Condition="'$(Configuration)'!='DEBUG'"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy. W tym sprawdzaniu nie jest rozróżniana wielkość liter.|
|\<, >, \<=, >=|Oblicza wartości liczbowe argumentów operacji. Zwraca `true` czy wartość oceny relacyjnej to true. Operandy muszą mieć wartość dziesiętną lub szesnastkową. Liczby szesnastkowe muszą zaczynać się od ciągu "0x". **Uwaga:**  W formacie XML, znaki `<` i `>` muszą być zmienione. Symbol `<` jest reprezentowany jako `&lt;` . Symbol `>` jest reprezentowany jako `&gt;` .|
|Istnieje (' `stringA` ')|Zwraca wartość, `true` Jeśli istnieje plik lub folder o nazwie `stringA` .<br /><br /> Na przykład:<br /><br /> `Condition="!Exists('$(Folder)')"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy.|
|HasTrailingSlash (' `stringA` ')|Zwraca wartość `true` , jeśli określony ciąg zawiera znak ukośnika odwrotnego ( \\ ) lub ukośnika (/).<br /><br /> Na przykład:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy.|
|!|Daje w `true` przypadku, gdy operand zwraca wartość `false` .|
|`And`|Zwraca wartość, `true` Jeśli oba operandy są oceniane do `true` .|
|`Or`|Zwraca wartość, `true` Jeśli co najmniej jeden z operandów ma wartość `true` .|
|()|Mechanizm grupowania, który jest obliczany w `true` wyrażeniach if zawartych w obliczaniu do `true` .|
|$if $ (% Expression%), $else $, $endif $|Sprawdza, czy określony `%expression%` pasuje do wartości ciągu podanego parametru szablonu niestandardowego. Jeśli `$if$` warunek ma wartość `true` , instrukcje są uruchamiane; w przeciwnym razie `$else$` warunek jest zaznaczony. Jeśli `$else$` warunek ma wartość `true` , instrukcje są uruchamiane; w przeciwnym razie warunek spowoduje `$endif$` zakończenie obliczania wyrażenia.<br /><br /> Przykłady użycia można znaleźć w temacie [logika parametrów projektu/elementu programu Visual Studio](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

Można użyć metod String w warunkach, jak pokazano w poniższym przykładzie, w którym funkcja [TrimEnd ()](/dotnet/api/system.string.trimend) służy do porównywania tylko odpowiedniej części ciągu, aby rozróżnić między .NET Framework i platformą docelową platformy .NET Core.

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

W plikach projektu MSBuild nie istnieje prawdziwy typ Boolean. Dane logiczne są reprezentowane we właściwościach, które mogą być puste lub mieć dowolną wartość. W związku z tym `'$(Prop)' == 'true'` oznacza "Jeśli prop jest `true` ,", ale `'$(Prop)' != 'false'` oznacza "Jeśli prop jest lub deduplikowane `true` lub ustawione na coś innego".

Logika logiczna jest obliczana tylko w kontekście warunków, dlatego ustawienia właściwości, takie jak `<Prop2>'$(Prop1)' == 'true'</Prop>` są reprezentowane jako ciąg (po rozszerzeniu zmiennej), nie są oceniane jako wartości logiczne.  

Program MSBuild implementuje kilka specjalnych reguł przetwarzania, aby ułatwić pracę z właściwościami ciągu, które są używane jako wartości logiczne. Literały logiczne są akceptowane, więc `Condition="true"` i `Condition="false"` działają zgodnie z oczekiwaniami. Program MSBuild zawiera również specjalne reguły obsługujące operator negacji logicznej. Tak więc, jeśli `$(Prop)` ma wartość "true", `!$(Prop)` rozwija się do `!true` i porównywane jest równe `false` , zgodnie z oczekiwaniami.

## <a name="see-also"></a>Zobacz też

- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md)
- [Przewodnik: Tworzenie pliku projektu MSBuild od zera](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
