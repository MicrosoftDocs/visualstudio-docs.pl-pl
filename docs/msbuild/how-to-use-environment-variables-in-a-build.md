---
title: 'Instrukcje: Użycie zmiennych środowiskowych w kompilacji | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 377b80b27a8e28da86f89f011bb7047b553d894a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56634646"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Instrukcje: Użycie zmiennych środowiskowych w kompilacji
Podczas kompilowania projektów często jest to konieczne, można ustawić opcji kompilacji, korzystając z informacji, który nie znajduje się w pliku projektu lub plików, wchodzące w skład projektu. Te informacje są zwykle przechowywane w zmiennych środowiskowych.

## <a name="reference-environment-variables"></a>Zmienne odwołujące się do środowiska
 Wszystkie zmienne środowiskowe są dostępne dla [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) pliku projektu jako właściwości.

> [!NOTE]
>  Jeśli plik projektu zawiera jawna definicja właściwości, która ma taką samą nazwę jak zmienna środowiskowa, właściwość w pliku projektu zastępuje wartość zmiennej środowiskowej.

#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Aby użyć zmiennej środowiskowej w projekcie programu MSBuild

- Odwoływać się do zmiennej środowiskowej w taki sam sposób, jak Zmienna zadeklarowana w pliku projektu. Na przykład poniższy kod odwołuje się do zmiennej środowiskowej BIN_PATH:

   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`

  Możesz użyć `Condition` atrybutu, aby podać wartość domyślną dla właściwości, jeśli nie ustawiono zmiennej środowiskowej.

#### <a name="to-provide-a-default-value-for-a-property"></a>Aby podać wartość domyślną dla właściwości

-   Użyj `Condition` atrybutu dla właściwości, aby ustawić wartość tylko wtedy, gdy właściwość nie ma wartości. Na przykład, poniższy kod ustawia `ToolsPath` właściwości *c:\tools* tylko wtedy, gdy `ToolsPath` nie ustawiono zmiennej środowiskowej:

     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`

    > [!NOTE]
    >  Nazwy właściwości nie jest rozróżniana wielkość liter więc zarówno `$(ToolsPath)` i `$(TOOLSPATH)` odwoływać się do tej samej zmiennej właściwości lub środowiska.

## <a name="example"></a>Przykład
 Następujący plik projektu używa zmiennych środowiskowych w celu określenia lokalizacji katalogów.

```xml
<Project DefaultTargets="FakeBuild">
    <PropertyGroup>
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">
            C:\Tools
        </ToolsPath>
    </PropertyGroup>
    <Target Name="FakeBuild">
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz także
- [MSBuild ](../msbuild/msbuild.md)
- [Właściwości programu MSBuild](../msbuild/msbuild-properties.md)
- [Instrukcje: Kompilacja tych samych plików źródłowych przy użyciu różnych opcji](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
