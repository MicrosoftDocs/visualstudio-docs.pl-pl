---
title: Pakiety robocze i identyfikatory składników programu Visual Studio Community 2019
titleSuffix: ''
description: Użyj obciążenia i identyfikatory składników, aby zainstalować program Visual Studio przy użyciu wiersza polecenia lub określić jako zależności w manifestu VSIX
keywords: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 09/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: fa7082b3d605fba394db77bfc470e5115cd61f6f
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71210293"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-community-2019"></a>Visual Studio Core Editor (dołączony do programu Visual Studio Community 2019)

**#C1** Microsoft.VisualStudio.Workload.CoreEditor

**Opis:** Podstawowe środowisko powłoki programu Visual Studio, w tym edytowanie kodu z rozpoznawaniem składni, Kontrola kodu źródłowego i zarządzanie elementami roboczymi.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Edytor rdzeni programu Visual Studio | 16.1.28811.260 | Wymagane
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Program Visual Studio uruchomić stronę dla użytkowników języka C++ | 16.0.28315.86 | Optional

## <a name="azure-development"></a>Programowanie na platformie Azure

**#C1** Microsoft. VisualStudio. obciążeni. Azure

**Opis:** Zestawy SDK platformy Azure, narzędzia i projekty do opracowywania aplikacji w chmurze i tworzenia zasobów przy użyciu platformy .NET Core i .NET Framework. Obejmuje także narzędzia do konteneryzowania aplikacji, w tym obsługę platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 16.0.28714.129 | Wymagane
Component.Microsoft.VisualStudio.Web.AzureFunctions | Narzędzia Azure WebJobs | 16.0.28714.129 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft. NET. Component. 4.8. SDK | Zestaw .NET Framework 4,8 SDK | 16.3.29230.54 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.3.29207.166 | Wymagane
Microsoft. WebCore. Component. DevelopmentTools | Narzędzia programistyczne dla platformy .NET Core | 16.3.29207.166 | Wymagane
Microsoft. WebCore. Component. SDK | Zestaw SDK platformy .NET Core 3,0 | 16.3.29318.74 | Wymagane
Microsoft. WebCore. Component. Web | Narzędzia programistyczne dla platformy .NET Core | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 16.1.28810.153 | Wymagane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.3.29230.54 | Wymagane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.3.29311.71 | Wymagane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.3.29103.31 | Wymagane
Microsoft.VisualStudio.Component.FSharp | F#Obsługa języków | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#Obsługa języka dla projektów sieci web | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagane
Microsoft. VisualStudio. Component. rozszerzenia intellicode | IntelliCode | 0.1 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 16.3.29230.54 | Wymagane
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik SQL Server ODBC | 16.0.28625.61 | Wymagane
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Wymagane
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Zestaw SDK języka TypeScript 3,6 | 16.0.29207.166 | Wymagane
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Wymagania wstępne dotyczące programowania dla platformy Azure | 16.3.29311.71 | Wymagane
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Narzędzia Azure WebJobs | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 16.3.29230.54 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Wymagane
Microsoft.Component.Azure.DataLake.Tools | Usługa Azure Data Lake i Stream Analytics Tools | 16.3.29207.166 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 16.0.28516.191 | Zalecane
Microsoft.Net.Core.Component.SDK.2.1 | Środowisko uruchomieniowe LTS programu .NET Core 2,1 | 16.3.29318.74 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane funkcje platformy ASP.NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Visual Studio Tools for Kubernetes | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Podstawowe narzędzia usługi Azure Resource Manager | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Narzędzia usługi Service Fabric | 16.3.29230.54 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton | Podstawowe narzędzia usługi Azure Cloud Services | 16.3.29311.71 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do kompilacji usługi Azure Cloud Services | 16.3.29207.166 | Zalecane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 16.3.29207.166 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Narzędzia usług w chmurze platformy Azure | 16.3.29311.71 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Narzędzia usługi Azure Resource Manager | 16.0.28528.71 | Zalecane
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net. Component. 4.8. TargetingPack | Pakiet docelowy .NET Framework 4,8 | 16.3.29230.54 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.6.1 | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET framework 4.6.2 Developer tools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia deweloperskie platformy .NET framework 4.7.1 | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7 | 16.3.29207.166 | Optional
Microsoft.Net. Component. 4.8. DeveloperTools | Narzędzia programistyczne .NET Framework 4,8 | 16.3.29230.54 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Usługa Azure Storage, narzędzia AzCopy | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional

## <a name="data-storage-and-processing"></a>Magazynowanie i przetwarzanie danych

**#C1** Microsoft. VisualStudio. obciążenie. Data

**Opis:** Łączenie, opracowywanie i testowanie rozwiązań z zakresu danych za pomocą SQL Server, Azure Data Lake lub usługi Hadoop.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 16.0.28714.129 | Zalecane
Component.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Zalecane
Microsoft.Component.Azure.DataLake.Tools | Usługa Azure Data Lake i Stream Analytics Tools | 16.3.29207.166 | Zalecane
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Zalecane
Microsoft. NET. Component. 4.8. SDK | Zestaw .NET Framework 4,8 SDK | 16.3.29230.54 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.3.29207.166 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 16.0.28516.191 | Zalecane
Microsoft. WebCore. Component. SDK | Zestaw SDK platformy .NET Core 3,0 | 16.3.29318.74 | Zalecane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 16.1.28810.153 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.3.29230.54 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton | Podstawowe narzędzia usługi Azure Cloud Services | 16.3.29311.71 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do kompilacji usługi Azure Cloud Services | 16.3.29207.166 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.3.29311.71 | Zalecane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.3.29103.31 | Zalecane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.3.29207.166 | Zalecane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 16.3.29230.54 | Zalecane
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik SQL Server ODBC | 16.0.28625.61 | Zalecane
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.1.28829.92 | Zalecane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Zalecane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Zalecane
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Zestaw SDK języka TypeScript 3,6 | 16.0.29207.166 | Zalecane
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 16.3.29230.54 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Zalecane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.FSharp.Desktop | F#Obsługa pulpitu języka | 16.0.28315.86 | Optional

## <a name="data-science-and-analytical-applications"></a>Aplikacje do analizy i przetwarzania danych

**#C1** Microsoft. VisualStudio. obciążenie. datascience

**Opis:** Języki i narzędzia do tworzenia aplikacji do nauki o danych, w tym F#Python i.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.PythonTools | Obsługa języka Python | 16.0.28625.61 | Zalecane
Microsoft.Component.PythonTools.Minicondax64 | Miniconda Python | 16.2.29003.222 | Zalecane
Microsoft.Component.PythonTools.Web | Obsługa sieci web w języku Python | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.3.29311.71 | Zalecane
Microsoft.VisualStudio.Component.FSharp.Desktop | F#Obsługa pulpitu języka | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.3.29207.166 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.1.28829.92 | Zalecane
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Zestaw SDK języka TypeScript 3,6 | 16.0.29207.166 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Zalecane
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Narzędzia do programowania natywnego języka Python | 16.2.29020.229 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla technologii DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | C++podstawowe funkcje | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania dla języka C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142-VS 2019 C++ x64/x86 Build Tools (v 14.23) | 16.3.29230.54 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.3.29311.71 | Optional
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Zestaw SDK systemu Windows 10 (10.0.18362.0) | 16.1.28829.92 | Optional

## <a name="net-desktop-development"></a>Programowanie aplikacji klasycznych dla platformy .NET

**#C1** Microsoft.VisualStudio.Workload.ManagedDesktop

**Opis:** Twórz aplikacje WPF, Windows Forms i konsolowe przy C#użyciu programów, Visual Basic F# i .NET Core i .NET Framework.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft. NET. Component. 4.8. SDK | Zestaw .NET Framework 4,8 SDK | 16.3.29230.54 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.3.29207.166 | Wymagane
Microsoft. WebCore. Component. SDK | Zestaw SDK platformy .NET Core 3,0 | 16.3.29318.74 | Wymagane
Microsoft. VisualStudio. Component. rozszerzenia intellicode | IntelliCode | 0.1 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 16.3.29230.54 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Narzędzia programistyczne dla platformy .NET | 16.3.29230.54 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Wymagane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.826 | Zalecane
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 16.0.28516.191 | Zalecane
Microsoft.Net.Core.Component.SDK.2.1 | Środowisko uruchomieniowe LTS programu .NET Core 2,1 | 16.3.29318.74 | Zalecane
Microsoft. WebCore. Component. DevelopmentTools | Narzędzia programistyczne dla platformy .NET Core | 16.3.29207.166 | Zalecane
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger Just In Time | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 16.3.29207.166 | Zalecane
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 tools | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.FSharp | F#Obsługa języków | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Zalecane
Component.Dotfuscator | Ochrona preEmptive — Dotfuscator | 16.0.28528.71 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 16.0.28714.129 | Optional
Component.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net. Component. 4.8. TargetingPack | Pakiet docelowy .NET Framework 4,8 | 16.3.29230.54 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.6.1 | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET framework 4.6.2 Developer tools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia deweloperskie platformy .NET framework 4.7.1 | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7 | 16.3.29207.166 | Optional
Microsoft.Net. Component. 4.8. DeveloperTools | Narzędzia programistyczne .NET Framework 4,8 | 16.3.29230.54 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.3.29311.71 | Optional
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.3.29103.31 | Optional
Microsoft.VisualStudio.Component.FSharp.Desktop | F#Obsługa pulpitu języka | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.3.29207.166 | Optional
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik SQL Server ODBC | 16.0.28625.61 | Optional
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Optional
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Optional
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Zestaw SDK języka TypeScript 3,6 | 16.0.29207.166 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 16.0.28517.75 | Optional
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Zestaw SDK systemu Windows 10 (10.0.18362.0) | 16.1.28829.92 | Optional
Microsoft. VisualStudio. Component. MSIX. pakowanie | Narzędzia do pakowania MSIX | 16.3.29230.54 | Optional
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 16.3.29230.54 | Optional
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Optional

## <a name="game-development-with-unity"></a>Programowanie gier za pomocą aparatu Unity

**#C1** Microsoft.VisualStudio.Workload.ManagedGame

**Opis:** Twórz gry 2D i 3D za pomocą aparatu Unity — zaawansowanego środowiska deweloperskiego dla wielu platform.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Narzędzia programistyczne programu .NET framework 3.5 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Unity | Narzędzia Visual Studio Tools for Unity | 16.0.28315.86 | Wymagane
Component.UnityEngine.x64 | Unity 2018,3 64 — Edytor bitowy | 16.1.28810.153 | Zalecane
Component.UnityEngine.x86 | Unity 5.6 32-bitowych edytora | 16.1.28811.260 | Zalecane

## <a name="linux-development-with-c"></a>Programowanie dla systemu Linux przy użyciu języka C++

**#C1** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Opis:** Twórz i Debuguj aplikacje działające w środowisku systemu Linux.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.MDD.Linux | C++dla rozwoju systemu Linux | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.VC.CoreIde | C++podstawowe funkcje | 16.0.28625.61 | Wymagane
Component.Linux.CMake | C++Narzędzia CMake dla systemu Linux | 16.2.29003.222 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Zalecane
Component.MDD.Linux.GCC.arm | Narzędzia programistyczne Embedded i IoT | 16.2.28915.88 | Optional

## <a name="desktop-development-with-c"></a>Programowanie aplikacji klasycznych w języku C++

**#C1** Microsoft.VisualStudio.Workload.NativeDesktop

**Opis:** Twórz nowoczesne C++ aplikacje dla systemu Windows przy użyciu wybranych przez siebie narzędzi, w tym MSVC, Clang, CMAKE lub MSBuild.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.VC.CoreIde | C++podstawowe funkcje | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++Aktualizacja redystrybucyjna 2019 | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | C++podstawowe funkcje pulpitu | 16.2.29012.281 | Wymagane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.826 | Zalecane
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger Just In Time | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla technologii DirectX | 16.0.28625.61 | Zalecane
Microsoft. VisualStudio. Component. rozszerzenia intellicode | IntelliCode | 0.1 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Zalecane
Microsoft.VisualStudio.Component.VC.ATL | C++ATL dla najnowszych narzędzi kompilacji v142 (x86 & x64) | 16.3.29230.54 | Zalecane
Microsoft.VisualStudio.Component.VC.CMake.Project | C++Narzędzia CMake dla systemu Windows | 16.3.29103.31 | Zalecane
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania dla języka C++ | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Rozszerzenia test Adapter for Boost.Test | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Test Adapter for Google Test | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142-VS 2019 C++ x64/x86 Build Tools (v 14.23) | 16.3.29230.54 | Zalecane
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Zestaw SDK systemu Windows 10 (10.0.18362.0) | 16.1.28829.92 | Zalecane
Microsoft. VisualStudio. Component. WebToolsExtensions. CMake | Edytor JSON | 16.3.29207.166 | Zalecane
Component.Incredibuild | IncrediBuild — przyspieszanie kompilacji | 16.0.28528.71 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.10 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Zestawu Windows Universal CRT SDK | 16.0.28625.61 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Optional
Microsoft. NET. Component. 4.8. SDK | Zestaw .NET Framework 4,8 SDK | 16.3.29230.54 | Optional
Microsoft.VisualStudio.Component.VC.140 | Narzędzia kompilacji MSVC wersji 140 — C++ vs 2015 (v 14.00) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | C++MFC dla najnowszych narzędzi kompilacji v142 (x86 & x64) | 16.3.29230.54 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C++Obsługa/CLI dla narzędzi kompilacji v142 (14,23) | 16.3.29230.54 | Optional
Microsoft. VisualStudio. Component. VC. LLVM. Clang | C++Kompilator Clang dla systemu Windows (8.0.1) | 16.3.29230.54 | Optional
Microsoft. VisualStudio. Component. VC. LLVM. ClangToolset | C++Clang-CL dla narzędzi kompilacji v142 (x64/x86) | 16.3.29207.166 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | C++Moduły dla narzędzi do kompilacji v142 (x64/x86 — eksperymentalne) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC najnowsze 141-VS 2017 C++ x64/x86 Build Tools (v 14.16) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | System Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | System Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Optional
Microsoft. VisualStudio. Component. NativeDesktop. LLVM. Clang | C++Clang Tools for Windows (8.0.1-x64/x86) | 16.3.29230.54 | Optional

## <a name="game-development-with-c"></a>Programowanie gier w języku C++

**#C1** Microsoft.VisualStudio.Workload.NativeGame

**Opis:** Korzystaj z pełnych możliwości C++ , aby tworzyć profesjonalne gry obsługiwane przez program DirectX, Unreal lub Cocos2d.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | C++podstawowe funkcje | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++Aktualizacja redystrybucyjna 2019 | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142-VS 2019 C++ x64/x86 Build Tools (v 14.23) | 16.3.29230.54 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.3.29311.71 | Wymagane
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla technologii DirectX | 16.0.28625.61 | Zalecane
Microsoft. VisualStudio. Component. rozszerzenia intellicode | IntelliCode | 0.1 | Zalecane
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania dla języka C++ | 16.0.28625.61 | Zalecane
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Zestaw SDK systemu Windows 10 (10.0.18362.0) | 16.1.28829.92 | Zalecane
Składnik. Android. NDK. R16B | Android NDK (R16B) | 16.3.29318.136 | Optional
Component.Android.SDK25.Private | Konfiguracja Android SDK (poziom interfejsu API 25) (lokalna instalacja na potrzeby opracowywania aplikacji mobilnych za pomocą C++programu) | 16.0.28625.61 | Optional
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Optional
Component.Cocos | Cocos | 16.0.28315.86 | Optional
Component.Incredibuild | IncrediBuild — przyspieszanie kompilacji | 16.0.28528.71 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.10 | Optional
Component.MDD.Android | Narzędzia programistyczne C++ Android | 16.0.28517.75 | Optional
Component.OpenJDK | OpenJDK (dystrybucja firmy Microsoft) | 16.1.28811.260 | Optional
Component.Unreal | Instalator aparatu unreal Engine | 16.1.28810.153 | Optional
Component.Unreal.Android | Obsługa środowiska IDE systemu Android dla aparatu Unreal | 16.1.28810.153 | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Optional
Microsoft. NET. Component. 4.8. SDK | Zestaw .NET Framework 4,8 SDK | 16.3.29230.54 | Optional
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 16.0.28516.191 | Optional
Microsoft.VisualStudio.Component.NuGet.BuildTools | Elementy docelowe i zadania kompilacji NuGet | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | System Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | System Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Optional

## <a name="mobile-development-with-c"></a>Tworzenie aplikacji mobilnych w języku C++

**#C1** Microsoft.VisualStudio.Workload.NativeMobile

**Opis:** Twórz aplikacje dla wielu platform dla systemów iOS, Android i Windows C++za pomocą programu.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Android.SDK25.Private | Konfiguracja Android SDK (poziom interfejsu API 25) (lokalna instalacja na potrzeby opracowywania aplikacji mobilnych za pomocą C++programu) | 16.0.28625.61 | Wymagane
Component.OpenJDK | OpenJDK (dystrybucja firmy Microsoft) | 16.1.28811.260 | Wymagane
Microsoft.VisualStudio.Component.VC.CoreIde | C++podstawowe funkcje | 16.0.28625.61 | Wymagane
Składnik. Android. NDK. R16B | Android NDK (R16B) | 16.3.29318.136 | Zalecane
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Zalecane
Component.MDD.Android | Narzędzia programistyczne C++ Android | 16.0.28517.75 | Zalecane
Microsoft. VisualStudio. Component. rozszerzenia intellicode | IntelliCode | 0.1 | Zalecane
Składnik. Android. NDK. R16B_3264 | Android NDK (R16B) (32-bitowe) | 16.3.29318.136 | Optional
Component.Google.Android.Emulator.API25.Private | Google Emulator systemu Android (poziom interfejsu API 25) (Instalacja lokalna) | 16.1.28810.153 | Optional
Component.HAXM.Private | Intel Hardware Accelerated Execution Menedżera (HAXM) (instalacja lokalna) | 16.0.28528.71 | Optional
Component.Incredibuild | IncrediBuild — przyspieszanie kompilacji | 16.0.28528.71 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.10 | Optional
Component.MDD.IOS | Narzędzia programistyczne dla systemu iOS C++ | 16.0.28517.75 | Optional

## <a name="net-core-cross-platform-development"></a>Programowanie dla wielu platform .NET core

**#C1** Microsoft.VisualStudio.Workload.NetCoreTools

**Opis:** Twórz aplikacje dla wielu platform przy użyciu technologii .NET Core, ASP.NET Core, HTML/JavaScript i kontenerów, łącznie z obsługą platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 16.0.28714.129 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft. NET. Component. 4.8. SDK | Zestaw .NET Framework 4,8 SDK | 16.3.29230.54 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.3.29207.166 | Wymagane
Microsoft. WebCore. Component. DevelopmentTools | Narzędzia programistyczne dla platformy .NET Core | 16.3.29207.166 | Wymagane
Microsoft. WebCore. Component. SDK | Zestaw SDK platformy .NET Core 3,0 | 16.3.29318.74 | Wymagane
Microsoft. WebCore. Component. Web | Narzędzia programistyczne dla platformy .NET Core | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.3.29311.71 | Wymagane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.3.29103.31 | Wymagane
Microsoft.VisualStudio.Component.FSharp | F#Obsługa języków | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#Obsługa języka dla projektów sieci web | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagane
Microsoft. VisualStudio. Component. rozszerzenia intellicode | IntelliCode | 0.1 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 16.3.29230.54 | Wymagane
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik SQL Server ODBC | 16.0.28625.61 | Wymagane
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Wymagane
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Zestaw SDK języka TypeScript 3,6 | 16.0.29207.166 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 16.3.29230.54 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Wymagane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.826 | Zalecane
Component.Microsoft.VisualStudio.Web.AzureFunctions | Narzędzia Azure WebJobs | 16.0.28714.129 | Zalecane
Microsoft.Net.Core.Component.SDK.2.1 | Środowisko uruchomieniowe LTS programu .NET Core 2,1 | 16.3.29318.74 | Zalecane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 16.2.28917.182 | Zalecane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 16.1.28810.153 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.3.29230.54 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 16.3.29207.166 | Zalecane
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Narzędzia Azure WebJobs | 16.0.28621.142 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Narzędzia do tworzenia aplikacji internetowych w chmurze | 16.2.29003.222 | Zalecane
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Zestaw SDK systemu Windows 10 (10.0.18362.0) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Obsługa usług IIS w czasie opracowywania | 16.0.28315.86 | Optional
Microsoft. VisualStudio. Component. MSIX. pakowanie | Narzędzia do pakowania MSIX | 16.3.29230.54 | Optional

## <a name="mobile-development-with-net"></a>Tworzenie aplikacji mobilnych przy użyciu platformy .NET

**#C1** Microsoft.VisualStudio.Workload.NetCrossPlat

**Opis:** Twórz aplikacje dla wielu platform dla systemów iOS, Android i Windows przy użyciu platformy Xamarin.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.OpenJDK | OpenJDK (dystrybucja firmy Microsoft) | 16.1.28811.260 | Wymagane
Component.Xamarin | Xamarin | 16.3.29207.166 | Wymagane
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 16.0.28315.86 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft. NET. Component. 4.8. SDK | Zestaw .NET Framework 4,8 SDK | 16.3.29230.54 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.3.29207.166 | Wymagane
Microsoft. WebCore. Component. DevelopmentTools | Narzędzia programistyczne dla platformy .NET Core | 16.3.29207.166 | Wymagane
Microsoft. WebCore. Component. SDK | Zestaw SDK platformy .NET Core 3,0 | 16.3.29318.74 | Wymagane
Microsoft.VisualStudio.Component.FSharp | F#Obsługa języków | 16.0.28315.86 | Wymagane
Microsoft. VisualStudio. Component. rozszerzenia intellicode | IntelliCode | 0.1 | Wymagane
Microsoft.VisualStudio.Component.Merq | Wspólne narzędzia wewnętrzne platformy Xamarin | 16.2.29012.281 | Wymagane
Microsoft.VisualStudio.Component.MonoDebugger | Debuger środowiska mono | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Aparat szablonów ASP.NET | 16.0.28315.86 | Wymagane
Składnik. Android. SDK28 | Konfiguracja Android SDK (poziom interfejsu API 28) | 16.2.29003.222 | Zalecane

## <a name="aspnet-and-web-development"></a>ASP.NET i tworzenie aplikacji internetowych

**#C1** Microsoft.VisualStudio.Workload.NetWeb

**Opis:** Twórz aplikacje sieci Web przy użyciu ASP.NET Core, ASP.NET, HTML/JavaScript i kontenerów, łącznie z obsługą platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 16.0.28714.129 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft. NET. Component. 4.8. SDK | Zestaw .NET Framework 4,8 SDK | 16.3.29230.54 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.3.29207.166 | Wymagane
Microsoft. WebCore. Component. DevelopmentTools | Narzędzia programistyczne dla platformy .NET Core | 16.3.29207.166 | Wymagane
Microsoft. WebCore. Component. SDK | Zestaw SDK platformy .NET Core 3,0 | 16.3.29318.74 | Wymagane
Microsoft. WebCore. Component. Web | Narzędzia programistyczne dla platformy .NET Core | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.3.29311.71 | Wymagane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.3.29103.31 | Wymagane
Microsoft.VisualStudio.Component.FSharp | F#Obsługa języków | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#Obsługa języka dla projektów sieci web | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagane
Microsoft. VisualStudio. Component. rozszerzenia intellicode | IntelliCode | 0.1 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 16.3.29230.54 | Wymagane
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik SQL Server ODBC | 16.0.28625.61 | Wymagane
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Wymagane
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Zestaw SDK języka TypeScript 3,6 | 16.0.29207.166 | Wymagane
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 16.3.29230.54 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Wymagane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.826 | Zalecane
Component.Microsoft.VisualStudio.Web.AzureFunctions | Narzędzia Azure WebJobs | 16.0.28714.129 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 16.0.28516.191 | Zalecane
Microsoft.Net.Core.Component.SDK.2.1 | Środowisko uruchomieniowe LTS programu .NET Core 2,1 | 16.3.29318.74 | Zalecane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 16.2.28917.182 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane funkcje platformy ASP.NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 16.1.28810.153 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.3.29230.54 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 16.3.29207.166 | Zalecane
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 tools | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Narzędzia Azure WebJobs | 16.0.28621.142 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Narzędzia do tworzenia aplikacji internetowych w chmurze | 16.2.29003.222 | Zalecane
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net. Component. 4.8. TargetingPack | Pakiet docelowy .NET Framework 4,8 | 16.3.29230.54 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.6.1 | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET framework 4.6.2 Developer tools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia deweloperskie platformy .NET framework 4.7.1 | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7 | 16.3.29207.166 | Optional
Microsoft.Net. Component. 4.8. DeveloperTools | Narzędzia programistyczne .NET Framework 4,8 | 16.3.29230.54 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Dodatkowe szablony projektu (poprzednie wersje) | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Obsługa usług IIS w czasie opracowywania | 16.0.28315.86 | Optional

## <a name="nodejs-development"></a>Tworzenia aplikacji node.js

**#C1** Microsoft. VisualStudio. obciążeni. Node

**Opis:** Twórz skalowalne aplikacje sieciowe przy użyciu środowiska Node. js, asynchronicznego, opartego na zdarzeniach środowisko uruchomieniowe JavaScript. 

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.Node.Tools | Narzędzia programistyczne środowiska Node. js | 16.0.28625.61 | Wymagane
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Zestaw SDK języka TypeScript 3,6 | 16.0.29207.166 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Wymagane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.826 | Zalecane
Microsoft. VisualStudio. Component. rozszerzenia intellicode | IntelliCode | 0.1 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 16.2.28917.182 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.3.29311.71 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | C++podstawowe funkcje | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142-VS 2019 C++ x64/x86 Build Tools (v 14.23) | 16.3.29230.54 | Optional

## <a name="officesharepoint-development"></a>Programowanie Office/SharePoint

**#C1** Microsoft.VisualStudio.Workload.Office

**Opis:** Twórz Dodatki dla pakietu Office i programu SharePoint, rozwiązania programu SharePoint i dodatki narzędzi VSTO przy C#użyciu języka, VB i JavaScript.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 16.0.28714.129 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft. NET. Component. 4.8. SDK | Zestaw .NET Framework 4,8 SDK | 16.3.29230.54 | Wymagane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.3.29207.166 | Wymagane
Microsoft. WebCore. Component. SDK | Zestaw SDK platformy .NET Core 3,0 | 16.3.29318.74 | Wymagane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 16.2.28917.182 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.3.29311.71 | Wymagane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.3.29103.31 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagane
Microsoft. VisualStudio. Component. rozszerzenia intellicode | IntelliCode | 0.1 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 16.3.29230.54 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Narzędzia programistyczne dla platformy .NET | 16.3.29230.54 | Wymagane
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik SQL Server ODBC | 16.0.28625.61 | Wymagane
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 16.3.29311.71 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Wymagane
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Zestaw SDK języka TypeScript 3,6 | 16.0.29207.166 | Wymagane
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 16.3.29230.54 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools dla pakietu Office (VSTO) | 16.3.29311.71 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net. Component. 4.8. TargetingPack | Pakiet docelowy .NET Framework 4,8 | 16.3.29230.54 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.6.1 | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET framework 4.6.2 Developer tools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia deweloperskie platformy .NET framework 4.7.1 | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7 | 16.3.29207.166 | Optional
Microsoft.Net. Component. 4.8. DeveloperTools | Narzędzia programistyczne .NET Framework 4,8 | 16.3.29230.54 | Optional
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3,5 | 16.0.28621.142 | Optional

## <a name="python-development"></a>Programowanie w języku Python

**#C1** Microsoft. VisualStudio. obciążeni. Python

**Opis:** Edytowanie, debugowanie, programowanie interaktywne i kontrola źródła dla języka Python.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.PythonTools | Obsługa języka Python | 16.0.28625.61 | Wymagane
Component.CPython3.x64 | Python 3 64-bit (3.7.4) | 3.7.4 | Zalecane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.826 | Zalecane
Microsoft.Component.PythonTools.Minicondax64 | Miniconda Python | 16.2.29003.222 | Zalecane
Microsoft.Component.PythonTools.Web | Obsługa sieci web w języku Python | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.3.29311.71 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.3.29207.166 | Zalecane
Microsoft. VisualStudio. Component. TypeScript. 3.6 | Zestaw SDK języka TypeScript 3,6 | 16.0.29207.166 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Zalecane
Component.CPython2.x64 | Python 2 64-bit (2.7.16) | 2.7.16 | Optional
Component.CPython2.x86 | Python 2 32-bit (2.7.16) | 2.7.16 | Optional
Component.CPython3.x86 | Python 3 32-bit (3.7.4) | 3.7.4 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 16.0.28714.129 | Optional
Component.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Optional
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Narzędzia do programowania natywnego języka Python | 16.2.29020.229 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Optional
Microsoft. NET. Component. 4.8. SDK | Zestaw .NET Framework 4,8 SDK | 16.3.29230.54 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.3.29207.166 | Optional
Microsoft. WebCore. Component. SDK | Zestaw SDK platformy .NET Core 3,0 | 16.3.29318.74 | Optional
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 16.1.28810.153 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.3.29230.54 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton | Podstawowe narzędzia usługi Azure Cloud Services | 16.3.29311.71 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do kompilacji usługi Azure Cloud Services | 16.3.29207.166 | Optional
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.3.29103.31 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla technologii DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 16.3.29230.54 | Optional
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik SQL Server ODBC | 16.0.28625.61 | Optional
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Optional
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | C++podstawowe funkcje | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania dla języka C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142-VS 2019 C++ x64/x86 Build Tools (v 14.23) | 16.3.29230.54 | Optional
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.3.29311.71 | Optional
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Zestaw SDK systemu Windows 10 (10.0.18362.0) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 16.3.29230.54 | Optional

## <a name="universal-windows-platform-development"></a>Opracowywanie zawartości dla platformy Windows Universal

**#C1** Microsoft. VisualStudio. obciążenia. Universal

**Opis:** Twórz aplikacje dla platforma uniwersalna systemu Windows przy użyciu C#, VB lub opcjonalnie C++.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | Architektura .NET Native | 16.0.28315.86 | Wymagane
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Wymagane
Microsoft. WebCore. Component. SDK | Zestaw SDK platformy .NET Core 3,0 | 16.3.29318.74 | Wymagane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 16.2.28917.182 | Wymagane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.Graphics | Obrazów i modeli 3W edytorów | 16.0.28517.75 | Wymagane
Microsoft. VisualStudio. Component. rozszerzenia intellicode | IntelliCode | 0.1 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Zestaw SDK systemu Windows 10 (10.0.18362.0) | 16.1.28829.92 | Wymagane
Microsoft. VisualStudio. Component. MSIX. pakowanie | Narzędzia do pakowania MSIX | 16.3.29230.54 | Wymagane
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | Architektura .NET native i .NET Standard | 16.3.29102.218 | Wymagane
Microsoft.VisualStudio.ComponentGroup.UWP.Support | Narzędzia platformy Windows uniwersalnej | 16.3.29311.71 | Wymagane
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Narzędzia platformy Windows uniwersalnej dla platformy Xamarin | 16.2.29020.229 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Optional
Microsoft. NET. Component. 4.8. SDK | Zestaw .NET Framework 4,8 SDK | 16.3.29230.54 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla technologii DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | C++Obsługa platforma uniwersalna systemu Windows narzędzi kompilacji v142 (ARM64) | 16.3.29207.166 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | C++podstawowe funkcje | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++Aktualizacja redystrybucyjna 2019 | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC v142-VS 2019 C++ ARM Build Tools (v 14.23) | 16.3.29230.54 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142-VS 2019 C++ arm64 Build Tools (v 14.23) | 16.3.29230.54 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142-VS 2019 C++ x64/x86 Build Tools (v 14.23) | 16.3.29230.54 | Optional
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC najnowsze 141-VS 2017 C++ ARM Build Tools (v 14.16) | 16.2.29003.222 | Optional
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC najnowsze 141-VS 2017 C++ arm64 Build Tools (v 14.16) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC najnowsze 141-VS 2017 C++ x64/x86 Build Tools (v 14.16) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | System Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | System Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Połączenie urządzenia USB | 16.2.29020.229 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | C++podstawowe funkcje pulpitu | 16.2.29012.281 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | C++(v142) Narzędzia platforma uniwersalna systemu Windows | 16.3.29207.166 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | C++Najnowsze 141 Narzędzia platforma uniwersalna systemu Windows | 16.1.28810.153 | Optional

## <a name="visual-studio-extension-development"></a>Programowanie rozszerzeń programu Visual Studio

**#C1** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Opis:** Twórz Dodatki i rozszerzenia dla programu Visual Studio, w tym nowe polecenia, analizatory kodu i okna narzędzi.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft. NET. Component. 4.8. SDK | Zestaw .NET Framework 4,8 SDK | 16.3.29230.54 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.3.29207.166 | Wymagane
Microsoft. VisualStudio. Component. rozszerzenia intellicode | IntelliCode | 0.1 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Visual Studio rozszerzenia wymagania wstępne dotyczące programowania | 16.3.29230.54 | Wymagane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 16.3.29207.166 | Zalecane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Zalecane
Microsoft.Component.CodeAnalysis.SDK | Zestaw SDK platformy kompilatora .NET | 16.2.29003.222 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 16.2.28917.182 | Optional
Microsoft.VisualStudio.Component.DslTools | Modeling SDK | 16.0.28315.86 | Optional

## <a name="unaffiliated-components"></a>Składniki nie podlega

Są to składniki, które nie są uwzględniane przy użyciu dowolnego obciążenia, ale można wybrać jako poszczególnych składników.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
Component.GitHub.VisualStudio | Rozszerzenie GitHub dla programu Visual Studio | 2.5.9.5485
Component.Xamarin.Inspector | Xamarin Inspector | 16.0.28315.86
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Component. Xamarin. skoroszyty | Xamarin Workbooks | 16.0.28315.86
Microsoft.Component.ClickOnce | Publikowania ClickOnce | 16.3.29311.71
Microsoft.Component.HelpViewer | Podgląd pomocy | 16.0.28625.61
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 16.3.29230.54
Microsoft.Net.Component.4.6.2.SDK | .NET framework 4.6.2 SDK | 16.3.29230.54
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 16.3.29230.54
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 16.3.29230.54
Microsoft.Net.Component.4.7.SDK | .NET framework 4.7 zestawu SDK | 16.3.29230.54
Microsoft.Net.Core.Component.SDK.2.2 | Środowisko uruchomieniowe programu .NET Core 2,2 | 16.3.29318.74
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programistyczne i .NET Core 2,1 | 16.3.29207.166
Microsoft.NetCore.ComponentGroup.Web.2.1 | Narzędzia programistyczne dla sieci Web i .NET Core 2,1 | 16.3.29207.166
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Integracja z usługą Azure DevOps Office | 16.0.28625.61
Microsoft.VisualStudio.Component.ClassDesigner | Projektant klas | 16.0.28528.71
Microsoft.VisualStudio.Component.DependencyValidation.Community | Weryfikacja zależności | 16.0.28517.75
Microsoft.VisualStudio.Component.Git | Git dla systemu Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.GraphDocument | Edytor DGML | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | LINQ to SQL Tools | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. 14.20. ARM | MSVC v142-VS 2019 C++ ARM Build Tools (v 14.20) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ARM. Spectre | MSVC v142-VS 2019 C++ ARM Spectre-libs (v 14.20) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ARM64 | MSVC v142-VS 2019 C++ arm64 Build Tools (v 14.20) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ARM64. Spectre | MSVC v142-VS 2019 C++ arm64 Spectre — skorygowane libs (v 14.20) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ATL | C++14.20 ATL dla narzędzi kompilacji v142 (x86 & x64) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ATL. ARM | C++14.20 ATL dla narzędzi kompilacji v142 (ARM) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ATL. ARM. Spectre | C++v 14.20 ATL dla narzędzi kompilacji v142 z ograniczeniami Spectre (ARM) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ATL. ARM64 | C++14.20 ATL dla narzędzi kompilacji v142 (ARM64) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ATL. ARM64. Spectre | C++14.20 ATL dla narzędzi kompilacji v142 z rozwiązaniami Spectre (ARM64) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. ATL. Spectre | C++v 14.20 ATL dla narzędzi kompilacji v142 z ograniczeniami Spectre (x86 & x64) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. CLI. Support | C++Obsługa/CLI dla narzędzi kompilacji v142 (14,20) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.20. MFC | C++v 14.20 MFC for v142 Build Tools (x86 & x64) | 16.2.29003.222
Microsoft. VisualStudio. Component. VC. 14.20. MFC. ARM | C++v 14.20 MFC for v142 Build Tools (ARM) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. MFC. ARM. Spectre | C++v 14.20 MFC dla narzędzi kompilacji v142 z ograniczeniami Spectre (ARM) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. MFC. ARM64 | C++v 14.20 MFC for v142 Build Tools (ARM64) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. MFC. ARM64. Spectre | C++v 14.20 MFC dla narzędzi kompilacji v142 z ograniczeniami Spectre (ARM64) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. MFC. Spectre | C++v 14.20 MFC dla narzędzi kompilacji v142 z ograniczeniami Spectre (x86 & x64) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. x86. x64 | MSVC v142-VS 2019 C++ x64/x86 Build Tools (v 14.20) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.20. x86. x64. Spectre | MSVC v142-VS 2019 C++ x64/x86 Spectre-libs (v 14.20) | 16.1.28829.92
Microsoft. VisualStudio. Component. VC. 14.21. ARM | MSVC v142-VS 2019 C++ ARM Build Tools (v 14.21) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.21. ARM. Spectre | MSVC v142-VS 2019 C++ ARM Spectre-libs (v 14.21) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.21. ARM64 | MSVC v142-VS 2019 C++ arm64 Build Tools (v 14.21) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.21. ARM64. Spectre | MSVC v142-VS 2019 C++ arm64 Spectre — skorygowane libs (v 14.21) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.21. ATL | C++14.21 ATL dla narzędzi kompilacji v142 (x86 & x64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. ATL. ARM | C++14.21 ATL dla narzędzi kompilacji v142 (ARM) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. ATL. ARM. Spectre | C++v 14.21 ATL dla narzędzi kompilacji v142 z ograniczeniami Spectre (ARM) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. ATL. ARM64 | C++14.21 ATL dla narzędzi kompilacji v142 (ARM64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. ATL. ARM64. Spectre | C++14.21 ATL dla narzędzi kompilacji v142 z rozwiązaniami Spectre (ARM64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. ATL. Spectre | C++v 14.21 ATL dla narzędzi kompilacji v142 z ograniczeniami Spectre (x86 & x64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. CLI. Support | C++Obsługa/CLI dla narzędzi kompilacji v142 (14,21) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.21. MFC | C++v 14.21 MFC for v142 Build Tools (x86 & x64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. MFC. ARM | C++v 14.21 MFC for v142 Build Tools (ARM) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. MFC. ARM. Spectre | C++v 14.21 MFC dla narzędzi kompilacji v142 z ograniczeniami Spectre (ARM) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. MFC. ARM64 | C++v 14.21 MFC for v142 Build Tools (ARM64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. MFC. ARM64. Spectre | C++v 14.21 MFC dla narzędzi kompilacji v142 z ograniczeniami Spectre (ARM64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. MFC. Spectre | C++v 14.21 MFC dla narzędzi kompilacji v142 z ograniczeniami Spectre (x86 & x64) | 16.2.29019.55
Microsoft. VisualStudio. Component. VC. 14.21. x86. x64 | MSVC v142-VS 2019 C++ x64/x86 Build Tools (v 14.21) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.21. x86. x64. Spectre | MSVC v142-VS 2019 C++ x64/x86 Spectre-libs (v 14.21) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. 14.22. ARM | MSVC v142-VS 2019 C++ ARM Build Tools (v 14.22) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ARM. Spectre | MSVC v142-VS 2019 C++ ARM Spectre-libs (v 14.22) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ARM64 | MSVC v142-VS 2019 C++ arm64 Build Tools (v 14.22) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ARM64. Spectre | MSVC v142-VS 2019 C++ arm64 Spectre — skorygowane libs (v 14.22) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ATL | C++14.22 ATL dla narzędzi kompilacji v142 (x86 & x64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ATL. ARM | C++14.22 ATL dla narzędzi kompilacji v142 (ARM) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ATL. ARM. Spectre | C++v 14.22 ATL dla narzędzi kompilacji v142 z ograniczeniami Spectre (ARM) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ATL. ARM64 | C++14.22 ATL dla narzędzi kompilacji v142 (ARM64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ATL. ARM64. Spectre | C++14.22 ATL dla narzędzi kompilacji v142 z rozwiązaniami Spectre (ARM64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. ATL. Spectre | C++v 14.22 ATL dla narzędzi kompilacji v142 z ograniczeniami Spectre (x86 & x64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. CLI. Support | C++Obsługa/CLI dla narzędzi kompilacji v142 (14,22) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. MFC | C++v 14.22 MFC for v142 Build Tools (x86 & x64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM | C++v 14.22 MFC for v142 Build Tools (ARM) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM. Spectre | C++v 14.22 MFC dla narzędzi kompilacji v142 z ograniczeniami Spectre (ARM) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM64 | C++v 14.22 MFC for v142 Build Tools (ARM64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM64. Spectre | C++v 14.22 MFC dla narzędzi kompilacji v142 z ograniczeniami Spectre (ARM64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. MFC. Spectre | C++v 14.22 MFC dla narzędzi kompilacji v142 z ograniczeniami Spectre (x86 & x64) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. x86. x64 | MSVC v142-VS 2019 C++ x64/x86 Build Tools (v 14.22) | 16.3.29230.54
Microsoft. VisualStudio. Component. VC. 14.22. x86. x64. Spectre | MSVC v142-VS 2019 C++ x64/x86 Spectre-libs (v 14.22) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.ATL.ARM | C++ATL dla najnowszych narzędzi kompilacji v142 (ARM) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | C++ATL dla najnowszych narzędzi kompilacji v142 z ograniczeniami Spectre (ARM) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | C++ATL dla najnowszych narzędzi kompilacji v142 (ARM64) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | C++ATL dla najnowszych narzędzi kompilacji v142 z ograniczeniami Spectre (ARM64) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.ATL.Spectre | C++ATL dla najnowszych narzędzi kompilacji v142 z ograniczeniami Spectre (x86 & x64) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | C++MFC dla najnowszych narzędzi kompilacji v142 z ograniczeniami Spectre (x86 & x64) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.MFC.ARM | C++MFC dla najnowszych narzędzi kompilacji v142 (ARM) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | C++MFC dla najnowszych narzędzi kompilacji v142 z ograniczeniami Spectre (ARM) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | C++MFC dla najnowszych narzędzi kompilacji v142 (ARM64) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | C++MFC dla najnowszych narzędzi kompilacji v142 z ograniczeniami Spectre (ARM64) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.Redist.MSM | C++2019 redystrybucyjny MSMs | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC v142-VS 2019 C++ ARM Spectre-libs (v 14.23) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC v142-VS 2019 C++ arm64 Spectre — skorygowane libs (v 14.23) | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC v142-VS 2019 C++ x64/x86 Spectre-libs (v 14.23)  | 16.3.29230.54
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC najnowsze 141-VS 2017 C++ ARM Spectre-libs (v 14.16) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC najnowsze 141-VS 2017 C++ arm64 Spectre — skorygowane libs (v 14.16) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.v141.ATL | C++Narzędzia do kompilacji ATL for najnowsze 141 (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | C++Narzędzia do kompilacji ATL for najnowsze 141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | C++Narzędzia do kompilacji ATL for najnowsze 141 z ograniczeniami Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | C++ATL for najnowsze 141 Build Tools (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | C++Narzędzia do kompilacji ATL for najnowsze 141 z ograniczeniami Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | C++Narzędzia do kompilacji ATL for najnowsze 141 z ograniczeniami Spectre (x86 & x64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. najnowsze 141. CLI. Support | C++Obsługa/CLI dla narzędzi kompilacji najnowsze 141 (14,16) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.v141.MFC | C++MFC for najnowsze 141 Build Tools (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | C++MFC for najnowsze 141 Build Tools (ARM) | 16.2.28915.88
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | C++MFC dla narzędzi kompilacji najnowsze 141 z ograniczeniami Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | C++MFC for najnowsze 141 Build Tools (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | C++MFC dla narzędzi kompilacji najnowsze 141 z ograniczeniami Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | C++MFC dla narzędzi kompilacji najnowsze 141 z ograniczeniami Spectre (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC najnowsze 141-VS 2017 C++ x64/x86 Spectre-libs (v 14.16) | 16.1.28829.92
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | C++Obsługa systemu Windows XP dla narzędzi VS 2017 (najnowsze 141) [przestarzałe] | 16.1.28811.260
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.1.28810.153
