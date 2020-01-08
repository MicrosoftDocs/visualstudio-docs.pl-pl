---
title: 'Instrukcje: korzystanie z tego samego obiektu docelowego w wielu plikach projektu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50a4b756e0f0926e6c0ccd1a68ab44b7bc13e25c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75574061"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Instrukcje: użycie tego samego elementu docelowego w wielu plikach projektu
Jeśli utworzono kilka [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] plików projektu, być może wykryto, że należy użyć tych samych zadań i elementów docelowych w różnych plikach projektu. Zamiast dołączać pełny opis tych zadań lub obiektów docelowych w każdym pliku projektu, można zapisać obiekt docelowy w osobnym pliku projektu, a następnie zaimportować ten projekt do dowolnego innego projektu, który musi używać celu.

## <a name="use-the-import-element"></a>Użyj elementu import
 Element `Import` jest używany do wstawiania jednego pliku projektu do innego pliku projektu. Importowany plik projektu musi być prawidłowym plikiem projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] i zawierać poprawnie sformułowany kod XML. Atrybut `Project` określa ścieżkę do zaimportowanego pliku projektu. Aby uzyskać więcej informacji na temat `Import` elementu, zobacz [Import element (MSBuild)](../msbuild/import-element-msbuild.md).

#### <a name="to-import-a-project"></a>Aby zaimportować projekt

1. Zdefiniuj w pliku projektu importowania wszystkie właściwości i elementy, które są używane jako parametry właściwości i elementów w zaimportowanym projekcie.

2. Użyj elementu `Import`, aby zaimportować projekt. Na przykład:

     `<Import Project="MyCommon.targets"/>`

3. Po elemencie `Import` Zdefiniuj wszystkie właściwości i elementy, które muszą przesłaniać domyślne definicje właściwości i elementów w zaimportowanym projekcie.

## <a name="order-of-evaluation"></a>Kolejność obliczeń
 Gdy [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] osiągnie element `Import`, importowany projekt jest efektywnie wstawiany do projektu importowania w lokalizacji elementu `Import`. W związku z tym lokalizacja elementu `Import` może mieć wpływ na wartości właściwości i elementów. Ważne jest zrozumienie właściwości i elementów ustawionych przez zaimportowany projekt oraz właściwości i elementów używanych przez zaimportowany projekt.

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

 Ponieważ projekt jest importowany po zdefiniowaniu `Name` właściwości w elemencie *MojaApl. proj*, definicja `Name` w elemencie *webcommon. targets* zastępuje definicję w programie *MojaApl. proj*. Jeśli projekt zostanie zaimportowany przed zdefiniowaniem nazwy właściwości, kompilacja wyświetli następujący komunikat:

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Podczas importowania projektów należy stosować następujące podejście:

1. Zdefiniuj w pliku projektu wszystkie właściwości i elementy, które są używane jako parametry właściwości i elementów w zaimportowanym projekcie.

2. Zaimportuj projekt.

3. Zdefiniuj w pliku projektu wszystkie właściwości i elementy, które muszą przesłaniać domyślne definicje właściwości i elementów w zaimportowanym projekcie.

## <a name="example"></a>Przykład
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

## <a name="example"></a>Przykład
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

## <a name="see-also"></a>Zobacz także
- [Import — element (MSBuild)](../msbuild/import-element-msbuild.md)
- [Docelowe elementy](../msbuild/msbuild-targets.md)
