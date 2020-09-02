---
title: 'Instrukcje: użycie zmiennych środowiskowych w kompilacji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 72d810f998b111aa2ec08a5874498ed8ee23a3be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64793715"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Porady: użycie zmiennych środowiskowych w kompilacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas kompilowania projektów często konieczne jest ustawienie opcji kompilacji przy użyciu informacji, które nie są w pliku projektu lub plików wchodzących w skład Twojego projektu. Te informacje są zwykle przechowywane w zmiennych środowiskowych.  
  
## <a name="referencing-environment-variables"></a>Odwołania do zmiennych środowiskowych  
 Wszystkie zmienne środowiskowe są dostępne dla [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu () jako właściwości.  
  
> [!NOTE]
> Jeśli plik projektu zawiera jawną definicję właściwości, która ma taką samą nazwę jak zmienna środowiskowa, właściwość w pliku projektu zastępuje wartość zmiennej środowiskowej.  
  
#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Aby użyć zmiennej środowiskowej w projekcie MSBuild  
  
- Odwołuje się do zmiennej środowiskowej w taki sam sposób jak zmienna zadeklarowana w pliku projektu. Na przykład poniższy kod odwołuje się do zmiennej środowiskowej BIN_PATH:  
  
   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`  
  
  Można użyć atrybutu, `Condition` Aby podać wartość domyślną właściwości, jeśli zmienna środowiskowa nie została ustawiona.  
  
#### <a name="to-provide-a-default-value-for-a-property"></a>Aby podać wartość domyślną dla właściwości  
  
- Użyj `Condition` atrybutu właściwości, aby ustawić wartość tylko wtedy, gdy właściwość nie ma wartości. Na przykład poniższy kod ustawia `ToolsPath` Właściwość na c:\Tools tylko wtedy, gdy `ToolsPath` zmienna środowiskowa nie jest ustawiona:  
  
     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`  
  
    > [!NOTE]
    > W nazwach właściwości nie jest rozróżniana wielkość liter, dlatego `$(ToolsPath)` `$(TOOLSPATH)` należy odwoływać się do tej samej właściwości lub zmiennej środowiskowej.  
  
## <a name="example"></a>Przykład  
 Następujący plik projektu używa zmiennych środowiskowych, aby określić lokalizację katalogów.  
  
```  
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

[MSBuild](msbuild.md)

[Właściwości programu MSBuild](../msbuild/msbuild-properties1.md)

[Instrukcje: Kompilacja tych samych plików źródłowych przy użyciu różnych opcji](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
