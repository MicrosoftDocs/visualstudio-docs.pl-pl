---
title: Identyfikatory obciążenia i składników społeczności programu Visual Studio 2019
titleSuffix: ''
description: Używanie identyfikatorów obciążenia i składników do instalowania programu Visual Studio przy użyciu wiersza polecenia lub określania zależności w manifeście vsix
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 03/16/2020
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 03537e74968e9c4e2fb9ffa42541575813dbca88
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79437683"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-community-2019"></a>Edytor podstawowy programu Visual Studio (dołączony do programu Visual Studio Community 2019)

**Identyfikator:** Microsoft.VisualStudio.Workload.CoreEditor

**Opis:** Środowisko powłoki rdzenia programu Visual Studio, w tym edycja kodu ze składni, kontrola kodu źródłowego i zarządzanie elementami roboczymi.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Edytor podstawowy programu Visual Studio | 16.1.28811.260 | Wymagany
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Strona startowa programu Visual Studio dla użytkowników języka C++ | 16.0.28315.86 | Optional (Opcjonalność)

## <a name="azure-development"></a>Tworzenie aplikacji na platformie Azure

**Identyfikator:** Platforma Microsoft.VisualStudio.Workload.Azure

**Opis:** Zestawy SDK platformy Azure, narzędzia i projekty do tworzenia aplikacji w chmurze i tworzenia zasobów przy użyciu platformy .NET Core i .NET Framework. Zawiera również narzędzia do konteneryzacji aplikacji, w tym obsługę platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.Microsoft.VisualStudio.RazorEkstrysja | Usługi językowe brzytwy | 16.0.28714.129 | Wymagany
Składnik.Microsoft.VisualStudio.Web.AzureFunkcje | Narzędzia azure webjobs | 16.0.28714.129 | Wymagany
Składnik.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Wymagany
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 16.0.28517.75 | Wymagany
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 16.0.28517.75 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 16.0.28517.75 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.7.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.7.2 | 16.0.28517.75 | Wymagany
Składnik Microsoft.Net.4.8.SDK | Plik SDK programu .NET Framework 4.8 | 16.4.29313.120 | Wymagany
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.7.2 | 16.3.29207.166 | Wymagany
Microsoft.NetCore.Component.DevelopmentTools | Narzędzia programistyczne .NET Core | 16.5.29721.120 | Wymagany
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko wykonawcze .NET Core 3.1 LTS | 16.5.29905.7 | Wymagany
Microsoft.NetCore.Component.SDK | Zestaw .NET Core SDK | 16.5.29905.7 | Wymagany
Składnik Microsoft.NetCore.Web | Narzędzia programistyczne .NET Core | 16.5.29721.120 | Wymagany
Narzędzia Microsoft.VisualStudio.Component.Azure.AuthoringTools | Narzędzia do tworzenia platformy Azure | 16.0.28625.61 | Wymagany
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki platformy Azure dla platformy .NET | 16.0.28315.86 | Wymagany
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 16.1.28810.153 | Wymagany
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.4.29313.120 | Wymagany
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Wymagany
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.4.29409.204 | Wymagany
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.4.29409.204 | Wymagany
Microsoft.VisualStudio.Component.FSharp | Obsługa języka Języka F# | 16.0.28315.86 | Wymagany
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Obsługa języka F# dla projektów internetowych | 16.3.29207.166 | Wymagany
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagany
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 16.5.29721.120 | Wymagany
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Rdzeń zarządzanego obciążenia pulpitu | 16.4.29318.151 | Wymagany
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik ODBC programu SQL Server | 16.0.28625.61 | Wymagany
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.5.29515.121 | Wymagany
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko wykonawcze SQL ADAL | 16.0.28517.75 | Wymagany
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagany
Źródła danych Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla obsługi programu SQL Server | 16.0.28315.86 | Wymagany
Środowisko wykonawcze Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagany
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Wymagany
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 16.0.28625.61 | Wymagany
Składnik Microsoft.VisualStudio.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Wymagany
Składnik Microsoft.VisualStudio.Web | narzędzia do tworzenia ASP.NET i tworzenia stron internetowych | 16.0.28517.75 | Wymagany
Wymagania wstępne microsoft.VisualStudio.ComponentGroup.Azure.Wymagania wstępne | Wymagania wstępne dotyczące tworzenia platformy Azure | 16.4.29409.204 | Wymagany
Microsoft.VisualStudio.ComponentGroup.AzureFunkcje | Narzędzia azure webjobs | 16.0.28621.142 | Wymagany
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne ASP.NET i narzędzi do tworzenia stron internetowych | 16.4.29318.151 | Wymagany
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.0.28621.142 | Wymagany
Narzędzia Microsoft.Component.Azure.DataLake.Tools | Narzędzia usługi Azure Data Lake i Stream Analytics | 16.5.29721.120 | Zalecane
Pakiet targetingu firmy Microsoft.Net.Component.4.5.1.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.1 | 16.0.28517.75 | Zalecane
Pakiet targeting firmy Microsoft.Net.Component.4.6.TargetingPack | Pakiet targetowania programu .NET Framework 4.6 | 16.0.28517.75 | Zalecane
Pakiet docelowy firmy Microsoft.Net.Component.4.TargetingPack | Pakiet targetowania programu .NET Framework 4 | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 narzędzia programistyczne | 16.0.28516.191 | Zalecane
Microsoft.Net.Core.Component.SDK.2.1 | Środowisko wykonawcze .NET Core 2.1 LTS | 16.5.29905.7 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane funkcje ASP.NET | 16.0.28315.86 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Narzędzia Visual Studio Tools for Kubernetes | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.Powershell | Azure PowerShell | 16.5.29515.121 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Podstawowe narzędzia usługi Azure Resource Manager | 16.4.29409.204 | Zalecane
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Narzędzia usługi Service Fabric | 16.4.29313.120 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton | Podstawowe narzędzia usług w chmurze azure | 16.4.29409.204 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do tworzenia usług w chmurze azure | 16.3.29207.166 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 16.5.29515.121 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Narzędzia usługi w chmurze platformy Azure | 16.4.29409.204 | Zalecane
Narzędzia Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Narzędzia usługi Azure Resource Manager | 16.0.28528.71 | Zalecane
Pakiet targetingpakingu microsoft.net.component.4.6.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.6.2 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targetingu firmy Microsoft.Net.Component.4.7.1.TargetingPack | Pakiet kierowania .NET Framework 4.7.1 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.7.TargetingPack | Pakiet targetowania programu .NET Framework 4.7 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.8.TargetingPack | Pakiet targetowania programu .NET Framework 4.8 | 16.4.29313.120 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Narzędzia programistyczne .NET Framework 4.6.1 | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Narzędzia programistyczne .NET Framework 4.6.2 | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7.1 | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7 | 16.3.29207.166 | Optional (Opcjonalność)
Narzędzia microsoft.net.componentgroup.4.8.DeveloperTools | Narzędzia programistyczne .NET Framework 4.8 | 16.4.29318.151 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional (Opcjonalność)

## <a name="data-storage-and-processing"></a>Magazynowanie i przetwarzanie danych

**Identyfikator:** Microsoft.VisualStudio.Workload.Data

**Opis:** Połącz, opracuj i przetestuj rozwiązania danych za pomocą programu SQL Server, usługi Azure Data Lake lub Hadoop.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.Microsoft.VisualStudio.RazorEkstrysja | Usługi językowe brzytwy | 16.0.28714.129 | Zalecane
Składnik.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Zalecane
Narzędzia Microsoft.Component.Azure.DataLake.Tools | Narzędzia usługi Azure Data Lake i Stream Analytics | 16.5.29721.120 | Zalecane
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Zalecane
Pakiet targetingu firmy Microsoft.Net.Component.4.5.1.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.1 | 16.0.28517.75 | Zalecane
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 16.0.28517.75 | Zalecane
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 16.0.28517.75 | Zalecane
Pakiet targeting firmy Microsoft.Net.Component.4.6.TargetingPack | Pakiet targetowania programu .NET Framework 4.6 | 16.0.28517.75 | Zalecane
Pakiet targetingpakingu microsoft.net.component.4.7.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.7.2 | 16.0.28517.75 | Zalecane
Składnik Microsoft.Net.4.8.SDK | Plik SDK programu .NET Framework 4.8 | 16.4.29313.120 | Zalecane
Pakiet docelowy firmy Microsoft.Net.Component.4.TargetingPack | Pakiet targetowania programu .NET Framework 4 | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.7.2 | 16.3.29207.166 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 narzędzia programistyczne | 16.0.28516.191 | Zalecane
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko wykonawcze .NET Core 3.1 LTS | 16.5.29905.7 | Zalecane
Microsoft.NetCore.Component.SDK | Zestaw .NET Core SDK | 16.5.29905.7 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.Azure.AuthoringTools | Narzędzia do tworzenia platformy Azure | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki platformy Azure dla platformy .NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 16.1.28810.153 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.4.29313.120 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton | Podstawowe narzędzia usług w chmurze azure | 16.4.29409.204 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do tworzenia usług w chmurze azure | 16.3.29207.166 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.4.29409.204 | Zalecane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.4.29409.204 | Zalecane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 16.5.29721.120 | Zalecane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Rdzeń zarządzanego obciążenia pulpitu | 16.4.29318.151 | Zalecane
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik ODBC programu SQL Server | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 16.0.28714.129 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.5.29515.121 | Zalecane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko wykonawcze SQL ADAL | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Zalecane
Źródła danych Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla obsługi programu SQL Server | 16.0.28315.86 | Zalecane
Środowisko wykonawcze Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Zalecane
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 16.0.28625.61 | Zalecane
Składnik Microsoft.VisualStudio.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Zalecane
Składnik Microsoft.VisualStudio.Web | narzędzia do tworzenia ASP.NET i tworzenia stron internetowych | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne ASP.NET i narzędzi do tworzenia stron internetowych | 16.4.29318.151 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.0.28621.142 | Zalecane
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.FSharp.Desktop | Obsługa języka pulpitu F# | 16.0.28315.86 | Optional (Opcjonalność)

## <a name="data-science-and-analytical-applications"></a>Aplikacje do analizy i przetwarzania danych

**Identyfikator:** Microsoft.VisualStudio.Workload.DataScience

**Opis:** Języki i narzędzia do tworzenia aplikacji do nauki o danych, w tym Python i F#.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.PythonTools | Obsługa języka Języka Python | 16.5.29515.121 | Zalecane
Składnik Microsoft.PythonDoczy.Minicondax64 | Python miniconda | 16.2.29003.222 | Zalecane
Microsoft.Component.PythonTools.Web | Pomoc techniczna języka Python | 16.0.28517.75 | Zalecane
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.4.29409.204 | Zalecane
Microsoft.VisualStudio.Component.FSharp.Desktop | Obsługa języka pulpitu F# | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 16.5.29721.120 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 16.0.28714.129 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.5.29515.121 | Zalecane
Składnik Microsoft.VisualStudio.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.0.28621.142 | Zalecane
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Natywne narzędzia programistyczne Języka Python | 16.2.29020.229 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler GPU dla DirectX | 16.0.28625.61 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.0.28625.61 | Optional (Opcjonalność)
Narzędzia diagnostyczne Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania języka C++ | 16.5.29515.121 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 narzędzia kompilacji (wersja 14.25) | 16.5.29721.120 | Optional (Opcjonalność)
Składnik Microsoft.VisualStudio.Component.Windows10SDK | Uniwersalny czas pracy systemu Windows C | 16.4.29409.204 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Optional (Opcjonalność)

## <a name="net-desktop-development"></a>Programowa firma .NET

**Identyfikator:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Opis:** Tworzenie aplikacji WPF, Windows Forms i konsoli przy użyciu języka C#, Visual Basic i F# za pomocą programów .NET Core i .NET Framework.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.7.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.7.2 | 16.0.28517.75 | Wymagany
Składnik Microsoft.Net.4.8.SDK | Plik SDK programu .NET Framework 4.8 | 16.4.29313.120 | Wymagany
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.7.2 | 16.3.29207.166 | Wymagany
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko wykonawcze .NET Core 3.1 LTS | 16.5.29905.7 | Wymagany
Microsoft.NetCore.Component.SDK | Zestaw .NET Core SDK | 16.5.29905.7 | Wymagany
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Wymagany
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Rdzeń zarządzanego obciążenia pulpitu | 16.4.29318.151 | Wymagany
Microsoft.VisualStudio.Component.ManagedDesktop.Wymagania wstępne | Narzędzia programistyczne dla komputerów .NET | 16.5.29514.35 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.5.29515.121 | Wymagany
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagany
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 16.0.28625.61 | Wymagany
Składnik.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Zalecane
Składnik Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Zalecane
Pakiet targetingu firmy Microsoft.Net.Component.4.5.1.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.1 | 16.0.28517.75 | Zalecane
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 16.0.28517.75 | Zalecane
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 16.0.28517.75 | Zalecane
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 16.0.28517.75 | Zalecane
Pakiet targeting firmy Microsoft.Net.Component.4.6.TargetingPack | Pakiet targetowania programu .NET Framework 4.6 | 16.0.28517.75 | Zalecane
Pakiet docelowy firmy Microsoft.Net.Component.4.TargetingPack | Pakiet targetowania programu .NET Framework 4 | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 narzędzia programistyczne | 16.0.28516.191 | Zalecane
Microsoft.Net.Core.Component.SDK.2.1 | Środowisko wykonawcze .NET Core 2.1 LTS | 16.5.29905.7 | Zalecane
Microsoft.NetCore.Component.DevelopmentTools | Narzędzia programistyczne .NET Core | 16.5.29721.120 | Zalecane
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger just-in-time | 16.0.28517.75 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 16.5.29515.121 | Zalecane
Microsoft.VisualStudio.Component.EntityFramework | Narzędzia entity Framework 6 | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.FSharp | Obsługa języka Języka F# | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Zalecane
Składnik.Dotfuscator | PreEmptive Protection — Dotfuscator | 16.0.28528.71 | Optional (Opcjonalność)
Składnik.Microsoft.VisualStudio.RazorEkstrysja | Usługi językowe brzytwy | 16.0.28714.129 | Optional (Opcjonalność)
Składnik.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.6.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.6.2 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targetingu firmy Microsoft.Net.Component.4.7.1.TargetingPack | Pakiet kierowania .NET Framework 4.7.1 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.7.TargetingPack | Pakiet targetowania programu .NET Framework 4.7 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.8.TargetingPack | Pakiet targetowania programu .NET Framework 4.8 | 16.4.29313.120 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Narzędzia programistyczne .NET Framework 4.6.1 | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Narzędzia programistyczne .NET Framework 4.6.2 | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7.1 | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7 | 16.3.29207.166 | Optional (Opcjonalność)
Narzędzia microsoft.net.componentgroup.4.8.DeveloperTools | Narzędzia programistyczne .NET Framework 4.8 | 16.4.29318.151 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.4.29409.204 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.4.29409.204 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.FSharp.Desktop | Obsługa języka pulpitu F# | 16.0.28315.86 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 16.5.29721.120 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik ODBC programu SQL Server | 16.0.28625.61 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.PortableBrary | Pakiet kierowania na bibliotekę przenośną platformy .NET | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko wykonawcze SQL ADAL | 16.0.28517.75 | Optional (Opcjonalność)
Źródła danych Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla obsługi programu SQL Server | 16.0.28315.86 | Optional (Opcjonalność)
Środowisko wykonawcze Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Optional (Opcjonalność)
Składnik Microsoft.VisualStudio.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional (Opcjonalność)
Składnik Microsoft.VisualStudio.Web | narzędzia do tworzenia ASP.NET i tworzenia stron internetowych | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Narzędzia do pakowania MSIX | 16.4.29409.204 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne ASP.NET i narzędzi do tworzenia stron internetowych | 16.4.29318.151 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.0.28621.142 | Optional (Opcjonalność)

## <a name="game-development-with-unity"></a>Opracowywanie gier za pomocą aparatu Unity

**Identyfikator:** Microsoft.VisualStudio.Workload.ManagedGame

**Opis:** Twórz gry 2D i 3D dzięki Unity, potężnemu środowisku programistycznemu na różnych platformach.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Narzędzia programistyczne .NET Framework 3.5 | 16.0.28517.75 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.7.1.TargetingPack | Pakiet kierowania .NET Framework 4.7.1 | 16.0.28517.75 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.5.29515.121 | Wymagany
Microsoft.VisualStudio.Component.Unity | Narzędzia Visual Studio Tools for Unity | 16.0.28315.86 | Wymagany
Składnik.UnityEngine.x64 | 64-bitowy edytor Unity 2019.2 | 16.5.29515.121 | Zalecane
Składnik.UnityEngine.x86 | Edytor 32-bitowy Unity 5.6 | 16.1.28811.260 | Zalecane

## <a name="linux-development-with-c"></a>Programowanie dla systemu Linux w języku C++

**Identyfikator:** Platforma Microsoft.VisualStudio.Workload.NativeCrossPlat

**Opis:** Tworzenie i debugowanie aplikacji działających w środowisku systemu Linux.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.MDD.Linux | C++ dla rozwoju Linuksa | 16.5.29515.121 | Wymagany
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Wymagany
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.0.28625.61 | Wymagany
Składnik.Linux.CMake | C++ CMake narzędzia dla Linuksa | 16.2.29003.222 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.0.28621.142 | Zalecane
Składnik.MDD.Linux.GCC.arm | Wbudowane i IoT narzędzia programistyczne | 16.5.29515.121 | Optional (Opcjonalność)

## <a name="desktop-development-with-c"></a>Programowanie aplikacji klasycznych w języku C++

**Identyfikator:** Microsoft.VisualStudio.Workload.NativeDesktop

**Opis:** Twórz nowoczesne aplikacje języka C++ dla systemu Windows przy użyciu wybranych narzędzi, takich jak MSVC, Clang, CMake lub MSBuild.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagany
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagany
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 16.0.28625.61 | Wymagany
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.0.28625.61 | Wymagany
Microsoft.VisualStudio.Component.VC.Redist.14.Najnowsze | Aktualizacja redystrybucjowa C++ 2019 | 16.5.29515.121 | Wymagany
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Funkcje pulpitu w języku C++ | 16.2.29012.281 | Wymagany
Składnik.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Zalecane
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger just-in-time | 16.0.28517.75 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler GPU dla DirectX | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Zalecane
Microsoft.VisualStudio.Component.VC.ASAN | Adresy C++Sanitizer (eksperymentalny) | 16.5.29515.121 | Zalecane
Microsoft.VisualStudio.Component.VC.ATL | C++ ATL dla najnowszych narzędzi do kompilacji w wersji 142 (x86 & x64) | 16.4.29313.120 | Zalecane
Microsoft.VisualStudio.Component.VC.CMake.Project | C++ CMake narzędzia dla systemu Windows | 16.3.29103.31 | Zalecane
Narzędzia diagnostyczne Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania języka C++ | 16.5.29515.121 | Zalecane
Test Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Adapter testowy do boost.test | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Adapter testowy do testu Google | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 narzędzia kompilacji (wersja 14.25) | 16.5.29721.120 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.CMake | edytor JSON | 16.3.29207.166 | Zalecane
Składnik.Incredibuild | IncrediBuild - Przyspieszenie kompilacji | 16.5.29721.120 | Optional (Opcjonalność)
Składnik.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Optional (Opcjonalność)
Składnik.VC.Środowisko wykonawcze.UCRTSDK firmy Microsoft.Component.VC.Runtime.UCRTSDK | Uniwersalny zestaw CRT systemu Windows | 16.0.28625.61 | Optional (Opcjonalność)
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 16.0.28517.75 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.8.SDK | Plik SDK programu .NET Framework 4.8 | 16.4.29313.120 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Optional (Opcjonalność)
Składnik.140 firmy Microsoft.VisualStudio.Component.VC.140 | MSVC v140 — VS 2015 C++ narzędzia kompilacji (wersja 14.00) | 16.0.28625.61 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.ATLMFC | C++ MFC dla najnowszych narzędzi do budowania v142 (x86 & x64) | 16.4.29313.120 | Optional (Opcjonalność)
Pomoc techniczna aplikacji Microsoft.VisualStudio.Component.VC.CLI.Support | Obsługa C++/CLI dla narzędzi kompilacji w wersji 142 (14.25) | 16.5.29721.120 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Llvm.Clang | Kompilator klanów C++ dla systemu Windows (9.0.0) | 16.5.29515.121 | Optional (Opcjonalność)
Zestaw microsoft.VisualStudio.Component.VC.Llvm.ClangToolset | C++ Clang-cl dla narzędzi do budowania v142 (x64/x86) | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduły C++ dla narzędzi do budowania wersji 142 (x64/x86 – eksperymentalne) | 16.0.28625.61 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ x64/x86 narzędzia kompilacji (wersja 14.16) | 16.1.28829.92 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Llvm.Clang | Narzędzia C++ Clang dla systemu Windows (9.0.0 - x64/x86) | 16.5.29514.35 | Optional (Opcjonalność)

## <a name="game-development-with-c"></a>Programowanie gier w języku C++

**Identyfikator:** Microsoft.VisualStudio.Workload.NativeGame

**Opis:** Wykorzystaj pełną moc języka C++, aby tworzyć profesjonalne gry oparte na programach DirectX, Unreal lub Cocos2d.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Wymagany
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.0.28625.61 | Wymagany
Microsoft.VisualStudio.Component.VC.Redist.14.Najnowsze | Aktualizacja redystrybucjowa C++ 2019 | 16.5.29515.121 | Wymagany
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 narzędzia kompilacji (wersja 14.25) | 16.5.29721.120 | Wymagany
Składnik Microsoft.VisualStudio.Component.Windows10SDK | Uniwersalny czas pracy systemu Windows C | 16.4.29409.204 | Wymagany
Narzędzia Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler GPU dla DirectX | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.VC.ASAN | Adresy C++Sanitizer (eksperymentalny) | 16.5.29515.121 | Zalecane
Narzędzia diagnostyczne Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania języka C++ | 16.5.29515.121 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Zalecane
Składnik.Android.NDK.R16B | Android NDK (R16B) | 16.5.29916.74 | Optional (Opcjonalność)
Składnik.Android.SDK25.Private | Konfiguracja SDK systemu Android (poziom INTERFEJSU API 25) (instalacja lokalna dla rozwoju urządzeń przenośnych z C++) | 16.0.28625.61 | Optional (Opcjonalność)
Składnik.Ant | Mrówka Apache (1.9.3) | 1.9.3.8 | Optional (Opcjonalność)
Składnik.Cocos | Cocos | 16.0.28315.86 | Optional (Opcjonalność)
Składnik.Incredibuild | IncrediBuild - Przyspieszenie kompilacji | 16.5.29721.120 | Optional (Opcjonalność)
Składnik.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Optional (Opcjonalność)
Składnik.MDD.Android | Narzędzia programistyczne dla systemu Android w języku C++ | 16.0.28517.75 | Optional (Opcjonalność)
Składnik.OpenJDK | OpenJDK (dystrybucja firmy Microsoft) | 16.1.28811.260 | Optional (Opcjonalność)
Składnik.Nierealne | Instalator Unreal Engine | 16.1.28810.153 | Optional (Opcjonalność)
Składnik.Unreal.Android | Obsługa środowiska Android IDE dla silnika Unreal | 16.1.28810.153 | Optional (Opcjonalność)
Pakiet targetingu firmy Microsoft.Net.Component.4.5.1.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.1 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.6.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.6.2 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.6.TargetingPack | Pakiet targetowania programu .NET Framework 4.6 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.7.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.7.2 | 16.0.28517.75 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.8.SDK | Plik SDK programu .NET Framework 4.8 | 16.4.29313.120 | Optional (Opcjonalność)
Pakiet docelowy firmy Microsoft.Net.Component.4.TargetingPack | Pakiet targetowania programu .NET Framework 4 | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.7.2 | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 narzędzia programistyczne | 16.0.28516.191 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet cele i budować zadania | 16.1.28829.92 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 16.0.28714.129 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.5.29515.121 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Optional (Opcjonalność)

## <a name="mobile-development-with-c"></a>Tworzenie aplikacji mobilnych w języku C++

**Identyfikator:** Microsoft.VisualStudio.Workload.NativeMobile

**Opis:** Tworzenie aplikacji wieloplatformowych dla systemów iOS, Android lub Windows przy użyciu języka C++.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.Android.SDK25.Private | Konfiguracja SDK systemu Android (poziom INTERFEJSU API 25) (instalacja lokalna dla rozwoju urządzeń przenośnych z C++) | 16.0.28625.61 | Wymagany
Składnik.OpenJDK | OpenJDK (dystrybucja firmy Microsoft) | 16.1.28811.260 | Wymagany
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Wymagany
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.0.28625.61 | Wymagany
Składnik.Android.NDK.R16B | Android NDK (R16B) | 16.5.29916.74 | Zalecane
Składnik.Ant | Mrówka Apache (1.9.3) | 1.9.3.8 | Zalecane
Składnik.MDD.Android | Narzędzia programistyczne dla systemu Android w języku C++ | 16.0.28517.75 | Zalecane
Składnik.Android.NDK.R16B_3264 | Android NDK (R16B) (32-bitowy) | 16.5.29916.74 | Optional (Opcjonalność)
Składnik.Google.Android.Emulator.API25.Private | Google Android Emulator (API Poziom 25) (instalacja lokalna) | 16.1.28810.153 | Optional (Opcjonalność)
Składnik.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (instalacja lokalna) | 16.0.28528.71 | Optional (Opcjonalność)
Składnik.Incredibuild | IncrediBuild - Przyspieszenie kompilacji | 16.5.29721.120 | Optional (Opcjonalność)
Składnik.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Optional (Opcjonalność)
Składnik.MDD.IOS | Narzędzia programistyczne systemu iOS w języku C++ | 16.0.28517.75 | Optional (Opcjonalność)

## <a name="net-core-cross-platform-development"></a>Tworzenie aplikacji dla wielu platform w środowisku .NET Core

**Identyfikator:** Microsoft.VisualStudio.Workload.NetCoreTools

**Opis:** Twórz aplikacje wieloplatformowe przy użyciu platformy .NET Core, ASP.NET Core, HTML/JavaScript i Kontenery, w tym obsługę platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.Microsoft.VisualStudio.RazorEkstrysja | Usługi językowe brzytwy | 16.0.28714.129 | Wymagany
Składnik.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Wymagany
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 16.0.28517.75 | Wymagany
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 16.0.28517.75 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 16.0.28517.75 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.7.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.7.2 | 16.0.28517.75 | Wymagany
Składnik Microsoft.Net.4.8.SDK | Plik SDK programu .NET Framework 4.8 | 16.4.29313.120 | Wymagany
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.7.2 | 16.3.29207.166 | Wymagany
Microsoft.NetCore.Component.DevelopmentTools | Narzędzia programistyczne .NET Core | 16.5.29721.120 | Wymagany
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko wykonawcze .NET Core 3.1 LTS | 16.5.29905.7 | Wymagany
Microsoft.NetCore.Component.SDK | Zestaw .NET Core SDK | 16.5.29905.7 | Wymagany
Składnik Microsoft.NetCore.Web | Narzędzia programistyczne .NET Core | 16.5.29721.120 | Wymagany
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.4.29409.204 | Wymagany
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.4.29409.204 | Wymagany
Microsoft.VisualStudio.Component.FSharp | Obsługa języka Języka F# | 16.0.28315.86 | Wymagany
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Obsługa języka F# dla projektów internetowych | 16.3.29207.166 | Wymagany
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagany
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 16.5.29721.120 | Wymagany
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Rdzeń zarządzanego obciążenia pulpitu | 16.4.29318.151 | Wymagany
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik ODBC programu SQL Server | 16.0.28625.61 | Wymagany
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.5.29515.121 | Wymagany
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko wykonawcze SQL ADAL | 16.0.28517.75 | Wymagany
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagany
Źródła danych Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla obsługi programu SQL Server | 16.0.28315.86 | Wymagany
Środowisko wykonawcze Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagany
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Wymagany
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 16.0.28625.61 | Wymagany
Składnik Microsoft.VisualStudio.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Wymagany
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne ASP.NET i narzędzi do tworzenia stron internetowych | 16.4.29318.151 | Wymagany
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.0.28621.142 | Wymagany
Składnik.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Zalecane
Składnik.Microsoft.VisualStudio.Web.AzureFunkcje | Narzędzia azure webjobs | 16.0.28714.129 | Zalecane
Microsoft.Net.Core.Component.SDK.2.1 | Środowisko wykonawcze .NET Core 2.1 LTS | 16.5.29905.7 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia do analizy deweloperów | 16.5.29515.121 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.Azure.AuthoringTools | Narzędzia do tworzenia platformy Azure | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki platformy Azure dla platformy .NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 16.1.28810.153 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.4.29313.120 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 16.5.29515.121 | Zalecane
Składnik Microsoft.VisualStudio.Web | narzędzia do tworzenia ASP.NET i tworzenia stron internetowych | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.AzureFunkcje | Narzędzia azure webjobs | 16.0.28621.142 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Narzędzia chmurowe do tworzenia stron internetowych | 16.2.29003.222 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.IISRozwój | Obsługa programów IIS w czasie rozwoju | 16.0.28315.86 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Narzędzia do pakowania MSIX | 16.4.29409.204 | Optional (Opcjonalność)

## <a name="mobile-development-with-net"></a>Rozwój urządzeń mobilnych z systemem .NET

**Identyfikator:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Opis:** Tworzenie aplikacji wieloplatformowych dla systemów iOS, Android lub Windows przy użyciu platformy Xamarin.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.OpenJDK | OpenJDK (dystrybucja firmy Microsoft) | 16.1.28811.260 | Wymagany
Składnik.Xamarin | Xamarin | 16.5.29721.120 | Wymagany
Składnik.Xamarin.RemotedSimulator | Symulator zdalnego sterowania platformy Xamarin | 16.0.28315.86 | Wymagany
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 16.0.28517.75 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.7.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.7.2 | 16.0.28517.75 | Wymagany
Składnik Microsoft.Net.4.8.SDK | Plik SDK programu .NET Framework 4.8 | 16.4.29313.120 | Wymagany
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.7.2 | 16.3.29207.166 | Wymagany
Microsoft.NetCore.Component.DevelopmentTools | Narzędzia programistyczne .NET Core | 16.5.29721.120 | Wymagany
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko wykonawcze .NET Core 3.1 LTS | 16.5.29905.7 | Wymagany
Microsoft.NetCore.Component.SDK | Zestaw .NET Core SDK | 16.5.29905.7 | Wymagany
Microsoft.VisualStudio.Component.FSharp | Obsługa języka Języka F# | 16.0.28315.86 | Wymagany
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Wymagany
Microsoft.VisualStudio.Component.Merq | Typowe narzędzia wewnętrzne platformy Xamarin | 16.2.29012.281 | Wymagany
Składnik Microsoft.VisualStudio.Component.MonoDebugger | Debuger mono | 16.0.28517.75 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.5.29515.121 | Wymagany
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | ASP.NET silnik do tworzenia maszyn | 16.0.28315.86 | Wymagany
Składnik.Android.SDK28 | Konfiguracja SDK systemu Android (poziom interfejsu API 28) | 16.2.29003.222 | Zalecane

## <a name="aspnet-and-web-development"></a>Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych

**Identyfikator:** Microsoft.VisualStudio.Workload.NetWeb

**Opis:** Twórz aplikacje internetowe przy użyciu ASP.NET Core, ASP.NET, HTML/JavaScript i Kontenery, w tym obsługę platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.Microsoft.VisualStudio.RazorEkstrysja | Usługi językowe brzytwy | 16.0.28714.129 | Wymagany
Składnik.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Wymagany
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 16.0.28517.75 | Wymagany
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 16.0.28517.75 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 16.0.28517.75 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.7.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.7.2 | 16.0.28517.75 | Wymagany
Składnik Microsoft.Net.4.8.SDK | Plik SDK programu .NET Framework 4.8 | 16.4.29313.120 | Wymagany
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.7.2 | 16.3.29207.166 | Wymagany
Microsoft.NetCore.Component.DevelopmentTools | Narzędzia programistyczne .NET Core | 16.5.29721.120 | Wymagany
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko wykonawcze .NET Core 3.1 LTS | 16.5.29905.7 | Wymagany
Microsoft.NetCore.Component.SDK | Zestaw .NET Core SDK | 16.5.29905.7 | Wymagany
Składnik Microsoft.NetCore.Web | Narzędzia programistyczne .NET Core | 16.5.29721.120 | Wymagany
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.4.29409.204 | Wymagany
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.4.29409.204 | Wymagany
Microsoft.VisualStudio.Component.FSharp | Obsługa języka Języka F# | 16.0.28315.86 | Wymagany
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Obsługa języka F# dla projektów internetowych | 16.3.29207.166 | Wymagany
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagany
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 16.5.29721.120 | Wymagany
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Rdzeń zarządzanego obciążenia pulpitu | 16.4.29318.151 | Wymagany
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik ODBC programu SQL Server | 16.0.28625.61 | Wymagany
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.5.29515.121 | Wymagany
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko wykonawcze SQL ADAL | 16.0.28517.75 | Wymagany
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagany
Źródła danych Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla obsługi programu SQL Server | 16.0.28315.86 | Wymagany
Środowisko wykonawcze Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagany
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Wymagany
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 16.0.28625.61 | Wymagany
Składnik Microsoft.VisualStudio.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Wymagany
Składnik Microsoft.VisualStudio.Web | narzędzia do tworzenia ASP.NET i tworzenia stron internetowych | 16.0.28517.75 | Wymagany
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne ASP.NET i narzędzi do tworzenia stron internetowych | 16.4.29318.151 | Wymagany
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.0.28621.142 | Wymagany
Składnik.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Zalecane
Składnik.Microsoft.VisualStudio.Web.AzureFunkcje | Narzędzia azure webjobs | 16.0.28714.129 | Zalecane
Pakiet targetingu firmy Microsoft.Net.Component.4.5.1.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.1 | 16.0.28517.75 | Zalecane
Pakiet targeting firmy Microsoft.Net.Component.4.6.TargetingPack | Pakiet targetowania programu .NET Framework 4.6 | 16.0.28517.75 | Zalecane
Pakiet docelowy firmy Microsoft.Net.Component.4.TargetingPack | Pakiet targetowania programu .NET Framework 4 | 16.0.28517.75 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 narzędzia programistyczne | 16.0.28516.191 | Zalecane
Microsoft.Net.Core.Component.SDK.2.1 | Środowisko wykonawcze .NET Core 2.1 LTS | 16.5.29905.7 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia do analizy deweloperów | 16.5.29515.121 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane funkcje ASP.NET | 16.0.28315.86 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.Azure.AuthoringTools | Narzędzia do tworzenia platformy Azure | 16.0.28625.61 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki platformy Azure dla platformy .NET | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 16.1.28810.153 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.4.29313.120 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 16.5.29515.121 | Zalecane
Microsoft.VisualStudio.Component.EntityFramework | Narzędzia entity Framework 6 | 16.0.28315.86 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.AzureFunkcje | Narzędzia azure webjobs | 16.0.28621.142 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Narzędzia chmurowe do tworzenia stron internetowych | 16.2.29003.222 | Zalecane
Pakiet targetingpakingu microsoft.net.component.4.6.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.6.2 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targetingu firmy Microsoft.Net.Component.4.7.1.TargetingPack | Pakiet kierowania .NET Framework 4.7.1 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.7.TargetingPack | Pakiet targetowania programu .NET Framework 4.7 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.8.TargetingPack | Pakiet targetowania programu .NET Framework 4.8 | 16.4.29313.120 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Narzędzia programistyczne .NET Framework 4.6.1 | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Narzędzia programistyczne .NET Framework 4.6.2 | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7.1 | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7 | 16.3.29207.166 | Optional (Opcjonalność)
Narzędzia microsoft.net.componentgroup.4.8.DeveloperTools | Narzędzia programistyczne .NET Framework 4.8 | 16.4.29318.151 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTyplates | Dodatkowe szablony projektów (poprzednie wersje) | 16.0.28621.142 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.IISRozwój | Obsługa programów IIS w czasie rozwoju | 16.0.28315.86 | Optional (Opcjonalność)

## <a name="nodejs-development"></a>Rozwój node.js

**Identyfikator:** Węzeł Microsoft.VisualStudio.Workload.Node

**Opis:** Twórz skalowalne aplikacje sieciowe przy użyciu node.js, asynchronisty środowiska wykonawczego JavaScript opartego na zdarzeniach. 

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 16.5.29721.120 | Wymagany
Narzędzia Microsoft.VisualStudio.Component.Node.Tools | Narzędzia programistyczne Node.js | 16.5.29515.121 | Wymagany
Składnik Microsoft.VisualStudio.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Wymagany
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.0.28621.142 | Wymagany
Składnik.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Zalecane
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia do analizy deweloperów | 16.5.29515.121 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.4.29409.204 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.0.28625.61 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 narzędzia kompilacji (wersja 14.25) | 16.5.29721.120 | Optional (Opcjonalność)

## <a name="officesharepoint-development"></a>Program rozwoju pakietu Office/programu SharePoint

**Identyfikator:** Microsoft.VisualStudio.Workload.Office

**Opis:** Tworzenie dodatków pakietu Office i programu SharePoint, rozwiązań programu SharePoint i dodatków VSTO przy użyciu dodatków C#, VB i JavaScript.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.Microsoft.VisualStudio.RazorEkstrysja | Usługi językowe brzytwy | 16.0.28714.129 | Wymagany
Składnik.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Wymagany
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 16.0.28517.75 | Wymagany
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 16.0.28517.75 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 16.0.28517.75 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.7.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.7.2 | 16.0.28517.75 | Wymagany
Składnik Microsoft.Net.4.8.SDK | Plik SDK programu .NET Framework 4.8 | 16.4.29313.120 | Wymagany
Pakiet docelowy firmy Microsoft.Net.Component.4.TargetingPack | Pakiet targetowania programu .NET Framework 4 | 16.0.28517.75 | Wymagany
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.7.2 | 16.3.29207.166 | Wymagany
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko wykonawcze .NET Core 3.1 LTS | 16.5.29905.7 | Wymagany
Microsoft.NetCore.Component.SDK | Zestaw .NET Core SDK | 16.5.29905.7 | Wymagany
Narzędzia Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia do analizy deweloperów | 16.5.29515.121 | Wymagany
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.4.29409.204 | Wymagany
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.4.29409.204 | Wymagany
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Wymagany
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 16.5.29721.120 | Wymagany
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Rdzeń zarządzanego obciążenia pulpitu | 16.4.29318.151 | Wymagany
Microsoft.VisualStudio.Component.ManagedDesktop.Wymagania wstępne | Narzędzia programistyczne dla komputerów .NET | 16.5.29514.35 | Wymagany
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik ODBC programu SQL Server | 16.0.28625.61 | Wymagany
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.5.29515.121 | Wymagany
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 16.4.29409.204 | Wymagany
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko wykonawcze SQL ADAL | 16.0.28517.75 | Wymagany
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagany
Źródła danych Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla obsługi programu SQL Server | 16.0.28315.86 | Wymagany
Środowisko wykonawcze Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Wymagany
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Wymagany
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 16.0.28625.61 | Wymagany
Składnik Microsoft.VisualStudio.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Wymagany
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Wymagany
Składnik Microsoft.VisualStudio.Web | narzędzia do tworzenia ASP.NET i tworzenia stron internetowych | 16.0.28517.75 | Wymagany
Przepływ pracy Microsoft.VisualStudio.Component.Work | Windows Workflow Foundation | 16.0.28315.86 | Wymagany
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne ASP.NET i narzędzi do tworzenia stron internetowych | 16.4.29318.151 | Wymagany
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.0.28621.142 | Wymagany
Microsoft.VisualStudio.Component.TeamOffice | Narzędzia programu Visual Studio dla pakietu Office (VSTO) | 16.4.29409.204 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Pakiet targetingpakingu microsoft.net.component.4.6.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.6.2 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targetingu firmy Microsoft.Net.Component.4.7.1.TargetingPack | Pakiet kierowania .NET Framework 4.7.1 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.7.TargetingPack | Pakiet targetowania programu .NET Framework 4.7 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.8.TargetingPack | Pakiet targetowania programu .NET Framework 4.8 | 16.4.29313.120 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Narzędzia programistyczne .NET Framework 4.6.1 | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Narzędzia programistyczne .NET Framework 4.6.2 | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7.1 | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7 | 16.3.29207.166 | Optional (Opcjonalność)
Narzędzia microsoft.net.componentgroup.4.8.DeveloperTools | Narzędzia programistyczne .NET Framework 4.8 | 16.4.29318.151 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Środowisko Windows Identity Foundation 3.5 | 16.0.28621.142 | Optional (Opcjonalność)

## <a name="python-development"></a>Rozwój Pythona

**Identyfikator:** Microsoft.VisualStudio.Workload.Python

**Opis:** Edycja, debugowanie, interaktywne tworzenie i kontrola źródła dla Języka Python.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.PythonTools | Obsługa języka Języka Python | 16.5.29515.121 | Wymagany
Składnik.CPython3.x64 | Python 3 64-bitowy (3.7.5) | 3.7.5 | Zalecane
Składnik.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Zalecane
Składnik Microsoft.PythonDoczy.Minicondax64 | Python miniconda | 16.2.29003.222 | Zalecane
Microsoft.Component.PythonTools.Web | Pomoc techniczna języka Python | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 16.4.29409.204 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 16.5.29721.120 | Zalecane
Składnik Microsoft.VisualStudio.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 16.0.28621.142 | Zalecane
Składnik.CPython2.x64 | Python 2 64-bitowy (2.7.16) | 2.7.16 | Optional (Opcjonalność)
Składnik.CPython2.x86 | Python 2 32-bitowy (2.7.16) | 2.7.16 | Optional (Opcjonalność)
Składnik.CPython3.x86 | Python 3 32-bitowy (3.7.5) | 3.7.5 | Optional (Opcjonalność)
Składnik.Microsoft.VisualStudio.RazorEkstrysja | Usługi językowe brzytwy | 16.0.28714.129 | Optional (Opcjonalność)
Składnik.Microsoft.Web.LibraryManager | Library Manager | 16.0.28315.86 | Optional (Opcjonalność)
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Optional (Opcjonalność)
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Natywne narzędzia programistyczne Języka Python | 16.2.29020.229 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 16.0.28517.75 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.7.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.7.2 | 16.0.28517.75 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.8.SDK | Plik SDK programu .NET Framework 4.8 | 16.4.29313.120 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.7.2 | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko wykonawcze .NET Core 3.1 LTS | 16.5.29905.7 | Optional (Opcjonalność)
Microsoft.NetCore.Component.SDK | Zestaw .NET Core SDK | 16.5.29905.7 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.Azure.AuthoringTools | Narzędzia do tworzenia platformy Azure | 16.0.28625.61 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki platformy Azure dla platformy .NET | 16.0.28315.86 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 16.1.28810.153 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 16.4.29313.120 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Azure.Waverton | Podstawowe narzędzia usług w chmurze azure | 16.4.29409.204 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do tworzenia usług w chmurze azure | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 16.4.29409.204 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler GPU dla DirectX | 16.0.28625.61 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Rdzeń zarządzanego obciążenia pulpitu | 16.4.29318.151 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.MSODBC.SQL | Sterownik ODBC programu SQL Server | 16.0.28625.61 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Narzędzia wiersza polecenia programu SQL Server | 16.0.28707.177 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 16.0.28714.129 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.5.29515.121 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko wykonawcze SQL ADAL | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Optional (Opcjonalność)
Źródła danych Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla obsługi programu SQL Server | 16.0.28315.86 | Optional (Opcjonalność)
Środowisko wykonawcze Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 16.0.28625.61 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.0.28625.61 | Optional (Opcjonalność)
Narzędzia diagnostyczne Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania języka C++ | 16.5.29515.121 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 narzędzia kompilacji (wersja 14.25) | 16.5.29721.120 | Optional (Opcjonalność)
Składnik Microsoft.VisualStudio.Web | narzędzia do tworzenia ASP.NET i tworzenia stron internetowych | 16.0.28517.75 | Optional (Opcjonalność)
Składnik Microsoft.VisualStudio.Component.Windows10SDK | Uniwersalny czas pracy systemu Windows C | 16.4.29409.204 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne ASP.NET i narzędzi do tworzenia stron internetowych | 16.4.29318.151 | Optional (Opcjonalność)

## <a name="universal-windows-platform-development"></a>Tworzenie uniwersalnej platformy systemu Windows

**Identyfikator:** Microsoft.VisualStudio.Workload.Universal

**Opis:** Tworzenie aplikacji dla platformy uniwersalnej systemu Windows z języka C#, VB lub opcjonalnie C++.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik Microsoft.NetFX.natywny | Architektura .NET Native | 16.5.29515.121 | Wymagany
Składnik Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Wymagany
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 16.0.28517.75 | Wymagany
Microsoft.NetCore.Component.Runtime.3.1 | Środowisko wykonawcze .NET Core 3.1 LTS | 16.5.29905.7 | Wymagany
Microsoft.NetCore.Component.SDK | Zestaw .NET Core SDK | 16.5.29905.7 | Wymagany
Narzędzia Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia do analizy deweloperów | 16.5.29515.121 | Wymagany
Narzędzia Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 16.5.29515.121 | Wymagany
Microsoft.VisualStudio.Component.Graphics | Edytory obrazów i modeli 3D | 16.0.28517.75 | Wymagany
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.5.29515.121 | Wymagany
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 16.0.28315.86 | Wymagany
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Wymagany
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Narzędzia do pakowania MSIX | 16.4.29409.204 | Wymagany
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | Natywny i .NET Standard platformy .NET | 16.3.29102.218 | Wymagany
Pomoc techniczna aplikacji Microsoft.VisualStudio.ComponentGroup.UWP.Support | Narzędzia platformy uniwersalnej systemu Windows | 16.4.29409.204 | Wymagany
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Narzędzia platformy uniwersalnej systemu Windows dla platformy Xamarin | 16.5.29514.35 | Wymagany
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.8.SDK | Plik SDK programu .NET Framework 4.8 | 16.4.29313.120 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler GPU dla DirectX | 16.0.28625.61 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 16.0.28625.61 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Obsługa platformy uniwersalnej systemu Windows c++ dla narzędzi kompilacji w wersji 142 (ARM64) | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje języka C++ | 16.0.28625.61 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Redist.14.Najnowsze | Aktualizacja redystrybucjowa C++ 2019 | 16.5.29515.121 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC v142 — VS 2019 C++ ARM build tools (v14.25) | 16.5.29721.120 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142 - VS 2019 C++ ARM64 narzędzia do budowania (v14.25) | 16.5.29721.120 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 narzędzia kompilacji (wersja 14.25) | 16.5.29721.120 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141 — VS 2017 C++ ARM build tools (wersja 14.16) | 16.2.29003.222 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141 - VS 2017 C++ ARM64 narzędzia kompilacji (wersja 14.16) | 16.1.28829.92 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ x64/x86 narzędzia kompilacji (wersja 14.16) | 16.1.28829.92 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 Preview SDK (10.0.19041.0) | 16.5.29721.120 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Łączność z urządzeniem USB | 16.5.29515.121 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Funkcje pulpitu w języku C++ | 16.2.29012.281 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Narzędzia uniwersalnej platformy systemu Windows w języku C++ (v142) | 16.3.29207.166 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | Narzędzia uniwersalnej platformy systemu Windows w języku C++ (v141) | 16.1.28810.153 | Optional (Opcjonalność)

## <a name="visual-studio-extension-development"></a>Programowanie rozszerzeń programu Visual Studio

**Identyfikator:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Opis:** Tworzenie dodatków i rozszerzeń dla programu Visual Studio, w tym nowych poleceń, analizatorów kodu i okien narzędzi.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Wymagany
Pakiet targeting firmy Microsoft.Net.Component.4.6.TargetingPack | Pakiet targetowania programu .NET Framework 4.6 | 16.0.28517.75 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.7.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.7.2 | 16.0.28517.75 | Wymagany
Składnik Microsoft.Net.4.8.SDK | Plik SDK programu .NET Framework 4.8 | 16.4.29313.120 | Wymagany
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.7.2 | 16.3.29207.166 | Wymagany
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 16.1.28829.92 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 16.0.28714.129 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 16.5.29515.121 | Wymagany
Składnik.VSSDK firmy Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Wymagany
Wymagania wstępne dotyczące programu Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Wymagania wstępne tworzenia rozszerzeń programu Visual Studio | 16.4.29318.151 | Wymagany
Narzędzia Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 16.5.29515.121 | Zalecane
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 16.0.28625.61 | Zalecane
Składnik.Składnik.CodeAnalysis.SDK | Zestaw SDK platformy kompilatora .NET | 16.2.29003.222 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia do analizy deweloperów | 16.5.29515.121 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.DslTools | Modelowanie SDK | 16.0.28315.86 | Optional (Opcjonalność)

## <a name="unaffiliated-components"></a>Składniki niepowiązane

Są to składniki, które nie są dołączone do żadnego obciążenia, ale mogą być wybrane jako pojedynczy składnik.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
Składnik.GitHub.VisualStudio | Rozszerzenie GitHub dla programu Visual Studio | 2.5.9.5485
Składnik.Xamarin.Inspektor | Xamarin Inspector | 16.0.28315.86
Składnik.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Składniki.Xamarin.Skoroszyty | Xamarin Workbooks | 16.0.28315.86
Składnik Microsoft.ClickOnce | Kliknij publikowanieonce | 16.4.29409.204
Microsoft.Component.HelpViewer | Podgląd pomocy | 16.0.28625.61
Składnik Microsoft.Net.4.6.1.SDK | Plik SDK programu .NET Framework 4.6.1 | 16.4.29409.204
Składnik Microsoft.Net.4.6.2.SDK | Plik SDK programu .NET Framework 4.6.2 | 16.4.29409.204
Składnik Microsoft.Net.4.7.1.SDK | Plik SDK programu .NET Framework 4.7.1 | 16.4.29409.204
Składnik Microsoft.Net.4.7.2.SDK | Plik SDK programu .NET Framework 4.7.2 | 16.4.29409.204
Składnik Microsoft.Net.4.7.SDK | Plik SDK programu .NET Framework 4.7 | 16.4.29409.204
Microsoft.Net.Core.Component.SDK.2.2 | .NET Core 2.2 Środowisko uruchomieniowe (EOL) | 16.5.29813.82
Microsoft.Net.Core.Component.SDK.3.0 | Środowisko uruchomieniowe .NET Core 3.0 (EOL) | 16.5.29905.7
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programistyczne plus .NET Core 2.1 | 16.3.29207.166
Microsoft.NetCore.ComponentGroup.Web.2.1 | Narzędzia do tworzenia stron internetowych plus .NET Core 2.1 | 16.3.29207.166
Integracja microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Integracja pakietu Office usługi Azure DevOps | 16.0.28625.61
Microsoft.VisualStudio.Component.ClassDesigner | Projektant klas | 16.0.28528.71
Microsoft.VisualStudio.Component.DependencyValidation.Community | Sprawdzanie poprawności zależności | 16.0.28517.75
Microsoft.VisualStudio.Component.Git | Git dla systemu Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.GraphDocument | Edytor DGML | 16.0.28625.61
Składnik Microsoft.VisualStudio.Komponent.LinqToSql | LINQ to SQL Tools | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 — VS 2019 C++ ARM build tools (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 — VS 2019 C++ ARM64 narzędzia do budowania (wersja 14.20) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Widmo-mitigated libs (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL | C++ v14.20 ATL dla narzędzi do budowania wersji 142 (x86 & x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | C++ v14.20 ATL dla narzędzi do budowania v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | C++ v14.20 ATL dla v142 budować narzędzia z Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64 | C++ v14.20 ATL dla narzędzi do budowania wersji 142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64.Spectre | C++ v14.20 ATL dla v142 budować narzędzia z Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.Spectre | C++ v14.20 ATL dla v142 budować narzędzia z Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.CLI.Support | Obsługa C++/CLI dla narzędzi kompilacji w wersji 142 (14.20) | 16.4.29409.204
Microsoft.VisualStudio.Component.VC.14.20.MFC | C++ v14.20 MFC dla v142 build tools (x86 & x64) | 16.2.29003.222
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM | C++ v14.20 MFC dla v142 build tools (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | C++ v14.20 MFC dla v142 budować narzędzia z Spectre Mitigations (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | C++ v14.20 MFC dla narzędzi do budowania v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | C++ v14.20 MFC dla v142 budować narzędzia z Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | C++ v14.20 MFC dla v142 budować narzędzia z Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 narzędzia kompilacji (wersja 14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Widmo-mitigated libs (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM | MSVC v142 — VS 2019 C++ ARM build tools (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM64 | MSVC v142 - VS 2019 C++ ARM64 narzędzia do budowania (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Widmo-mitigated libs (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL | C++ v14.21 ATL dla narzędzi do budowania wersji 142 (x86 & x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM | C++ v14.21 ATL dla narzędzi do budowania v142 (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM.Spectre | C++ v14.21 ATL dla v142 budować narzędzia z Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64 | C++ v14.21 ATL dla narzędzi do budowania wersji 142 (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64.Spectre | C++ v14.21 ATL dla v142 budować narzędzia z Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL.Spectre | C++ v14.21 ATL dla v142 budować narzędzia z Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.CLI.Support | Obsługa C++/CLI dla narzędzi kompilacji w wersji 142 (14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.MFC | C++ v14.21 MFC dla v142 build tools (x86 & x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM | C++ v14.21 MFC dla v142 build tools (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM.Spectre | C++ v14.21 MFC dla v142 budować narzędzia z Spectre Mitigations (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64 | C++ v14.21 MFC dla narzędzi do budowania v142 (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64.Spectre | C++ v14.21 MFC dla v142 budować narzędzia z Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.Spectre | C++ v14.21 MFC dla v142 budować narzędzia z Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 narzędzia kompilacji (wersja 14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Widmo-mitigated libs (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM | MSVC v142 — VS 2019 C++ ARM build tools (v14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM64 | MSVC v142 - VS 2019 C++ ARM64 narzędzia do budowania (v14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Widmo-mitigated libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL | C++ v14.22 ATL dla v142 budować narzędzia (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM | C++ v14.22 ATL dla narzędzi do budowania v142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM.Spectre | C++ v14.22 ATL dla v142 budować narzędzia z Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64 | C++ v14.22 ATL dla narzędzi do budowania v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64.Spectre | C++ v14.22 ATL dla v142 budować narzędzia z Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL.Spectre | C++ v14.22 ATL dla v142 budować narzędzia z Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.CLI.Support | Obsługa C++/CLI dla narzędzi kompilacji w wersji 142 (14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC | C++ v14.22 MFC dla v142 build tools (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM | C++ v14.22 MFC dla v142 build tools (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM.Spectre | C++ v14.22 MFC dla v142 budować narzędzia z Spectre Mitigations (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64 | C++ v14.22 MFC dla v142 build tools (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64.Spectre | C++ v14.22 MFC dla v142 budować narzędzia z Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.Spectre | C++ v14.22 MFC dla v142 budować narzędzia z Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 narzędzia kompilacji (wersja 14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Widmo-mitigated libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM | MSVC v142 — VS 2019 C++ ARM build tools (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64 | MSVC v142 - VS 2019 C++ ARM64 narzędzia do budowania (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Widmo-mitigated libs (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL | C++ v14.23 ATL dla v142 budować narzędzia (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM | C++ v14.23 ATL dla narzędzi do budowania v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM.Spectre | C++ v14.23 ATL dla v142 budować narzędzia z Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64 | C++ v14.23 ATL dla narzędzi do budowania v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64.Spectre | C++ v14.23 ATL dla v142 budować narzędzia z Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.Spectre | C++ v14.23 ATL dla v142 budować narzędzia z Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.CLI.Support | Obsługa C++/CLI dla narzędzi kompilacji w wersji 142 (14.23) | 16.4.29409.204
Microsoft.VisualStudio.Component.VC.14.23.MFC | C++ v14.23 MFC dla v142 build tools (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM | C++ v14.23 MFC dla v142 build tools (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM.Spectre | C++ v14.23 MFC dla v142 budować narzędzia z Spectre Mitigations (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64 | C++ v14.23 MFC dla v142 build tools (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64.Spectre | C++ v14.23 MFC dla v142 budować narzędzia z Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.Spectre | C++ v14.23 MFC dla v142 budować narzędzia z Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 narzędzia kompilacji (wersja 14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Widmo-mitigated libs (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.24.ARM | MSVC v142 — VS 2019 C++ ARM build tools (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM64 | MSVC v142 - VS 2019 C++ ARM64 narzędzia do budowania (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Widmo-mitigated libs (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL | C++ v14.24 ATL dla v142 budować narzędzia (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM | C++ v14.24 ATL dla narzędzi do budowania v142 (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM.Spectre | C++ v14.24 ATL dla v142 budować narzędzia z Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64 | C++ v14.24 ATL dla narzędzi do budowania v142 (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64.Spectre | C++ v14.24 ATL dla v142 budować narzędzia z Spectre Mitigations (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.Spectre | C++ v14.24 ATL dla v142 budować narzędzia z Spectre Mitigations (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.CLI.Support | Obsługa C++/CLI dla narzędzi kompilacji w wersji 142 (14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC | C++ v14.24 MFC dla v142 build tools (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM | C++ v14.24 MFC dla v142 build tools (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM.Spectre | C++ v14.24 MFC dla v142 budować narzędzia z Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64 | C++ v14.24 MFC dla v142 build tools (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64.Spectre | C++ v14.24 MFC dla v142 budować narzędzia z Spectre Mitigations (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.Spectre | C++ v14.24 MFC dla v142 budować narzędzia z Spectre Mitigations (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 narzędzia kompilacji (wersja 14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Widmo-mitigated libs (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM | C++ ATL dla najnowszych narzędzi kompilacji w wersji 142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | C++ ATL dla najnowszych narzędzi kompilacji v142 z Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | C++ ATL dla najnowszych narzędzi do tworzenia v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | C++ ATL dla najnowszych narzędzi kompilacji v142 z Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATL.Spectre | C++ ATL dla najnowszych narzędzi kompilacji v142 z Spectre Mitigations (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | C++ MFC dla najnowszych narzędzi kompilacji v142 z Spectre Mitigations (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM | C++ MFC dla najnowszych narzędzi do budowania v142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | C++ MFC dla najnowszych narzędzi kompilacji v142 z Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | C++ MFC dla najnowszych narzędzi do kompilacji v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | C++ MFC dla najnowszych narzędzi kompilacji v142 z Spectre Mitigations (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Redist.MSM | C++ 2019 Redystrybucyjne MSM | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.25) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Widmo-mitigated libs (v14.25) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Widmo-mitigated libs (v14.25)  | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141 - VS 2017 C++ ARM Spectre-mitigated libs (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141 - VS 2017 C++ ARM64 Widmo-mitigated libs (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ATL | C++ ATL dla v141 build tools (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | Narzędzia do budowania C++ ATL dla wersji 141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | Narzędzia do tworzenia narzędzi kompilacji C++ ATL dla wersji 141 z ograniczeniami spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | Narzędzia do budowania C++ ATL dla wersji 141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | Narzędzia do tworzenia narzędzi kompilacji C++ ATL dla wersji 141 z ograniczeniami spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | Narzędzia do tworzenia zestawów ATL w języku C++ dla wersji 141 z ograniczeniami spectre (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | Obsługa C++/CLI dla narzędzi kompilacji w wersji 141 (14.16) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.v141.MFC | C++ MFC dla v141 build tools (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | C++ MFC dla v141 build tools (ARM) | 16.2.28915.88
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | Narzędzia do tworzenia aplikacji C++ MFC dla wersji 141 z ograniczeniami spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | C++ MFC dla v141 build tools (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | Narzędzia do tworzenia aplikacji C++ MFC dla wersji 141 z ograniczeniami spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | Narzędzia do tworzenia aplikacji C++ MFC dla wersji 141 z ograniczeniami spectre (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141 - VS 2017 C++ x64/x86 Widmo-mitigated libs (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | Obsługa systemu C++ Windows XP dla narzędzi programu VS 2017 (w wersji 141) [Przestarzała] | 16.1.28811.260
Grupa składników Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.1.28810.153
