---
title: 'Jak: Użyj tego samego celu w wielu plikach projektu | Dokumenty firmy Microsoft'
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
ms.openlocfilehash: 1b7b36a829e2e406ecd3f10ba3a2b588c6f7df25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633762"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Jak: Użyj tego samego obiektu docelowego w wielu plikach projektu

Jeśli masz autorem kilku plików projektu MSBuild, być może odkryto, że trzeba użyć tych samych zadań i obiektów docelowych w różnych plikach projektu. Zamiast uwzględniać pełny opis tych zadań lub obiektów docelowych w każdym pliku projektu, można zapisać obiekt docelowy w oddzielnym pliku projektu, a następnie zaimportować ten projekt do dowolnego innego projektu, który musi użyć obiektu docelowego.
## <a name="use-the-import-element"></a>Użyj importu elementu

 Element `Import` jest używany do wstawiania jednego pliku projektu do innego pliku projektu. Importowany plik projektu musi być prawidłowym plikiem projektu MSBuild i zawierać dobrze sformułowany plik XML. Atrybut `Project` określa ścieżkę do importowanego pliku projektu. Aby uzyskać więcej `Import` informacji na temat elementu, zobacz [Importuj element (MSBuild)](../msbuild/import-element-msbuild.md).
Element `Import` jest używany do wstawiania jednego pliku projektu do innego pliku projektu. Importowany plik projektu musi być prawidłowym plikiem projektu MSBuild i zawierać dobrze sformułowany plik XML. Atrybut `Project` określa ścieżkę do importowanego pliku projektu. Aby uzyskać więcej `Import` informacji na temat elementu, zobacz [Importuj element (MSBuild)](../msbuild/import-element-msbuild.md).

#### <a name="to-import-a-project"></a>Aby zaimportować projekt

1. Zdefiniuj w pliku projektu importującego wszystkie właściwości i elementy, które są używane jako parametry właściwości i elementów w importowanym projekcie.

2. Użyj `Import` elementu, aby zaimportować projekt. Przykład:

     `<Import Project="MyCommon.targets"/>`

3. Po `Import` elemencie zdefiniuj wszystkie właściwości i elementy, które muszą zastąpić domyślne definicje właściwości i elementów w importowanym projekcie.

## <a name="order-of-evaluation"></a>Kolejność obliczeń

 Gdy MSBuild osiągnie `Import` element, importowany projekt jest skutecznie wstawiany do `Import` projektu importowania w lokalizacji elementu. W związku z tym `Import` lokalizacja elementu może mieć wpływ na wartości właściwości i elementów. Ważne jest, aby zrozumieć właściwości i elementy, które są ustawiane przez importowany projekt oraz właściwości i elementy, które używa importowanego projektu.

 Podczas tworzenia projektu wszystkie właściwości są oceniane najpierw, a następnie elementy. Na przykład następujący kod XML definiuje importowany plik projektu *MyCommon.targets:*

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

 Następujący kod XML definiuje *plik MyApp.proj*, który importuje *plik MyCommon.targets:*

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

 Podczas tworzenia projektu wyświetlany jest następujący komunikat:

 `Name="MyCommon"`

 Ponieważ projekt jest importowany `Name` po zdefiniowaniu właściwości w *myapp.proj,* definicja `Name` w *MyCommon.targets* zastępuje definicję w *MyApp.proj*. Jeśli projekt jest importowany przed zdefiniowaniem właściwości Name, kompilacja wyświetli następujący komunikat:

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Podczas importowania projektów należy stosować następujące podejście

1. Zdefiniuj w pliku projektu wszystkie właściwości i elementy, które są używane jako parametry właściwości i elementów w importowanym projekcie.

2. Zaimportuj projekt.

3. Zdefiniuj w pliku projektu wszystkie właściwości i elementy, które muszą zastąpić domyślne definicje właściwości i elementów w importowanym projekcie.

## <a name="example"></a>Przykład

 Poniższy przykład kodu pokazuje *plik MyCommon.targets,* który importuje drugi przykład kodu. Plik *.targets* ocenia właściwości z projektu importowania w celu skonfigurowania kompilacji.

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

 Poniższy przykład kodu importuje plik *MyCommon.targets.*

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

- [Importuj element (MSBuild)](../msbuild/import-element-msbuild.md)
- [Cele](../msbuild/msbuild-targets.md)
