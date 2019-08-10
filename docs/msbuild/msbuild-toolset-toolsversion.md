---
title: Zestaw narzędzi MSBuild (ToolsVersion) | Microsoft Docs
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f87513a8124b728568f78bee9efdf48fb35a5301
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926373"
---
# <a name="msbuild-toolset-toolsversion"></a>Zestaw narzędzi MSBuild (ToolsVersion)

Program MSBuild korzysta z zestawu narzędzi do tworzenia aplikacji, obiektów docelowych i narzędzia. Zazwyczaj zestaw narzędzi programu MSBuild zawiera plik *Microsoft. Common. Tasks* , plik *Microsoft. Common. targets* oraz kompilatory, takie jak *CSC. exe* i *VBC. exe*. Większość zestawów narzędzi może służyć do kompilowania aplikacji do więcej niż jednej wersji .NET Framework i więcej niż jednej platformy systemowej. Jednak zestaw narzędzi MSBuild 2,0 może służyć do określania tylko .NET Framework 2,0.

## <a name="toolsversion-attribute"></a>ToolsVersion — atrybut
::: moniker range=">=vs-2019"
 Określ zestaw narzędzi w `ToolsVersion` atrybucie elementu [projektu](../msbuild/project-element-msbuild.md) w pliku projektu. W poniższym przykładzie określono, że projekt powinien zostać skompilowany przy użyciu zestawu narzędzi MSBuild "Current".

```xml
<Project ToolsVersion="Current" ... </Project>
```

::: moniker-end

::: moniker range="vs-2017"
 Określ zestaw narzędzi w `ToolsVersion` atrybucie elementu [projektu](../msbuild/project-element-msbuild.md) w pliku projektu. Poniższy przykład określa, że projekt powinien zostać skompilowany przy użyciu zestawu narzędzi MSBuild 15,0.

```xml
<Project ToolsVersion="15.0" ... </Project>
```

::: moniker-end

> [!NOTE]
> Niektóre typy projektów używają `sdk` atrybutu `ToolsVersion`zamiast. Aby uzyskać więcej informacji, zobacz [pakiety, metadane i struktury](/dotnet/core/packages) i [Dodatki do formatu csproj dla platformy .NET Core](/dotnet/core/tools/csproj).

## <a name="how-the-toolsversion-attribute-works"></a>Jak działa atrybut ToolsVersion

 Gdy tworzysz projekt w programie Visual Studio lub uaktualniasz istniejący projekt, atrybut o nazwie `ToolsVersion` jest automatycznie dołączany do pliku projektu, a jego wartość odnosi się do wersji programu MSBuild, która jest dołączona do programu Visual Studio Edition. Aby uzyskać więcej informacji, zobacz temat [Omówienie funkcji określania wartości docelowej](../ide/visual-studio-multi-targeting-overview.md).

 `ToolsVersion` Gdy wartość jest zdefiniowana w pliku projektu, MSBuild używa tej wartości do określenia wartości właściwości zestawu narzędzi, które są dostępne dla projektu. Jedna Właściwość zestawu narzędzi `$(MSBuildToolsPath)`to, która określa ścieżkę .NET Framework narzędzi. Wymagana jest tylko ta właściwość zestawu `$(MSBuildBinPath)`narzędzi (lub).

 Począwszy od Visual Studio 2013, wersja zestawu narzędzi MSBuild jest taka sama jak numer wersji programu Visual Studio. Program MSBuild domyślnie ustawia ten zestaw narzędzi w programie Visual Studio i w wierszu polecenia, niezależnie od wersji zestawu narzędzi określonego w pliku projektu.  To zachowanie można zastąpić przy użyciu flagi-ToolsVersion. Aby uzyskać więcej informacji, zobacz [zastąpienie ustawień ToolsVersion](../msbuild/overriding-toolsversion-settings.md).

 W poniższym przykładzie MSBuild znajduje plik *Microsoft. CSharp. targets* przy użyciu `MSBuildToolsPath` zastrzeżonej właściwości.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

 Możesz zmodyfikować wartość `MSBuildToolsPath` przez zdefiniowanie niestandardowego zestawu narzędzi. Aby uzyskać więcej informacji, zobacz [konfiguracje zestawu narzędzi standardowych i niestandardowych](../msbuild/standard-and-custom-toolset-configurations.md).

 Gdy tworzysz rozwiązanie w wierszu polecenia i określisz `ToolsVersion` dla programu *MSBuild. exe*, wszystkie projekty i zależności między projektami są kompilowane według tego `ToolsVersion`, nawet jeśli każdy projekt w rozwiązaniu określa własny `ToolsVersion`. Aby zdefiniować `ToolsVersion` wartość dla poszczególnych projektów, zobacz [przesłanianie ustawień ToolsVersion](../msbuild/overriding-toolsversion-settings.md).

 Ten `ToolsVersion` atrybut jest również używany do migracji projektu. Na przykład po otwarciu projektu programu Visual Studio 2008 w programie Visual Studio 2010 plik projektu zostanie zaktualizowany tak, aby zawierał ToolsVersion = "4.0". Jeśli następnie spróbujesz otworzyć ten projekt w programie Visual Studio 2008, nie rozpoznaje uaktualnionego `ToolsVersion` i dlatego kompiluje projekt, tak jakby atrybut był nadal ustawiony na 3,5.

 Visual Studio 2010 i Visual Studio 2012 używają ToolsVersion 4,0. Visual Studio 2013 używa ToolsVersion 12,0. Program Visual Studio 2015 używa ToolsVersion 14,0, a program Visual Studio 2017 używa ToolsVersion 15,0. W wielu przypadkach można otworzyć projekt w wielu wersjach programu Visual Studio bez modyfikacji. Program Visual Studio zawsze korzysta z poprawnego zestawu narzędzi, ale użytkownik zostanie powiadomiony, jeśli używana wersja nie jest zgodna z wersją w pliku projektu. W prawie wszystkich przypadkach to ostrzeżenie jest niegroźne, ponieważ zestawy narzędzi są zgodne w większości przypadków.

 Podzestawy podrzędne, które są opisane w dalszej części tego tematu, umożliwiają programowi MSBuild automatyczne przełączać zestaw narzędzi do użycia na podstawie kontekstu, w którym jest uruchamiana kompilacja. Na przykład w programie MSBuild jest używany nowszy zestaw narzędzi, które są uruchamiane w programie Visual Studio 2012 niż w przypadku uruchamiania w programie Visual Studio 2010, bez konieczności jawnego zmieniania pliku projektu.

## <a name="toolset-implementation"></a>Implementacja zestawu narzędzi

 Zaimplementuj zestaw narzędzi, wybierając ścieżki różnych elementów, obiektów docelowych i zadań, które tworzą zestaw narzędzi. Narzędzia w zestawie narzędzi, które program MSBuild definiuje, pochodzą z następujących źródeł:

- Folder .NET Framework.

- Dodatkowe narzędzia zarządzane.

  Narzędzia zarządzane obejmują *Resgen. exe* i *Tlbimp. exe*.

Program MSBuild oferuje dwa sposoby dostępu do zestawu narzędzi:

- Przy użyciu właściwości zestawu narzędzi

- Przy użyciu <xref:Microsoft.Build.Utilities.ToolLocationHelper> metod

Właściwości zestawu narzędzi określają ścieżki narzędzia. Począwszy od programu Visual Studio 2017, program MSBuild nie ma już stałej lokalizacji. Domyślnie znajduje się on w folderze *MSBuild\15.0\bin* względem lokalizacji instalacji programu Visual Studio. We wcześniejszych wersjach MSBuild używa wartości `ToolsVersion` atrybutu w pliku projektu, aby zlokalizować odpowiedni klucz rejestru, a następnie używa informacji w kluczu rejestru, aby ustawić właściwości zestawu narzędzi. Na przykład jeśli `ToolsVersion` ma wartość `12.0`, MSBuild ustawia właściwości zestawu narzędzi zgodnie z tym kluczem rejestru: **HKLM\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0**.

 Są to właściwości zestawu narzędzi:

- `MSBuildToolsPath`Określa ścieżkę plików binarnych programu MSBuild.

- `SDK40ToolsPath`Określa ścieżkę dodatkowych narzędzi zarządzanych dla programu MSBuild 4. x (może to być 4,0 lub 4,5).

- `SDK35ToolsPath`Określa ścieżkę dodatkowych narzędzi zarządzanych dla programu MSBuild 3,5.

Alternatywnie można programowo określić zestaw narzędzi, wywołując metody <xref:Microsoft.Build.Utilities.ToolLocationHelper> klasy. Klasa obejmuje następujące metody:

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A>zwraca ścieżkę do folderu .NET Framework.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A>zwraca ścieżkę pliku w folderze .NET Framework.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A>zwraca ścieżkę folderu Managed Tools.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A>zwraca ścieżkę pliku, który zazwyczaj znajduje się w folderze Managed Tools.

- [GetPathToBuildTools](/previous-versions/visualstudio/visual-studio-2013/dn251121(v=vs.121)) zwraca ścieżkę narzędzi do kompilacji.

### <a name="sub-toolsets"></a>Podzestawy narzędzi

 W przypadku wersji programu MSBuild wcześniejszych niż 15,0 program MSBuild używa klucza rejestru w celu określenia ścieżki podstawowych narzędzi. Jeśli klucz ma podklucz, MSBuild używa go do określenia ścieżki podzestawu narzędzi zawierającego dodatkowe narzędzia. W takim przypadku zestaw narzędzi jest definiowany przez połączenie definicji właściwości, które są zdefiniowane w obu kluczach.

> [!NOTE]
> W przypadku kolizji nazw właściwości zestawu narzędzi wartość zdefiniowana dla ścieżki podklucza zastępuje wartość, która jest zdefiniowana dla ścieżki klucza głównego.

 Podzestawy narzędzi stają się aktywne w obecności `VisualStudioVersion` właściwości kompilacja. Ta właściwość może przyjmować jedną z następujących wartości:

- "10,0" określa podzestaw .NET Framework 4

- "11,0" określa podzestaw narzędzi .NET Framework 4,5

- "12,0" określa podzestaw .NET Framework 4.5.1

Podzestawów 10,0 i 11,0 należy używać z ToolsVersion 4,0. W nowszych wersjach wersja zestawu narzędzi sub i ToolsVersion powinna być zgodna.

Podczas kompilacji program MSBuild automatycznie określa i ustawia wartość domyślną dla `VisualStudioVersion` właściwości, jeśli nie została jeszcze zdefiniowana.

Program MSBuild oferuje przeciążenia dla `ToolLocationHelper` metod, które `VisualStudioVersion` dodają wartość wyliczaną jako parametr

Podzestawy narzędzi zostały wprowadzone w .NET Framework 4,5.

## <a name="see-also"></a>Zobacz także

- [Konfiguracje standardowego i niestandardowego zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md)
- [Wielowersyjność kodu](../msbuild/msbuild-multitargeting-overview.md)
