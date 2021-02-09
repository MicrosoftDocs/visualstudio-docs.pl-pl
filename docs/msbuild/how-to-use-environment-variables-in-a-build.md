---
title: 'Instrukcje: użycie zmiennych środowiskowych w kompilacji | Microsoft Docs'
description: Dowiedz się, jak uzyskać dostęp do zmiennych środowiskowych w plikach projektów programu MSBuild, i użyć zmiennych środowiskowych, aby ustawić opcje kompilacji bez modyfikowania pliku projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c7c81f36d37d071593a013067f661451b8916caa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914200"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Instrukcje: użycie zmiennych środowiskowych w kompilacji

Podczas kompilowania projektów często konieczne jest ustawienie opcji kompilacji przy użyciu informacji, które nie są w pliku projektu lub plików wchodzących w skład Twojego projektu. Te informacje są zwykle przechowywane w zmiennych środowiskowych.

## <a name="reference-environment-variables"></a>Zmienne środowiskowe referencyjne

 Wszystkie zmienne środowiskowe są dostępne dla pliku projektu Microsoft Build Engine (MSBuild) jako właściwości.

> [!NOTE]
> Jeśli plik projektu zawiera jawną definicję właściwości, która ma taką samą nazwę jak zmienna środowiskowa, właściwość w pliku projektu zastępuje wartość zmiennej środowiskowej.

#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Aby użyć zmiennej środowiskowej w projekcie MSBuild

- Odwołuje się do zmiennej środowiskowej w taki sam sposób jak zmienna zadeklarowana w pliku projektu. Na przykład poniższy kod odwołuje się do zmiennej środowiskowej BIN_PATH:

   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`

  Można użyć atrybutu, `Condition` Aby podać wartość domyślną właściwości, jeśli zmienna środowiskowa nie została ustawiona.

#### <a name="to-provide-a-default-value-for-a-property"></a>Aby podać wartość domyślną dla właściwości

- Użyj `Condition` atrybutu właściwości, aby ustawić wartość tylko wtedy, gdy właściwość nie ma wartości. Na przykład poniższy kod ustawia `ToolsPath` Właściwość na *c:\Tools* tylko wtedy, gdy `ToolsPath` zmienna środowiskowa nie jest ustawiona:

     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`

    > [!NOTE]
    > W nazwach właściwości nie jest rozróżniana wielkość liter, dlatego `$(ToolsPath)` `$(TOOLSPATH)` należy odwoływać się do tej samej właściwości lub zmiennej środowiskowej.

## <a name="example"></a>Przykład

 Następujący plik projektu używa zmiennych środowiskowych, aby określić lokalizację katalogów.

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

## <a name="see-also"></a>Zobacz też

- [MSBuild](../msbuild/msbuild.md)
- [właściwości programu MSBuild](../msbuild/msbuild-properties.md)
- [Instrukcje: kompilowanie tych samych plików źródłowych przy użyciu różnych opcji](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
