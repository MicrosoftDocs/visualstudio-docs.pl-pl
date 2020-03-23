---
title: 'Jak: Używanie zmiennych środowiskowych w kompilacji | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: afc679f9b782b8bc9ed3e04a2b8fb684cdbc1a20
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633788"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Jak: Używanie zmiennych środowiskowych w kompilacji

Podczas tworzenia projektów często konieczne jest ustawienie opcji kompilacji przy użyciu informacji, które nie znajdują się w pliku projektu lub plików, które składają się na projekt. Te informacje są zazwyczaj przechowywane w zmiennych środowiskowych.

## <a name="reference-environment-variables"></a>Referencyjne zmienne środowiskowe

 Wszystkie zmienne środowiskowe są dostępne w pliku projektu Microsoft Build Engine (MSBuild) jako właściwości.

> [!NOTE]
> Jeśli plik projektu zawiera jawną definicję właściwości, która ma taką samą nazwę jak zmienna środowiskowa, właściwość w pliku projektu zastępuje wartość zmiennej środowiskowej.

#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Aby użyć zmiennej środowiskowej w projekcie MSBuild

- Odwołaj się do zmiennej środowiskowej w taki sam sposób, jak zmienna zadeklarowana w pliku projektu. Na przykład następujący kod odwołuje się do BIN_PATH zmiennej środowiskowej:

   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`

  Za pomocą `Condition` atrybutu można podać wartość domyślną właściwości, jeśli zmienna środowiskowa nie została ustawiona.

#### <a name="to-provide-a-default-value-for-a-property"></a>Aby podać wartość domyślną dla właściwości

- Użyj `Condition` atrybutu we właściwości, aby ustawić wartość tylko wtedy, gdy właściwość nie ma wartości. Na przykład następujący kod `ToolsPath` ustawia właściwość na *c:\tools* tylko wtedy, gdy zmienna środowiskowa `ToolsPath` nie jest ustawiona:

     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`

    > [!NOTE]
    > W nazwach właściwości nie `$(ToolsPath)` rozróżniana jest wielkość liter, więc zarówno i `$(TOOLSPATH)` odwołuje się do tej samej właściwości lub zmiennej środowiskowej.

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

- [Msbuild](../msbuild/msbuild.md)
- [Właściwości MSBuild](../msbuild/msbuild-properties.md)
- [Jak: Tworzenie tych samych plików źródłowych z różnymi opcjami](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
