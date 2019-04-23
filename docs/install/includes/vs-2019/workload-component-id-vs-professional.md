---
title: Visual Studio Professional 2019 obciążeń i składników identyfikatorów
titleSuffix: ''
description: Użyj obciążenia i identyfikatory składników, aby zainstalować program Visual Studio przy użyciu wiersza polecenia lub określić jako zależności w manifestu VSIX
keywords: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 04/02/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 23cbd90b81bcc05fef34040b4934c7152f79ae41
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118783"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-professional-2019"></a>Edytor Visual Studio core (dołączone do programu Visual Studio Professional 2019)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Opis:** Visual Studio podstawowe funkcje powłoki, w tym kodu uwzględniającej składnię, edycji i kontroli kodu źródłowego i zarządzanie elementami roboczymi.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Edytor rdzeni programu Visual Studio | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Program Visual Studio uruchomić stronę dla użytkowników języka C++ | 16.0.28315.86 | Optional

## <a name="azure-development"></a>Programowanie na platformie Azure

**ID:** Microsoft.VisualStudio.Workload.Azure

**Opis:** Zestawy SDK platformy Azure, narzędzia i projekty do tworzenia aplikacji w chmurze obsługuje tworzenie zasobów i kompilowania kontenerów platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 16.0.28714.129 | Wymagane
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs Tools | 16.0.28714.129 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.0.28516.191 | Wymagane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28621.142 | Wymagane
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28516.191 | Wymagane
Microsoft.NetCore.ComponentGroup.Web.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 16.0.28720.110 | Wymagane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.FSharp | F#Obsługa języków | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#Obsługa języka dla projektów sieci web | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik ODBC SQL Server | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.3 | TypeScript 3.3 zestawu SDK | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Wymagania wstępne dotyczące programowania dla platformy Azure | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs Tools | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Wymagane
Microsoft.Component.Azure.DataLake.Tools | Usługa Azure Data Lake i Stream Analytics Tools | 16.0.28720.110 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 16.0.28516.191 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane funkcje platformy ASP.NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Visual Studio Tools for Kubernetes | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Podstawowe narzędzia usługi Azure Resource Manager | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Narzędzia usługi Service Fabric | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton | Podstawowe narzędzia usługi Azure Cloud Services | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do kompilacji usługi Azure Cloud Services | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Narzędzia usług w chmurze platformy Azure | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Narzędzia usługi Azure Resource Manager | 16.0.28528.71 | Zalecane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET framework 4.6.2 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | .NET framework 4.7 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.6.1 | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET framework 4.6.2 Developer tools | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia deweloperskie platformy .NET framework 4.7.1 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7 | 16.0.28516.191 | Optional
Microsoft.Net.Core.Component.SDK.2.2 | Narzędzia programistyczne programu .NET core 2.2 | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Narzędzia programistyczne programu .NET core 2.2 | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.Web.2.2 | Narzędzia programistyczne programu .NET core 2.2 | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Usługa Azure Storage, narzędzia AzCopy | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional

## <a name="data-storage-and-processing"></a>Magazynowanie i przetwarzanie danych

**ID:** Microsoft.VisualStudio.Workload.Data

**Opis:** Łączenie, opracowywanie i testowanie rozwiązań danych przy użyciu programu SQL Server, usługa Azure Data Lake lub usługi Hadoop.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 16.0.28714.129 | Zalecane
Component.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Zalecane
Microsoft.Component.Azure.DataLake.Tools | Usługa Azure Data Lake i Stream Analytics Tools | 16.0.28720.110 | Zalecane
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.0.28516.191 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 16.0.28516.191 | Zalecane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28621.142 | Zalecane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 16.0.28720.110 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton | Podstawowe narzędzia usługi Azure Cloud Services | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do kompilacji usługi Azure Cloud Services | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 16.0.28621.142 | Zalecane
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik ODBC SQL Server | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.TypeScript.3.3 | TypeScript 3.3 zestawu SDK | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 16.0.28621.142 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Zalecane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.FSharp.Desktop | F#Obsługa pulpitu języka | 16.0.28315.86 | Optional

## <a name="data-science-and-analytical-applications"></a>Aplikacje do analizy i przetwarzania danych

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Opis:** Języki i narzędzia do tworzenia aplikacji do analizy danych, w tym języka Python i F#.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.PythonTools | Obsługa języka Python | 16.0.28625.61 | Zalecane
Microsoft.Component.PythonTools.Minicondax64 | Python, miniconda | 16.0.28625.61 | Zalecane
Microsoft.Component.PythonTools.Web | Obsługa sieci web w języku Python | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.FSharp.Desktop | F#Obsługa pulpitu języka | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.TypeScript.3.3 | TypeScript 3.3 zestawu SDK | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Zalecane
Microsoft.Component.VC.Runtime.UCRTSDK | Zestawu Windows Universal CRT SDK | 16.0.28625.61 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Narzędzia do programowania natywnego języka Python | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla technologii DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.140 | W wersji 140 MSVC — VS 2015 C++ narzędzia build tools (14.00) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania dla języka C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | V142 MSVC — narzędzia do kompilacji x64/x86 VS 2019 C++ (v14.20) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | System Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Optional

## <a name="net-desktop-development"></a>Programowanie aplikacji klasycznych dla platformy .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Opis:** Tworzenie WPF, Windows Forms i aplikacji konsolowych przy użyciu C#, Visual Basic i F#.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.0.28516.191 | Wymagane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Narzędzia programistyczne dla platformy .NET | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Wymagane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Zalecane
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 16.0.28516.191 | Zalecane
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger Just In Time | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 tools | 16.0.28315.86 | Zalecane
Component.Dotfuscator | Ochrona preEmptive — Dotfuscator | 16.0.28528.71 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 16.0.28714.129 | Optional
Component.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Optional
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET framework 4.6.2 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | .NET framework 4.7 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.6.1 | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET framework 4.6.2 Developer tools | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia deweloperskie platformy .NET framework 4.7.1 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7 | 16.0.28516.191 | Optional
Microsoft.Net.Core.Component.SDK.2.2 | Narzędzia programistyczne programu .NET core 2.2 | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Narzędzia programistyczne programu .NET core 2.2 | 16.0.28516.191 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.FSharp | F#Obsługa języków | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.FSharp.Desktop | F#Obsługa pulpitu języka | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik ODBC SQL Server | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Optional
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.TypeScript.3.3 | TypeScript 3.3 zestawu SDK | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 16.0.28517.75 | Optional
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Optional

## <a name="game-development-with-unity"></a>Programowanie gier za pomocą aparatu Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Opis:** Twórz gry 2D i 3D za pomocą aparatu Unity, zaawansowane Międzyplatformowe środowisko programistyczne.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Narzędzia programistyczne programu .NET framework 3.5 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Unity | Narzędzia Visual Studio Tools for Unity | 16.0.28315.86 | Wymagane
Component.UnityEngine.x64 | Edytor 64-bitowych 2018.3 aparatu Unity | 16.0.28707.178 | Zalecane
Component.UnityEngine.x86 | Unity 5.6 32-bitowych edytora | 16.0.28707.178 | Zalecane

## <a name="linux-development-with-c"></a>Programowanie dla systemu Linux przy użyciu języka C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Opis:** Twórz i Debuguj aplikacje działające w środowisku systemu Linux.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.MDD.Linux | Programowanie dla systemu Linux w języku C++ | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje C++ | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.0.28315.86 | Wymagane
Component.Linux.CMake | Narzędzia C++ CMake dla systemu Linux | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | V142 MSVC — narzędzia do kompilacji x64/x86 VS 2019 C++ (v14.20) | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.17763 | System Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Zalecane
Component.MDD.Linux.GCC.arm | Osadzone i narzędzia programistyczne IoT | 16.0.28625.61 | Optional

## <a name="desktop-development-with-c"></a>Programowanie aplikacji klasycznych w języku C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Opis:** Twórz aplikacje pulpitu Windows przy użyciu zestawu narzędzi Microsoft C++, ATL lub MFC.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje C++ | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Pakiet redystrybucyjny Update C++ 2019 | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Visual C++ podstawowe funkcje języka | 16.0.28315.86 | Wymagane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Zalecane
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger Just In Time | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla technologii DirectX | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.VC.ATL | C++ ATL dla narzędzia do kompilacji v142 (x86 & x64) | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.VC.CMake.Project | Narzędzia C++ CMake dla Windows | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania dla języka C++ | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Rozszerzenia test Adapter for Boost.Test | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Test Adapter for Google Test | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | V142 MSVC — narzędzia do kompilacji x64/x86 VS 2019 C++ (v14.20) | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.17763 | System Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Zalecane
Component.Incredibuild | IncrediBuild — przyspieszanie kompilacji | 16.0.28528.71 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.3 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Zestawu Windows Universal CRT SDK | 16.0.28625.61 | Optional
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.VC.140 | W wersji 140 MSVC — VS 2015 C++ narzędzia build tools (14.00) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | C++ MFC dla narzędzia do kompilacji v142 (x86 & x64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/ Obsługę interfejsu wiersza polecenia dla narzędzia do kompilacji v142 | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduły języka C++ dla v142 narzędzia build tools (x64/x86 — wersja eksperymentalna) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | Wersji 141 MSVC — narzędzia do kompilacji x64/x86 programu VS 2017 C++ (v14.16) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | System Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Optional

## <a name="game-development-with-c"></a>Programowanie gier w języku C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Opis:** Użyj pełnych możliwości języka C++, aby tworzyć profesjonalne gry obsługiwane przez program DirectX, Unreal i Cocos2d.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje C++ | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Pakiet redystrybucyjny Update C++ 2019 | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | V142 MSVC — narzędzia do kompilacji x64/x86 VS 2019 C++ (v14.20) | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla technologii DirectX | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania dla języka C++ | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.17763 | System Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Zalecane
Component.Android.NDK.R16B | Android NDK (R16B) | 16.0.28728.38 | Optional
Component.Android.SDK25.Private | Instalacja zestawu android SDK (poziom interfejsu API 25) (lokalna instalacja na potrzeby opracowywania aplikacji mobilnych przy użyciu języka C++) | 16.0.28625.61 | Optional
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Optional
Component.Cocos | Cocos | 16.0.28315.86 | Optional
Component.Incredibuild | IncrediBuild — przyspieszanie kompilacji | 16.0.28528.71 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.3 | Optional
Component.MDD.Android | Narzędzia programistyczne C++ Android | 16.0.28517.75 | Optional
Component.OpenJDK | OpenJDK (dystrybucja firmy Microsoft) | 16.0.28625.61 | Optional
Component.Unreal | Instalator aparatu unreal Engine | 16.0.28625.61 | Optional
Component.Unreal.Android | Obsługa systemu android środowisko IDE dla aparatu Unreal engine | 16.0.28625.61 | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 16.0.28516.191 | Optional
Microsoft.VisualStudio.Component.NuGet.BuildTools | Elementy docelowe i zadania kompilacji NuGet | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | System Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Optional

## <a name="mobile-development-with-c"></a>Tworzenie aplikacji mobilnych w języku C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Opis:** Twórz aplikacje Międzyplatformowe dla systemów iOS, Android lub Windows przy użyciu języka C++.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Android.SDK25.Private | Instalacja zestawu android SDK (poziom interfejsu API 25) (lokalna instalacja na potrzeby opracowywania aplikacji mobilnych przy użyciu języka C++) | 16.0.28625.61 | Wymagane
Component.OpenJDK | OpenJDK (dystrybucja firmy Microsoft) | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje C++ | 16.0.28625.61 | Wymagane
Component.Android.NDK.R16B | Android NDK (R16B) | 16.0.28728.38 | Zalecane
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Zalecane
Component.MDD.Android | Narzędzia programistyczne C++ Android | 16.0.28517.75 | Zalecane
Component.Android.NDK.R16B_3264 | Android NDK (R16B) (32bit) | 16.0.28728.38 | Optional
Component.Google.Android.Emulator.API25.Private | Emulator systemu Google Android (interfejs API poziom 25) (instalacja lokalna) | 16.0.28625.61 | Optional
Component.HAXM.Private | Intel Hardware Accelerated Execution Menedżera (HAXM) (instalacja lokalna) | 16.0.28528.71 | Optional
Component.Incredibuild | IncrediBuild — przyspieszanie kompilacji | 16.0.28528.71 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.3 | Optional
Component.MDD.IOS | Narzędzia programistyczne dla systemu iOS C++ | 16.0.28517.75 | Optional

## <a name="net-core-cross-platform-development"></a>Programowanie dla wielu platform .NET core

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Opis:** Twórz aplikacje dla wielu platform przy użyciu platformy .NET Core, ASP.NET Core, HTML/JavaScript i kontenerów, w tym obsługę platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 16.0.28714.129 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.0.28516.191 | Wymagane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28621.142 | Wymagane
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28516.191 | Wymagane
Microsoft.NetCore.ComponentGroup.Web.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.FSharp | F#Obsługa języków | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#Obsługa języka dla projektów sieci web | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik ODBC SQL Server | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.3 | TypeScript 3.3 zestawu SDK | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Wymagane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Zalecane
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs Tools | 16.0.28714.129 | Zalecane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 16.0.28720.110 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs Tools | 16.0.28621.142 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Narzędzia do tworzenia aplikacji internetowych w chmurze | 16.0.28621.142 | Zalecane
Microsoft.Net.Core.Component.SDK.2.2 | Narzędzia programistyczne programu .NET core 2.2 | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Narzędzia programistyczne programu .NET core 2.2 | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.Web.2.2 | Narzędzia programistyczne programu .NET core 2.2 | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Obsługa usług IIS w czasie opracowywania | 16.0.28315.86 | Optional

## <a name="mobile-development-with-net"></a>Tworzenie aplikacji mobilnych przy użyciu platformy .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Opis:** Twórz aplikacje Międzyplatformowe dla systemów iOS, Android i Windows za pomocą platformy Xamarin.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Xamarin | Xamarin | 16.0.28625.61 | Wymagane
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 16.0.28315.86 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.0.28516.191 | Wymagane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28621.142 | Wymagane
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28516.191 | Wymagane
Microsoft.VisualStudio.Component.FSharp | F#Obsługa języków | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.Merq | Wspólne narzędzia wewnętrzne platformy Xamarin | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.MonoDebugger | Debuger środowiska mono | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Aparat szablonów ASP.NET | 16.0.28315.86 | Wymagane
Component.Android.SDK27 | Instalacja zestawu android SDK (poziom 27 interfejsu API) | 16.0.28517.75 | Zalecane
Component.OpenJDK | OpenJDK (dystrybucja firmy Microsoft) | 16.0.28625.61 | Zalecane

## <a name="aspnet-and-web-development"></a>ASP.NET i tworzenie aplikacji internetowych

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Opis:** Twórz aplikacje sieci web za pomocą programu ASP.NET, ASP.NET Core, HTML/JavaScript i kontenerów, w tym obsługę platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 16.0.28714.129 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.0.28516.191 | Wymagane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28621.142 | Wymagane
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28516.191 | Wymagane
Microsoft.NetCore.ComponentGroup.Web.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.FSharp | F#Obsługa języków | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#Obsługa języka dla projektów sieci web | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik ODBC SQL Server | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.3 | TypeScript 3.3 zestawu SDK | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Wymagane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Zalecane
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs Tools | 16.0.28714.129 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 16.0.28516.191 | Zalecane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane funkcje platformy ASP.NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 16.0.28720.110 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 tools | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs Tools | 16.0.28621.142 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Narzędzia do tworzenia aplikacji internetowych w chmurze | 16.0.28621.142 | Zalecane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET framework 4.6.2 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | .NET framework 4.7 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.6.1 | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET framework 4.6.2 Developer tools | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia deweloperskie platformy .NET framework 4.7.1 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7 | 16.0.28516.191 | Optional
Microsoft.Net.Core.Component.SDK.2.2 | Narzędzia programistyczne programu .NET core 2.2 | 16.0.28621.142 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Narzędzia programistyczne programu .NET core 2.2 | 16.0.28516.191 | Optional
Microsoft.NetCore.ComponentGroup.Web.2.2 | Narzędzia programistyczne programu .NET core 2.2 | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Szablony projektów dodatkowe (poprzednie wersje) | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Obsługa usług IIS w czasie opracowywania | 16.0.28315.86 | Optional

## <a name="nodejs-development"></a>Tworzenia aplikacji node.js

**ID:** Microsoft.VisualStudio.Workload.Node

**Opis:** Tworzenie skalowalnych aplikacji sieciowych przy użyciu platformy Node.js i asynchronicznego oparte na zdarzeniach środowiska uruchomieniowego JavaScript. 

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Node.Tools | Narzędzia programistyczne środowiska node.js | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.3 | TypeScript 3.3 zestawu SDK | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Wymagane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | V142 MSVC — narzędzia do kompilacji x64/x86 VS 2019 C++ (v14.20) | 16.0.28625.61 | Optional

## <a name="officesharepoint-development"></a>Programowanie Office/SharePoint

**ID:** Microsoft.VisualStudio.Workload.Office

**Opis:** Tworzenie dodatków narzędzi VSTO za pomocą pakietu Office i programu SharePoint dodatków oraz rozwiązań programu SharePoint C#, VB i JavaScript.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 16.0.28714.129 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.0.28516.191 | Wymagane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Narzędzia programistyczne dla platformy .NET | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik ODBC SQL Server | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.3 | TypeScript 3.3 zestawu SDK | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools dla pakietu Office (VSTO) | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET framework 4.6.2 SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.SDK | .NET framework 4.7 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.6.1 | 16.0.28621.142 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET framework 4.6.2 Developer tools | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia deweloperskie platformy .NET framework 4.7.1 | 16.0.28516.191 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne programu .NET framework 4.7 | 16.0.28516.191 | Optional
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | Optional

## <a name="python-development"></a>Programowanie w języku Python

**ID:** Microsoft.VisualStudio.Workload.Python

**Opis:** Edytowanie, debugowanie, opracowywanie interakcyjne oraz kontrola źródła dla języka Python.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.PythonTools | Obsługa języka Python | 16.0.28625.61 | Wymagane
Component.CPython3.x64 | Python 3 64-bitowy (3.7.2) | 3.7.2 | Zalecane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.12 | Zalecane
Microsoft.Component.PythonTools.Minicondax64 | Python, miniconda | 16.0.28625.61 | Zalecane
Microsoft.Component.PythonTools.Web | Obsługa sieci web w języku Python | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.TypeScript.3.3 | TypeScript 3.3 zestawu SDK | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Zalecane
Component.CPython2.x64 | Python 2 64-bitowa (2.7.15) | 2.7.15 | Optional
Component.CPython2.x86 | Python 2 32-bitowa (2.7.15) | 2.7.15 | Optional
Component.CPython3.x86 | Python 3 32-bitowy (3.7.2) | 3.7.2 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 16.0.28714.129 | Optional
Component.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Optional
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Zestawu Windows Universal CRT SDK | 16.0.28625.61 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Narzędzia do programowania natywnego języka Python | 16.0.28621.142 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.0.28516.191 | Optional
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 16.0.28720.110 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton | Podstawowe narzędzia usługi Azure Cloud Services | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do kompilacji usługi Azure Cloud Services | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla technologii DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 16.0.28621.142 | Optional
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik ODBC SQL Server | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Optional
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.140 | W wersji 140 MSVC — VS 2015 C++ narzędzia build tools (14.00) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania dla języka C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | V142 MSVC — narzędzia do kompilacji x64/x86 VS 2019 C++ (v14.20) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | System Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 16.0.28621.142 | Optional

## <a name="universal-windows-platform-development"></a>Opracowywanie zawartości dla platformy Windows Universal

**ID:** Microsoft.VisualStudio.Workload.Universal

**Opis:** Tworzenie aplikacji uniwersalnych platformy Windows za pomocą C#, VB lub opcjonalnie C++.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | Architektura .NET Native | 16.0.28315.86 | Wymagane
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 16.0.28517.75 | Wymagane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Graphics | Obrazów i modeli 3W edytorów | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.3 | TypeScript 3.3 zestawu SDK | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK.17763 | System Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | Architektura .NET native i .NET Standard | 16.0.28516.191 | Wymagane
Microsoft.VisualStudio.ComponentGroup.UWP.Support | Narzędzia platformy Windows uniwersalnej | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Narzędzia platformy Windows uniwersalnej dla platformy Xamarin | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 16.0.28621.142 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Optional
Microsoft.Component.VC.Runtime.OSSupport | Środowisko wykonawcze C++ Universal Windows Platform, dla narzędzia do kompilacji v142 | 16.0.28625.61 | Optional
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla technologii DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Obsługa języka C++ Universal Windows Platform v142 narzędzia kompilacji (ARM64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Pakiet redystrybucyjny Update C++ 2019 | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | V142 MSVC — VS 2019 C++ ARM (v14.20) narzędzia do kompilacji | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | V142 MSVC — VS 2019 C++ ARM64 narzędzia build tools (v14.20) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | V142 MSVC — narzędzia do kompilacji x64/x86 VS 2019 C++ (v14.20) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.v141.ARM | Wersji 141 MSVC — narzędzia (v14.16) kompilacji programu VS 2017 C++ ARM | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.v141.ARM64 | Narzędzia wersji 141 MSVC — ARM64 C++ programu VS 2017 build tools (v14.16) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | Wersji 141 MSVC — narzędzia do kompilacji x64/x86 programu VS 2017 C++ (v14.16) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | System Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Połączenie urządzenia USB | 16.0.28320.51 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Visual C++ podstawowe funkcje języka | 16.0.28315.86 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Narzędzia platformy uniwersalnej Windows C++ (v142) | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | Narzędzia platformy uniwersalnej Windows C++ (w wersji 141) | 16.0.28621.142 | Optional

## <a name="visual-studio-extension-development"></a>Programowanie rozszerzeń programu Visual Studio

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Opis:** Twórz dodatki i rozszerzenia dla programu Visual Studio, w tym nowe polecenia, analizatory kodu i okna narzędzi.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.SDK | .NET framework 4.7.2 zestawu SDK | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET framework 4.7.2 targeting pack | 16.0.28517.75 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.7.2 | 16.0.28516.191 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Visual Studio rozszerzenia wymagania wstępne dotyczące programowania | 16.0.28621.142 | Wymagane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 16.0.28625.61 | Zalecane
Component.Dotfuscator | Ochrona preEmptive — Dotfuscator | 16.0.28528.71 | Optional
Microsoft.Component.CodeAnalysis.SDK | Zestaw SDK platformy kompilatora .NET | 16.0.28625.61 | Optional
Microsoft.Component.VC.Runtime.OSSupport | Środowisko wykonawcze C++ Universal Windows Platform, dla narzędzia do kompilacji v142 | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Projektant klas | 16.0.28528.71 | Optional
Microsoft.VisualStudio.Component.DslTools | Modeling SDK | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.VC.ATL | C++ ATL dla narzędzia do kompilacji v142 (x86 & x64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | C++ MFC dla narzędzia do kompilacji v142 (x86 & x64) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje C++ | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | V142 MSVC — narzędzia do kompilacji x64/x86 VS 2019 C++ (v14.20) | 16.0.28625.61 | Optional

## <a name="unaffiliated-components"></a>Składniki nie podlega

Są to składniki, które nie są uwzględniane przy użyciu dowolnego obciążenia, ale można wybrać jako poszczególnych składników.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
Component.GitHub.VisualStudio | Rozszerzenie GitHub dla programu Visual Studio | 2.5.9.5485
Component.Xamarin.Inspector | Xamarin Inspector | 16.0.28315.86
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Component.Xamarin.Workbooks | Xamarin Workbooks | 16.0.28315.86
Microsoft.Component.ClickOnce | Publikowania ClickOnce | 16.0.28707.177
Microsoft.Component.HelpViewer | Podgląd pomocy | 16.0.28625.61
Microsoft.NetCore.1x.ComponentGroup.Web | .NET core 1.0 – 1.1 narzędzi programistycznych dla sieci Web | 16.0.28621.142
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Integracja z usługą Azure DevOps Office | 16.0.28625.61
Microsoft.VisualStudio.Component.DependencyValidation.Community | Weryfikacja zależności | 16.0.28517.75
Microsoft.VisualStudio.Component.Git | Git dla systemu Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.GraphDocument | Edytor DGML | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | Narzędzi LINQ to SQL | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM | C++ ATL dla narzędzia do kompilacji v142 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | C++ ATL dla narzędzia do kompilacji v142 z krokami zaradczymi dla luki Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | C++ ATL dla narzędzia do kompilacji v142 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | C++ ATL dla v142 narzędzia build tools z krokami zaradczymi dla luki Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.Spectre | C++ ATL dla narzędzia do kompilacji v142 z krokami zaradczymi dla luki Spectre (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | C++ MFC dla narzędzia do kompilacji v142 z krokami zaradczymi dla luki Spectre (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM | C++ MFC dla narzędzia do kompilacji v142 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | C++ MFC dla narzędzia do kompilacji v142 z krokami zaradczymi dla luki Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | C++ MFC dla narzędzia do kompilacji v142 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | C++ MFC dla v142 narzędzia build tools z krokami zaradczymi dla luki Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Redist.MSM | Pakiet redystrybucyjny MSMs C++ 2019 | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | V142 MSVC — skorygowane VS 2019 C++ ARM Spectre libs (v14.20) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | V142 MSVC — skorygowane VS 2019 C++ ARM64 Spectre libs (v14.20) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | V142 MSVC — VS 2019 C++ x64/x86 skorygowane z krokami zaradczymi dla luki libs (v14.20)  | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | Wersji 141 MSVC — skorygowane z krokami zaradczymi dla luki programu VS 2017 C++ ARM libs (v14.16) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | Wersji 141 MSVC — skorygowane z krokami zaradczymi dla luki programu VS 2017 C++ ARM64 libs (v14.16) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL | C++ ATL dla narzędzia do kompilacji wersji 141 (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | C++ ATL dla narzędzia kompilacji w wersji 141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | C++ ATL dla narzędzia kompilacji w wersji 141 z krokami zaradczymi dla luki Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | C++ ATL dla narzędzia kompilacji w wersji 141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | C++ ATL dla wersji 141 narzędzia build tools z krokami zaradczymi dla luki Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | C++ ATL dla narzędzia kompilacji w wersji 141 z krokami zaradczymi dla luki Spectre (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | C++/ Obsługę interfejsu wiersza polecenia dla narzędzia kompilacji w wersji 141 | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC | C++ MFC dla narzędzia do kompilacji wersji 141 (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | C++ MFC dla narzędzia kompilacji w wersji 141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | C++ MFC dla narzędzia kompilacji w wersji 141 z krokami zaradczymi dla luki Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | C++ MFC dla narzędzia kompilacji w wersji 141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | C++ MFC dla wersji 141 narzędzia build tools z krokami zaradczymi dla luki Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | C++ MFC dla narzędzia kompilacji w wersji 141 z krokami zaradczymi dla luki Spectre (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | Wersji 141 MSVC — programu VS 2017 C++ x64/x86 skorygowane z krokami zaradczymi dla luki libs (v14.16) | 16.0.28625.61
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | C++Windows XP obsługę narzędzi programu VS 2017 (w wersji 141) [przestarzałe] | 16.0.28625.61
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.0.28621.142
