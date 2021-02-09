---
title: 'Instrukcje: korzystanie z tego samego obiektu docelowego w wielu plikach projektu | Microsoft Docs'
description: Dowiedz się, jak zapisać obiekt docelowy w pliku projektu programu MSBuild i zaimportować go do dowolnego innego projektu, który musi używać elementu docelowego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5c351b7f676dec678bd4f070a1f8fb9af97c5d28
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914117"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Instrukcje: użycie tego samego elementu docelowego w wielu plikach projektu

Jeśli użytkownik utworzył kilka plików projektu MSBuild, może wykryć, że należy użyć tych samych zadań i elementów docelowych w różnych plikach projektu. Zamiast dołączać pełny opis tych zadań lub obiektów docelowych w każdym pliku projektu, można zapisać obiekt docelowy w osobnym pliku projektu, a następnie zaimportować ten projekt do dowolnego innego projektu, który musi używać celu.

## <a name="use-the-import-element"></a>Użyj elementu import

`Import`Element jest używany do wstawiania jednego pliku projektu do innego pliku projektu. Importowany plik projektu musi być prawidłowym plikiem projektu programu MSBuild i zawierać poprawnie sformułowany kod XML. Ten `Project` atrybut określa ścieżkę do zaimportowanego pliku projektu. Aby uzyskać więcej informacji na temat `Import` elementu, zobacz [import elementu (MSBuild)](../msbuild/import-element-msbuild.md).

#### <a name="to-import-a-project"></a>Aby zaimportować projekt

1. Zdefiniuj w pliku projektu importowania wszystkie właściwości i elementy, które są używane jako parametry właściwości i elementów w zaimportowanym projekcie.

2. Użyj `Import` elementu, aby zaimportować projekt. Na przykład:

     `<Import Project="MyCommon.targets"/>`

3. Po `Import` elemencie Zdefiniuj wszystkie właściwości i elementy, które muszą przesłaniać domyślne definicje właściwości i elementów w zaimportowanym projekcie.

## <a name="order-of-evaluation"></a>Kolejność obliczania

 Gdy MSBuild osiągnie `Import` element, importowany projekt jest efektywnie wstawiany do projektu importowania w lokalizacji `Import` elementu. W związku z tym lokalizacja `Import` elementu może mieć wpływ na wartości właściwości i elementów. Ważne jest zrozumienie właściwości i elementów ustawionych przez zaimportowany projekt oraz właściwości i elementów używanych przez zaimportowany projekt.

 Podczas kompilacji projektu wszystkie właściwości są oceniane jako pierwsze, a następnie elementy. Na przykład poniższy kod XML definiuje zaimportowany plik projektu *. targets*:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyCommon</Name>
    </PropertyGroup>

    <Target Name="Go">
        <Message Text="Name=$(Name)"/>
    </Target>
</Project>
```

 Poniższy kod XML definiuje plik *MojaApl. proj*, który importuje *wspólne elementy. targets*:

```xml
<Project
    DefaultTargets="Go"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyApp</Name>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

 Podczas kompilacji projektu zostanie wyświetlony następujący komunikat:

 `Name="MyCommon"`

 Ponieważ projekt został zaimportowany po `Name` zdefiniowaniu właściwości w *MojaApl. proj*, definicja elementu `Name` *webcommon. targets* zastępuje definicję w programie *MojaApl. proj*. Jeśli projekt zostanie zaimportowany przed zdefiniowaniem nazwy właściwości, kompilacja wyświetli następujący komunikat:

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Podczas importowania projektów należy stosować następujące podejście:

1. Zdefiniuj w pliku projektu wszystkie właściwości i elementy, które są używane jako parametry właściwości i elementów w zaimportowanym projekcie.

2. Zaimportuj projekt.

3. Zdefiniuj w pliku projektu wszystkie właściwości i elementy, które muszą przesłaniać domyślne definicje właściwości i elementów w zaimportowanym projekcie.

## <a name="example-1"></a>Przykład 1

 Poniższy przykład kodu pokazuje plik *webcommon. Target* , który został zaimportowany przez drugi przykład kodu. Plik *. targets* szacuje właściwości z projektu importowania, aby skonfigurować kompilację.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>
        <appname>$(MSBuildProjectName)</appname>
    <PropertyGroup>
    <Target Name="Build">
        <Csc Sources="hello.cs"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe"/>
    </Target>
</Project>
```

## <a name="example-2"></a>Przykład 2

 Poniższy przykład kodu importuje plik *webcommon. targets* .

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor>RETAIL</Flavor>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Import — element (MSBuild)](../msbuild/import-element-msbuild.md)
- [Targets (Obiekty docelowe)](../msbuild/msbuild-targets.md)
