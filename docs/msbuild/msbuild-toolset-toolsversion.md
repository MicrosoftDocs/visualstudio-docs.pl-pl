---
title: MSBuild Toolset (ToolsVersion) | Dokumenty firmy Microsoft
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6aaa6309e04f5143b70ff233c0b621ab2350b9c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633125"
---
# <a name="msbuild-toolset-toolsversion"></a>Zestaw narzędzi MSBuild (ToolsVersion)

MSBuild używa zestawu narzędzi zadań, obiektów docelowych i narzędzi do tworzenia aplikacji. Zazwyczaj zestaw narzędzi MSBuild Zawiera plik *microsoft.common.tasks,* plik *microsoft.common.targets* i kompilatory, takie jak *csc.exe* i *vbc.exe*. Większość zestawów narzędzi może służyć do kompilowania aplikacji do więcej niż jednej wersji programu .NET Framework i więcej niż jednej platformy systemowej. Jednak zestaw narzędzi MSBuild 2.0 może służyć tylko do kierowania tylko .NET Framework 2.0.

## <a name="toolsversion-attribute"></a>Atrybut ToolsVersion

::: moniker range=">=vs-2019"
 Określ zestaw narzędzi `ToolsVersion` w atrybucie [elementu Projekt](../msbuild/project-element-msbuild.md) w pliku projektu. Poniższy przykład określa, że projekt powinien być zbudowany przy użyciu zestawu narzędzi MSBuild "Current".

```xml
<Project ToolsVersion="Current" ... </Project>
```

::: moniker-end

::: moniker range="vs-2017"
 Określ zestaw narzędzi `ToolsVersion` w atrybucie [elementu Projekt](../msbuild/project-element-msbuild.md) w pliku projektu. Poniższy przykład określa, że projekt powinien być zbudowany przy użyciu zestawu narzędzi MSBuild 15.0.

```xml
<Project ToolsVersion="15.0" ... </Project>
```

::: moniker-end

> [!NOTE]
> Niektóre typy `sdk` projektów używają atrybutu `ToolsVersion`zamiast . Aby uzyskać więcej informacji, zobacz [Pakiety, metadane i struktury](/dotnet/core/packages) oraz [Dodatki do formatu csproj dla .NET Core](/dotnet/core/tools/csproj).

## <a name="how-the-toolsversion-attribute-works"></a>Jak działa atrybut ToolsVersion

 Podczas tworzenia projektu w programie Visual Studio lub uaktualnienia `ToolsVersion` istniejącego projektu, atrybut o nazwie jest automatycznie uwzględniany w pliku projektu, a jego wartość odpowiada wersji programu MSBuild, która jest uwzględniona w wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [omówienie kierowania na ramy](../ide/visual-studio-multi-targeting-overview.md).

 Gdy `ToolsVersion` wartość jest zdefiniowana w pliku projektu, MSBuild używa tej wartości do określenia wartości właściwości zestawu narzędzi, które są dostępne dla projektu. Jedna właściwość `$(MSBuildToolsPath)`zestawu narzędzi jest , która określa ścieżkę narzędzi .NET Framework. Wymagana jest tylko właściwość zestawu toolset (lub). `$(MSBuildBinPath)`

 Począwszy od programu Visual Studio 2013 wersja zestawu narzędzi MSBuild jest taka sama jak numer wersji programu Visual Studio. MSBuild domyślnie ten zestaw narzędzi w programie Visual Studio i w wierszu polecenia, niezależnie od wersji zestawu narzędzi określonej w pliku projektu.  To zachowanie można zastąpić przy użyciu -ToolsVersion flagi. Aby uzyskać więcej informacji, zobacz [Zastępowanie ustawień narzędzi.](../msbuild/overriding-toolsversion-settings.md)

 W poniższym przykładzie MSBuild znajduje plik *Microsoft.CSharp.targets* przy użyciu właściwości zastrzeżonej. `MSBuildToolsPath`

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

 Wartość można zmodyfikować, `MSBuildToolsPath` definiując niestandardowy zestaw narzędzi. Aby uzyskać więcej informacji, zobacz [Standardowe i niestandardowe konfiguracje zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md).

 Podczas tworzenia rozwiązania w wierszu polecenia `ToolsVersion` i określić dla *msbuild.exe*, wszystkie projekty i ich `ToolsVersion`zależności projektu do projektu są budowane zgodnie z tym, nawet jeśli każdy projekt w rozwiązaniu określa swój własny `ToolsVersion`. Aby zdefiniować `ToolsVersion` wartość dla na podstawie projektu, zobacz [Zastępowanie ustawień narzędziaswersja](../msbuild/overriding-toolsversion-settings.md).

 Atrybut `ToolsVersion` jest również używany do migracji projektu. Na przykład po otwarciu projektu programu Visual Studio 2008 w programie Visual Studio 2010, plik projektu jest aktualizowany w celu uwzględnienia ToolsVersion ="4.0". Jeśli następnie spróbujesz otworzyć ten projekt w programie Visual Studio 2008, nie rozpoznaje uaktualniony `ToolsVersion` i w związku z tym tworzy projekt tak, jakby atrybut był nadal ustawiony na 3.5.

 Visual Studio 2010 i Visual Studio 2012 używają ToolsVersion 4.0. Visual Studio 2013 używa ToolsVersion 12.0. Visual Studio 2015 używa ToolsVersion 14.0, a Visual Studio 2017 używa ToolsVersion 15.0. W wielu przypadkach można otworzyć projekt w wielu wersjach programu Visual Studio bez modyfikacji. Visual Studio zawsze używa poprawnego zestawu narzędzi, ale zostaniesz powiadomiony, jeśli używana wersja nie pasuje do wersji w pliku projektu. W prawie wszystkich przypadkach to ostrzeżenie jest łagodne, ponieważ zestawy narzędzi są zgodne w większości przypadków.

 Zestawy narzędzi podrzędnych, które są opisane w dalszej części tego tematu, umożliwiają MSBuild automatycznie przełączać zestaw narzędzi do użycia na podstawie kontekstu, w którym jest uruchamiana kompilacja. Na przykład MSBuild używa nowszego zestawu narzędzi, gdy jest uruchamiany w programie Visual Studio 2012 niż podczas uruchamiania w programie Visual Studio 2010, bez konieczności jawnej zmiany pliku projektu.

## <a name="toolset-implementation"></a>Implementacja zestawu narzędzi

 Zaimplementuj zestaw narzędzi, wybierając ścieżki różnych narzędzi, obiektów docelowych i zadań, które składają się na zestaw narzędzi. Narzędzia w zestawie narzędzi zdefiniowane przez MSBuild pochodzą z następujących źródeł:

- Folder .NET Framework.

- Dodatkowe narzędzia zarządzane.

  Zarządzane narzędzia obejmują *ResGen.exe* i *TlbImp.exe*.

MSBuild udostępnia dwa sposoby dostępu do zestawu narzędzi:

- Za pomocą właściwości zestawu narzędzi

- Za <xref:Microsoft.Build.Utilities.ToolLocationHelper> pomocą metod

Właściwości zestawu narzędzi określają ścieżki narzędzi. Począwszy od programu Visual Studio 2017, MSBuild nie ma już stałej lokalizacji. Domyślnie znajduje się w folderze *MSBuild\15.0\Bin* względem lokalizacji instalacji programu Visual Studio. We wcześniejszych wersjach MSBuild używa `ToolsVersion` wartości atrybutu w pliku projektu, aby zlokalizować odpowiedni klucz rejestru, a następnie używa informacji w kluczu rejestru, aby ustawić właściwości zestawu narzędzi. Na przykład, `ToolsVersion` jeśli `12.0`ma wartość, następnie MSBuild ustawia właściwości zestawu narzędzi zgodnie z tym kluczem rejestru: **HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0**.

 Są to właściwości zestawu narzędzi:

- `MSBuildToolsPath`określa ścieżkę plików binarnych MSBuild.

- `SDK40ToolsPath`określa ścieżkę dodatkowych narzędzi zarządzanych dla MSBuild 4.x (która może być 4.0 lub 4.5).

- `SDK35ToolsPath`określa ścieżkę dodatkowych narzędzi zarządzanych dla MSBuild 3.5.

Alternatywnie można określić Toolset programowo wywołując metody <xref:Microsoft.Build.Utilities.ToolLocationHelper> klasy. Klasa zawiera następujące metody:

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A>zwraca ścieżkę folderu .NET Framework.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A>zwraca ścieżkę pliku w folderze .NET Framework.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A>zwraca ścieżkę folderu narzędzi zarządzanych.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A>zwraca ścieżkę pliku, która zazwyczaj znajduje się w folderze narzędzi zarządzanych.

- [GetPathToBuildTools](/previous-versions/visualstudio/visual-studio-2013/dn251121(v=vs.121)) zwraca ścieżkę narzędzi kompilacji.

### <a name="sub-toolsets"></a>Zestawy narzędzi podrzędnych

 W przypadku wersji MSBuild przed 15.0, MSBuild używa klucza rejestru, aby określić ścieżkę podstawowych narzędzi. Jeśli klucz ma podklucz, MSBuild używa go do określenia ścieżki poddostawki, która zawiera dodatkowe narzędzia. W takim przypadku Zestaw narzędzi jest zdefiniowany przez połączenie definicji właściwości, które są zdefiniowane w obu kluczach.

> [!NOTE]
> Jeśli nazwy właściwości zestawu narzędzi toolset zderzają się, wartość zdefiniowana dla ścieżki podklucza zastępuje wartość zdefiniowaną dla ścieżki klucza głównego.

 Zestawy narzędzi podrzędnych stają się `VisualStudioVersion` aktywne w obecności właściwości kompilacji. Ta właściwość może mieć jedną z następujących wartości:

- "10.0" określa poddomiat .NET Framework 4

- "11.0" określa poddosystem .NET Framework 4.5

- "12.0" określa poddostawę .NET Framework 4.5.1

Zestawy narzędzi podrzędnych 10,0 i 11,0 powinny być używane z ToolsVersion 4.0. W nowszych wersjach poddostosowania i ToolsVersion powinny być zgodne.

Podczas kompilacji MSBuild automatycznie określa i ustawia wartość `VisualStudioVersion` domyślną dla właściwości, jeśli nie jest jeszcze zdefiniowana.

MSBuild zapewnia przeciążenia `ToolLocationHelper` dla metod, które dodają wyliczoną `VisualStudioVersion` wartość jako parametr

Zestawy narzędzi podrzędnych zostały wprowadzone w .NET Framework 4.5.

## <a name="see-also"></a>Zobacz też

- [Standardowe i niestandardowe konfiguracje zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md)
- [Wielotargowe](../msbuild/msbuild-multitargeting-overview.md)
