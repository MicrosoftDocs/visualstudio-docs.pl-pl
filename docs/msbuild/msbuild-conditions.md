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
- Exists, MSBuild condition function
- HasTrailingSlash, MSBuild condition function
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fea7763bf1cbce5fac36ce2cd5e54c40e1da989a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289238"
---
# <a name="msbuild-conditions"></a>Warunki MSBuild

Program MSBuild obsługuje określony zestaw warunków, które mogą być stosowane wszędzie tam, gdzie `Condition` atrybut jest dozwolony. W poniższej tabeli opisano te warunki.

|Warunek|Opis|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Zwraca wartość, `true` Jeśli `stringA` jest równa `stringB` .<br /><br /> Przykład:<br /><br /> `Condition="'$(Configuration)'=='DEBUG'"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy. W tym sprawdzaniu nie jest rozróżniana wielkość liter.|
|'`stringA`' != '`stringB`'|Daje w `true` przypadku, gdy `stringA` nie jest równe `stringB` .<br /><br /> Przykład:<br /><br /> `Condition="'$(Configuration)'!='DEBUG'"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy. W tym sprawdzaniu nie jest rozróżniana wielkość liter.|
|\<, >, \<=, >=|Oblicza wartości liczbowe argumentów operacji. Zwraca `true` czy wartość oceny relacyjnej to true. Operandy muszą mieć wartość dziesiętną lub szesnastkową. Liczby szesnastkowe muszą zaczynać się od ciągu "0x". **Uwaga:**  W formacie XML, znaki `<` i `>` muszą być zmienione. Symbol `<` jest reprezentowany jako `&lt;` . Symbol `>` jest reprezentowany jako `&gt;` .|
|Istnieje (' `stringA` ')|Zwraca wartość, `true` Jeśli istnieje plik lub folder o nazwie `stringA` .<br /><br /> Przykład:<br /><br /> `Condition="!Exists('$(Folder)')"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy.|
|HasTrailingSlash (' `stringA` ')|Zwraca wartość `true` , jeśli określony ciąg zawiera znak ukośnika odwrotnego ( \\ ) lub ukośnika (/).<br /><br /> Przykład:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Pojedyncze cudzysłowy nie są wymagane w przypadku prostych ciągów alfanumerycznych lub wartości logicznych. Jednak dla pustych wartości są wymagane pojedyncze cudzysłowy.|
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

## <a name="see-also"></a>Zobacz też

- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md)
- [Przewodnik: Tworzenie pliku projektu MSBuild od podstaw](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
