---
title: Zestaw narzędzi MSBuild (ToolsVersion) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 192fdd737816d2239b15530e2d5c03d73f82e0d5
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59657509"
---
# <a name="msbuild-toolset-toolsversion"></a>Zestaw narzędzi MSBuild (ToolsVersion)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program MSBuild używa narzędzi zadania, celów i narzędzi do tworzenia aplikacji. Zazwyczaj zestaw narzędzi MSBuild zawiera plik microsoft.common.tasks, microsoft.common.targets i kompilatory, takie jak csc.exe i vbc.exe. Większość zestawów narzędzi może służyć do kompilowania aplikacji, aby więcej niż jedna wersja programu .NET Framework i więcej niż jedną platformę systemu. Jednak zestaw narzędzi w wersji 2.0 programu MSBuild może służyć do docelowych tylko .NET Framework 2.0.  
  
## <a name="toolsversion-attribute"></a>ToolsVersion — atrybut  
 Określ zestaw narzędzi w `ToolsVersion` atrybutu na [projektu](../msbuild/project-element-msbuild.md) elementu w pliku projektu. W poniższym przykładzie określono, że projekt powinny zostać skompilowane przy użyciu zestawu narzędzi programu MSBuild 12.0.  
  
```  
<Project ToolsVersion="12.0" ... </Project>  
```  
  
## <a name="how-the-toolsversion-attribute-works"></a>Jak działa ten atrybut ToolsVersion  
 Podczas tworzenia projektu w programie Visual Studio lub uaktualnienie istniejącego projektu o nazwie atrybutu `ToolsVersion` zostaną automatycznie włączone w projekcie pliku i jego wartość odnosi się do wersji programu MSBuild, który znajduje się w wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [przeznaczonych dla określonej wersji programu .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 Gdy `ToolsVersion` wartość jest zdefiniowana w pliku projektu, program MSBuild używa tej wartości można określić wartości właściwości zestawu narzędzi, które są dostępne dla projektu. Jedna właściwość zestawu narzędzi jest `$(MSBuildToolsPath)`, która określa ścieżkę do narzędzia programu .NET Framework. Tej właściwości zestawu narzędzi (lub `$(MSBuildBinPath)`), jest wymagana.  
  
 Począwszy od programu Visual Studio 2013 w wersji zestaw narzędzi MSBuild jest taki sam jak numer wersji programu Visual Studio. Domyślnie ten zestaw narzędzi w programie Visual Studio i w wierszu polecenia, niezależnie od wersji zestawu narzędzi, określone w pliku projektu MSBuild.  To zachowanie można zastąpić za pomocą flagi /ToolsVersion. Aby uzyskać więcej informacji, zobacz [zastępowanie ustawień ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 W poniższym przykładzie MSBuild znajduje przy użyciu pliku Microsoft.CSharp.targets `MSBuildToolsPath` zastrzeżone właściwości.  
  
```  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 Można zmodyfikować wartości `MSBuildToolsPath` przez zdefiniowanie niestandardowego zestawu narzędzi. Aby uzyskać więcej informacji, zobacz [standardowego i niestandardowego zestawu narzędzi konfiguracji](../msbuild/standard-and-custom-toolset-configurations.md)  
  
 Podczas kompilowania rozwiązania z wiersza polecenia i określić `ToolsVersion` msbuild.exe, wszystkie projekty i ich zależności projektu do projektu są tworzone zgodnie z tym `ToolsVersion`nawet w przypadku każdego projektu w rozwiązaniu określa swój własny `ToolsVersion`. Aby zdefiniować `ToolsVersion` wartości na podstawie projektu, zobacz [zastępowanie ustawień ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 `ToolsVersion` Atrybut służy do migracji projektu. Na przykład po otwarciu projektu programu Visual Studio 2008 w programie Visual Studio 2010 plik projektu zostanie zaktualizowany do uwzględnienia ToolsVersion = "4.0". Jeśli następnie spróbujesz otworzyć ten projekt w programie Visual Studio 2008, nie rozpoznaje uaktualnionego `ToolsVersion` i w związku z tym tworzy projekt tak, jakby atrybut nadal został ustawiony na 3.5.  
  
 Visual Studio 2010 i Visual Studio 2012 należy użyć ToolsVersion 4.0. ToolsVersion 12.0 korzysta z programu Visual Studio 2013. W wielu przypadkach możesz otworzyć projekt we wszystkich trzech wersjach programu Visual Studio bez żadnych modyfikacji. Program Visual Studio zawsze używa poprawny zestaw narzędzi, ale użytkownik będzie powiadamiany, gdy wersja używana jest niezgodna z wersją w pliku projektu. W większości przypadków to ostrzeżenie jest korzystna, zestawy narzędzi są zgodne w większości przypadków.  
  
 Sub — zestawy narzędzi, które są opisane w dalszej części tego tematu, umożliwiają MSBuild, automatyczne przełączanie, który zestaw narzędzi do użycia na podstawie kontekstu w którym kompilacja jest uruchamiana. Na przykład program MSBuild używa nowszej zestaw funkcji wspomagających po uruchomieniu programu Visual Studio 2012, niż w przypadku uruchomienia jej w programie Visual Studio 2010, bez konieczności jawnego zmiany w pliku projektu. Aby uzyskać więcej informacji, zobacz [wprowadzanie niestandardowych projektów rozpoznający wersje](../misc/making-custom-projects-version-aware.md).  
  
## <a name="toolset-implementation"></a>Zestaw narzędzi wdrażania  
 Implementowanie zestawu narzędzi, wybierając ścieżki różnych narzędzi, obiektów docelowych i zadań, które tworzą zestaw narzędzi. Narzędzia w zestawie narzędzi, który definiuje MSBuild pochodzić z następujących źródeł:  
  
- Folder .NET Framework.  
  
- Dodatkowe narzędzia zarządzanych.  
  
  Narzędzia zarządzanych obejmują ResGen.exe i TlbImp.exe.  
  
  MSBuild zapewnia dostęp do zestawu narzędzi na dwa sposoby:  
  
- Za pomocą właściwości zestawu narzędzi  
  
- Za pomocą <xref:Microsoft.Build.Utilities.ToolLocationHelper> metod  
  
  Właściwości zestawu narzędzi, określ ścieżki narzędzi. Program MSBuild używa wartości `ToolsVersion` atrybutu w pliku projektu, aby zlokalizować odpowiedni klucz rejestru, a następnie używa informacji w kluczu rejestru, aby ustawić właściwości zestawu narzędzi. Na przykład jeśli `ToolsVersion` ma wartość `12.0`, a następnie program MSBuild ustawia właściwości zestawu narzędzi, zgodnie z tego klucza rejestru: HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0.  
  
  Poniżej przedstawiono właściwości zestawu narzędzi:  
  
- `MSBuildToolsPath` Określa ścieżkę do plików binarnych programu MSBuild.  
  
- `SDK40ToolsPath` Określa ścieżkę dodatkowe narzędzia zarządzanych dla platformy MSBuild 4.x, (która może być 4.0 lub 4.5).  
  
- `SDK35ToolsPath` Określa ścieżkę dodatkowe narzędzia zarządzanego programu MSBuild 3.5.  
  
  Alternatywnie można określić zestaw narzędzi programowo przez wywołanie metody <xref:Microsoft.Build.Utilities.ToolLocationHelper> klasy. Klasa zawiera następujących metod:  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A> zwraca ścieżkę do folderu .NET Framework.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A> zwraca ścieżkę do pliku w folderze .NET Framework.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> zwraca ścieżkę do folderu Narzędzia zarządzanych.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> zwraca ścieżkę pliku, który zazwyczaj znajduje się w folderze Narzędzia zarządzanych.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToBuildTools%2A> zwraca ścieżkę narzędzia do kompilacji.  
  
### <a name="sub-toolsets"></a>Sub — zestawy narzędzi  
 Zgodnie z opisem we wcześniejszej części tego tematu, program MSBuild używa klucza rejestru, aby określić ścieżkę podstawowe narzędzia. Jeśli klucz ma podklucza, program MSBuild używa do określenia ścieżki podzestawu narzędzi, które zawiera dodatkowe narzędzia. W tym przypadku zestaw narzędzi jest zdefiniowany, łącząc definicji właściwości, które są zdefiniowane w obydwu kluczy.  
  
> [!NOTE]
>  W przypadku kolizji nazw właściwości zestawu narzędzi, wartość, która jest zdefiniowana dla ścieżki podkluczy zastępuje wartość, która jest zdefiniowana dla ścieżki klucza głównego.  
  
 Zestawy narzędzi Sub stają się aktywne, w przypadku obecności `VisualStudioVersion` właściwości kompilacji. Ta właściwość może mieć jedną z następujących wartości:  
  
- "10.0" Określa podzestawu narzędzi programu .NET Framework 4  
  
- "11.0" Określa podzestawu narzędzi programu .NET Framework 4.5  
  
- "12,0" Określa podzestawu narzędzi programu .NET Framework 4.5.1  
  
  Sub — procesami 10.0 i 11.0 powinien być używany z ToolsVersion 4.0. W nowszych wersjach powinna być zgodna z wersją podzestawu narzędzi i narzędzi.  
  
  Podczas kompilacji MSBuild automatycznie określa i ustawia wartość domyślną dla `VisualStudioVersion` właściwość, jeśli jeszcze nie został zdefiniowany.  
  
  Program MSBuild zapewnia przeciążenia `ToolLocationHelper` metodach dodających `VisualStudioVersion` wyliczonych wartości jako parametr  
  
  Zestawy narzędzi podrzędne zostały wprowadzone w .NET Framework 4.5.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfiguracje standardowego i niestandardowego zestawu narzędzi.](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Wielowersyjność kodu](../msbuild/msbuild-multitargeting-overview.md)
