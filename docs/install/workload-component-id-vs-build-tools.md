---
title: Visual Studio 2017 kompilacji narzędzia obciążeń i składników identyfikatorów
titleSuffix: ''
description: Użyj identyfikatory obciążeń i składników programu Visual Studio do tworzenia klasycznych aplikacji opartych na Windows
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
ms.workload:
- multiple
ms.openlocfilehash: 2e47eca638e81cf1b99a451e3017614be45d2c59
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063049"
---
# <a name="visual-studio-build-tools-2017-component-directory"></a>Visual Studio 2017 kompilacji narzędzia składników katalogu

Tabele na tej stronie listy identyfikatorów, w której można zainstalować program Visual Studio przy użyciu wiersza polecenia lub można określić jako zależności w manifestu VSIX. Należy pamiętać, że dodamy dodatkowe składniki, jak wydaniu aktualizacji do programu Visual Studio.

Ponadto należy pamiętać, że informacje o stronie:

* Każde obciążenie ma osobny rozdział, następuje identyfikator obciążenia i tabeli składników, które są dostępne dla obciążenia.
* Domyślnie **wymagane** składniki zostaną zainstalowane po zainstalowaniu obciążenia.
* Jeśli chcesz, możesz także zainstalować **zalecane** i **opcjonalnie** składników.
* Dodaliśmy również sekcję, która zawiera listę dodatkowych składników, które nie są powiązane z dowolnych obciążeń.

Po ustawieniu współzależności w manifeście VSIX tylko należy określić identyfikatory składników. Użyj tabel na tej stronie, aby określić nasze zależności minimalnej składnika. W niektórych scenariuszach to oznaczać, że należy określić tylko jeden składnik z obciążenia. W innych przypadkach może oznaczać, możesz określić wiele składników z pojedynczego obciążenia lub wielu składników z wielu obciążeń. Aby uzyskać więcej informacji, zobacz [instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) strony.

Aby uzyskać więcej informacji na temat używania tych identyfikatorów, zobacz [Użyj parametry wiersza polecenia, aby zainstalować program Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) strony. I dla listy, obciążenie i identyfikatorów składników dla innych produktów, zobacz [Visual Studio 2017 obciążenia i identyfikatory składnika](workload-and-component-ids.md) strony.

## <a name="azure-development-build-tools"></a>Narzędzia do kompilacji programowanie na platformie Azure

**Identyfikator:** Microsoft.VisualStudio.Workload.AzureBuildTools

**Opis:** MSBuild zadania i elementy docelowe do tworzenia aplikacji platformy Azure.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do kompilacji usługi Azure Cloud Services | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia programistyczne kontenera — narzędzia Build Tools | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | Elementy docelowe i zadania kompilacji NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 zestawu SDK | 15.0.28218.60 | Wymagane
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Narzędzia do kompilacji programowanie WCF | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Narzędzia kompilacji programowanie sieci Web | 15.8.27729.1 | Wymagane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 15.6.27406.0 | Zalecane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane funkcje platformy ASP.NET | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Microsoft.Net.Component.3.5.DeveloperTools | Narzędzia programistyczne programu .NET framework 3.5 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET framework 4.6.2 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET framework 4.7 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET framework 4.6.2 Developer tools | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia deweloperskie platformy .NET framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7 | 15.6.27406.0 | Optional

## <a name="data-storage-and-processing-build-tools"></a>Przechowywanie i przetwarzanie danych narzędzia do kompilacji

**Identyfikator:** Microsoft.VisualStudio.Workload.DataBuildTools

**Opis:** kompilacji projektów bazodanowych SQL Server

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.SQL.SSDTBuildSku | SQL Server Data Tools — narzędzia do kompilacji | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Zalecane

## <a name="net-desktop-build-tools"></a>Narzędzia kompilacji klasycznej platformy .NET

**Identyfikator:** Microsoft.VisualStudio.Workload.ManagedDesktopBuildTools

**Opis:** narzędzia do tworzenia aplikacji WPF, Windows Forms i aplikacji konsolowych przy użyciu C#, Visual Basic i F#.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | Elementy docelowe i zadania kompilacji NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.Component.ClickOnce.MSBuild | Narzędzia do kompilacji ClickOnce | 15.7.27617.1 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 15.6.27406.0 | Zalecane
Microsoft.Net.Core.Component.SDK | Narzędzia programistyczne programu .NET core 2.0 | 15.6.27406.0 | Zalecane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Zalecane
Microsoft.VisualStudio.Component.TestTools.BuildTools | Narzędzia do testowania podstawowe funkcje - Build Tools | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Narzędzia do kompilacji programowanie WCF | 15.6.27309.0 | Zalecane
Microsoft.Net.Component.3.5.DeveloperTools | Narzędzia programistyczne programu .NET framework 3.5 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET framework 4.6.2 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET framework 4.7 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET framework 4.6.2 Developer tools | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia deweloperskie platformy .NET framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | .NET core 1.0 – 1.1 narzędzia programistyczne | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.FSharp.MSBuild | kompilator F# | 15.8.27825.0 | Optional

## <a name="msbuild-tools"></a>Narzędzia MSBuild

**ID:** Microsoft.VisualStudio.Workload.MSBuildTools

**Opis:** zapewnia narzędzia wymagane do kompilowania aplikacji opartych na platformie MSBuild.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.VisualStudio.Component.CoreBuildTools | Program Visual Studio Tworzenie podstawowych narzędzi | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane

## <a name="net-core-build-tools"></a>Narzędzia kompilacji platformy .NET core

**ID:** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**Opis:** narzędzia do tworzenia aplikacji przy użyciu platformy .NET Core, ASP.NET Core, HTML/JavaScript i kontenerów.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Wymagane
Microsoft.NetCore.BuildTools.ComponentGroup | Narzędzia kompilacji platformy .NET core | 15.8.27906.1 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | Elementy docelowe i zadania kompilacji NuGet | 15.9.28016.0 | Wymagane
Microsoft.Net.Core.Component.SDK | Narzędzia programistyczne programu .NET core 2.0 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | .NET core 1.0 – 1.1 narzędzia programistyczne | 15.6.27406.0 | Optional

## <a name="nodejs-build-tools"></a>Narzędzia do kompilacji node.js

**ID:** Microsoft.VisualStudio.Workload.NodeBuildTools

**Opis:** zadania MSBuild i elementy docelowe do tworzenia skalowalnych sieci aplikacji przy użyciu platformy Node.js i asynchronicznego oparte na zdarzeniach środowiska uruchomieniowego JavaScript.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Node.Build | Obsługa MSBuild dla środowiska node.js | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 zestawu SDK | 15.0.28218.60 | Wymagane

## <a name="officesharepoint-build-tools"></a>Narzędzia do kompilacji pakietu Office/SharePoint

**Identyfikator:** Microsoft.VisualStudio.Workload.OfficeBuildTools

**Opis:** twórz dodatki pakietu Office i programu SharePoint i dodatków narzędzi VSTO.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.ClickOnce.MSBuild | Narzędzia do kompilacji ClickOnce | 15.7.27617.1 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | Elementy docelowe i zadania kompilacji NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Sharepoint.BuildTools | Narzędzia do kompilacji rozwoju pakietu Office/SharePoint | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.Workflow.BuildTools | Narzędzia kompilacji programu Windows Workflow Foundation | 15.8.27906.1 | Wymagane
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Narzędzia do kompilacji programowanie WCF | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Narzędzia kompilacji programowanie sieci Web | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.TeamOffice.BuildTools | Narzędzia do kompilacji programu Visual Studio Tools dla pakietu Office (VSTO) | 15.7.27617.1 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Microsoft.Net.Component.4.6.2.SDK | .NET framework 4.6.2 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET framework 4.7 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET framework 4.6.2 Developer tools | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia deweloperskie platformy .NET framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7 | 15.6.27406.0 | Optional

## <a name="universal-windows-platform-build-tools"></a>Narzędzia do kompilacji Universal Windows Platform

**Identyfikator:** Microsoft.VisualStudio.Workload.UniversalBuildTools

**Opis:** zapewnia narzędzia wymagane do kompilowania aplikacji uniwersalnych platformy Windows.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Component.NetFX.Native | Architektura .NET Native | 15.0.26208.0 | Wymagane
Microsoft.Component.VC.Runtime.OSSupport | Środowisko uruchomieniowe Visual C++ dla platformy uniwersalnej systemu Windows | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | Elementy docelowe i zadania kompilacji NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.VC.Tools.ARM | Kompilatory języka Visual C++ i bibliotek dla ARM | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 w wersji 15.9 v14.16 najnowszych wersji 141 narzędzi | 15.9.28230.55 | Wymagane
Microsoft.VisualStudio.ComponentGroup.UWP.BuildTools | Wymagania wstępne kompilowania dla platformy Windows Universal | 15.8.27705.0 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.10240 | System Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | System Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | System Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | System Windows 10 SDK (10.0.15063.0) for Desktop C++ [x86 i x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | System Windows 10 SDK (10.0.15063.0) dla platformy UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | System Windows 10 SDK (10.0.15063.0) dla platformy UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | System Windows 10 SDK (10.0.16299.0) for Desktop C++ [x86 i x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | System Windows 10 SDK (10.0.16299.0) for Desktop C++ [ARM i ARM64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | System Windows 10 SDK (10.0.16299.0) dla platformy UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | System Windows 10 SDK (10.0.16299.0) dla platformy UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | System Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | System Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | Optional

## <a name="visual-c-build-tools"></a>Narzędzi Visual C++ build tools

**ID:** Microsoft.VisualStudio.Workload.VCTools

**Opis:** Twórz aplikacje klasyczne Windows przy użyciu zestawu narzędzi Microsoft C++, ATL lub MFC.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Narzędzia Visual C++ Build Tools podstawowe funkcje | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aktualizacji pakietu redystrybucyjnego Visual C++ 2017 | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 w wersji 15.9 v14.16 najnowszych wersji 141 narzędzi | 15.9.28230.55 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.TestTools.BuildTools | Narzędzia do testowania podstawowe funkcje - Build Tools | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Component.VC.CMake.Project | Visual C++ tools for CMake | 15.8.27906.1 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Zalecane
Microsoft.Component.VC.Runtime.UCRTSDK | Zestawu Windows Universal CRT SDK | 15.6.27309.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | VC ++ 2015.3 14.00 (wersja 140) z zestawu narzędzi dla pulpitu | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL dla x86 i x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC dla x86 i x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C + +/ interfejsu wiersza polecenia | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduły biblioteki standardowej (eksperymentalne) | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | Kompilatory języka Visual C++ i bibliotek dla ARM | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Kompilatory języka Visual C++ i bibliotek dla architektury ARM64 | 15.9.28230.55 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | System Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | System Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | System Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | System Windows 10 SDK (10.0.15063.0) for Desktop C++ [x86 i x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | System Windows 10 SDK (10.0.15063.0) dla platformy UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | System Windows 10 SDK (10.0.15063.0) dla platformy UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | System Windows 10 SDK (10.0.16299.0) for Desktop C++ [x86 i x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | System Windows 10 SDK (10.0.16299.0) for Desktop C++ [ARM i ARM64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | System Windows 10 SDK (10.0.16299.0) dla platformy UWP: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | System Windows 10 SDK (10.0.16299.0) dla platformy UWP: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Zestaw SDK systemu Windows 8.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.WinXP | Windows XP podporu androidu Pro C++ | 15.8.27924.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK i UCRT SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Windows XP podporu androidu Pro C++ | 15.8.27705.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | System Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | System Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | Optional

## <a name="visual-studio-extension-development"></a>Programowanie rozszerzeń programu Visual Studio

**Identyfikator:** Microsoft.VisualStudio.Workload.VisualStudioExtensionBuildTools

**Opis:** narzędzia do tworzenia dodatków i rozszerzeń dla programu Visual Studio, w tym nowe polecenia, analizatory kodu i okna narzędzi.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | Elementy docelowe i zadania kompilacji NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.VSSDKBuildTools | Zestaw SDK programu Visual Studio Tworzenie podstawowych narzędzi | 15.8.27924.0 | Wymagane
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtensionBuildTools.Prerequisites | Visual Studio rozszerzenia wymagania wstępne dotyczące programowania | 15.8.27729.1 | Wymagane
Component.Dotfuscator | Ochrona preEmptive — Dotfuscator | 15.0.26208.0 | Optional
Microsoft.Component.VC.Runtime.OSSupport | Środowisko uruchomieniowe Visual C++ dla platformy uniwersalnej systemu Windows | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL dla x86 i x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC dla x86 i x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 w wersji 15.9 v14.16 najnowszych wersji 141 narzędzi | 15.9.28230.55 | Optional

## <a name="web-development-build-tools"></a>Narzędzia kompilacji programowanie sieci Web

**ID:** Microsoft.VisualStudio.Workload.WebBuildTools

**Opis:** zadania MSBuild i elementy docelowe do tworzenia aplikacji sieci web.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | Elementy docelowe i zadania kompilacji NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 zestawu SDK | 15.0.28218.60 | Wymagane
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Narzędzia kompilacji programowanie sieci Web | 15.8.27729.1 | Wymagane
Microsoft.Component.ClickOnce.MSBuild | Narzędzia do kompilacji ClickOnce | 15.7.27617.1 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 15.6.27406.0 | Zalecane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane funkcje platformy ASP.NET | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia programistyczne kontenera — narzędzia Build Tools | 15.7.27617.1 | Zalecane
Microsoft.VisualStudio.Component.TestTools.BuildTools | Narzędzia do testowania podstawowe funkcje - Build Tools | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Narzędzia do kompilacji programowanie WCF | 15.6.27309.0 | Zalecane
Microsoft.Net.Component.3.5.DeveloperTools | Narzędzia programistyczne programu .NET framework 3.5 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET framework 4.6.2 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET framework 4.7 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET framework 4.6.2 Developer tools | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia deweloperskie platformy .NET framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7.2 | 15.8.27825.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK | Narzędzia programistyczne programu .NET core 2.0 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | .NET core 1.0 – 1.1 narzędzia programistyczne | 15.6.27406.0 | Optional

## <a name="mobile-development-with-net"></a>Tworzenie aplikacji mobilnych przy użyciu platformy .NET

**Identyfikator:** Microsoft.VisualStudio.Workload.XamarinBuildTools

**Opis:** narzędzia do tworzenia aplikacji dla wielu platform dla systemów iOS, Android i Windows przy użyciu C# i F#.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | Elementy docelowe i zadania kompilacji NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Component.Android.SDK25 | Instalacja zestawu android SDK (poziom interfejsu API 25) | 15.9.28107.0 | Optional
Component.OpenJDK | Dystrybucja Microsoft OpenJDK | 15.9.28125.51 | Optional

## <a name="unaffiliated-components"></a>Składniki nie podlega

Są to składniki, które nie są uwzględniane przy użyciu dowolnego obciążenia, ale można wybrać jako poszczególnych składników.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 zestawu SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.3 | TypeScript 2.3 zestawu SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.6 | TypeScript w wersji 2.6 zestawu SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.7 | TypeScript 2.7 zestawu SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 zestawu SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.9 | TypeScript 2.9 zestawu SDK | 15.0.27924.0
Microsoft.VisualStudio.Component.TypeScript.3.0 | TypeScript 3.0 zestawu SDK | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.ATL.ARM | Visual C++ ATL dla ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Visual C++ ATL dla ARM z krokami zaradczymi dla luki Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | Visual C++ ATL dla architektury ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | Visual C++ ATL dla architektury ARM64 z krokami zaradczymi dla luki Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.Spectre | Visual C++ ATL — x86/x64 64 z krokami zaradczymi dla luki Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Visual C++ MFC x86/x64 z krokami zaradczymi dla luki Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (wersja eksperymentalna) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | Visual C++ MFC dla ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | Visual C++ MFC dla ARM z krokami zaradczymi dla luki Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | Visual C++ MFC dla architektury ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Visual C++ MFC z obsługą architektury arm64 z krokami zaradczymi dla luki Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | VC ++ 2017 w wersji 15.9 v14.16 Libs krokami zaradczymi dla luki (ARM) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | VC ++ 2017 w wersji 15.9 v14.16 Libs dla luki Spectre (ARM64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | VC ++ 2017 w wersji 15.9 v14.16 Libs dla luki Spectre (x86 i x64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Tools.14.11 | Zestaw narzędzi 14.11 dla programu VC ++ 2017 w wersji 15.4 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | Zestaw narzędzi 14.12 dla programu VC ++ 2017 w wersji 15.5 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | Zestaw narzędzi 14.13 dla programu VC ++ 2017 w wersji 15.6 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.14 | Zestaw narzędzi w wersji 14.14 dotyczące VC ++ 2017 w wersji 15.7 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.15 | Zestaw narzędzi programu VC ++ 2017 w wersji 15.8 v14.15 | 15.0.28230.55

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Build Tools for Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017#build-tools-for-visual-studio-2017)
* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
* [Podręcznik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
