---
title: Visual Studio Community 2019 i identyfikatory składników
titleSuffix: ''
description: Użyj identyfikatorów obciążeń i składników, aby Visual Studio za pomocą wiersza polecenia lub określić jako zależność w manifeście VSIX
keywords: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.date: 05/24/2021
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 539b6a1d614bc0e3e7d61a14debcf14a495013a9
ms.sourcegitcommit: 18e7300d4878f2fcd0263a4aff31a755ae8fc289
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2021
ms.locfileid: "110449763"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-community-2019"></a>Visual Studio podstawowy (dołączony do Visual Studio Community 2019 r.)

**Identyfikator:** Microsoft.VisualStudio.Workload.CoreEditor

**Opis:** Środowisko Visual Studio, w tym edytowanie kodu uwzględniające składnię, kontrolę kodu źródłowego i zarządzanie elementami pracy.

### <a name="components-included-by-this-workload"></a>Składniki dołączone do tego obciążenia

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio edytora podstawowego | 16.1.28811.260 | Wymagane
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Visual Studio startowa dla użytkowników języka C++ | 16.0.28315.86 | Opcjonalne

## <a name="azure-development"></a>Tworzenie aplikacji na platformie Azure

**Identyfikator:** Microsoft.VisualStudio.Workload.Azure

**Opis:** Zestawy SDK platformy Azure, narzędzia i projekty do tworzenia aplikacji w chmurze i tworzenia zasobów przy użyciu platformy .NET i .NET Framework. Zawiera również narzędzia do konteneryzowania aplikacji, w tym obsługę platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki dołączone do tego obciążenia

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi językowe Razor | 16.10.31205.252 | Wymagane
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs narzędzi | 16.10.31205.252 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 16.10.31205.180 | Wymagane
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Podgląd internetowy na żywo | 0.7.22.39845 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagane
Microsoft.ComponentGroup.ClickOnce.Publish | Publikowanie ClickOnce dla .NET  | 16.10.31303.231 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework docelowy 4.6.1 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework docelowych w pakiecie 4.7.2 | 16.10.31205.252 | Wymagane
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 | 16.3.29207.166 | Wymagane
Microsoft.NetCore.Component.DevelopmentTools | Narzędzia programowe .NET | 16.10.31303.231 | Wymagane
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko uruchomieniowe .NET Core 3.1 (LTS) | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.Runtime.5.0 | Środowisko uruchomieniowe .NET 5.0 | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.SDK | Zestaw SDK .NET | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.Web | Narzędzia programowe .NET | 16.10.31303.231 | Wymagane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Narzędzia do tworzenia na platformie Azure | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki platformy Azure dla platformy .NET | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure Compute emulatora | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.4.29313.120 | Wymagane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia do łączności i publikowania | 16.4.29409.204 | Wymagane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.4.29409.204 | Wymagane
Microsoft.VisualStudio.Component.FSharp | Obsługa języka F# | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Obsługa języka F# dla projektów internetowych | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka języka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.10.31303.231 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 16.4.29318.151 | Wymagane
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server sterownika ODBC | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server narzędzi wiersza polecenia | 16.0.28707.177 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe biblioteki ADAL SQL | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na SQL Server danych | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcanie szablonu tekstu | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Wymagane
Microsoft.VisualStudio.Component.Web | ASP.NET i narzędzia do tworzenia aplikacji internetowych | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Wymagania wstępne dotyczące tworzenia aplikacji na platformie Azure | 16.10.31303.231 | Wymagane
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs narzędzi | 16.10.31205.180 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET i narzędzia do tworzenia aplikacji internetowych | 16.10.31205.180 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.10.31205.180 | Wymagane
Microsoft.Component.Azure.DataLake.Tools | Usługi Azure Data Lake i Stream Analytics Tools | 16.10.31205.252 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework docelowy 4.5.1 | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework docelowy w 4.6 | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4–4.6 | 16.0.28516.191 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane ASP.NET aplikacji | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Narzędzia Visual Studio Tools for Kubernetes | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.Azure.Powershell | Azure PowerShell | 16.5.29515.121 | Zalecane
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Azure Resource Manager podstawowe narzędzia | 16.4.29409.204 | Zalecane
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Narzędzia usługi Service Fabric | 16.4.29313.120 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services podstawowe narzędzia | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services narzędzi kompilacji | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Azure Cloud Services narzędzi | 16.10.31205.180 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Azure Resource Manager narzędzi | 16.0.28528.71 | Zalecane
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 | 16.0.28517.75 | Opcjonalne
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework docelowy 4.7.1 | 16.10.31205.252 | Opcjonalne
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework docelowy 4.7 | 16.10.31205.252 | Opcjonalne
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 | 16.4.29313.120 | Opcjonalne
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 | 16.4.29318.151 | Opcjonalne
Microsoft.Net.Core.Component.SDK.2.1 | Środowisko uruchomieniowe .NET Core 2.1 (LTS) | 16.10.31320.204 | Opcjonalne
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 16.0.28517.75 | Opcjonalne
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Opcjonalne

## <a name="data-storage-and-processing"></a>Magazynowanie i przetwarzanie danych

**Identyfikator:** Microsoft.VisualStudio.Workload.Data

**Opis:** Łączenie, opracowywanie i testowanie rozwiązań do przetwarzania danych za SQL Server, Azure Data Lake lub Hadoop.

### <a name="components-included-by-this-workload"></a>Składniki uwzględnione w tym obciążeniu

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi językowe Razor | 16.10.31205.252 | Zalecane
Component.Microsoft.Web.LibraryManager | Library Manager | 16.10.31205.180 | Zalecane
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Internetowa wersja zapoznawcza na żywo | 0.7.22.39845 | Zalecane
Microsoft.Component.Azure.DataLake.Tools | Usługi Azure Data Lake i Stream Analytics Tools | 16.10.31205.252 | Zalecane
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework docelowy 4.5.1 | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework docelowy 4.5.2 | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework docelowy w 4.6 | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework docelowy 4.7.2 | 16.10.31205.252 | Zalecane
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework programowe w 4.7.2 | 16.3.29207.166 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4–4.6 | 16.0.28516.191 | Zalecane
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko uruchomieniowe .NET Core 3.1 (LTS) | 16.10.31320.204 | Zalecane
Microsoft.NetCore.Component.Runtime.5.0 | Środowisko uruchomieniowe .NET 5.0 | 16.10.31320.204 | Zalecane
Microsoft.NetCore.Component.SDK | Zestaw SDK .NET | 16.10.31320.204 | Zalecane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Narzędzia do tworzenia na platformie Azure | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki platformy Azure dla platformy .NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure Compute emulatora | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.4.29313.120 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services podstawowe narzędzia | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services narzędzi kompilacji | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia do łączności i publikowania | 16.4.29409.204 | Zalecane
Microsoft.VisualStudio.Component.Docnarzędzia kerTools | Narzędzia programistyczne dla kontenerów | 16.4.29409.204 | Zalecane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka języka JavaScript | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.10.31303.231 | Zalecane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 16.4.29318.151 | Zalecane
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server sterownika ODBC | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server narzędzi wiersza polecenia | 16.0.28707.177 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# Visual Basic Roslyn | 16.0.28714.129 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe biblioteki ADAL SQL | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla SQL Server | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla SQL Server technicznej | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Zalecane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcanie szablonu tekstu | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Zalecane
Microsoft.VisualStudio.Component.Web | ASP.NET i narzędzia do tworzenia aplikacji internetowych | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET i narzędzia do tworzenia aplikacji internetowych | 16.10.31205.180 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.10.31205.180 | Zalecane
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework docelowy 4.6.1 | 16.0.28517.75 | Opcjonalne
Microsoft.VisualStudio.Component.FSharp.Desktop | Obsługa języka F# desktop | 16.0.28315.86 | Opcjonalne

## <a name="data-science-and-analytical-applications"></a>Aplikacje do analizy i przetwarzania danych

**Identyfikator:** Microsoft.VisualStudio.Workload.DataScience

**Opis:** Języki i narzędzia do tworzenia aplikacji do nauki o danych, w tym python i F#.

### <a name="components-included-by-this-workload"></a>Składniki dołączone do tego obciążenia

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.PythonTools | Obsługa języka Python | 16.10.31313.127 | Zalecane
Microsoft.Component.PythonTools.Minicondax64 | Miniconda języka Python (bez obsługi) | 16.10.31313.127 | Zalecane
Microsoft.Component.PythonTools.Web | Obsługa sieci Web w języku Python | 16.10.31205.252 | Zalecane
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework docelowy 4.6.1 | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia do łączności i publikowania | 16.4.29409.204 | Zalecane
Microsoft.VisualStudio.Component.FSharp.Desktop | Obsługa języka F# desktop | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.10.31303.231 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# Visual Basic Roslyn | 16.0.28714.129 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.10.31205.180 | Zalecane
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Natywne narzędzia programskie języka Python | 16.10.31205.180 | Opcjonalne
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla DirectX | 16.0.28625.61 | Opcjonalne
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania języka C++ | 16.5.29515.121 | Opcjonalne
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 — narzędzia kompilacji w języku C++ x64/x86 w programie VS 2019 (najnowsza wersja) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK | Uniwersalne środowisko uruchomieniowe języka C systemu Windows | 16.4.29409.204 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Opcjonalne

## <a name="net-desktop-development"></a>Tworzenie aplikacji klasycznych dla programu .NET

**Identyfikator:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Opis:** Twórz aplikacje WPF, Windows Forms i konsolowe przy użyciu języka C#, Visual Basic i F# przy użyciu platformy .NET i .NET Framework.

### <a name="components-included-by-this-workload"></a>Składniki uwzględnione w tym obciążeniu

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework docelowych w pakiecie 4.7.2 | 16.10.31205.252 | Wymagane
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 | 16.3.29207.166 | Wymagane
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko uruchomieniowe .NET Core 3.1 (LTS) | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.Runtime.5.0 | Środowisko uruchomieniowe .NET 5.0 | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.SDK | Zestaw SDK .NET | 16.10.31320.204 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 16.4.29318.151 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Narzędzia programskie dla komputerów stacjonarnych .NET | 16.10.31205.180 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcanie szablonu tekstu | 16.0.28625.61 | Wymagane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4062 | Zalecane
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Zalecane
Microsoft.ComponentGroup.ClickOnce.Publish | Publikowanie ClickOnce dla .NET  | 16.10.31303.231 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework docelowy 4.5.1 | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework docelowy 4.5.2 | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework docelowy 4.6.1 | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4–4.6 | 16.0.28516.191 | Zalecane
Microsoft.NetCore.Component.DevelopmentTools | Narzędzia programowe .NET | 16.10.31303.231 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia do łączności i publikowania | 16.4.29409.204 | Zalecane
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger just in time | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.DotNetModelBuilder | ML.NET Model Builder (wersja zapoznawcza) | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 narzędzi | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.FSharp | Obsługa języka F# | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.10.31303.231 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Zalecane
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.10.31205.180 | Zalecane
Component.Dotfuscator | PreEmptive Protection — Dotfuscator | 16.10.31205.252 | Opcjonalne
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.10.31205.252 | Opcjonalne
Component.Microsoft.Web.LibraryManager | Library Manager | 16.10.31205.180 | Opcjonalne
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Podgląd internetowy na żywo | 0.7.22.39845 | Opcjonalne
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 | 16.0.28517.75 | Opcjonalne
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework docelowy w 4.7.1 | 16.10.31205.252 | Opcjonalne
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework docelowy w 4.7 | 16.10.31205.252 | Opcjonalne
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 | 16.4.29313.120 | Opcjonalne
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework programowe w 4.6.1 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 | 16.4.29318.151 | Opcjonalne
Microsoft.Net.Core.Component.SDK.2.1 | Środowisko uruchomieniowe .NET Core 2.1 (LTS) | 16.10.31320.204 | Opcjonalne
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.4.29409.204 | Opcjonalne
Microsoft.VisualStudio.Component.FSharp.Desktop | Obsługa języka F# desktop | 16.0.28315.86 | Opcjonalne
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Opcjonalne
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka języka JavaScript | 16.0.28517.75 | Opcjonalne
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server sterownika ODBC | 16.0.28625.61 | Opcjonalne
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server narzędzi wiersza polecenia | 16.0.28707.177 | Opcjonalne
Microsoft.VisualStudio.Component.PortableLibrary | Pakiet docelowy przenośnej biblioteki .NET | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe biblioteki ADAL SQL | 16.0.28517.75 | Opcjonalne
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na SQL Server danych | 16.0.28315.86 | Opcjonalne
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Opcjonalne
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Opcjonalne
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Opcjonalne
Microsoft.VisualStudio.Component.Web | ASP.NET i narzędzia do tworzenia aplikacji internetowych | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Narzędzia do tworzenia pakietów MSIX | 16.10.31205.180 | Opcjonalne
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET i narzędzia do tworzenia aplikacji internetowych | 16.10.31205.180 | Opcjonalne

## <a name="game-development-with-unity"></a>Opracowywanie gier za pomocą aparatu Unity

**Identyfikator:** Microsoft.VisualStudio.Workload.ManagedGame

**Opis:** Twórz gry 2D i 3D za pomocą aparatu Unity— zaawansowanego międzyplatformowego środowiska projektowego.

### <a name="components-included-by-this-workload"></a>Składniki uwzględnione w tym obciążeniu

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework docelowy w 4.7.1 | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.Unity | Narzędzia Visual Studio Tools for Unity | 16.0.28315.86 | Wymagane
Component.UnityEngine.x64 | Unity Hub | 16.10.31205.252 | Zalecane
Component.UnityEngine.x86 | 32-bitowy edytor aparatu Unity 5.6 | 16.1.28811.260 | Zalecane

## <a name="linux-development-with-c"></a>Programowanie dla systemu Linux w języku C++

**Identyfikator:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Opis:** Tworzenie i debugowanie aplikacji uruchomionych w środowisku systemu Linux.

### <a name="components-included-by-this-workload"></a>Składniki dołączone do tego obciążenia

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.MDD.Linux | Tworzenie aplikacji w języku C++ dla systemu Linux | 16.5.29515.121 | Wymagane
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.10.31205.252 | Wymagane
Component.Linux.CMake | Narzędzia CMake języka C++ dla systemu Linux | 16.2.29003.222 | Zalecane
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.10.31205.180 | Zalecane
Component.MDD.Linux.GCC.arm | Narzędzia deweloperskie osadzone i IoT | 16.5.29515.121 | Opcjonalne

## <a name="desktop-development-with-c"></a>Programowanie aplikacji klasycznych w języku C++

**Identyfikator:** Microsoft.VisualStudio.Workload.NativeDesktop

**Opis:** Twórz nowoczesne aplikacje C++ dla systemu Windows przy użyciu narzędzi, takich jak MSVC, Clang, CMake lub MSBuild.

### <a name="components-included-by-this-workload"></a>Składniki uwzględnione w tym obciążeniu

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcanie szablonu tekstu | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aktualizacja redystrybucyjna języka C++ 2019 | 16.5.29515.121 | Wymagane
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Podstawowe funkcje pulpitu języka C++ | 16.2.29012.281 | Wymagane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4062 | Zalecane
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger just in time | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla DirectX | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.10.31303.231 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Zalecane
Microsoft.VisualStudio.Component.VC.ASAN | C++ AddressSanitizer | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.VC.ATL | C++ ATL for latest v142 build tools (x86 & x64) | 16.4.29313.120 | Zalecane
Microsoft.VisualStudio.Component.VC.CMake.Project | Narzędzia CMake języka C++ dla systemu Windows | 16.3.29103.31 | Zalecane
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania języka C++ | 16.5.29515.121 | Zalecane
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Adapter testowy dla boost.test | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Test Adapter for Google Test | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 — narzędzia kompilacji języka C++ x64/x86 w programie VS 2019 (najnowsza wersja) | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.10.31205.180 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.CMake | edytor JSON | 16.10.31205.180 | Zalecane
Component.Incredibuild | Incredibuild — przyspieszanie kompilacji | 16.10.31205.252 | Opcjonalne
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Opcjonalne
Microsoft.Component.VC.Runtime.UCRTSDK | Zestaw SDK uniwersalnego zestawu CRT systemu Windows | 16.0.28625.61 | Opcjonalne
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework docelowy 4.6.1 | 16.0.28517.75 | Opcjonalne
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Opcjonalne
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka języka JavaScript | 16.0.28517.75 | Opcjonalne
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 — narzędzia kompilacji języka C++ w programie VS 2015 (wersja 14.00) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.VC.ATLMFC | C++ MFC dla najnowszych narzędzi kompilacji v142 (x86 & x64) | 16.4.29313.120 | Opcjonalne
Microsoft.VisualStudio.Component.VC.CLI.Support | Obsługa języka C++/interfejsu wiersza polecenia dla narzędzi kompilacji w wersji 142 (najnowsza wersja) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.VC.Llvm.Clang | Kompilator Clang języka C++ dla systemu Windows (11.0.0) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset | C++ Clang-cl dla narzędzi kompilacji v142 (x64/x86) | 16.3.29207.166 | Opcjonalne
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduły języka C++ dla narzędzi kompilacji w wersji 142 (x64/x86 — eksperymentalne) | 16.0.28625.61 | Opcjonalne
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142 — narzędzia kompilacji ARM64 języka C++ w programie VS 2019 (najnowsza wersja) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 — narzędzia kompilacji programu VS 2017 C++ x64/x86 (wersja 14.16) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Opcjonalne
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Llvm.Clang | Narzędzia Clang dla języka C++ dla systemu Windows (11.0.0 – x64/x86) | 16.10.31205.180 | Opcjonalne

## <a name="game-development-with-c"></a>Programowanie gier w języku C++

**Identyfikator:** Microsoft.VisualStudio.Workload.NativeGame

**Opis:** Korzystaj z pełnych możliwości języka C++, aby tworzyć profesjonalne gry obsługiwane przez DirectX, Unreal lub Cocos2d.

### <a name="components-included-by-this-workload"></a>Składniki uwzględnione w tym obciążeniu

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aktualizacja redystrybucyjna języka C++ 2019 | 16.5.29515.121 | Wymagane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 — narzędzia kompilacji języka C++ x64/x86 w programie VS 2019 (najnowsza wersja) | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK | Środowisko uruchomieniowe uniwersalnego języka C systemu Windows | 16.4.29409.204 | Wymagane
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla DirectX | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Zalecane
Microsoft.VisualStudio.Component.VC.ASAN | C++ AddressSanitizer | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania języka C++ | 16.5.29515.121 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Zalecane
Component.Android.NDK.R16B | Android NDK (R16B) | 16.10.31320.204 | Opcjonalne
Component.Android.SDK25.Private | Android SDK konfiguracji (poziom interfejsu API 25) (instalacja lokalna do programowania aplikacji mobilnych w języku C++) | 16.0.28625.61 | Opcjonalne
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Opcjonalne
Component.Cocos | Cocos | 16.0.28315.86 | Opcjonalne
Component.Incredibuild | Incredibuild — przyspieszanie kompilacji | 16.10.31205.252 | Opcjonalne
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Opcjonalne
Component.MDD.Android | Narzędzia deweloperskie dla systemu Android w języku C++ | 16.0.28517.75 | Opcjonalne
Component.OpenJDK | OpenJDK (dystrybucja firmy Microsoft) | 16.10.31303.311 | Opcjonalne
Component.Unreal | Instalator unreal engine | 16.1.28810.153 | Opcjonalne
Component.Unreal.Android | Obsługa środowiska IDE systemu Android dla aparatu Unreal Engine | 16.1.28810.153 | Opcjonalne
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework docelowy 4.5.1 | 16.0.28517.75 | Opcjonalne
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework docelowy 4.5.2 | 16.0.28517.75 | Opcjonalne
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework docelowych 4.5 | 16.0.28517.75 | Opcjonalne
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 | 16.0.28517.75 | Opcjonalne
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework docelowy w 4.6 | 16.0.28517.75 | Opcjonalne
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework docelowy 4.7.2 | 16.10.31205.252 | Opcjonalne
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Opcjonalne
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 | 16.0.28517.75 | Opcjonalne
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework programowe w 4.7.2 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4–4.6 | 16.0.28516.191 | Opcjonalne
Microsoft.VisualStudio.Component.NuGet.BuildTools | Obiekty docelowe nuGet i zadania kompilacji | 16.1.28829.92 | Opcjonalne
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# Visual Basic Roslyn | 16.0.28714.129 | Opcjonalne
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Opcjonalne

## <a name="mobile-development-with-c"></a>Tworzenie aplikacji mobilnych w języku C++

**Identyfikator:** Microsoft.VisualStudio.Workload.NativeMobile

**Opis:** Twórz aplikacje dla wielu platform dla systemów iOS, Android lub Windows przy użyciu języka C++.

### <a name="components-included-by-this-workload"></a>Składniki uwzględnione w tym obciążeniu

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Android.SDK25.Private | Android SDK konfiguracji (poziom interfejsu API 25) (instalacja lokalna do programowania aplikacji mobilnych w języku C++) | 16.0.28625.61 | Wymagane
Component.OpenJDK | OpenJDK (dystrybucja firmy Microsoft) | 16.10.31303.311 | Wymagane
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.10.31205.252 | Wymagane
Component.Android.NDK.R16B | Android NDK (R16B) | 16.10.31320.204 | Zalecane
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Zalecane
Component.MDD.Android | Narzędzia deweloperskie dla systemu Android w języku C++ | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Zalecane
Component.Android.NDK.R16B_3264 | Android NDK (R16B) (32-bitowy) | 16.10.31320.204 | Opcjonalne
Component.Google.Android.Emulator.API25.Private | Google Emulator systemu Android (poziom interfejsu API 25) (instalacja lokalna) | 16.1.28810.153 | Opcjonalne
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (instalacja lokalna) | 16.0.28528.71 | Opcjonalne
Component.Incredibuild | Incredibuild — przyspieszanie kompilacji | 16.10.31205.252 | Opcjonalne
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Opcjonalne
Component.MDD.iOS | Narzędzia programskie dla systemu iOS w języku C++ | 16.0.28517.75 | Opcjonalne

## <a name="net-cross-platform-development"></a>Tworzenie aplikacji międzyplatformowych na platformie .NET

**Identyfikator:** Microsoft.VisualStudio.Workload.NetCoreTools

**Opis:** Twórz aplikacje dla wielu platform przy użyciu platform .NET, ASP.NET Core, HTML/JavaScript i kontenerów, w tym obsługę platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki uwzględnione w tym obciążeniu

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi językowe Razor | 16.10.31205.252 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 16.10.31205.180 | Wymagane
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Podgląd internetowy na żywo | 0.7.22.39845 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagane
Microsoft.ComponentGroup.ClickOnce.Publish | ClickOnce Publishing for .NET  | 16.10.31303.231 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework docelowy 4.5.2 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework docelowy 4.6.1 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework docelowych w pakiecie 4.7.2 | 16.10.31205.252 | Wymagane
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework programowe w 4.7.2 | 16.3.29207.166 | Wymagane
Microsoft.NetCore.Component.DevelopmentTools | Narzędzia programowe .NET | 16.10.31303.231 | Wymagane
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko uruchomieniowe .NET Core 3.1 (LTS) | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.Runtime.5.0 | Środowisko uruchomieniowe .NET 5.0 | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.SDK | Zestaw SDK .NET | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.Web | Narzędzia programowe .NET | 16.10.31303.231 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia do łączności i publikowania | 16.4.29409.204 | Wymagane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.4.29409.204 | Wymagane
Microsoft.VisualStudio.Component.FSharp | Obsługa języka F# | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Obsługa języka F# dla projektów internetowych | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka języka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.10.31303.231 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 16.4.29318.151 | Wymagane
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server sterownika ODBC | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server narzędzi wiersza polecenia | 16.0.28707.177 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe biblioteki ADAL SQL | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na SQL Server danych | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcanie szablonu tekstu | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET i narzędzia do tworzenia aplikacji internetowych | 16.10.31205.180 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.10.31205.180 | Wymagane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4062 | Zalecane
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs narzędzi | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia developer Analytics | 16.5.29515.121 | Zalecane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Narzędzia do tworzenia na platformie Azure | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki platformy Azure dla platformy .NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure Compute emulatora | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.4.29313.120 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger just in time | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.DotNetModelBuilder | ML.NET Model Builder (wersja zapoznawcza) | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Zalecane
Microsoft.VisualStudio.Component.Web | ASP.NET i narzędzia do tworzenia aplikacji internetowych | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.WslDebugging | Debugowanie .NET za pomocą programu WSL 2 | 16.10.31303.231 | Zalecane
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs narzędzi | 16.10.31205.180 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Narzędzia w chmurze do tworzenia aplikacji internetowych | 16.10.31205.180 | Zalecane
Microsoft.Net.Core.Component.SDK.2.1 | Środowisko uruchomieniowe .NET Core 2.1 (LTS) | 16.10.31320.204 | Opcjonalne
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Obsługa usług IIS w czasie projektowania | 16.10.31205.180 | Opcjonalne
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Narzędzia do tworzenia pakietów MSIX | 16.10.31205.180 | Opcjonalne

## <a name="mobile-development-with-net"></a>Opracowywanie aplikacji mobilnych za pomocą platformy .NET

**Identyfikator:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Opis:** Twórz aplikacje dla wielu platform dla systemów iOS, Android lub Windows przy użyciu platformy Xamarin.

### <a name="components-included-by-this-workload"></a>Składniki uwzględnione w tym obciążeniu

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.OpenJDK | OpenJDK (dystrybucja firmy Microsoft) | 16.10.31303.311 | Wymagane
Component.Xamarin | Xamarin | 16.10.31205.252 | Wymagane
Component.Xamarin.RemotedSimulator | Zdalny symulator platformy Xamarin | 16.10.31205.252 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagane
Microsoft.ComponentGroup.ClickOnce.Publish | ClickOnce Publishing for .NET  | 16.10.31303.231 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework docelowy 4.6.1 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework docelowych w pakiecie 4.7.2 | 16.10.31205.252 | Wymagane
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework programowe w 4.7.2 | 16.3.29207.166 | Wymagane
Microsoft.NetCore.Component.DevelopmentTools | Narzędzia programowe .NET | 16.10.31303.231 | Wymagane
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko uruchomieniowe .NET Core 3.1 (LTS) | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.Runtime.5.0 | Środowisko uruchomieniowe .NET 5.0 | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.SDK | Zestaw SDK .NET | 16.10.31320.204 | Wymagane
Microsoft.VisualStudio.Component.FSharp | Obsługa języka F# | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.Merq | Typowe narzędzia wewnętrzne platformy Xamarin | 16.2.29012.281 | Wymagane
Microsoft.VisualStudio.Component.MonoDebugger | Debuger mono | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | ASP.NET szablonów | 16.10.31205.180 | Wymagane
Component.Android.SDK30 | Android SDK konfiguracji (poziom interfejsu API 30) | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Zalecane

## <a name="aspnet-and-web-development"></a>Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych

**Identyfikator:** Microsoft.VisualStudio.Workload.NetWeb

**Opis:** Twórz aplikacje internetowe przy użyciu ASP.NET Core, ASP.NET, HTML/JavaScript i kontenerów, w tym obsługę platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki uwzględnione w tym obciążeniu

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi językowe Razor | 16.10.31205.252 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 16.10.31205.180 | Wymagane
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Podgląd internetowy na żywo | 0.7.22.39845 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagane
Microsoft.ComponentGroup.ClickOnce.Publish | Publikowanie ClickOnce dla .NET  | 16.10.31303.231 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework docelowy 4.5.2 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework docelowy 4.6.1 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework docelowych w pakiecie 4.7.2 | 16.10.31205.252 | Wymagane
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 | 16.3.29207.166 | Wymagane
Microsoft.NetCore.Component.DevelopmentTools | Narzędzia programowe .NET | 16.10.31303.231 | Wymagane
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko uruchomieniowe .NET Core 3.1 (LTS) | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.Runtime.5.0 | Środowisko uruchomieniowe .NET 5.0 | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.SDK | Zestaw SDK .NET | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.Web | Narzędzia programowe .NET | 16.10.31303.231 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia do łączności i publikowania | 16.4.29409.204 | Wymagane
Microsoft.VisualStudio.Component.Docnarzędzia kerTools | Narzędzia programistyczne dla kontenerów | 16.4.29409.204 | Wymagane
Microsoft.VisualStudio.Component.FSharp | Obsługa języka F# | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Obsługa języka F# dla projektów internetowych | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka języka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.10.31303.231 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 16.4.29318.151 | Wymagane
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server sterownika ODBC | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server narzędzi wiersza polecenia | 16.0.28707.177 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe biblioteki ADAL SQL | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla SQL Server technicznej | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcanie szablonu tekstu | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Wymagane
Microsoft.VisualStudio.Component.Web | ASP.NET i narzędzia do tworzenia aplikacji internetowych | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET i narzędzia do tworzenia aplikacji internetowych | 16.10.31205.180 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web.Client | ASP.NET i narzędzia do tworzenia aplikacji internetowych | 16.10.31205.180 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.10.31205.180 | Wymagane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4062 | Zalecane
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs narzędzi | 16.10.31205.252 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework docelowy 4.5.1 | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework docelowy w 4.6 | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4–4.6 | 16.0.28516.191 | Zalecane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia developer Analytics | 16.5.29515.121 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane ASP.NET aplikacji | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Narzędzia do tworzenia na platformie Azure | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki platformy Azure dla platformy .NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure Compute emulatora | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.4.29313.120 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger just in time | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 narzędzi | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.WslDebugging | Debugowanie .NET za pomocą programu WSL 2 | 16.10.31303.231 | Zalecane
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs narzędzi | 16.10.31205.180 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Narzędzia w chmurze do tworzenia aplikacji internetowych | 16.10.31205.180 | Zalecane
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 | 16.0.28517.75 | Opcjonalne
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework docelowy 4.7.1 | 16.10.31205.252 | Opcjonalne
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework docelowy 4.7 | 16.10.31205.252 | Opcjonalne
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 | 16.4.29313.120 | Opcjonalne
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 | 16.4.29318.151 | Opcjonalne
Microsoft.Net.Core.Component.SDK.2.1 | Środowisko uruchomieniowe .NET Core 2.1 (LTS) | 16.10.31320.204 | Opcjonalne
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Opcjonalne
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Dodatkowe szablony projektów (poprzednie wersje) | 16.10.31205.180 | Opcjonalne
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Obsługa usług IIS w czasie projektowania | 16.10.31205.180 | Opcjonalne

## <a name="nodejs-development"></a>Node.js tworzenia aplikacji

**Identyfikator:** Microsoft.VisualStudio.Workload.Node

**Opis:** Twórz skalowalne aplikacje sieciowe przy Node.js, asynchronicznego środowiska uruchomieniowego JavaScript opartego na zdarzeniach. 

### <a name="components-included-by-this-workload"></a>Składniki uwzględnione w tym obciążeniu

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka języka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.10.31303.231 | Wymagane
Microsoft.VisualStudio.Component.Node.Tools | Node.js narzędzi deweloperskie | 16.5.29515.121 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.10.31205.180 | Wymagane
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4062 | Zalecane
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger just in time | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# Visual Basic Roslyn | 16.0.28714.129 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia developer Analytics | 16.5.29515.121 | Opcjonalne
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia do łączności i publikowania | 16.4.29409.204 | Opcjonalne
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 — narzędzia kompilacji języka C++ x64/x86 w programie VS 2019 (najnowsza wersja) | 16.10.31205.252 | Opcjonalne

## <a name="officesharepoint-development"></a>Opracowywanie zawartości dla pakietu Office/programu SharePoint

**Identyfikator:** Microsoft.VisualStudio.Workload.Office

**Opis:** Twórz dodatki pakietu Office i programu SharePoint, rozwiązania programu SharePoint i dodatki VSTO przy użyciu języków C#, VB i JavaScript.

### <a name="components-included-by-this-workload"></a>Składniki dołączone do tego obciążenia

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi językowe Razor | 16.10.31205.252 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 16.10.31205.180 | Wymagane
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Internetowa wersja zapoznawcza na żywo | 0.7.22.39845 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework docelowy 4.5.2 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework docelowych 4.5 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework docelowy 4.6.1 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework docelowy 4.7.2 | 16.10.31205.252 | Wymagane
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Wymagane
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 | 16.0.28517.75 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework programowe w 4.7.2 | 16.3.29207.166 | Wymagane
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko uruchomieniowe .NET Core 3.1 (LTS) | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.Runtime.5.0 | Środowisko uruchomieniowe .NET 5.0 | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.SDK | Zestaw SDK .NET | 16.10.31320.204 | Wymagane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia developer Analytics | 16.5.29515.121 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia do łączności i publikowania | 16.4.29409.204 | Wymagane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.4.29409.204 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka języka JavaScript | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.10.31303.231 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 16.4.29318.151 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Narzędzia programskie dla komputerów stacjonarnych .NET | 16.10.31205.180 | Wymagane
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server sterownika ODBC | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server narzędzi wiersza polecenia | 16.0.28707.177 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 16.4.29409.204 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe biblioteki ADAL SQL | 16.0.28517.75 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na SQL Server danych | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcanie szablonu tekstu | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Wymagane
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Wymagane
Microsoft.VisualStudio.Component.Web | ASP.NET i narzędzia do tworzenia aplikacji internetowych | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET i narzędzia do tworzenia aplikacji internetowych | 16.10.31205.180 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.10.31205.180 | Wymagane
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Zalecane
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools dla pakietu Office (VSTO) | 16.4.29409.204 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework docelowy 4.6.2 | 16.0.28517.75 | Opcjonalne
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework docelowy 4.7.1 | 16.10.31205.252 | Opcjonalne
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework docelowy 4.7 | 16.10.31205.252 | Opcjonalne
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 | 16.4.29313.120 | Opcjonalne
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 | 16.3.29207.166 | Opcjonalne
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 | 16.4.29318.151 | Opcjonalne
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Środowisko Windows Identity Foundation 3.5 | 16.0.28621.142 | Opcjonalne

## <a name="python-development"></a>Programowanie w języku Python

**Identyfikator:** Microsoft.VisualStudio.Workload.Python

**Opis:** Edytowanie, debugowanie, programowanie interakcyjne i kontrola źródła dla języka Python.

### <a name="components-included-by-this-workload"></a>Składniki uwzględnione w tym obciążeniu

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.PythonTools | Obsługa języka Python | 16.10.31313.127 | Wymagane
Component.CPython3.x64 | 64-bitowy język Python 3 (3.7.8) | 3.7.8 | Zalecane
Component.CPython2.x64 | 64-bitowy język Python 2 (2.7.18) (bez obsługi) | 2.7.18.2 | Opcjonalne
Component.CPython2.x86 | 32-bitowy język Python 2 (2.7.18) (bez obsługi) | 2.7.18.2 | Opcjonalne
Component.CPython3.x86 | 32-bitowy język Python 3 (3.7.8) | 3.7.8 | Opcjonalne
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4062 | Opcjonalne
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.10.31205.252 | Opcjonalne
Component.Microsoft.Web.LibraryManager | Library Manager | 16.10.31205.180 | Opcjonalne
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Podgląd internetowy na żywo | 0.7.22.39845 | Opcjonalne
Microsoft.Component.IronPython | IronPython (bez obsługi) | 16.10.31303.231 | Opcjonalne
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Opcjonalne
Microsoft.Component.PythonTools.Minicondax64 | Python miniconda (poza pomocą techniczną) | 16.10.31313.127 | Opcjonalne
Microsoft.Component.PythonTools.Web | Obsługa sieci Web w języku Python | 16.10.31205.252 | Opcjonalne
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Natywne narzędzia programskie języka Python | 16.10.31205.180 | Opcjonalne
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework docelowy 4.5.2 | 16.0.28517.75 | Opcjonalne
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 16.0.28517.75 | Opcjonalne
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework docelowych w pakiecie 4.7.2 | 16.10.31205.252 | Opcjonalne
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Opcjonalne
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 | 16.3.29207.166 | Opcjonalne
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko uruchomieniowe .NET Core 3.1 (LTS) | 16.10.31320.204 | Opcjonalne
Microsoft.NetCore.Component.Runtime.5.0 | Środowisko uruchomieniowe .NET 5.0 | 16.10.31320.204 | Opcjonalne
Microsoft.NetCore.Component.SDK | Zestaw SDK .NET | 16.10.31320.204 | Opcjonalne
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Narzędzia do tworzenia na platformie Azure | 16.0.28625.61 | Opcjonalne
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki platformy Azure dla platformy .NET | 16.0.28315.86 | Opcjonalne
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure Compute emulatora | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.4.29313.120 | Opcjonalne
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services podstawowe narzędzia | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services narzędzi kompilacji | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia do łączności i publikowania | 16.4.29409.204 | Opcjonalne
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger just in time | 16.0.28517.75 | Opcjonalne
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.4.29409.204 | Opcjonalne
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla DirectX | 16.0.28625.61 | Opcjonalne
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Opcjonalne
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka języka JavaScript | 16.0.28517.75 | Opcjonalne
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 16.10.31303.231 | Opcjonalne
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload Core | 16.4.29318.151 | Opcjonalne
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server sterownika ODBC | 16.0.28625.61 | Opcjonalne
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server narzędzi wiersza polecenia | 16.0.28707.177 | Opcjonalne
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Opcjonalne
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# Visual Basic Roslyn | 16.0.28714.129 | Opcjonalne
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe biblioteki ADAL SQL | 16.0.28517.75 | Opcjonalne
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla SQL Server | 16.0.28315.86 | Opcjonalne
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na SQL Server danych | 16.0.28315.86 | Opcjonalne
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Opcjonalne
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Opcjonalne
Microsoft.VisualStudio.Component.TextTemplating | Przekształcanie szablonu tekstu | 16.0.28625.61 | Opcjonalne
Microsoft.VisualStudio.Component.TypeScript.4.2 | TypeScript 4.2 SDK | 16.0.31303.231 | Opcjonalne
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania języka C++ | 16.5.29515.121 | Opcjonalne
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 — narzędzia kompilacji w języku C++ x64/x86 w programie VS 2019 (najnowsza wersja) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.Web | ASP.NET i narzędzia do tworzenia aplikacji internetowych | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK | Uniwersalne środowisko uruchomieniowe języka C systemu Windows | 16.4.29409.204 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET i narzędzia do tworzenia aplikacji internetowych | 16.10.31205.180 | Opcjonalne
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.10.31205.180 | Opcjonalne

## <a name="universal-windows-platform-development"></a>platforma uniwersalna systemu Windows tworzenia aplikacji

**Identyfikator:** Microsoft.VisualStudio.Workload.Universal

**Opis:** Twórz aplikacje dla aplikacji platforma uniwersalna systemu Windows języka C#, VB lub opcjonalnie języka C++.

### <a name="components-included-by-this-workload"></a>Składniki dołączone do tego obciążenia

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | Architektura .NET Native | 16.5.29515.121 | Wymagane
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 | 16.0.28517.75 | Wymagane
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko uruchomieniowe .NET Core 3.1 (LTS) | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.Runtime.5.0 | Środowisko uruchomieniowe .NET 5.0 | 16.10.31320.204 | Wymagane
Microsoft.NetCore.Component.SDK | Zestaw SDK .NET | 16.10.31320.204 | Wymagane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia developer Analytics | 16.5.29515.121 | Wymagane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.Graphics | Edytory obrazów i modeli 3D | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla SQL Server | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Narzędzia do tworzenia pakietów MSIX | 16.10.31205.180 | Wymagane
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native i .NET Standard | 16.3.29102.218 | Wymagane
Microsoft.VisualStudio.ComponentGroup.UWP.Support | platforma uniwersalna systemu Windows narzędzi | 16.10.31205.180 | Wymagane
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | platforma uniwersalna systemu Windows narzędzi dla platformy Xamarin | 16.10.31205.180 | Wymagane
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Zalecane
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Opcjonalne
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla DirectX | 16.0.28625.61 | Opcjonalne
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Obsługa platforma uniwersalna systemu Windows kompilacji w wersji 142 w języku C++ (ARM64) | 16.3.29207.166 | Opcjonalne
Microsoft.VisualStudio.Component.UWP.VC.ARM64EC | Obsługa platforma uniwersalna systemu Windows kompilacji w wersji 142 w języku C++ (ARM64EC — wersja eksperymentalna) | 16.10.31303.231 | Opcjonalne
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC v142 — narzędzia kompilacji ARM języka C++ w programie VS 2019 (najnowsza wersja) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142 — narzędzia kompilacji ARM64 języka C++ w programie VS 2019 (najnowsza wersja) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.VC.Tools.ARM64EC | MSVC v142 — narzędzia kompilacji ARM64EC języka C++ w programie VS 2019 (najnowsza wersja — eksperymentalne) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 — narzędzia kompilacji języka C++ x64/x86 w programie VS 2019 (najnowsza wersja) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141 — narzędzia kompilacji ARM języka C++ w programie VS 2017 (wersja 14.16) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141 — narzędzia kompilacji ARM64 języka C++ w programie VS 2017 (wersja 14.16) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 — narzędzia kompilacji programu VS 2017 C++ x64/x86 (wersja 14.16) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Opcjonalne
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Łączność urządzenia USB | 16.10.31205.252 | Opcjonalne
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Narzędzia platforma uniwersalna systemu Windows C++ (wersja 142) | 16.10.31205.180 | Opcjonalne
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | Narzędzia platforma uniwersalna systemu Windows C++ (wersja 141) | 16.1.28810.153 | Opcjonalne

## <a name="visual-studio-extension-development"></a>Programowanie rozszerzeń programu Visual Studio

**Identyfikator:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Opis:** Tworzenie dodatków i rozszerzeń dla aplikacji Visual Studio, w tym nowych poleceń, analizatorów kodu i okien narzędzi.

### <a name="components-included-by-this-workload"></a>Składniki uwzględnione w tym obciążeniu

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagane
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 | 16.0.28517.75 | Wymagane
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework docelowych w pakiecie 4.7.2 | 16.10.31205.252 | Wymagane
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 | 16.3.29207.166 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# Visual Basic Roslyn | 16.0.28714.129 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.10.31205.252 | Wymagane
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Wymagane
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Visual Studio wstępne dotyczące tworzenia rozszerzenia | 16.10.31205.180 | Wymagane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 16.10.31205.252 | Zalecane
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.10.31305.154 | Zalecane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcanie szablonu tekstu | 16.0.28625.61 | Zalecane
Microsoft.Component.CodeAnalysis.SDK | Zestaw SDK platformy kompilatora .NET | 16.2.29003.222 | Opcjonalne
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia developer Analytics | 16.5.29515.121 | Opcjonalne
Microsoft.VisualStudio.Component.DslTools | Zestaw SDK modelowania | 16.0.28315.86 | Opcjonalne

## <a name="unaffiliated-components"></a>Składniki nieskonflilitowane

Są to składniki, które nie są dołączone do żadnego obciążenia, ale mogą być wybrane jako pojedynczy składnik.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
Component.GitHub.VisualStudio | Rozszerzenie usługi GitHub dla Visual Studio | 2.5.9.5485
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Microsoft.Component.ClickOnce | Publikowanie ClickOnce | 16.4.29409.204
Microsoft.Component.HelpViewer | Podgląd Pomocy | 16.0.28625.61
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.4.29409.204
Microsoft.Net.Core.Component.SDK.2.2 | Środowisko uruchomieniowe .NET Core 2.2 (bez obsługi) | 16.10.31205.252
Microsoft.Net.Core.Component.SDK.3.0 | Środowisko uruchomieniowe .NET Core 3.0 (bez obsługi) | 16.10.31320.204
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programowe i program .NET Core 2.1 | 16.10.31205.252
Microsoft.NetCore.ComponentGroup.Web.2.1 | Web Development Tools plus .NET Core 2.1 | 16.10.31205.252
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Azure DevOps pakietu Office | 16.0.28625.61
Microsoft.VisualStudio.Component.ClassDesigner | Projektant klas | 16.0.28528.71
Microsoft.VisualStudio.Component.DependencyValidation.Community | Walidacja zależności | 16.0.28517.75
Microsoft.VisualStudio.Component.Git | Git dla systemu Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.GraphDocument | Edytor DGML | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | LINQ to SQL Tools | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 — narzędzia kompilacji ARM języka C++ w programie VS 2019 (wersja 14.20) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC v142 — biblioteki z ograniczeniami Spectre języka C++ ARM w programie VS 2019 (wersja 14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 — narzędzia kompilacji ARM64 języka C++ w programie VS 2019 (wersja 14.20) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC v142 — biblioteki z ograniczeniami Spectre w programie VS 2019 C++ ARM64 (wersja 14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL | C++ v14.20 ATL for v142 build tools (x86 & x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | C++ v14.20 ATL for v142 build tools (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | C++ v14.20 ATL for v142 build tools with Spectre Mitigations (ARM) (C++ v14.20 ATL for v142 build tools with Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64 | C++ v14.20 ATL for v142 build tools (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64.Spectre | C++ v14.20 ATL for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.20 ATL for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.20 ATL for v142 build tools with Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.Spectre | C++ v14.20 ATL for v142 build tools with Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.CLI.Support | Obsługa języka C++/interfejsu wiersza polecenia dla narzędzi kompilacji w wersji 142 (14.20) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.20.MFC | C++ v14.20 MFC for v142 build tools (x86 & x64) | 16.2.29003.222
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM | C++ v14.20 MFC for v142 build tools (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | C++ v14.20 MFC for v142 build tools with Spectre Mitigations (ARM) (C++ 14.20 MFC for v142 build tools with Spectre Mitigations (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | C++ 14.20 MFC dla narzędzi kompilacji v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | C++ v14.20 MFC for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.20 MFC for v142 build tools with Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | C++ v14.20 MFC for v142 build tools with Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC v142 — narzędzia kompilacji w języku C++ x64/x86 w programie VS 2019 (wersja 14.20) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC v142 — biblioteki z ograniczeniami Spectre w programie VS 2019 C++ x64/x86 (wersja 14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM | MSVC v142 — narzędzia kompilacji ARM języka C++ w programie VS 2019 (wersja 14.21) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.21.ARM.Spectre | MSVC v142 — biblioteki z ograniczeniem ryzyka spectre dla języka C++ ARM w programie VS 2019 (wersja 14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM64 | MSVC v142 — narzędzia kompilacji ARM64 języka C++ w programie VS 2019 (wersja 14.21) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.21.ARM64.Spectre | MSVC v142 — biblioteki z ograniczeniem ryzyka spectre w programie VS 2019 C++ ARM64 (wersja 14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL | C++ v14.21 ATL for v142 build tools (x86 & x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM | C++ v14.21 ATL for v142 build tools (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM.Spectre | C++ v14.21 ATL for v142 build tools with Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64 | C++ v14.21 ATL for v142 build tools (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64.Spectre | C++ v14.21 ATL for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.21 ATL for v142 build tools with Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL.Spectre | C++ v14.21 ATL for v142 build tools with Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.CLI.Support | Obsługa C++/CLI dla narzędzi kompilacji w wersji 142 (14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.MFC | C++ 14.21 MFC dla narzędzi kompilacji v142 (x86 & x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM | C++ 14.21 MFC dla narzędzi kompilacji v142 (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM.Spectre | C++ v14.21 MFC for v142 build tools with Spectre Mitigations (ARM) (C++ v14.21 MFC for v142 build tools with Spectre Mitigations (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64 | C++ v14.21 MFC for v142 build tools (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64.Spectre | C++ v14.21 MFC for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.21 MFC for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.21 MFC for v142 build tools with Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.Spectre | C++ v14.21 MFC for v142 build tools with Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.x86.x64 | MSVC v142 — vs 2019 C++ x64/x86 build tools (v14.21) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.21.x86.x64.Spectre | MSVC v142 — biblioteki z ograniczeniem ryzyka Spectre w programie VS 2019 C++ x64/x86 (wersja 14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM | MSVC v142 — narzędzia kompilacji ARM języka C++ w programie VS 2019 (wersja 14.22) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.22.ARM.Spectre | MSVC v142 — biblioteki z ograniczeniem ryzyka spectre dla języka C++ ARM w programie VS 2019 (wersja 14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM64 | MSVC v142 — narzędzia kompilacji ARM64 języka C++ w programie VS 2019 (wersja 14.22) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.22.ARM64.Spectre | MSVC v142 — biblioteki z ograniczeniami Spectre w programie VS 2019 C++ ARM64 (wersja 14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL | C++ v14.22 ATL for v142 build tools (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM | C++ v14.22 ATL for v142 build tools (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM.Spectre | C++ v14.22 ATL for v142 build tools with Spectre Mitigations (ARM) (C++ v14.22 ATL for v142 build tools with Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64 | C++ v14.22 ATL for v142 build tools (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64.Spectre | C++ v14.22 ATL for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.22 ATL for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.22 ATL for v142 build tools with Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL.Spectre | C++ v14.22 ATL for v142 build tools with Spectre Mitigations (X86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.CLI.Support | Obsługa języka C++/interfejsu wiersza polecenia dla narzędzi kompilacji w wersji 142 (14.22) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.22.MFC | C++ v14.22 MFC for v142 build tools (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM | C++ v14.22 MFC for v142 build tools (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM.Spectre | C++ v14.22 MFC for v142 build tools with Spectre Mitigations (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64 | C++ v14.22 MFC for v142 build tools (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64.Spectre | C++ v14.22 MFC for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.22 MFC for v142 build tools with Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.Spectre | C++ v14.22 MFC for v142 build tools with Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.x86.x64 | MSVC v142 — narzędzia kompilacji w języku C++ x64/x86 w programie VS 2019 (wersja 14.22) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.22.x86.x64.Spectre | MSVC v142 — biblioteki z ograniczeniami Spectre w programie VS 2019 C++ x64/x86 (wersja 14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM | MSVC v142 — narzędzia kompilacji ARM języka C++ w programie VS 2019 (wersja 14.23) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.23.ARM.Spectre | MSVC v142 — biblioteki z ograniczeniami Spectre w programie VS 2019 C++ ARM (wersja 14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64 | MSVC v142 — narzędzia kompilacji ARM64 języka C++ w programie VS 2019 (wersja 14.23) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.23.ARM64.Spectre | MSVC v142 — biblioteki ze specyfikacją ARM64 w programie VS 2019 C++ z ograniczeniem ryzyka (wersja 14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL | C++ v14.23 ATL for v142 build tools (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM | C++ v14.23 ATL for v142 build tools (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM.Spectre | C++ v14.23 ATL for v142 build tools with Spectre Mitigations (ARM) (C++ v14.23 ATL for v142 build tools with Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64 | C++ v14.23 ATL for v142 build tools (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64.Spectre | C++ v14.23 ATL for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.23 ATL for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.23 ATL for v142 build tools with Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.Spectre | C++ v14.23 ATL for v142 build tools with Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.CLI.Support | Obsługa C++/CLI dla narzędzi kompilacji w wersji 142 (14.23) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.23.MFC | C++ v14.23 MFC for v142 build tools (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM | C++ 14.23 MFC dla narzędzi kompilacji v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM.Spectre | C++ v14.23 MFC for v142 build tools with Spectre Mitigations (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64 | C++ v14.23 MFC for v142 build tools (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64.Spectre | C++ v14.23 MFC for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.23 MFC for v142 build tools with Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.Spectre | C++ v14.23 MFC for v142 build tools with Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.x86.x64 | MSVC v142 — vs 2019 C++ x64/x86 build tools (v14.23) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.23.x86.x64.Spectre | MSVC v142 — biblioteki z ograniczeniem ryzyka Spectre w programie VS 2019 C++ x64/x86 (wersja 14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.24.ARM | MSVC v142 — narzędzia kompilacji ARM języka C++ w programie VS 2019 (wersja 14.24) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.24.ARM.Spectre | MSVC v142 — biblioteki z ograniczeniem ryzyka spectre języka C++ ARM w programie VS 2019 (wersja 14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM64 | MSVC v142 — narzędzia kompilacji ARM64 języka C++ w programie VS 2019 (wersja 14.24) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.24.ARM64.Spectre | MSVC v142 — biblioteki z ograniczeniem ryzyka spectre w języku C++ ARM64 w wersji 2019 (wersja 14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL | C++ v14.24 ATL for v142 build tools (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM | C++ v14.24 ATL for v142 build tools (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM.Spectre | C++ v14.24 ATL for v142 build tools with Spectre Mitigations (ARM) (C++ v14.24 ATL for v142 build tools with Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64 | C++ v14.24 ATL for v142 build tools (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64.Spectre | C++ v14.24 ATL for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.24 ATL for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.24 ATL for v142 build tools with Spectre Mitigations (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.Spectre | C++ v14.24 ATL for v142 build tools with Spectre Mitigations (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.24.CLI.Support | Obsługa C++/CLI dla narzędzi kompilacji w wersji 142 (14.24) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.24.MFC | C++ v14.24 MFC for v142 build tools (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM | C++ 14.24 MFC dla narzędzi kompilacji w wersji 142 (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM.Spectre | C++ v14.24 MFC for v142 build tools with Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64 | C++ 14.24 MFC dla narzędzi kompilacji w wersji 142 (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64.Spectre | C++ v14.24 MFC for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.24 MFC for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.24 MFC for v142 build tools with Spectre Mitigations (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.24.MFC.Spectre | C++ v14.24 MFC for v142 build tools with Spectre Mitigations (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.24.x86.x64 | MSVC v142 — narzędzia kompilacji języka C++ x64/x86 w programie VS 2019 (wersja 14.24) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.24.x86.x64.Spectre | MSVC v142 — biblioteki z ograniczeniami Spectre w programie VS 2019 C++ x64/x86 (wersja 14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.25.ARM | MSVC v142 — narzędzia kompilacji ARM języka C++ w programie VS 2019 (wersja 14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ARM.Spectre | MSVC v142 — biblioteki z ograniczeniami Spectre języka C++ ARM w programie VS 2019 (wersja 14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ARM64 | MSVC v142 — narzędzia kompilacji ARM64 języka C++ w programie VS 2019 (wersja 14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ARM64.Spectre | MSVC v142 — biblioteki z ograniczeniami Spectre w programie VS 2019 C++ ARM64 (wersja 14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ATL | C++ v14.25 ATL for v142 build tools (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM | C++ v14.25 ATL for v142 build tools (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM.Spectre | C++ v14.25 ATL for v142 build tools with Spectre Mitigations (ARM) (C++ v14.25 ATL for v142 build tools with Spectre Mitigations (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM64 | C++ v14.25 ATL for v142 build tools (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM64.Spectre | C++ v14.25 ATL for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.25 ATL for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.25 ATL for v142 build tools with Spectre Mitigations (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.ATL.Spectre | C++ v14.25 ATL for v142 build tools with Spectre Mitigations (X86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.CLI.Support | Obsługa języka C++/interfejsu wiersza polecenia dla narzędzi kompilacji w wersji 142 (14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC | C++ 14.25 MFC dla narzędzi kompilacji w wersji 142 (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM | C++ 14.25 MFC dla narzędzi kompilacji v142 (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM.Spectre | C++ v14.25 MFC for v142 build tools with Spectre Mitigations (ARM) (C++ 14.25 MFC for v142 build tools with Spectre Mitigations (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM64 | C++ 14.25 MFC dla narzędzi kompilacji v142 (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM64.Spectre | C++ v14.25 MFC for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.25 MFC for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.25 MFC for v142 build tools with Spectre Mitigations (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.Spectre | C++ v14.25 MFC for v142 build tools with Spectre Mitigations (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.x86.x64 | MSVC v142 — narzędzia kompilacji w języku C++ x64/x86 w programie VS 2019 (wersja 14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.x86.x64.Spectre | MSVC v142 — vs 2019 C++ x64/x86 Biblioteki z ograniczeniem ryzyka spectre (wersja 14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ARM | MSVC v142 — narzędzia kompilacji ARM języka C++ w programie VS 2019 (wersja 14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ARM.Spectre | MSVC v142 — biblioteki arm, których ograniczanie jest ograniczane przez spectre języka C++ w programie VS 2019 (wersja 14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ARM64 | MSVC v142 — narzędzia kompilacji ARM64 języka C++ w programie VS 2019 (wersja 14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ARM64.Spectre | MSVC v142 — biblioteki ze specyfikacją ARM64 w programie VS 2019 C++ ARM64 (wersja 14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL | C++ v14.26 ATL for v142 build tools (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM | C++ v14.26 ATL for v142 build tools (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM.Spectre | C++ v14.26 ATL for v142 build tools with Spectre Mitigations (ARM) (C++ v14.26 ATL for v142 build tools with Spectre Mitigations (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM64 | C++ v14.26 ATL for v142 build tools (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM64.Spectre | C++ v14.26 ATL for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.26 ATL for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.26 ATL for v142 build tools with Spectre Mitigations (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.Spectre | C++ v14.26 ATL for v142 build tools with Spectre Mitigations (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.CLI.Support | Obsługa C++/CLI dla narzędzi kompilacji w wersji 142 (14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.MFC | C++ v14.26 MFC for v142 build tools (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM | C++ 14.26 MFC dla narzędzi kompilacji v142 (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM.Spectre | C++ v14.26 MFC for v142 build tools with Spectre Mitigations (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM64 | C++ 14.26 MFC dla narzędzi kompilacji w wersji 142 (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM64.Spectre | C++ v14.26 MFC for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.26 MFC for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.26 MFC for v142 build tools with Spectre Mitigations (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.MFC.Spectre | C++ 14.26 MFC for v142 build tools with Spectre Mitigations (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.x86.x64 | MSVC v142 — narzędzia kompilacji programu VS 2019 C++ x64/x86 (wersja 14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.x86.x64.Spectre | MSVC v142 — biblioteki z ograniczeniem ryzyka Spectre w programie VS 2019 C++ x64/x86 (wersja 14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ARM | MSVC v142 — narzędzia kompilacji ARM języka C++ w programie VS 2019 (wersja 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ARM.Spectre | MSVC v142 — biblioteki z ograniczeniami Spectre języka C++ ARM w programie VS 2019 (wersja 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ARM64 | MSVC v142 — narzędzia kompilacji ARM64 języka C++ w programie VS 2019 (wersja 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ARM64.Spectre | MSVC v142 — biblioteki z ograniczeniami Spectre w programie VS 2019 C++ ARM64 (wersja 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL | C++ v14.27 ATL for v142 build tools (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM | C++ v14.27 ATL for v142 build tools (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM.Spectre | C++ v14.27 ATL for v142 build tools with Spectre Mitigations (ARM) (C++ v14.27 ATL for v142 build tools with Spectre Mitigations (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM64 | C++ v14.27 ATL for v142 build tools (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM64.Spectre | C++ v14.27 ATL for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.27 ATL for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.27 ATL for v142 build tools with Spectre Mitigations (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL.Spectre | C++ v14.27 ATL for v142 build tools with Spectre Mitigations (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.CLI.Support | Obsługa języka C++/interfejsu wiersza polecenia dla narzędzi kompilacji w wersji 142 (14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC | C++ v14.27 MFC for v142 build tools (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM | C++ v14.27 MFC for v142 build tools (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM.Spectre | C++ v14.27 MFC for v142 build tools with Spectre Mitigations (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM64 | C++ 14.27 MFC dla narzędzi kompilacji v142 (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM64.Spectre | C++ v14.27 MFC for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.27 MFC for v142 build tools with Spectre Mitigations (ARM64) (C++ v14.27 MFC for v142 build tools with Spectre Mitigations (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.Spectre | C++ v14.27 MFC for v142 build tools with Spectre Mitigations (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.x86.x64 | MSVC v142 — narzędzia kompilacji w języku C++ x64/x86 w programie VS 2019 (wersja 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.x86.x64.Spectre | MSVC v142 — biblioteki z ograniczeniami Spectre w programie VS 2019 C++ x64/x86 (wersja 14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.16.9.ARM | MSVC v142 — narzędzia kompilacji ARM języka C++ w programie VS 2019 (wersja 14.28-16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ARM.Spectre | MSVC v142 — biblioteki z ograniczeniami spectre języka C++ ARM w programie VS 2019 (wersja 14.28–16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ARM64 | MSVC v142 — narzędzia kompilacji ARM64 języka C++ w programie VS 2019 (wersja 14.28-16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ARM64.Spectre | MSVC v142 — biblioteki z ograniczeniem ryzyka Spectre w programie VS 2019 C++ ARM64 (wersja 14.28-16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL | C++ v14.28 (16.9) ATL for v142 build tools (x86 & x64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL.ARM | C++ v14.28 (16.9) ATL for v142 build tools (ARM) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL.ARM.Spectre | C++ v14.28 (16.9) ATL for v142 build tools with Spectre Mitigations (ARM) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL.ARM64 | C++ v14.28 (16.9) ATL for v142 build tools (ARM64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL.ARM64.Spectre | C++ v14.28 (16.9) ATL for v142 build tools with Spectre Mitigations (ARM64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL.Spectre | C++ v14.28 (16.9) ATL for v142 build tools with Spectre Mitigations (x86 & x64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.CLI.Support | Obsługa C++/CLI dla narzędzi kompilacji w wersji 142 (14.28–16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC | C++ v14.28 (16.9) MFC for v142 build tools (x86 & x64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC.ARM | C++ 14.28 (16.9) MFC dla narzędzi kompilacji v142 (ARM) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC.ARM.Spectre | C++ v14.28 (16.9) MFC for v142 build tools with Spectre Mitigations (ARM) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC.ARM64 | C++ v14.28 (16.9) MFC for v142 build tools (ARM64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC.ARM64.Spectre | C++ v14.28 (16.9) MFC for v142 build tools with Spectre Mitigations (ARM64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC.Spectre | C++ v14.28 (16.9) MFC for v142 build tools with Spectre Mitigations (x86 & x64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.x86.x64 | MSVC v142 — narzędzia kompilacji języka C++ x64/x86 w programie VS 2019 (wersja 14.28–16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.x86.x64.Spectre | MSVC v142 — VS 2019 C++ x64/x86 Biblioteki z ograniczeniem ryzyka spectre (wersja 14.28-16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.ARM | MSVC v142 — narzędzia kompilacji ARM języka C++ w programie VS 2019 (wersja 14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ARM.Spectre | MSVC v142 — biblioteki z ograniczeniem ryzyka spectre w programie VS 2019 C++ ARM (wersja 14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ARM64 | MSVC v142 — narzędzia kompilacji ARM64 języka C++ w programie VS 2019 (wersja 14.28–16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ARM64.Spectre | MSVC v142 — biblioteki z ograniczeniami Spectre w programie VS 2019 C++ ARM64 (wersja 14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL | C++ v14.28 (16.8) ATL for v142 build tools (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM | C++ v14.28 (16.8) ATL for v142 build tools (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM.Spectre | C++ v14.28 (16.8) ATL for v142 build tools with Spectre Mitigations (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM64 | C++ v14.28 (16.8) ATL for v142 build tools (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM64.Spectre | C++ v14.28 (16.8) ATL for v142 build tools with Spectre Mitigations (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.Spectre | C++ v14.28 (16.8) ATL for v142 build tools with Spectre Mitigations (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.CLI.Support | Obsługa języka C++/interfejsu wiersza polecenia dla narzędzi kompilacji w wersji 142 (14.28–16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.MFC | C++ v14.28 (16.8) MFC for v142 build tools (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.MFC.ARM | C++ v14.28 (16.8) MFC for v142 build tools (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.MFC.ARM.Spectre | C++ v14.28 (16.8) MFC for v142 build tools with Spectre Mitigations (ARM) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.MFC.ARM64 | C++ v14.28 (16.8) MFC for v142 build tools (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.MFC.ARM64.Spectre | C++ v14.28 (16.8) MFC for v142 build tools with Spectre Mitigations (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.MFC.Spectre | C++ v14.28 (16.8) MFC for v142 build tools with Spectre Mitigations (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.x86.x64 | MSVC v142 — narzędzia kompilacji w języku C++ x64/x86 w programie VS 2019 (wersja 14.28–16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.x86.x64.Spectre | MSVC v142 — vs 2019 C++ x64/x86 biblioteki z ograniczeniami Spectre (v14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.29.16.10.ARM | MSVC v142 — narzędzia kompilacji ARM języka C++ w programie VS 2019 (wersja 14.29-16.10) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.ARM.Spectre | MSVC v142 — biblioteki z ograniczeniami Spectre w programie VS 2019 C++ ARM (wersja 14.29-16.10) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.ARM64 | MSVC v142 — narzędzia kompilacji ARM64 języka C++ w programie VS 2019 (wersja 14.29-16.10) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.ARM64.Spectre | MSVC v142 — biblioteki ze specyfikacją ARM64 w programie VS 2019 c++ arm64 (wersja 14.29-16.10) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.ATL | C++ v14.29 (16.10) ATL for v142 build tools (x86 & x64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.ATL.ARM | C++ v14.29 (16.10) ATL for v142 build tools (ARM) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.ATL.ARM.Spectre | C++ v14.29 (16.10) ATL for v142 build tools with Spectre Mitigations (ARM) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.ATL.ARM64 | C++ v14.29 (16.10) ATL for v142 build tools (ARM64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.ATL.ARM64.Spectre | C++ v14.29 (16.10) ATL for v142 build tools with Spectre Mitigations (ARM64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.ATL.Spectre | C++ v14.29 (16.10) ATL for v142 build tools with Spectre Mitigations (x86 & x64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.CLI.Support | Obsługa języka C++/interfejsu wiersza polecenia dla narzędzi kompilacji w wersji 142 (14.29–16.10) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC | C++ v14.29 (16.10) MFC for v142 build tools (x86 & x64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM | C++ v14.29 (16.10) MFC for v142 build tools (ARM) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM.Spectre | C++ v14.29 (16.10) MFC for v142 build tools with Spectre Mitigations (ARM) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM64 | C++ 14.29 (16.10) MFC dla narzędzi kompilacji v142 (ARM64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM64.Spectre | C++ v14.29 (16.10) MFC for v142 build tools with Spectre Mitigations (ARM64) (C++ 14.29 (16.10) MFC for v142 build tools with Spectre Mitigations (ARM64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.Spectre | C++ v14.29 (16.10) MFC for v142 build tools with Spectre Mitigations (x86 & x64) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.x86.x64 | MSVC v142 — narzędzia kompilacji programu VS 2019 C++ x64/x86 (wersja 14.29-16.10) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.14.29.16.10.x86.x64.Spectre | MSVC v142 — VS 2019 C++ x64/x86 Biblioteki z ograniczeniem ryzyka spectre (wersja 14.29-16.10) | 16.10.31313.121
Microsoft.VisualStudio.Component.VC.ATL.ARM | C++ ATL dla najnowszych narzędzi kompilacji w wersji 142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | C++ ATL for latest v142 build tools with Spectre Mitigations (ARM) (C++ ATL for latest v142 build tools with Spectre Mitigations (ARM) (C++ ATL for latest v142 build tools with Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | C++ ATL dla najnowszych narzędzi do kompilacji w wersji 142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | C++ ATL for latest v142 build tools with Spectre Mitigations (ARM64) (C++ ATL for latest v142 build tools with Spectre Mitigations (ARM64) (C++ ATL for latest v142 build tools with Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATL.ARM64EC | C++ ATL dla najnowszych narzędzi do kompilacji w wersji 142 (ARM64EC — eksperymentalne) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.ATL.ARM64EC.Spectre | C++ ATL for latest v142 build tools with Spectre Mitigations (ARM64EC — experimental) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.ATL.Spectre | C++ ATL for latest v142 build tools with Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | C++ MFC for latest v142 build tools with Spectre Mitigations (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM | C++ MFC dla najnowszych narzędzi do kompilacji w wersji 142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | C++ MFC dla najnowszych narzędzi kompilacji w wersji 142 z ograniczeniem ryzyka Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | C++ MFC dla najnowszych narzędzi do kompilacji w wersji 142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | C++ MFC dla najnowszych narzędzi kompilacji w wersji 142 z ograniczeniem ryzyka Spectre (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64EC | C++ MFC dla najnowszych narzędzi kompilacji w wersji 142 (ARM64EC — eksperymentalne) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.MFC.ARM64EC.Spectre | C++ MFC dla najnowszych narzędzi do kompilacji w wersji 142 z ograniczeniem ryzyka Spectre (ARM64EC — eksperymentalne) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.Redist.MSM | Redystrybucyjne msMs w języku C++ 2019 | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC v142 — biblioteki arm, których ograniczanie jest ograniczane przez spectre języka C++ w programie VS 2019 (najnowsza wersja) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC v142 — biblioteki z ograniczeniem ryzyka spectre w programie VS 2019 C++ ARM64 (najnowsza wersja) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64EC.Spectre | MSVC v142 — VS 2019 C++ ARM64EC Biblioteki minimalizowane przez spectre (Najnowsza wersja — eksperymentalne) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC v142 — biblioteki z ograniczeniami Spectre w programie VS 2019 C++ x64/x86 (najnowsza wersja)  | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141 — biblioteki z ograniczeniami Spectre w programie VS 2017 C++ ARM (wersja 14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141 — biblioteki z ograniczeniami Spectre w programie VS 2017 C++ ARM64 (wersja 14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ATL | C++ ATL for v141 build tools (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | C++ ATL for v141 build tools (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | C++ ATL for v141 build tools with Spectre Mitigations (ARM) (C++ ATL for v141 build tools with Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | C++ ATL for v141 build tools (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | C++ ATL for v141 build tools with Spectre Mitigations (ARM64) (C++ ATL for v141 build tools with Spectre Mitigations (ARM64) (C++ ATL for v141 build tools with Spectre Mitigations (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | C++ ATL for v141 build tools with Spectre Mitigations (X86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | Obsługa języka C++/interfejsu wiersza polecenia dla narzędzi kompilacji w wersji 141 (14.16) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.v141.MFC | C++ MFC for v141 build tools (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | C++ MFC for v141 build tools (ARM) | 16.2.28915.88
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | C++ MFC for v141 build tools with Spectre Mitigations (ARM) (C++ MFC for v141 build tools with Spectre Mitigations (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | C++ MFC dla narzędzi kompilacji v141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | C++ MFC for v141 build tools with Spectre Mitigations (ARM64) (C++ MFC for v141 build tools with Spectre Mitigations (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | Narzędzia kompilacji MFC języka C++ dla wersji 141 z ograniczeniem ryzyka Spectre (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141 — biblioteki z ograniczeniami Spectre w programie VS 2017 C++ x64/x86 (wersja 14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usługi | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | Obsługa języka C++ w systemie Windows XP dla narzędzi programu VS 2017 (wersja 141) [przestarzałe] | 16.10.31205.252
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.10.31205.180
