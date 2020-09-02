---
title: Zastępowanie ustawień ToolsVersion | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 468561a627a3ad7eb477328b5afef794c7acf2c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199948"
---
# <a name="overriding-toolsversion-settings"></a>Zastępowanie ustawień ToolsVersion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zestaw narzędzi dla projektów i rozwiązań można zmienić na jeden z trzech sposobów:  
  
1. za pomocą `/ToolsVersion` przełącznika (lub `/tv` , do krótko) podczas kompilowania projektu lub rozwiązania z wiersza polecenia  
  
2. przez ustawienie `ToolsVersion` parametru w zadaniu MSBuild  
  
3. ustawiając `$(ProjectToolsVersion)` Właściwość w projekcie w ramach rozwiązania. Dzięki temu można skompilować projekt w rozwiązaniu przy użyciu wersji zestawu narzędzi, która różni się od innych projektów.  
  
## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Zastąp ustawienia ToolsVersion projektów i rozwiązań w kompilacjach w wierszu polecenia  
 Mimo że projekty programu Visual Studio zwykle kompilują się z ToolsVersion określonym w pliku projektu, można użyć `/ToolsVersion` przełącznika (lub `/tv` ) w wierszu polecenia, aby przesłonić tę wartość i skompilować wszystkie projekty i współzależności między projektami a różnymi zestawami narzędzi. Na przykład:  
  
```  
msbuild.exe someproj.proj /tv:12.0 /p:Configuration=Debug  
```  
  
 W tym przykładzie wszystkie projekty zostały skompilowane przy użyciu ToolsVersion 12,0. (Zobacz sekcję "kolejność pierwszeństwa" w dalszej części tego tematu).  
  
 W przypadku korzystania z `/tv` przełącznika w wierszu polecenia można opcjonalnie użyć `$(ProjectToolsVersion)` właściwości w poszczególnych projektach, aby skompilować je przy użyciu innej wartości ToolsVersion niż pozostałe projekty w rozwiązaniu.  
  
## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>Zastąp ustawienia ToolsVersion przy użyciu parametru ToolsVersion zadania MSBuild  
 Zadanie MSBuild jest podstawowym środkiem dla jednego projektu do kompilacji innego. Aby umożliwić zadanie MSBuild Kompilowanie projektu z innym ToolsVersion niż określony w projekcie, udostępnia opcjonalny parametr zadania o nazwie `ToolsVersion` . Poniższy przykład ilustruje sposób użycia tego parametru:  
  
1. Utwórz plik o nazwie i zawierający `projectA.proj` Poniższy kod:  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go" >   
            <Message Text="projectA.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
  
            <MSBuild Projects="projectB.proj"  
                ToolsVersion="2.0"  
                Targets="go" />  
        </Target>  
    </Project>  
    ```  
  
2. Utwórz inny plik o nazwie `projectB.proj` i zawierający poniższy kod:  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go">  
            <Message Text="projectB.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
        </Target>  
    </Project>  
    ```  
  
3. W wierszu polecenia wprowadź następujące polecenie:  
  
    ```  
    msbuild projectA.proj /t:go /toolsversion:3.5  
    ```  
  
4. Pojawią się następujące dane wyjściowe. W przypadku `projectA` , `/toolsversion:3.5` ustawienie w wierszu polecenia zastępuje `ToolsVersion=12.0` ustawienie w `Project` tagu.  
  
     `ProjectB` jest wywoływana przez zadanie w `projectA` . To zadanie ma `ToolsVersion=2.0` , które zastępuje inne `ToolsVersion` Ustawienia dla `projectB` .  
  
    ```  
    Output:  
      projectA.proj  
      MSBuildToolsVersion: 3.5  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5  
  
      projectB.proj  
      MSBuildToolsVersion: 2.0  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727  
    ```  
  
## <a name="order-of-precedence"></a>Hierarchia ważności  
 Kolejność pierwszeństwa, od najwyższego do najniższego, służąca do określenia `ToolsVersion` :  
  
1. `ToolsVersion`Atrybut zadania programu MSBuild używany do kompilowania projektu, jeśli istnieje.  
  
2. `/toolsversion`Przełącznik (lub `/tv` ), który jest używany w poleceniu msbuild.exe, jeśli istnieje.  
  
3. Jeśli zmienna środowiskowa `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` jest ustawiona, Użyj bieżącej `ToolsVersion` .  
  
4. Jeśli zmienna środowiskowa `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` jest ustawiona, a `ToolsVersion` zdefiniowana w pliku projektu jest nowsza niż bieżąca `ToolsVersion` , Użyj bieżącej `ToolsVersion` .  
  
5. Jeśli zmienna środowiskowa `MSBUILDLEGACYDEFAULTTOOLSVERSION` jest ustawiona, lub jeśli `ToolsVersion` nie jest ustawiona, są używane następujące czynności:  
  
    1. `ToolsVersion`Atrybut elementu [projektu](../msbuild/project-element-msbuild.md) w pliku projektu. Jeśli ten atrybut nie istnieje, zakłada się, że jest to bieżąca wersja.  
  
    2. Domyślna wersja narzędzi w pliku MSBuild.exe.config.  
  
    3. Domyślna wersja narzędzi w rejestrze. Aby uzyskać więcej informacji, zobacz [konfiguracje zestawu narzędzi standardowych i niestandardowych](../msbuild/standard-and-custom-toolset-configurations.md).  
  
6. Jeśli zmienna środowiskowa `MSBUILDLEGACYDEFAULTTOOLSVERSION` nie jest ustawiona, są używane następujące czynności:  
  
    1. Jeśli zmienna środowiskowa `MSBUILDDEFAULTTOOLSVERSION` ma ustawioną wartość `ToolsVersion` , należy ją użyć.  
  
    2. Jeśli `DefaultOverrideToolsVersion` jest ustawiona w MSBuild.exe.config, należy go użyć.  
  
    3. Jeśli `DefaultOverrideToolsVersion` jest ustawiona w rejestrze, należy go użyć.  
  
    4. W przeciwnym razie Użyj bieżącej `ToolsVersion` .  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowersyjności kodu](../msbuild/msbuild-multitargeting-overview.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)   
 [Konfiguracje standardowego i niestandardowego zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md)
