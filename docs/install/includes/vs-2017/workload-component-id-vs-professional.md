---
title: Identyfikatory obciążenia i składników programu Visual Studio Professional 2017
titleSuffix: ''
description: Używanie identyfikatorów obciążenia i składników do instalowania programu Visual Studio przy użyciu wiersza polecenia lub określania zależności w manifeście vsix
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 2/12/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 118c818c194b50d8eabbd0139e29c15dafd90708
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76158877"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-professional-2017"></a>Edytor podstawowy programu Visual Studio (dołączony do programu Visual Studio Professional 2017)

**Identyfikator:** Microsoft.VisualStudio.Workload.CoreEditor

**Opis:** Środowisko powłoki rdzenia programu Visual Studio, w tym edycja kodu ze składni, kontrola kodu źródłowego i zarządzanie elementami roboczymi.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Edytor podstawowy programu Visual Studio | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Strona startowa programu Visual Studio dla użytkowników języka C++ | 15.0.27128.1 | Optional (Opcjonalność)

## <a name="azure-development"></a>Tworzenie aplikacji na platformie Azure

**Identyfikator:** Platforma Microsoft.VisualStudio.Workload.Azure

**Opis:** Zestawy SDK platformy Azure, narzędzia i projekty do tworzenia aplikacji w chmurze, tworzenia zasobów i tworzenia kontenerów, w tym obsługi platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.Microsoft.VisualStudio.RazorEkstrysja | Usługi językowe brzytwy | 15.0.26720.2 | Wymagany
Składnik.Microsoft.VisualStudio.Web.AzureFunkcje | Narzędzia Microsoft Azure WebJobs | 15.7.27617.1 | Wymagany
Składnik.Microsoft.Web.LibraryManager | Library Manager | 15.8.27705.0 | Wymagany
Składnik.WebSocket | Sieć WebSocket4Net | 15.0.26606.0 | Wymagany
Składnik Microsoft.ClickOnce | Kliknij publikowanieonce | 15.8.27825.0 | Wymagany
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagany
Microsoft.Component.NetFX.Core.Środowisko wykonawcze | Core .NET środowisko uruchomieniowe | 15.0.26208.0 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 15.6.27406.0 | Wymagany
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 15.6.27406.0 | Wymagany
Składnik Microsoft.Net.4.6.1.SDK | Plik SDK programu .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.6.1 | 15.8.27825.0 | Wymagany
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne .NET Core 2.1 | 15.8.27924.0 | Wymagany
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programistyczne .NET Core 2.1 | 15.8.27924.0 | Wymagany
Microsoft.NetCore.ComponentGroup.Web.2.1 | Narzędzia programistyczne .NET Core 2.1 | 15.8.27924.0 | Wymagany
Narzędzia Microsoft.VisualStudio.Component.Azure.AuthoringTools | Narzędzia do tworzenia platformy Azure | 15.9.28307.421 | Wymagany
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki platformy Azure dla platformy .NET | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 15.9.28307.421 | Wymagany
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 15.9.28125.51 | Wymagany
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Wymagany
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Wymagany
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 15.8.27906.1 | Wymagany
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia do tworzenia kontenerów — narzędzia do tworzenia | 15.7.27617.1 | Wymagany
Microsoft.VisualStudio.Component.FSharp | Obsługa języka Języka F# | 15.8.27825.0 | Wymagany
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Obsługa języka F# dla projektów internetowych | 15.9.28307.421 | Wymagany
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 15.9.28125.51 | Wymagany
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Rdzeń zarządzanego obciążenia pulpitu | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagany
Microsoft.VisualStudio.Component.PortableBrary | Pakiet kierowania na bibliotekę przenośną platformy .NET | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko wykonawcze SQL ADAL | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.SQL.CMDUtils | Narzędzia wiersza polecenia programu SQL Server | 15.0.26208.0 | Wymagany
Źródła danych Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla obsługi programu SQL Server | 15.0.26621.2 | Wymagany
Środowisko wykonawcze Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Wymagany
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Wymagany
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 15.0.26208.0 | Wymagany
Składnik Microsoft.VisualStudio.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Wymagany
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagany
Składnik Microsoft.VisualStudio.Web | narzędzia do tworzenia ASP.NET i tworzenia stron internetowych | 15.8.27825.0 | Wymagany
Wymagania wstępne microsoft.VisualStudio.ComponentGroup.Azure.Wymagania wstępne | Wymagania wstępne dotyczące tworzenia platformy Azure | 15.9.28107.0 | Wymagany
Microsoft.VisualStudio.ComponentGroup.AzureFunkcje | Narzędzia Microsoft Azure WebJobs | 15.7.27617.1 | Wymagany
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne ASP.NET i narzędzi do tworzenia stron internetowych | 15.9.28219.51 | Wymagany
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 15.8.27825.0 | Wymagany
Narzędzia Microsoft.Component.Azure.DataLake.Tools | Narzędzia usługi Azure Data Lake i Stream Analytics | 15.9.28107.0 | Zalecane
Pakiet targetingu firmy Microsoft.Net.Component.4.5.1.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.1 | 15.6.27406.0 | Zalecane
Pakiet targeting firmy Microsoft.Net.Component.4.6.TargetingPack | Pakiet targetowania programu .NET Framework 4.6 | 15.6.27406.0 | Zalecane
Pakiet docelowy firmy Microsoft.Net.Component.4.TargetingPack | Pakiet targetowania programu .NET Framework 4 | 15.6.27406.0 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 narzędzia programistyczne | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane funkcje ASP.NET | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Zestaw SDK aplikacji mobilnych platformy Azure | 15.7.27625.0 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Podstawowe narzędzia usługi Azure Resource Manager | 15.9.28107.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Narzędzia usługi Service Fabric | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton | Podstawowe narzędzia usług w chmurze azure | 15.9.28107.0 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do tworzenia usług w chmurze azure | 15.7.27617.1 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Narzędzia usługi w chmurze platformy Azure | 15.0.26504.0 | Zalecane
Narzędzia Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Narzędzia usługi Azure Resource Manager | 15.0.27005.2 | Zalecane
Składnik Microsoft.Net.4.6.2.SDK | Plik SDK programu .NET Framework 4.6.2 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.6.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.6.2 | 15.6.27406.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.7.1.SDK | Plik SDK programu .NET Framework 4.7.1 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targetingu firmy Microsoft.Net.Component.4.7.1.TargetingPack | Pakiet kierowania .NET Framework 4.7.1 | 15.6.27406.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.7.2.SDK | Plik SDK programu .NET Framework 4.7.2 | 15.8.27825.0 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.7.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.7.2 | 15.8.27825.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.7.SDK | Plik SDK programu .NET Framework 4.7 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.7.TargetingPack | Pakiet targetowania programu .NET Framework 4.7 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Narzędzia programistyczne .NET Framework 4.6.2 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7.1 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7.2 | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7 | 15.6.27406.0 | Optional (Opcjonalność)
Plik Microsoft.Net.Core.Component.SDK | Narzędzia programistyczne .NET Core 2.0 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 narzędzia programistyczne | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.NetCore.1x.ComponentGroup.Web | .NET Core 1.0 - 1.1 narzędzia programistyczne dla sieci Web | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Narzędzia programistyczne .NET Core 2.0 | 15.8.27729.1 | Optional (Opcjonalność)
Microsoft.NetCore.ComponentGroup.Web | Narzędzia programistyczne .NET Core 2.0 | 15.7.27625.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 15.0.26906.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Optional (Opcjonalność)

## <a name="data-storage-and-processing"></a>Magazynowanie i przetwarzanie danych

**Identyfikator:** Microsoft.VisualStudio.Workload.Data

**Opis:** Połącz, opracuj i przetestuj rozwiązania danych za pomocą programu SQL Server, usługi Azure Data Lake lub Hadoop.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.Microsoft.VisualStudio.RazorEkstrysja | Usługi językowe brzytwy | 15.0.26720.2 | Zalecane
Składnik.Microsoft.Web.LibraryManager | Library Manager | 15.8.27705.0 | Zalecane
Składnik.Redgate.SQLSearch.VSExtension | Redgate SQL Search | 3.1.7.2062 | Zalecane
Składnik.WebSocket | Sieć WebSocket4Net | 15.0.26606.0 | Zalecane
Narzędzia Microsoft.Component.Azure.DataLake.Tools | Narzędzia usługi Azure Data Lake i Stream Analytics | 15.9.28107.0 | Zalecane
Składnik Microsoft.ClickOnce | Kliknij publikowanieonce | 15.8.27825.0 | Zalecane
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Zalecane
Pakiet targetingu firmy Microsoft.Net.Component.4.5.1.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.1 | 15.6.27406.0 | Zalecane
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 15.6.27406.0 | Zalecane
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 15.6.27406.0 | Zalecane
Składnik Microsoft.Net.4.6.1.SDK | Plik SDK programu .NET Framework 4.6.1 | 15.6.27406.0 | Zalecane
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 15.6.27406.0 | Zalecane
Pakiet targeting firmy Microsoft.Net.Component.4.6.TargetingPack | Pakiet targetowania programu .NET Framework 4.6 | 15.6.27406.0 | Zalecane
Pakiet docelowy firmy Microsoft.Net.Component.4.TargetingPack | Pakiet targetowania programu .NET Framework 4 | 15.6.27406.0 | Zalecane
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.6.1 | 15.8.27825.0 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 narzędzia programistyczne | 15.6.27406.0 | Zalecane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne .NET Core 2.1 | 15.8.27924.0 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.Azure.AuthoringTools | Narzędzia do tworzenia platformy Azure | 15.9.28307.421 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki platformy Azure dla platformy .NET | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 15.9.28307.421 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 15.9.28125.51 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton | Podstawowe narzędzia usług w chmurze azure | 15.9.28107.0 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do tworzenia usług w chmurze azure | 15.7.27617.1 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Zalecane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 15.8.27906.1 | Zalecane
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia do tworzenia kontenerów — narzędzia do tworzenia | 15.7.27617.1 | Zalecane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 15.9.28125.51 | Zalecane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Rdzeń zarządzanego obciążenia pulpitu | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Zalecane
Microsoft.VisualStudio.Component.PortableBrary | Pakiet kierowania na bibliotekę przenośną platformy .NET | 15.6.27309.0 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 15.6.27309.0 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko wykonawcze SQL ADAL | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.SQL.CMDUtils | Narzędzia wiersza polecenia programu SQL Server | 15.0.26208.0 | Zalecane
Źródła danych Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla obsługi programu SQL Server | 15.0.26621.2 | Zalecane
Środowisko wykonawcze Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Zalecane
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Zalecane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 15.0.26208.0 | Zalecane
Składnik Microsoft.VisualStudio.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Zalecane
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Zalecane
Składnik Microsoft.VisualStudio.Web | narzędzia do tworzenia ASP.NET i tworzenia stron internetowych | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne ASP.NET i narzędzi do tworzenia stron internetowych | 15.9.28219.51 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.Component.FSharp.Desktop | Obsługa języka pulpitu F# | 15.8.27825.0 | Optional (Opcjonalność)

## <a name="data-science-and-analytical-applications"></a>Aplikacje do analizy i przetwarzania danych

**Identyfikator:** Microsoft.VisualStudio.Workload.DataScience

**Opis:** Języki i narzędzia do tworzenia aplikacji do nauki o danych, w tym Python, R i F#.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.Anaconda3.x64 | Anaconda3 64-bitowy (5.2.0) | 5.2.0 | Zalecane
Microsoft.Component.CookiecutterTools | Obsługa szablonów cookiecutter | 15.0.26621.2 | Zalecane
Microsoft.Component.PythonTools | Obsługa języka Języka Python | 15.0.26823.1 | Zalecane
Microsoft.Component.PythonTools.Web | Pomoc techniczna języka Python | 15.9.28107.0 | Zalecane
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Zalecane
Microsoft.VisualStudio.Component.FSharp.Desktop | Obsługa języka pulpitu F# | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 15.9.28125.51 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Zalecane
Microsoft.VisualStudio.Component.R.Open | Klient Microsoft R (3.3.2) | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.RHost | Obsługa środowiska uruchomieniowego dla narzędzi programistycznych R | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 15.6.27309.0 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.RTools | Obsługa języka R | 15.0.26919.1 | Zalecane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Zalecane
Składnik Microsoft.VisualStudio.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Zalecane
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 15.8.27825.0 | Zalecane
Składnik.Anaconda2.x64 | Anaconda2 64-bitowy (5.2.0) | 5.2.0 | Optional (Opcjonalność)
Składnik.Anaconda2.x86 | Anaconda2 32-bitowy (5.2.0) | 5.2.0 | Optional (Opcjonalność)
Składnik.Anaconda3.x86 | Anaconda3 32-bitowy (5.2.0) | 5.2.0 | Optional (Opcjonalność)
Składnik.VC.Środowisko wykonawcze.UCRTSDK firmy Microsoft.Component.VC.Runtime.UCRTSDK | Uniwersalny zestaw CRT systemu Windows | 15.6.27309.0 | Optional (Opcjonalność)
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Natywne narzędzia programistyczne Języka Python | 15.9.28307.102 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler GPU dla DirectX | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Graphics.Win81 | Narzędzia graficzne Zestaw Windows 8.1 SDK | 15.6.27406.0 | Optional (Opcjonalność)
Składnik.140 firmy Microsoft.VisualStudio.Component.VC.140 | Zestaw narzędzi VC++ 2015.3 v14.00 (v140) dla komputerów stacjonarnych | 15.7.27617.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Optional (Opcjonalność)
Narzędzia diagnostyczne Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania języka C++ | 15.0.26823.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 wersja 15.9 v14.16 najnowsze narzędzia v141 | 15.9.28230.55 | Optional (Opcjonalność)
Składnik Microsoft.VisualStudio.Component.Windows10SDK | Uniwersalny czas pracy systemu Windows C | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Optional (Opcjonalność)
Składnik Microsoft.VisualStudio.Component.Windows81SDK | Zestaw SDK systemu Windows 8.1 | 15.6.27406.0 | Optional (Opcjonalność)

## <a name="net-desktop-development"></a>Programowa firma .NET

**Identyfikator:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Opis:** Tworzenie aplikacji WPF, Windows Forms i konsoli przy użyciu języka C#, Visual Basic i F#.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik Microsoft.ClickOnce | Kliknij publikowanieonce | 15.8.27825.0 | Wymagany
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagany
Składnik Microsoft.Net.4.6.1.SDK | Plik SDK programu .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.6.1 | 15.8.27825.0 | Wymagany
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Rdzeń zarządzanego obciążenia pulpitu | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.ManagedDesktop.Wymagania wstępne | Narzędzia programistyczne dla komputerów .NET | 15.7.27625.0 | Wymagany
Microsoft.VisualStudio.Component.PortableBrary | Pakiet kierowania na bibliotekę przenośną platformy .NET | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagany
Składnik Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.6.27406.0 | Zalecane
Pakiet targetingu firmy Microsoft.Net.Component.4.5.1.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.1 | 15.6.27406.0 | Zalecane
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 15.6.27406.0 | Zalecane
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 15.6.27406.0 | Zalecane
Pakiet targeting firmy Microsoft.Net.Component.4.6.TargetingPack | Pakiet targetowania programu .NET Framework 4.6 | 15.6.27406.0 | Zalecane
Pakiet docelowy firmy Microsoft.Net.Component.4.TargetingPack | Pakiet targetowania programu .NET Framework 4 | 15.6.27406.0 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 narzędzia programistyczne | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger just-in-time | 15.0.27005.2 | Zalecane
Microsoft.VisualStudio.Component.EntityFramework | Narzędzia entity Framework 6 | 15.6.27406.0 | Zalecane
Składnik.Dotfuscator | PreEmptive Protection — Dotfuscator | 15.0.26208.0 | Optional (Opcjonalność)
Składnik.Microsoft.VisualStudio.RazorEkstrysja | Usługi językowe brzytwy | 15.0.26720.2 | Optional (Opcjonalność)
Składnik.Microsoft.Web.LibraryManager | Library Manager | 15.8.27705.0 | Optional (Opcjonalność)
Składnik.WebSocket | Sieć WebSocket4Net | 15.0.26606.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.6.2.SDK | Plik SDK programu .NET Framework 4.6.2 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.6.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.6.2 | 15.6.27406.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.7.1.SDK | Plik SDK programu .NET Framework 4.7.1 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targetingu firmy Microsoft.Net.Component.4.7.1.TargetingPack | Pakiet kierowania .NET Framework 4.7.1 | 15.6.27406.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.7.2.SDK | Plik SDK programu .NET Framework 4.7.2 | 15.8.27825.0 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.7.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.7.2 | 15.8.27825.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.7.SDK | Plik SDK programu .NET Framework 4.7 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.7.TargetingPack | Pakiet targetowania programu .NET Framework 4.7 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Narzędzia programistyczne .NET Framework 4.6.2 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7.1 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7.2 | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7 | 15.6.27406.0 | Optional (Opcjonalność)
Plik Microsoft.Net.Core.Component.SDK | Narzędzia programistyczne .NET Core 2.0 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 narzędzia programistyczne | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne .NET Core 2.1 | 15.8.27924.0 | Optional (Opcjonalność)
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Narzędzia programistyczne .NET Core 2.0 | 15.8.27729.1 | Optional (Opcjonalność)
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programistyczne .NET Core 2.1 | 15.8.27924.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 15.8.27906.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia do tworzenia kontenerów — narzędzia do tworzenia | 15.7.27617.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.FSharp | Obsługa języka Języka F# | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.FSharp.Desktop | Obsługa języka pulpitu F# | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 15.9.28125.51 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko wykonawcze SQL ADAL | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.SQL.CMDUtils | Narzędzia wiersza polecenia programu SQL Server | 15.0.26208.0 | Optional (Opcjonalność)
Źródła danych Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla obsługi programu SQL Server | 15.0.26621.2 | Optional (Opcjonalność)
Środowisko wykonawcze Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Optional (Opcjonalność)
Składnik Microsoft.VisualStudio.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Optional (Opcjonalność)
Składnik Microsoft.VisualStudio.Web | narzędzia do tworzenia ASP.NET i tworzenia stron internetowych | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne ASP.NET i narzędzi do tworzenia stron internetowych | 15.9.28219.51 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 15.8.27825.0 | Optional (Opcjonalność)

## <a name="game-development-with-unity"></a>Opracowywanie gier za pomocą aparatu Unity

**Identyfikator:** Microsoft.VisualStudio.Workload.ManagedGame

**Opis:** Twórz gry 2D i 3D dzięki Unity, potężnemu środowisku programistycznemu na różnych platformach.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Narzędzia programistyczne .NET Framework 3.5 | 15.6.27406.0 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.7.1.TargetingPack | Pakiet kierowania .NET Framework 4.7.1 | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.Unity | Narzędzia Visual Studio Tools for Unity | 15.7.27617.1 | Wymagany
Składnik.UnityEngine.x64 | 64-bitowy edytor Unity 2018.3 | 15.9.28307.271 | Zalecane
Składnik.UnityEngine.x86 | Edytor 32-bitowy Unity 5.6 | 15.6.27406.0 | Zalecane

## <a name="linux-development-with-c"></a>Programowanie dla systemu Linux w języku C++

**Identyfikator:** Platforma Microsoft.VisualStudio.Workload.NativeCrossPlat

**Opis:** Tworzenie i debugowanie aplikacji działających w środowisku systemu Linux.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.MDD.Linux | Visual C++ dla rozwoju linuksa | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Wymagany
Składnik Microsoft.VisualStudio.Component.Windows10SDK | Uniwersalny czas pracy systemu Windows C | 15.6.27406.0 | Wymagany
Składnik.Linux.CMake | Narzędzia Visual C++ dla CMake i Linux | 15.9.28307.102 | Zalecane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 wersja 15.9 v14.16 najnowsze narzędzia v141 | 15.9.28230.55 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 15.8.27825.0 | Zalecane
Składnik.MDD.Linux.GCC.arm | Wbudowane i IoT Development | 15.6.27309.0 | Optional (Opcjonalność)

## <a name="desktop-development-with-c"></a>Programowanie aplikacji klasycznych w języku C++

**Identyfikator:** Microsoft.VisualStudio.Workload.NativeDesktop

**Opis:** Tworzenie aplikacji klasycznych systemu Windows przy użyciu zestawu narzędzi Microsoft C++, ATL lub MFC.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.VC.Redist.14.Najnowsze | Aktualizacja redystrybucjowa programu Visual C++ 2017 | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Funkcje pulpitu w języku Visual C++ | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger just-in-time | 15.0.27005.2 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler GPU dla DirectX | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.Graphics.Win81 | Narzędzia graficzne Zestaw Windows 8.1 SDK | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Zalecane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL dla x86 i x64 | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Component.VC.CMake.Project | Narzędzia Visual C++ dla CMake | 15.9.28307.102 | Zalecane
Narzędzia diagnostyczne Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania języka C++ | 15.0.26823.1 | Zalecane
Test Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Adapter testowy do boost.test | 15.8.27906.1 | Zalecane
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Adapter testowy do testu Google | 15.8.27906.1 | Zalecane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 wersja 15.9 v14.16 najnowsze narzędzia v141 | 15.9.28230.55 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 15.8.27825.0 | Zalecane
Składnik.Incredibuild | IncrediBuild - Przyspieszenie kompilacji | 15.7.27617.1 | Optional (Opcjonalność)
Składnik.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Optional (Opcjonalność)
Składnik.VC.Środowisko wykonawcze.UCRTSDK firmy Microsoft.Component.VC.Runtime.UCRTSDK | Uniwersalny zestaw CRT systemu Windows | 15.6.27309.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.6.1.SDK | Plik SDK programu .NET Framework 4.6.1 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 15.6.27406.0 | Optional (Opcjonalność)
Składnik.140 firmy Microsoft.VisualStudio.Component.VC.140 | Zestaw narzędzi VC++ 2015.3 v14.00 (v140) dla komputerów stacjonarnych | 15.7.27617.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC dla x86 i x64 | 15.7.27625.0 | Optional (Opcjonalność)
Pomoc techniczna aplikacji Microsoft.VisualStudio.Component.VC.CLI.Support | Obsługa języka C++/CLI | 15.6.27309.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduły do biblioteki standardowej (eksperymentalne) | 15.6.27309.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) dla pulpitu C++ [x86 i x64] | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C++ | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) dla pulpitu C++ [x86 i x64] | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Windows 10 SDK (10.0.16299.0) dla pulpitu C++ [ARM i ARM64] | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C++ | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.9.28307.102 | Optional (Opcjonalność)
Składnik Microsoft.VisualStudio.Component.Windows81SDK | Zestaw SDK systemu Windows 8.1 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.WinXP | Obsługa języka Windows XP dla języka C++ | 15.8.27924.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK i UCRT SDK | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Obsługa języka Windows XP dla języka C++ | 15.8.27705.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | Optional (Opcjonalność)

## <a name="game-development-with-c"></a>Programowanie gier w języku C++

**Identyfikator:** Microsoft.VisualStudio.Workload.NativeGame

**Opis:** Wykorzystaj pełną moc języka C++, aby tworzyć profesjonalne gry oparte na programach DirectX, Unreal lub Cocos2d.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.VC.Redist.14.Najnowsze | Aktualizacja redystrybucjowa programu Visual C++ 2017 | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 wersja 15.9 v14.16 najnowsze narzędzia v141 | 15.9.28230.55 | Wymagany
Składnik Microsoft.VisualStudio.Component.Windows10SDK | Uniwersalny czas pracy systemu Windows C | 15.6.27406.0 | Wymagany
Narzędzia Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler GPU dla DirectX | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.Graphics.Win81 | Narzędzia graficzne Zestaw Windows 8.1 SDK | 15.6.27406.0 | Zalecane
Narzędzia diagnostyczne Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania języka C++ | 15.0.26823.1 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Zalecane
Składnik.Android.NDK.R12B | Android NDK (R12B) | 12.1.10 | Optional (Opcjonalność)
Składnik.Android.SDK23.Private | Konfiguracja SDK Systemu Android (poziom API 23) (instalacja lokalna dla rozwoju urządzeń przenośnych z JavaScript / C++) | 15.9.28016.0 | Optional (Opcjonalność)
Składnik.Ant | Mrówka Apache (1.9.3) | 1.9.3.8 | Optional (Opcjonalność)
Składnik.Cocos | Cocos | 15.0.26906.1 | Optional (Opcjonalność)
Składnik.Incredibuild | IncrediBuild - Przyspieszenie kompilacji | 15.7.27617.1 | Optional (Opcjonalność)
Składnik.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Optional (Opcjonalność)
Składnik.MDD.Android | Narzędzia programistyczne dla systemu Android w języku C++ | 15.0.26606.0 | Optional (Opcjonalność)
Składnik.OpenJDK | Dystrybucja Firmy Microsoft OpenJDK | 15.9.28125.51 | Optional (Opcjonalność)
Składnik.Nierealne | Instalator Unreal Engine | 15.8.27729.1 | Optional (Opcjonalność)
Składnik.Unreal.Android | Obsługa systemu Visual Studio dla systemu Android dla unreal engine | 15.9.28307.341 | Optional (Opcjonalność)
Składnik.VC.Środowisko wykonawcze.UCRTSDK firmy Microsoft.Component.VC.Runtime.UCRTSDK | Uniwersalny zestaw CRT systemu Windows | 15.6.27309.0 | Optional (Opcjonalność)
Pakiet targetingu firmy Microsoft.Net.Component.4.5.1.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.1 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 15.6.27406.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.6.1.SDK | Plik SDK programu .NET Framework 4.6.1 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.6.TargetingPack | Pakiet targetowania programu .NET Framework 4.6 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet docelowy firmy Microsoft.Net.Component.4.TargetingPack | Pakiet targetowania programu .NET Framework 4 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.6.1 | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 narzędzia programistyczne | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet cele i budować zadania | 15.9.28016.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 15.6.27309.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) dla pulpitu C++ [x86 i x64] | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C++ | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) dla pulpitu C++ [x86 i x64] | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Windows 10 SDK (10.0.16299.0) dla pulpitu C++ [ARM i ARM64] | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C++ | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.9.28307.102 | Optional (Opcjonalność)
Składnik Microsoft.VisualStudio.Component.Windows81SDK | Zestaw SDK systemu Windows 8.1 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK i UCRT SDK | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | Optional (Opcjonalność)

## <a name="mobile-development-with-c"></a>Tworzenie aplikacji mobilnych w języku C++

**Identyfikator:** Microsoft.VisualStudio.Workload.NativeMobile

**Opis:** Tworzenie aplikacji wieloplatformowych dla systemów iOS, Android lub Windows przy użyciu języka C++.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.Android.SDK19.Private | Konfiguracja SDK Systemu Android (poziom API 19) (instalacja lokalna dla rozwoju urządzeń przenośnych z JavaScript / C++) | 15.9.28107.0 | Wymagany
Składnik.Android.SDK21.Private | Konfiguracja SDK Systemu Android (poziom API 21) (instalacja lokalna dla rozwoju urządzeń przenośnych z JavaScript / C++) | 15.9.28016.0 | Wymagany
Składnik.Android.SDK22.Private | Konfiguracja SDK Systemu Android (poziom API 22) (instalacja lokalna dla rozwoju urządzeń przenośnych z JavaScript / C++) | 15.9.28016.0 | Wymagany
Składnik.Android.SDK23.Private | Konfiguracja SDK Systemu Android (poziom API 23) (instalacja lokalna dla rozwoju urządzeń przenośnych z JavaScript / C++) | 15.9.28016.0 | Wymagany
Składnik.Android.SDK25.Private | Konfiguracja SDK Systemu Android (poziom API 25) (instalacja lokalna dla rozwoju urządzeń przenośnych z JavaScript / C++) | 15.9.28016.0 | Wymagany
Składnik.OpenJDK | Dystrybucja Firmy Microsoft OpenJDK | 15.9.28125.51 | Wymagany
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Wymagany
Składnik.Android.NDK.R15C | Android NDK (R15C) | 15.2.1 | Zalecane
Składnik.Ant | Mrówka Apache (1.9.3) | 1.9.3.8 | Zalecane
Składnik.MDD.Android | Narzędzia programistyczne dla systemu Android w języku C++ | 15.0.26606.0 | Zalecane
Składnik.Android.NDK.R12B | Android NDK (R12B) | 12.1.10 | Optional (Opcjonalność)
Składnik.Android.NDK.R12B_3264 | Android NDK (R12B) (32-bitowy) | 12.1.11 | Optional (Opcjonalność)
Składnik.Android.NDK.R13B | Android NDK (R13B) | 13.1.7 | Optional (Opcjonalność)
Składnik.Android.NDK.R13B_3264 | Android NDK (R13B) (32-bitowy) | 13.1.8 | Optional (Opcjonalność)
Składnik.Android.NDK.R15C_3264 | Android NDK (R15C) (32-bitowy) | 15.2.1 | Optional (Opcjonalność)
Składnik.Google.Android.Emulator.API23.Private | Google Android Emulator (POZIOM API 23) (instalacja lokalna) | 15.6.27413.0 | Optional (Opcjonalność)
Składnik.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (instalacja lokalna) | 15.9.28307.421 | Optional (Opcjonalność)
Składnik.Incredibuild | IncrediBuild - Przyspieszenie kompilacji | 15.7.27617.1 | Optional (Opcjonalność)
Składnik.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Optional (Opcjonalność)
Składnik.MDD.IOS | Narzędzia programistyczne systemu iOS w języku C++ | 15.0.26621.2 | Optional (Opcjonalność)

## <a name="net-core-cross-platform-development"></a>Tworzenie aplikacji dla wielu platform w środowisku .NET Core

**Identyfikator:** Microsoft.VisualStudio.Workload.NetCoreTools

**Opis:** Twórz aplikacje wieloplatformowe przy użyciu platformy .NET Core, ASP.NET Core, HTML/JavaScript i Kontenery, w tym obsługę platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.Microsoft.VisualStudio.RazorEkstrysja | Usługi językowe brzytwy | 15.0.26720.2 | Wymagany
Składnik.Microsoft.Web.LibraryManager | Library Manager | 15.8.27705.0 | Wymagany
Składnik.WebSocket | Sieć WebSocket4Net | 15.0.26606.0 | Wymagany
Składnik Microsoft.ClickOnce | Kliknij publikowanieonce | 15.8.27825.0 | Wymagany
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 15.6.27406.0 | Wymagany
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 15.6.27406.0 | Wymagany
Składnik Microsoft.Net.4.6.1.SDK | Plik SDK programu .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.6.1 | 15.8.27825.0 | Wymagany
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne .NET Core 2.1 | 15.8.27924.0 | Wymagany
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programistyczne .NET Core 2.1 | 15.8.27924.0 | Wymagany
Microsoft.NetCore.ComponentGroup.Web.2.1 | Narzędzia programistyczne .NET Core 2.1 | 15.8.27924.0 | Wymagany
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Wymagany
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 15.8.27906.1 | Wymagany
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia do tworzenia kontenerów — narzędzia do tworzenia | 15.7.27617.1 | Wymagany
Microsoft.VisualStudio.Component.FSharp | Obsługa języka Języka F# | 15.8.27825.0 | Wymagany
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Obsługa języka F# dla projektów internetowych | 15.9.28307.421 | Wymagany
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 15.9.28125.51 | Wymagany
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Rdzeń zarządzanego obciążenia pulpitu | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagany
Microsoft.VisualStudio.Component.PortableBrary | Pakiet kierowania na bibliotekę przenośną platformy .NET | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko wykonawcze SQL ADAL | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.SQL.CMDUtils | Narzędzia wiersza polecenia programu SQL Server | 15.0.26208.0 | Wymagany
Źródła danych Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla obsługi programu SQL Server | 15.0.26621.2 | Wymagany
Środowisko wykonawcze Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Wymagany
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Wymagany
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 15.0.26208.0 | Wymagany
Składnik Microsoft.VisualStudio.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Wymagany
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne ASP.NET i narzędzi do tworzenia stron internetowych | 15.9.28219.51 | Wymagany
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 15.8.27825.0 | Wymagany
Składnik.Microsoft.VisualStudio.Web.AzureFunkcje | Narzędzia Microsoft Azure WebJobs | 15.7.27617.1 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia do analizy deweloperów | 15.8.27825.0 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.Azure.AuthoringTools | Narzędzia do tworzenia platformy Azure | 15.9.28307.421 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki platformy Azure dla platformy .NET | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 15.9.28307.421 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 15.9.28125.51 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 15.8.27729.1 | Zalecane
Składnik Microsoft.VisualStudio.Web | narzędzia do tworzenia ASP.NET i tworzenia stron internetowych | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.ComponentGroup.AzureFunkcje | Narzędzia Microsoft Azure WebJobs | 15.7.27617.1 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Narzędzia chmurowe do tworzenia stron internetowych | 15.8.27729.1 | Zalecane
Plik Microsoft.Net.Core.Component.SDK | Narzędzia programistyczne .NET Core 2.0 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 narzędzia programistyczne | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.NetCore.1x.ComponentGroup.Web | .NET Core 1.0 - 1.1 narzędzia programistyczne dla sieci Web | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Narzędzia programistyczne .NET Core 2.0 | 15.8.27729.1 | Optional (Opcjonalność)
Microsoft.NetCore.ComponentGroup.Web | Narzędzia programistyczne .NET Core 2.0 | 15.7.27625.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.IISRozwój | Obsługa programów IIS w czasie rozwoju | 15.9.28219.51 | Optional (Opcjonalność)

## <a name="mobile-development-with-net"></a>Rozwój urządzeń mobilnych z systemem .NET

**Identyfikator:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Opis:** Tworzenie aplikacji wieloplatformowych dla systemów iOS, Android lub Windows przy użyciu platformy Xamarin.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.Xamarin | Xamarin | 15.8.27906.1 | Wymagany
Składnik.Xamarin.RemotedSimulator | Symulator zdalnego sterowania platformy Xamarin | 15.6.27323.2 | Wymagany
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagany
Składnik Microsoft.Net.4.6.1.SDK | Plik SDK programu .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.6.1 | 15.8.27825.0 | Wymagany
Plik Microsoft.Net.Core.Component.SDK | Narzędzia programistyczne .NET Core 2.0 | 15.6.27406.0 | Wymagany
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Narzędzia programistyczne .NET Core 2.0 | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.FSharp | Obsługa języka Języka F# | 15.8.27825.0 | Wymagany
Microsoft.VisualStudio.Component.Merq | Typowe narzędzia wewnętrzne platformy Xamarin | 15.8.27924.0 | Wymagany
Składnik Microsoft.VisualStudio.Component.MonoDebugger | Debuger mono | 15.0.26720.2 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagany
Microsoft.VisualStudio.Component.PortableBrary | Pakiet kierowania na bibliotekę przenośną platformy .NET | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | ASP.NET silnik do tworzenia maszyn | 15.8.27729.1 | Wymagany
Składnik.Android.SDK27 | Konfiguracja SDK systemu Android (poziom interfejsu API 27) | 15.9.28016.0 | Zalecane
Składnik.Google.Android.Emulator.API27 | Google Android Emulator (POZIOM API 27) | 15.9.28307.421 | Zalecane
Składnik.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) (instalacja globalna) | 15.9.28307.421 | Zalecane
Składnik.OpenJDK | Dystrybucja Firmy Microsoft OpenJDK | 15.9.28125.51 | Zalecane
Składnik.Xamarin.Inspektor | Xamarin Workbooks | 15.0.26606.0 | Optional (Opcjonalność)
Składnik Microsoft.ClickOnce | Kliknij publikowanieonce | 15.8.27825.0 | Optional (Opcjonalność)
Składnik Microsoft.NetFX.natywny | Architektura .NET Native | 15.0.26208.0 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia do analizy deweloperów | 15.8.27825.0 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 15.8.27729.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Graphics | Edytory obrazów i modeli 3D | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Narzędzia platformy uniwersalnej systemu Windows dla platformy Xamarin | 15.9.28307.102 | Optional (Opcjonalność)

## <a name="aspnet-and-web-development"></a>Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych

**Identyfikator:** Microsoft.VisualStudio.Workload.NetWeb

**Opis:** Twórz aplikacje internetowe przy użyciu ASP.NET, ASP.NET Core, HTML/JavaScript i Kontenery, w tym obsługę platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.Microsoft.VisualStudio.RazorEkstrysja | Usługi językowe brzytwy | 15.0.26720.2 | Wymagany
Składnik.Microsoft.Web.LibraryManager | Library Manager | 15.8.27705.0 | Wymagany
Składnik.WebSocket | Sieć WebSocket4Net | 15.0.26606.0 | Wymagany
Składnik Microsoft.ClickOnce | Kliknij publikowanieonce | 15.8.27825.0 | Wymagany
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 15.6.27406.0 | Wymagany
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 15.6.27406.0 | Wymagany
Składnik Microsoft.Net.4.6.1.SDK | Plik SDK programu .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.6.1 | 15.8.27825.0 | Wymagany
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne .NET Core 2.1 | 15.8.27924.0 | Wymagany
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programistyczne .NET Core 2.1 | 15.8.27924.0 | Wymagany
Microsoft.NetCore.ComponentGroup.Web.2.1 | Narzędzia programistyczne .NET Core 2.1 | 15.8.27924.0 | Wymagany
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Wymagany
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 15.8.27906.1 | Wymagany
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia do tworzenia kontenerów — narzędzia do tworzenia | 15.7.27617.1 | Wymagany
Microsoft.VisualStudio.Component.FSharp | Obsługa języka Języka F# | 15.8.27825.0 | Wymagany
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Obsługa języka F# dla projektów internetowych | 15.9.28307.421 | Wymagany
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 15.9.28125.51 | Wymagany
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Rdzeń zarządzanego obciążenia pulpitu | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagany
Microsoft.VisualStudio.Component.PortableBrary | Pakiet kierowania na bibliotekę przenośną platformy .NET | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko wykonawcze SQL ADAL | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.SQL.CMDUtils | Narzędzia wiersza polecenia programu SQL Server | 15.0.26208.0 | Wymagany
Źródła danych Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla obsługi programu SQL Server | 15.0.26621.2 | Wymagany
Środowisko wykonawcze Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Wymagany
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Wymagany
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 15.0.26208.0 | Wymagany
Składnik Microsoft.VisualStudio.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Wymagany
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagany
Składnik Microsoft.VisualStudio.Web | narzędzia do tworzenia ASP.NET i tworzenia stron internetowych | 15.8.27825.0 | Wymagany
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne ASP.NET i narzędzi do tworzenia stron internetowych | 15.9.28219.51 | Wymagany
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 15.8.27825.0 | Wymagany
Składnik.Microsoft.VisualStudio.Web.AzureFunkcje | Narzędzia Microsoft Azure WebJobs | 15.7.27617.1 | Zalecane
Pakiet targetingu firmy Microsoft.Net.Component.4.5.1.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.1 | 15.6.27406.0 | Zalecane
Pakiet targeting firmy Microsoft.Net.Component.4.6.TargetingPack | Pakiet targetowania programu .NET Framework 4.6 | 15.6.27406.0 | Zalecane
Pakiet docelowy firmy Microsoft.Net.Component.4.TargetingPack | Pakiet targetowania programu .NET Framework 4 | 15.6.27406.0 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 narzędzia programistyczne | 15.6.27406.0 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia do analizy deweloperów | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane funkcje ASP.NET | 15.7.27625.0 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.Azure.AuthoringTools | Narzędzia do tworzenia platformy Azure | 15.9.28307.421 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki platformy Azure dla platformy .NET | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 15.9.28307.421 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 15.9.28125.51 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.EntityFramework | Narzędzia entity Framework 6 | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.ComponentGroup.AzureFunkcje | Narzędzia Microsoft Azure WebJobs | 15.7.27617.1 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Narzędzia chmurowe do tworzenia stron internetowych | 15.8.27729.1 | Zalecane
Składnik Microsoft.Net.4.6.2.SDK | Plik SDK programu .NET Framework 4.6.2 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.6.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.6.2 | 15.6.27406.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.7.1.SDK | Plik SDK programu .NET Framework 4.7.1 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targetingu firmy Microsoft.Net.Component.4.7.1.TargetingPack | Pakiet kierowania .NET Framework 4.7.1 | 15.6.27406.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.7.2.SDK | Plik SDK programu .NET Framework 4.7.2 | 15.8.27825.0 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.7.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.7.2 | 15.8.27825.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.7.SDK | Plik SDK programu .NET Framework 4.7 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.7.TargetingPack | Pakiet targetowania programu .NET Framework 4.7 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Narzędzia programistyczne .NET Framework 4.6.2 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7.1 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7.2 | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7 | 15.6.27406.0 | Optional (Opcjonalność)
Plik Microsoft.Net.Core.Component.SDK | Narzędzia programistyczne .NET Core 2.0 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 narzędzia programistyczne | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.NetCore.1x.ComponentGroup.Web | .NET Core 1.0 - 1.1 narzędzia programistyczne dla sieci Web | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Narzędzia programistyczne .NET Core 2.0 | 15.8.27729.1 | Optional (Opcjonalność)
Microsoft.NetCore.ComponentGroup.Web | Narzędzia programistyczne .NET Core 2.0 | 15.7.27625.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.IISRozwój | Obsługa programów IIS w czasie rozwoju | 15.9.28219.51 | Optional (Opcjonalność)
Grupa składników Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 15.6.27406.0 | Optional (Opcjonalność)

## <a name="nodejs-development"></a>Rozwój node.js

**Identyfikator:** Węzeł Microsoft.VisualStudio.Workload.Node

**Opis:** Twórz skalowalne aplikacje sieciowe przy użyciu node.js, asynchronisty środowiska wykonawczego JavaScript opartego na zdarzeniach. 

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.WebSocket | Sieć WebSocket4Net | 15.0.26606.0 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 15.9.28125.51 | Wymagany
Microsoft.VisualStudio.Component.Node.Build | Obsługa aplikacji Node.js MSBuild | 15.8.27825.0 | Wymagany
Narzędzia Microsoft.VisualStudio.Component.Node.Tools | Pomoc techniczna aplikacji Node.js development | 15.8.27825.0 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagany
Microsoft.VisualStudio.Component.TestTools.Core | Podstawowe funkcje narzędzi testowych | 15.7.27520.0 | Wymagany
Składnik Microsoft.VisualStudio.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Wymagany
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 15.8.27825.0 | Wymagany
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Narzędzia Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia do analizy deweloperów | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 wersja 15.9 v14.16 najnowsze narzędzia v141 | 15.9.28230.55 | Optional (Opcjonalność)

## <a name="officesharepoint-development"></a>Program rozwoju pakietu Office/programu SharePoint

**Identyfikator:** Microsoft.VisualStudio.Workload.Office

**Opis:** Tworzenie dodatków pakietu Office i programu SharePoint, rozwiązań programu SharePoint i dodatków VSTO przy użyciu dodatków C#, VB i JavaScript.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.Microsoft.VisualStudio.RazorEkstrysja | Usługi językowe brzytwy | 15.0.26720.2 | Wymagany
Składnik.Microsoft.Web.LibraryManager | Library Manager | 15.8.27705.0 | Wymagany
Składnik.WebSocket | Sieć WebSocket4Net | 15.0.26606.0 | Wymagany
Składnik Microsoft.ClickOnce | Kliknij publikowanieonce | 15.8.27825.0 | Wymagany
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 15.6.27406.0 | Wymagany
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 15.6.27406.0 | Wymagany
Składnik Microsoft.Net.4.6.1.SDK | Plik SDK programu .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Pakiet docelowy firmy Microsoft.Net.Component.4.TargetingPack | Pakiet targetowania programu .NET Framework 4 | 15.6.27406.0 | Wymagany
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.6.1 | 15.8.27825.0 | Wymagany
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne .NET Core 2.1 | 15.8.27924.0 | Wymagany
Narzędzia Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia do analizy deweloperów | 15.8.27825.0 | Wymagany
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Wymagany
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 15.8.27906.1 | Wymagany
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia do tworzenia kontenerów — narzędzia do tworzenia | 15.7.27617.1 | Wymagany
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 15.9.28125.51 | Wymagany
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Rdzeń zarządzanego obciążenia pulpitu | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.ManagedDesktop.Wymagania wstępne | Narzędzia programistyczne dla komputerów .NET | 15.7.27625.0 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagany
Microsoft.VisualStudio.Component.PortableBrary | Pakiet kierowania na bibliotekę przenośną platformy .NET | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 15.8.27924.0 | Wymagany
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko wykonawcze SQL ADAL | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.SQL.CMDUtils | Narzędzia wiersza polecenia programu SQL Server | 15.0.26208.0 | Wymagany
Źródła danych Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla obsługi programu SQL Server | 15.0.26621.2 | Wymagany
Środowisko wykonawcze Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Wymagany
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Wymagany
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 15.0.26208.0 | Wymagany
Składnik Microsoft.VisualStudio.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Wymagany
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Wymagany
Składnik Microsoft.VisualStudio.Web | narzędzia do tworzenia ASP.NET i tworzenia stron internetowych | 15.8.27825.0 | Wymagany
Przepływ pracy Microsoft.VisualStudio.Component.Work | Windows Workflow Foundation | 15.8.27825.0 | Wymagany
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne ASP.NET i narzędzi do tworzenia stron internetowych | 15.9.28219.51 | Wymagany
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 15.8.27825.0 | Wymagany
Microsoft.VisualStudio.Component.TeamOffice | Narzędzia programu Visual Studio dla pakietu Office (VSTO) | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Składnik Microsoft.Net.4.6.2.SDK | Plik SDK programu .NET Framework 4.6.2 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.6.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.6.2 | 15.6.27406.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.7.1.SDK | Plik SDK programu .NET Framework 4.7.1 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targetingu firmy Microsoft.Net.Component.4.7.1.TargetingPack | Pakiet kierowania .NET Framework 4.7.1 | 15.6.27406.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.7.2.SDK | Plik SDK programu .NET Framework 4.7.2 | 15.8.27825.0 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.7.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.7.2 | 15.8.27825.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.7.SDK | Plik SDK programu .NET Framework 4.7 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.7.TargetingPack | Pakiet targetowania programu .NET Framework 4.7 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Narzędzia programistyczne .NET Framework 4.6.2 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7.1 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7.2 | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia programistyczne .NET Framework 4.7 | 15.6.27406.0 | Optional (Opcjonalność)

## <a name="python-development"></a>Rozwój Pythona

**Identyfikator:** Microsoft.VisualStudio.Workload.Python

**Opis:** Edycja, debugowanie, interaktywne tworzenie i kontrola źródła dla Języka Python.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.PythonTools | Obsługa języka Języka Python | 15.0.26823.1 | Wymagany
Składnik.CPython3.x64 | Python 3 64-bitowy (3.6.6) | 3.6.6 | Zalecane
Microsoft.Component.CookiecutterTools | Obsługa szablonów cookiecutter | 15.0.26621.2 | Zalecane
Microsoft.Component.PythonTools.Web | Pomoc techniczna języka Python | 15.9.28107.0 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 15.9.28125.51 | Zalecane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Zalecane
Składnik Microsoft.VisualStudio.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Zalecane
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 15.8.27825.0 | Zalecane
Składnik.Anaconda2.x64 | Anaconda2 64-bitowy (5.2.0) | 5.2.0 | Optional (Opcjonalność)
Składnik.Anaconda2.x86 | Anaconda2 32-bitowy (5.2.0) | 5.2.0 | Optional (Opcjonalność)
Składnik.Anaconda3.x64 | Anaconda3 64-bitowy (5.2.0) | 5.2.0 | Optional (Opcjonalność)
Składnik.Anaconda3.x86 | Anaconda3 32-bitowy (5.2.0) | 5.2.0 | Optional (Opcjonalność)
Składnik.CPython2.x64 | Python 2 64-bitowy (2.7.14) | 2.7.14 | Optional (Opcjonalność)
Składnik.CPython2.x86 | Python 2 32-bitowy (2.7.14) | 2.7.14 | Optional (Opcjonalność)
Składnik.CPython3.x86 | Python 3 32-bitowy (3.6.6) | 3.6.6 | Optional (Opcjonalność)
Składnik.Microsoft.VisualStudio.RazorEkstrysja | Usługi językowe brzytwy | 15.0.26720.2 | Optional (Opcjonalność)
Składnik.Microsoft.Web.LibraryManager | Library Manager | 15.8.27705.0 | Optional (Opcjonalność)
Składnik.WebSocket | Sieć WebSocket4Net | 15.0.26606.0 | Optional (Opcjonalność)
Składnik Microsoft.ClickOnce | Kliknij publikowanieonce | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Optional (Opcjonalność)
Składnik Microsoft.NetFX.natywny | Architektura .NET Native | 15.0.26208.0 | Optional (Opcjonalność)
Microsoft.Component.PythonTools.UwP | Pomoc techniczna aplikacji Python IoT | 15.0.26606.0 | Optional (Opcjonalność)
Składnik.VC.Środowisko wykonawcze.UCRTSDK firmy Microsoft.Component.VC.Runtime.UCRTSDK | Uniwersalny zestaw CRT systemu Windows | 15.6.27309.0 | Optional (Opcjonalność)
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Natywne narzędzia programistyczne Języka Python | 15.9.28307.102 | Optional (Opcjonalność)
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 15.6.27406.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.6.1.SDK | Plik SDK programu .NET Framework 4.6.1 | 15.6.27406.0 | Optional (Opcjonalność)
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.6.1 | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne .NET Core 2.1 | 15.8.27924.0 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia do analizy deweloperów | 15.8.27825.0 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.Azure.AuthoringTools | Narzędzia do tworzenia platformy Azure | 15.9.28307.421 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki platformy Azure dla platformy .NET | 15.0.26208.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 15.9.28307.421 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 15.9.28125.51 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Azure.Waverton | Podstawowe narzędzia usług w chmurze azure | 15.9.28107.0 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do tworzenia usług w chmurze azure | 15.7.27617.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.ClassDesigner | Projektant klas | 15.0.26208.0 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 15.8.27729.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 15.8.27906.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia do tworzenia kontenerów — narzędzia do tworzenia | 15.7.27617.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Graphics | Edytory obrazów i modeli 3D | 15.6.27406.0 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler GPU dla DirectX | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Graphics.Win81 | Narzędzia graficzne Zestaw Windows 8.1 SDK | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Rdzeń zarządzanego obciążenia pulpitu | 15.8.27729.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.PortableBrary | Pakiet kierowania na bibliotekę przenośną platformy .NET | 15.6.27309.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 15.6.27309.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko wykonawcze SQL ADAL | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.SQL.CMDUtils | Narzędzia wiersza polecenia programu SQL Server | 15.0.26208.0 | Optional (Opcjonalność)
Źródła danych Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych dla obsługi programu SQL Server | 15.0.26621.2 | Optional (Opcjonalność)
Środowisko wykonawcze Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 15.0.26208.0 | Optional (Opcjonalność)
Składnik.140 firmy Microsoft.VisualStudio.Component.VC.140 | Zestaw narzędzi VC++ 2015.3 v14.00 (v140) dla komputerów stacjonarnych | 15.7.27617.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Optional (Opcjonalność)
Narzędzia diagnostyczne Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania języka C++ | 15.0.26823.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 wersja 15.9 v14.16 najnowsze narzędzia v141 | 15.9.28230.55 | Optional (Opcjonalność)
Składnik Microsoft.VisualStudio.Web | narzędzia do tworzenia ASP.NET i tworzenia stron internetowych | 15.8.27825.0 | Optional (Opcjonalność)
Składnik Microsoft.VisualStudio.Component.Windows10SDK | Uniwersalny czas pracy systemu Windows C | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Optional (Opcjonalność)
Składnik Microsoft.VisualStudio.Component.Windows81SDK | Zestaw SDK systemu Windows 8.1 | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne ASP.NET i narzędzi do tworzenia stron internetowych | 15.9.28219.51 | Optional (Opcjonalność)

## <a name="universal-windows-platform-development"></a>Tworzenie uniwersalnej platformy systemu Windows

**Identyfikator:** Microsoft.VisualStudio.Workload.Universal

**Opis:** Tworzenie aplikacji dla platformy uniwersalnej systemu Windows za pomocą języka C#, VB, JavaScript lub opcjonalnie języka C++.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.WebSocket | Sieć WebSocket4Net | 15.0.26606.0 | Wymagany
Składnik Microsoft.ClickOnce | Kliknij publikowanieonce | 15.8.27825.0 | Wymagany
Składnik Microsoft.NetFX.natywny | Architektura .NET Native | 15.0.26208.0 | Wymagany
Składnik Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.6.27406.0 | Wymagany
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 15.6.27406.0 | Wymagany
Składnik Microsoft.Net.4.6.1.SDK | Plik SDK programu .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne .NET Core 2.1 | 15.8.27924.0 | Wymagany
Narzędzia Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia do analizy deweloperów | 15.8.27825.0 | Wymagany
Narzędzia Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.Graphics | Edytory obrazów i modeli 3D | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 15.9.28125.51 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagany
Microsoft.VisualStudio.Component.PortableBrary | Pakiet kierowania na bibliotekę przenośną platformy .NET | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Wymagany
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Wymagany
Składnik Microsoft.VisualStudio.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Wymagany
Pomoc techniczna aplikacji Microsoft.VisualStudio.Component.UWP.Support | Narzędzia platformy uniwersalnej systemu Windows | 15.9.28119.51 | Wymagany
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Wymagany
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Uniwersalne narzędzia platformy systemu Windows dla Cordova | 15.9.28307.102 | Wymagany
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | Natywny i .NET Standard platformy .NET | 15.8.27906.1 | Wymagany
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Narzędzia platformy uniwersalnej systemu Windows dla platformy Xamarin | 15.9.28307.102 | Wymagany
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 15.8.27825.0 | Wymagany
Microsoft.Component.VC.Runtime.OSSport | Środowisko wykonawcze Visual C++ dla platformy uniwersalnej systemu i platformy uniwersalnej | 15.6.27406.0 | Optional (Opcjonalność)
Składnik Microsoft.Net.4.7.2.SDK | Plik SDK programu .NET Framework 4.7.2 | 15.8.27825.0 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler GPU dla DirectX | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Graphics.Win81 | Narzędzia graficzne Zestaw Windows 8.1 SDK | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Windows 10 Mobile Emulator (Fall Creators Update) | 15.0.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Narzędzia platformy uniwersalnej systemu Windows c++ dla ARM64 | 15.0.28125.51 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Tools.ARM | Kompilatory i biblioteki visual C++ dla ARM | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Kompilatory i biblioteki visual c++ dla ARM64 | 15.9.28230.55 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 wersja 15.9 v14.16 najnowsze narzędzia v141 | 15.9.28230.55 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) dla pulpitu C++ [x86 i x64] | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C++ | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) dla pulpitu C++ [x86 i x64] | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Windows 10 SDK (10.0.16299.0) dla pulpitu C++ [ARM i ARM64] | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C++ | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.9.28307.102 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Łączność z urządzeniem USB | 15.9.28307.102 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Narzędzia platformy uniwersalnej systemu Windows w języku C++ | 15.9.28307.102 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | Optional (Opcjonalność)

## <a name="visual-studio-extension-development"></a>Programowanie rozszerzeń programu Visual Studio

**Identyfikator:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Opis:** Tworzenie dodatków i rozszerzeń dla programu Visual Studio, w tym nowych poleceń, analizatorów kodu i okien narzędzi.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik Microsoft.ClickOnce | Kliknij publikowanieonce | 15.8.27825.0 | Wymagany
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagany
Składnik Microsoft.Net.4.6.1.SDK | Plik SDK programu .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Pakiet targeting firmy Microsoft.Net.Component.4.6.TargetingPack | Pakiet targetowania programu .NET Framework 4.6 | 15.6.27406.0 | Wymagany
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.6.1 | 15.8.27825.0 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagany
Microsoft.VisualStudio.Component.PortableBrary | Pakiet kierowania na bibliotekę przenośną platformy .NET | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia analizy statycznej | 15.0.26208.0 | Wymagany
Składnik.VSSDK firmy Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 15.8.27729.1 | Wymagany
Wymagania wstępne dotyczące programu Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Wymagania wstępne tworzenia rozszerzeń programu Visual Studio | 15.7.27625.0 | Wymagany
Narzędzia Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.TextTemplating | Transformacja szablonu tekstu | 15.0.26208.0 | Zalecane
Składnik.Dotfuscator | PreEmptive Protection — Dotfuscator | 15.0.26208.0 | Optional (Opcjonalność)
Składnik.Składnik.CodeAnalysis.SDK | Zestaw SDK platformy kompilatora .NET | 15.0.27729.1 | Optional (Opcjonalność)
Microsoft.Component.VC.Runtime.OSSport | Środowisko wykonawcze Visual C++ dla platformy uniwersalnej systemu i platformy uniwersalnej | 15.6.27406.0 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia do analizy deweloperów | 15.8.27825.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.ClassDesigner | Projektant klas | 15.0.26208.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.DslTools | Modelowanie SDK | 15.0.27005.2 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL dla x86 i x64 | 15.7.27625.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC dla x86 i x64 | 15.7.27625.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 wersja 15.9 v14.16 najnowsze narzędzia v141 | 15.9.28230.55 | Optional (Opcjonalność)

## <a name="mobile-development-with-javascript"></a>Tworzenie aplikacji mobilnych w języku JavaScript

**Identyfikator:** Microsoft.VisualStudio.Workload.WebCrossPlat

**Opis:** Tworzenie aplikacji systemu Android, iOS i platformy uniwersalnej systemu Windows przy użyciu narzędzi dla Apache Cordova.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik.CordovaToolset.6.3.1 | Zestaw narzędzi Cordova 6.3.1 | 15.7.27625.0 | Wymagany
Składnik.WebSocket | Sieć WebSocket4Net | 15.0.26606.0 | Wymagany
Microsoft.VisualStudio.Component.Cordova | Rozwój urządzeń mobilnych z podstawowymi funkcjami JavaScript | 15.0.26606.0 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.ProjectSystem | JavaScript ProjectSystem i narzędzia współdzielone | 15.0.26606.0 | Wymagany
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języka JavaScript i TypeScript | 15.9.28125.51 | Wymagany
Składnik Microsoft.VisualStudio.TypeScript.2.3 | TypeScript 2.3 SDK | 15.8.27729.1 | Wymagany
Składnik Microsoft.VisualStudio.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | Wymagany
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions Microsoft. | Tworzenie aplikacji na platformie ASP.NET i aplikacji internetowych | 15.8.27825.0 | Wymagany
Składnik.Android.SDK23.Private | Konfiguracja SDK Systemu Android (poziom API 23) (instalacja lokalna dla rozwoju urządzeń przenośnych z JavaScript / C++) | 15.9.28016.0 | Optional (Opcjonalność)
Składnik.Google.Android.Emulator.API23.Private | Google Android Emulator (POZIOM API 23) (instalacja lokalna) | 15.6.27413.0 | Optional (Opcjonalność)
Składnik.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (instalacja lokalna) | 15.9.28307.421 | Optional (Opcjonalność)
Składnik.OpenJDK | Dystrybucja Firmy Microsoft OpenJDK | 15.9.28125.51 | Optional (Opcjonalność)
Składnik Microsoft.ClickOnce | Kliknij publikowanieonce | 15.8.27825.0 | Optional (Opcjonalność)
Składnik Microsoft.NetFX.natywny | Architektura .NET Native | 15.0.26208.0 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia do analizy deweloperów | 15.8.27825.0 | Optional (Opcjonalność)
Narzędzia Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania .NET | 15.8.27729.1 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Git | Git dla systemu Windows | 15.0.26208.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Graphics | Edytory obrazów i modeli 3D | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Windows 10 Mobile Emulator (Fall Creators Update) | 15.0.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Optional (Opcjonalność)
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Optional (Opcjonalność)
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Uniwersalne narzędzia platformy systemu Windows dla Cordova | 15.9.28307.102 | Optional (Opcjonalność)

## <a name="unaffiliated-components"></a>Składniki niepowiązane

Są to składniki, które nie są dołączone do żadnego obciążenia, ale mogą być wybrane jako pojedynczy składnik.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
Składnik.Android.Emulator | Emulator programu Visual Studio dla systemu Android | 15.6.27413.0
Składnik.Android.NDK.R11C | Android NDK (R11C) | 11.3.14
Składnik.Android.NDK.R11C_3264 | Android NDK (R11C) (32-bitowy) | 11.3.16
Składnik.Android.SDK23 | Konfiguracja SDK systemu Android (poziom interfejsu API 23) (instalacja globalna) | 15.9.28107.0
Składnik.Android.SDK25 | Konfiguracja SDK systemu Android (poziom interfejsu API 25) | 15.9.28107.0
Składnik.GitHub.VisualStudio | Rozszerzenie GitHub dla programu Visual Studio | 2.5.2.2500
Składnik.Google.Android.Emulator.API23.V2 | Google Android Emulator (API Level 23) (instalacja globalna) | 15.6.27413.0
Składnik.Google.Android.Emulator.API25 | Google Android Emulator (POZIOM API 25) | 15.7.27604.0
Składnik.Składnik.Mieszanie.SDK.WPF | Blend for Visual Studio SDK for .NET Blend for Visual Studio SDK for .NET Blend for Visual Studio SDK for .NET Blend for | 15.6.27406.0
Microsoft.Component.HelpViewer | Podgląd pomocy | 15.9.28307.421
Microsoft.VisualStudio.Component.DependencyValidation.Community | Sprawdzanie poprawności zależności | 15.0.26208.0
Microsoft.VisualStudio.Component.GraphDocument | Edytor DGML | 15.0.27005.2
Składnik Microsoft.VisualStudio.Komponent.LinqToSql | LINQ to SQL Tools | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator | Windows 10 Mobile Emulator (Anniversary Edition) | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Emulator windows 10 Mobile (Aktualizacja twórców) | 15.6.27406.0
Microsoft.VisualStudio.Component.Runtime.Node.x86.6.4.0 | Środowisko uruchomieniowe dla składników opartych na node.js v6.4.0 (x86) | 15.7.27617.1
Microsoft.VisualStudio.Component.Runtime.Node.x86.7.4.0 | Środowisko uruchomieniowe dla składników opartych na node.js v7.4.0 (x86) | 15.7.27617.1
Składnik Microsoft.VisualStudio.TypeScript.2.0 | TypeScript 2.0 SDK | 15.8.27729.1
Składnik Microsoft.VisualStudio.TypeScript.2.1 | TypeScript 2.1 SDK | 15.8.27729.1
Składnik Microsoft.VisualStudio.TypeScript.2.2 | TypeScript 2.2 SDK | 15.8.27729.1
Składnik Microsoft.VisualStudio.TypeScript.2.5 | TypeScript 2.5 SDK | 15.6.27406.0
Składnik Microsoft.VisualStudio.TypeScript.2.6 | TypeScript 2.6 SDK | 15.0.27729.1
Składnik Microsoft.VisualStudio.TypeScript.2.7 | TypeScript 2.7 SDK | 15.0.27729.1
Składnik Microsoft.VisualStudio.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27729.1
Składnik Microsoft.VisualStudio.TypeScript.2.9 | TypeScript 2.9 SDK | 15.0.27924.0
Składnik Microsoft.VisualStudio.TypeScript.3.0 | TypeScript 3.0 SDK | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.ATL.ARM | Visual C++ ATL dla ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Visual C++ ATL dla ARM z spectre mitigations | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | Visual C++ ATL dla ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | Visual C++ ATL dla ARM64 z spectre mitigations | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.Spectre | Visual C++ ATL (x86/x64) z widmami | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Visual C++ MFC dla x86/x64 z spectre mitigations | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (eksperymentalny) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | Visual C++ MFC dla ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | Visual C++ MFC dla ARM z spectre mitigations | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | Visual C++ MFC dla ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Obsługa visual C++ MFC dla ARM64 z spectre mitigations | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | VC++ 2017 wersja 15.9 v14.16 Libs for Spectre (ARM) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | VC++ 2017 wersja 15.9 v14.16 Libs for Spectre (ARM64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | VC++ 2017 wersja 15.9 v14.16 Libs for Spectre (x86 i x64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Tools.14.11 | VC++ 2017 wersja 15.4 v14.11 zestaw narzędzi | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | VC++ 2017 wersja 15.5 v14.12 zestaw narzędzi | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | VC++ 2017 wersja 15.6 v14.13 zestaw narzędzi | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.14 | VC++ 2017 wersja 15.7 v14.14 zestaw narzędzi | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.15 | VC++ 2017 wersja 15.8 v14.15 zestaw narzędzi | 15.0.28230.55
