---
title: Ustawienia zastępowania narzędzi | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13c33f0ef43707390aa32d4c26c0380a8a32883e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633021"
---
# <a name="override-toolsversion-settings"></a>Zastępowanie ustawień narzędziaSwersja

Zestaw narzędzi dla projektów i rozwiązań można zmienić na jeden z trzech sposobów:

1. Za pomocą `-ToolsVersion` przełącznika `-tv`(lub , w skrócie) podczas tworzenia projektu lub rozwiązania z wiersza polecenia.

2. Ustawiając `ToolsVersion` parametr w zadaniu MSBuild.

3. Ustawiając `$(ProjectToolsVersion)` właściwość na projekcie w ramach rozwiązania. Dzięki temu można utworzyć projekt w rozwiązaniu z wersją zestawu narzędzi, która różni się od innych projektów.

## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Zastępowanie ustawień ToolsVersion projektów i rozwiązań w kompilacjach wierszy poleceń

 Chociaż projekty programu Visual Studio zazwyczaj kompilacji z ToolsVersion określony `-ToolsVersion` w `-tv`pliku projektu, można użyć (lub ) włączyć wiersz polecenia, aby zastąpić tę wartość i utworzyć wszystkie projekty i ich zależności projektu do projektu z innym zestawem narzędzi. Przykład:

```cmd
msbuild.exe someproj.proj -tv:12.0 -p:Configuration=Debug
```

 W tym przykładzie wszystkie projekty są tworzone przy użyciu ToolsVersion 12.0. (Jednak zobacz sekcję [Kolejność pierwszeństwa](#order-of-precedence) w dalszej części tego tematu.

 Korzystając z `-tv` przełącznika w wierszu polecenia, `$(ProjectToolsVersion)` można opcjonalnie użyć właściwości w poszczególnych projektach, aby utworzyć je z inną wartością ToolsVersion niż inne projekty w rozwiązaniu.

## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>Zastępowanie ustawień ToolsVersion za pomocą parametru ToolsVersion zadania MSBuild

 Zadanie MSBuild jest podstawowym środkiem dla jednego projektu do tworzenia innego. Aby włączyć zadanie MSBuild do tworzenia projektu z inną platformą ToolsVersion niż określona `ToolsVersion`w projekcie, udostępnia on opcjonalny parametr zadania o nazwie . W poniższym przykładzie pokazano, jak używać tego parametru:

1. Utwórz plik o nazwie *projectA.proj* i który zawiera następujący kod:

    ```xml
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

2. Utwórz inny plik o nazwie *projectB.proj* i który zawiera następujący kod:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    ToolsVersion="12.0">

        <Target Name="go">
            <Message Text="projectB.proj" />
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />
        </Target>
    </Project>
    ```

3. Wprowadź następujące polecenie w wierszu polecenia:

    ```cmd
    msbuild projectA.proj -t:go -toolsversion:3.5
    ```

4. Pojawi się następujące dane wyjściowe. Dla `projectA`, `-toolsversion:3.5` ustawienie w wierszu polecenia `ToolsVersion=12.0` zastępuje `Project` ustawienie w tagu.

     `ProjectB`jest wywoływana przez `projectA`zadanie w pliku . To zadanie `ToolsVersion=2.0`ma , który `ToolsVersion` zastępuje `projectB`inne ustawienia dla .

    ```
    Output:
      projectA.proj
      MSBuildToolsVersion: 3.5
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5

      projectB.proj
      MSBuildToolsVersion: 2.0
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727
    ```

## <a name="order-of-precedence"></a>Kolejność pierwszeństwa

 Kolejność pierwszeństwa, od najwyższego do najniższego, `ToolsVersion` używana do określenia jest:

1. Atrybut `ToolsVersion` w zadaniu MSBuild używane do tworzenia projektu, jeśli istnieje.

2. Przełącznik `-toolsversion` (lub), `-tv`który jest używany w msbuild.exe polecenia, jeśli istnieje.

3. Jeśli ustawiona `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` jest zmienna środowiskowa, użyj bieżącego `ToolsVersion`pliku .

4. Jeśli zmienna `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` środowiskowa `ToolsVersion` jest ustawiona, a zdefiniowana `ToolsVersion`w pliku `ToolsVersion`projektu jest większa niż bieżąca, użyj bieżącego .

5. Jeśli zmienna `MSBUILDLEGACYDEFAULTTOOLSVERSION` środowiskowa jest `ToolsVersion` ustawiona lub jeśli nie jest ustawiona, używane są następujące kroki:

    1. Atrybut `ToolsVersion` [Project](../msbuild/project-element-msbuild.md) element pliku projektu. Jeśli ten atrybut nie istnieje, zakłada się, że jest to bieżąca wersja.

    2. Domyślna wersja narzędzi w pliku *MSBuild.exe.config.*

    3. Domyślna wersja narzędzi w rejestrze. Aby uzyskać więcej informacji, zobacz [Standardowe i niestandardowe konfiguracje zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md).

6. Jeśli zmienna `MSBUILDLEGACYDEFAULTTOOLSVERSION` środowiskowa nie jest ustawiona, stosuje się następujące kroki:

    1. Jeśli zmienna `MSBUILDDEFAULTTOOLSVERSION` środowiskowa `ToolsVersion` jest ustawiona na istniejącą, użyj jej.

    2. Jeśli `DefaultOverrideToolsVersion` jest ustawiona w *pliku MSBuild.exe.config,* użyj go.

    3. Jeśli `DefaultOverrideToolsVersion` jest ustawiona w rejestrze, użyj go.

    4. W przeciwnym razie `ToolsVersion`należy użyć bieżącego pliku .

## <a name="see-also"></a>Zobacz też

- [Wielotargowe](../msbuild/msbuild-multitargeting-overview.md)
- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
- [Zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
- [Standardowe i niestandardowe konfiguracje zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md)
