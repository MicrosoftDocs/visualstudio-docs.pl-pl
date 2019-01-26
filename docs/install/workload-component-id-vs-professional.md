---
title: Visual Studio Professional 2017 obciążeń i składników identyfikatorów
titleSuffix: ''
description: Użyj obciążenia i identyfikatory składników, aby zainstalować program Visual Studio przy użyciu wiersza polecenia lub określić jako zależności w manifestu VSIX
keywords: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.prod: visual-studio-dev15
ms.assetid: 5719032b-2c2e-416e-a281-a4573ec74e38
ms.workload:
- multiple
ms.openlocfilehash: 05cca1fd8f6621254f7ab5c3c427c2450d83802e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017841"
---
# <a name="visual-studio-professional-2017-component-directory"></a>Visual Studio Professional 2017 składników katalogu

Tabele na tej stronie listy identyfikatorów, w której można zainstalować program Visual Studio przy użyciu wiersza polecenia lub można określić jako zależności w manifestu VSIX. Należy pamiętać, że dodamy dodatkowe składniki, jak wydaniu aktualizacji do programu Visual Studio.

Ponadto należy pamiętać, że informacje o stronie:

* Każde obciążenie ma osobny rozdział, następuje identyfikator obciążenia i tabeli składników, które są dostępne dla obciążenia.
* Domyślnie **wymagane** składniki zostaną zainstalowane po zainstalowaniu obciążenia.
* Jeśli chcesz, możesz także zainstalować **zalecane** i **opcjonalnie** składników.
* Dodaliśmy również sekcję, która zawiera listę dodatkowych składników, które nie są powiązane z dowolnych obciążeń.

Po ustawieniu współzależności w manifeście VSIX tylko należy określić identyfikatory składników. Użyj tabel na tej stronie, aby określić nasze zależności minimalnej składnika. W niektórych scenariuszach to oznaczać, że należy określić tylko jeden składnik z obciążenia. W innych przypadkach może oznaczać, możesz określić wiele składników z pojedynczego obciążenia lub wielu składników z wielu obciążeń. Aby uzyskać więcej informacji, zobacz [jak: Migrowanie projektów rozszerzalności do programu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) strony.

Aby uzyskać więcej informacji na temat używania tych identyfikatorów, zobacz [Użyj parametry wiersza polecenia, aby zainstalować program Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) strony. I dla listy, obciążenie i identyfikatorów składników dla innych produktów, zobacz [Visual Studio 2017 obciążenia i identyfikatory składnika](workload-and-component-ids.md) strony.

## <a name="visual-studio-core-editor-included-with-visual-studio-professional-2017"></a>Edytor Visual Studio core (dostarczane z Visual Studio Professional 2017)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Opis:** Visual Studio podstawowe funkcje powłoki, w tym kodu uwzględniającej składnię, edycji i kontroli kodu źródłowego i zarządzanie elementami roboczymi.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Edytor rdzeni programu Visual Studio | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Program Visual Studio uruchomić stronę dla użytkowników języka C++ | 15.0.27128.1 | Optional

## <a name="azure-development"></a>Programowanie na platformie Azure

**ID:** Microsoft.VisualStudio.Workload.Azure

**Opis:** Zestawy SDK platformy Azure, narzędzia i projekty do tworzenia aplikacji w chmurze obsługuje tworzenie zasobów i kompilowania kontenerów platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 15.0.26720.2 | Wymagane
Component.Microsoft.VisualStudio.Web.AzureFunctions | Narzędzia usługi Microsoft Azure WebJobs | 15.7.27617.1 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 15.8.27705.0 | Wymagane
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Wymagane
Microsoft.Component.ClickOnce | Publikowania ClickOnce | 15.8.27825.0 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Component.NetFX.Core.Runtime | Środowisko uruchomieniowe programu .NET core | 15.0.26208.0 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Wymagane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Wymagane
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Wymagane
Microsoft.NetCore.ComponentGroup.Web.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Wymagane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 15.0.26621.2 | Wymagane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 15.9.28125.51 | Wymagane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Wymagane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 15.8.27906.1 | Wymagane
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia programistyczne kontenera — narzędzia Build Tools | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.Component.FSharp | F#Obsługa języków | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#Obsługa języka dla projektów sieci web | 15.8.27705.0 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 15.9.28125.51 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.CMDUtils | Narzędzia wiersza polecenia programu SQL Server | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 15.0.26621.2 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Wymagane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 zestawu SDK | 15.0.28218.60 | Wymagane
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Wymagania wstępne dotyczące programowania dla platformy Azure | 15.9.28107.0 | Wymagane
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Narzędzia usługi Microsoft Azure WebJobs | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 15.9.28219.51 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 15.8.27825.0 | Wymagane
Microsoft.Component.Azure.DataLake.Tools | Usługa Azure Data Lake i Stream Analytics Tools | 15.9.28107.0 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane funkcje platformy ASP.NET | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Zestaw SDK aplikacji mobilnych platformy Azure | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Podstawowe narzędzia usługi Azure Resource Manager | 15.9.28107.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Narzędzia usługi Service Fabric | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton | Podstawowe narzędzia usługi Azure Cloud Services | 15.9.28107.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do kompilacji usługi Azure Cloud Services | 15.7.27617.1 | Zalecane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Narzędzia usług w chmurze platformy Azure | 15.0.26504.0 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Narzędzia usługi Azure Resource Manager | 15.0.27005.2 | Zalecane
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
Microsoft.NetCore.1x.ComponentGroup.Web | .NET core 1.0 – 1.1 narzędzi programistycznych dla sieci Web | 15.6.27406.0 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Narzędzia programistyczne programu .NET core 2.0 | 15.8.27729.1 | Optional
Microsoft.NetCore.ComponentGroup.Web | Narzędzia programistyczne programu .NET core 2.0 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Usługa Azure Storage, narzędzia AzCopy | 15.0.26906.1 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Optional

## <a name="data-storage-and-processing"></a>Magazynowanie i przetwarzanie danych

**ID:** Microsoft.VisualStudio.Workload.Data

**Opis:** Łączenie, opracowywanie i testowanie rozwiązań danych przy użyciu programu SQL Server, usługa Azure Data Lake lub usługi Hadoop.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 15.0.26720.2 | Zalecane
Component.Microsoft.Web.LibraryManager | Library Manager | 15.8.27705.0 | Zalecane
Component.Redgate.SQLSearch.VSExtension | Redgate SQL Search | 3.1.7.2062 | Zalecane
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Zalecane
Microsoft.Component.Azure.DataLake.Tools | Usługa Azure Data Lake i Stream Analytics Tools | 15.9.28107.0 | Zalecane
Microsoft.Component.ClickOnce | Publikowania ClickOnce | 15.8.27825.0 | Zalecane
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 15.6.27406.0 | Zalecane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 15.0.26621.2 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 15.9.28125.51 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton | Podstawowe narzędzia usługi Azure Cloud Services | 15.9.28107.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do kompilacji usługi Azure Cloud Services | 15.7.27617.1 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Zalecane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 15.8.27906.1 | Zalecane
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia programistyczne kontenera — narzędzia Build Tools | 15.7.27617.1 | Zalecane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 15.9.28125.51 | Zalecane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Zalecane
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.SQL.CMDUtils | Narzędzia wiersza polecenia programu SQL Server | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 15.0.26621.2 | Zalecane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Zalecane
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Zalecane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 zestawu SDK | 15.0.28218.60 | Zalecane
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 15.9.28219.51 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.Component.FSharp.Desktop | F#Obsługa pulpitu języka | 15.8.27825.0 | Optional

## <a name="data-science-and-analytical-applications"></a>Aplikacje do analizy i przetwarzania danych

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Opis:** Języki i narzędzia do tworzenia aplikacji do analizy danych, w tym języka Python, R i F#.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Anaconda3.x64 | Anaconda3 64-bitowa (5.2.0) | 5.2.0 | Zalecane
Microsoft.Component.CookiecutterTools | Obsługa szablonów Cookiecutter | 15.0.26621.2 | Zalecane
Microsoft.Component.PythonTools | Obsługa języka Python | 15.0.26823.1 | Zalecane
Microsoft.Component.PythonTools.Web | Obsługa sieci web w języku Python | 15.9.28107.0 | Zalecane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Zalecane
Microsoft.VisualStudio.Component.FSharp.Desktop | F#Obsługa pulpitu języka | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 15.9.28125.51 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Zalecane
Microsoft.VisualStudio.Component.R.Open | Microsoft R Client (3.3.2) | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.RHost | Obsługa środowiska uruchomieniowego dla narzędzi programistycznych języka R | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.RTools | Obsługa języka R | 15.0.26919.1 | Zalecane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 zestawu SDK | 15.0.28218.60 | Zalecane
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 15.8.27825.0 | Zalecane
Component.Anaconda2.x64 | Anaconda2 64-bitowa (5.2.0) | 5.2.0 | Optional
Component.Anaconda2.x86 | Anaconda2 32-bitowa (5.2.0) | 5.2.0 | Optional
Component.Anaconda3.x86 | Anaconda3 32-bitowa (5.2.0) | 5.2.0 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Zestawu Windows Universal CRT SDK | 15.6.27309.0 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Narzędzia do programowania natywnego języka Python | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla technologii DirectX | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | Windows 8.1 narzędzi graficznych dla zestawu SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | VC ++ 2015.3 14.00 (wersja 140) z zestawu narzędzi dla pulpitu | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania dla języka C++ | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 w wersji 15.9 v14.16 najnowszych wersji 141 narzędzi | 15.9.28230.55 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Zestaw SDK systemu Windows 8.1 | 15.6.27406.0 | Optional

## <a name="net-desktop-development"></a>Programowanie aplikacji klasycznych dla platformy .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Opis:** Tworzenie WPF, Windows Forms i aplikacji konsolowych przy użyciu C#, Visual Basic i F#.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publikowania ClickOnce | 15.8.27825.0 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Narzędzia programistyczne dla platformy .NET | 15.7.27625.0 | Wymagane
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagane
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger Just In Time | 15.0.27005.2 | Zalecane
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 tools | 15.6.27406.0 | Zalecane
Component.Dotfuscator | Ochrona preEmptive — Dotfuscator | 15.0.26208.0 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 15.0.26720.2 | Optional
Component.Microsoft.Web.LibraryManager | Library Manager | 15.8.27705.0 | Optional
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Optional
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
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Narzędzia programistyczne programu .NET core 2.0 | 15.8.27729.1 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Optional
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 15.8.27906.1 | Optional
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia programistyczne kontenera — narzędzia Build Tools | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.FSharp | F#Obsługa języków | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.FSharp.Desktop | F#Obsługa pulpitu języka | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 15.9.28125.51 | Optional
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.SQL.CMDUtils | Narzędzia wiersza polecenia programu SQL Server | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Optional
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 zestawu SDK | 15.0.28218.60 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Optional
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 15.9.28219.51 | Optional
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 15.8.27825.0 | Optional

## <a name="game-development-with-unity"></a>Programowanie gier za pomocą aparatu Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Opis:** Twórz gry 2D i 3D za pomocą aparatu Unity, zaawansowane Międzyplatformowe środowisko programistyczne.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Narzędzia programistyczne programu .NET framework 3.5 | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.Unity | Narzędzia Visual Studio Tools for Unity | 15.7.27617.1 | Wymagane
Component.UnityEngine.x64 | Edytor 64-bitowych 2018.1 aparatu Unity | 15.8.27924.0 | Zalecane
Component.UnityEngine.x86 | Unity 5.6 32-bitowych edytora | 15.6.27406.0 | Zalecane

## <a name="linux-development-with-c"></a>Programowanie dla systemu Linux przy użyciu języka C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Opis:** Twórz i Debuguj aplikacje działające w środowisku systemu Linux.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.MDD.Linux | Visual C++ for Linux Development | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Wymagane
Component.Linux.CMake | Visual C++ tools for CMake and Linux | 15.8.27906.1 | Zalecane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 w wersji 15.9 v14.16 najnowszych wersji 141 narzędzi | 15.9.28230.55 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 15.8.27825.0 | Zalecane
Component.MDD.Linux.GCC.arm | Osadzonych i IoT rozwoju | 15.6.27309.0 | Optional

## <a name="desktop-development-with-c"></a>Programowanie aplikacji klasycznych w języku C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Opis:** Twórz aplikacje pulpitu Windows przy użyciu zestawu narzędzi Microsoft C++, ATL lub MFC.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aktualizacji pakietu redystrybucyjnego Visual C++ 2017 | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Visual C++ podstawowe funkcje języka | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debuger Just In Time | 15.0.27005.2 | Zalecane
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla technologii DirectX | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.Graphics.Win81 | Windows 8.1 narzędzi graficznych dla zestawu SDK | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Zalecane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL dla x86 i x64 | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Component.VC.CMake.Project | Visual C++ tools for CMake | 15.8.27906.1 | Zalecane
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania dla języka C++ | 15.0.26823.1 | Zalecane
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Rozszerzenia test Adapter for Boost.Test | 15.8.27906.1 | Zalecane
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Test Adapter for Google Test | 15.8.27906.1 | Zalecane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 w wersji 15.9 v14.16 najnowszych wersji 141 narzędzi | 15.9.28230.55 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 15.8.27825.0 | Zalecane
Component.Incredibuild | IncrediBuild — przyspieszanie kompilacji | 15.7.27617.1 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Zestawu Windows Universal CRT SDK | 15.6.27309.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | VC ++ 2015.3 14.00 (wersja 140) z zestawu narzędzi dla pulpitu | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC dla x86 i x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C + +/ interfejsu wiersza polecenia | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduły biblioteki standardowej (eksperymentalne) | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | System Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | System Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | System Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | System Windows 10 SDK (10.0.15063.0) for Desktop C++ [x86 i x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | System Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | System Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | System Windows 10 SDK (10.0.16299.0) for Desktop C++ [x86 i x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | System Windows 10 SDK (10.0.16299.0) for Desktop C++ [ARM i ARM64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | System Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | System Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Zestaw SDK systemu Windows 8.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.WinXP | Windows XP podporu androidu Pro C++ | 15.8.27924.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK i UCRT SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Windows XP podporu androidu Pro C++ | 15.8.27705.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | System Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | System Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | Optional

## <a name="game-development-with-c"></a>Programowanie gier w języku C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Opis:** Użyj pełnych możliwości języka C++, aby tworzyć profesjonalne gry obsługiwane przez program DirectX, Unreal i Cocos2d.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aktualizacji pakietu redystrybucyjnego Visual C++ 2017 | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 w wersji 15.9 v14.16 najnowszych wersji 141 narzędzi | 15.9.28230.55 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla technologii DirectX | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.Graphics.Win81 | Windows 8.1 narzędzi graficznych dla zestawu SDK | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania dla języka C++ | 15.0.26823.1 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Zalecane
Component.Android.NDK.R12B | Android NDK (r12b, wersja) | 12.1.10 | Optional
Component.Android.SDK23.Private | Instalacja zestawu android SDK (poziom interfejsu API 23) (lokalna instalacja na potrzeby opracowywania aplikacji mobilnych za pomocą języka JavaScript / C++) | 15.9.28016.0 | Optional
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Optional
Component.Cocos | Cocos | 15.0.26906.1 | Optional
Component.Incredibuild | IncrediBuild — przyspieszanie kompilacji | 15.7.27617.1 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Optional
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.6.27406.0 | Optional
Component.MDD.Android | Narzędzia programistyczne C++ Android | 15.0.26606.0 | Optional
Component.OpenJDK | Dystrybucja Microsoft OpenJDK | 15.9.28125.51 | Optional
Component.Unreal | Instalator aparatu unreal Engine | 15.8.27729.1 | Optional
Component.Unreal.Android | Visual Studio dla systemu Android Obsługa aparatu Unreal Engine | 15.0.27005.2 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Zestawu Windows Universal CRT SDK | 15.6.27309.0 | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.NuGet.BuildTools | Elementy docelowe i zadania kompilacji NuGet | 15.9.28016.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | System Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | System Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | System Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | System Windows 10 SDK (10.0.15063.0) for Desktop C++ [x86 i x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | System Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | System Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | System Windows 10 SDK (10.0.16299.0) for Desktop C++ [x86 i x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | System Windows 10 SDK (10.0.16299.0) for Desktop C++ [ARM i ARM64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | System Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | System Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Zestaw SDK systemu Windows 8.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK i UCRT SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | System Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | System Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | Optional

## <a name="mobile-development-with-c"></a>Tworzenie aplikacji mobilnych w języku C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Opis:** Twórz aplikacje Międzyplatformowe dla systemów iOS, Android lub Windows przy użyciu języka C++.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Android.SDK19.Private | Instalacja zestawu android SDK (poziom 19 interfejsu API) (lokalna instalacja na potrzeby opracowywania aplikacji mobilnych za pomocą języka JavaScript / C++) | 15.9.28107.0 | Wymagane
Component.Android.SDK21.Private | Instalacja zestawu android SDK (poziom 21 interfejsu API) (lokalna instalacja na potrzeby opracowywania aplikacji mobilnych za pomocą języka JavaScript / C++) | 15.9.28016.0 | Wymagane
Component.Android.SDK22.Private | Instalacja zestawu android SDK (poziom 22 interfejsu API) (lokalna instalacja na potrzeby opracowywania aplikacji mobilnych za pomocą języka JavaScript / C++) | 15.9.28016.0 | Wymagane
Component.Android.SDK23.Private | Instalacja zestawu android SDK (poziom interfejsu API 23) (lokalna instalacja na potrzeby opracowywania aplikacji mobilnych za pomocą języka JavaScript / C++) | 15.9.28016.0 | Wymagane
Component.Android.SDK25.Private | Instalacja zestawu android SDK (poziom interfejsu API 25) (lokalna instalacja na potrzeby opracowywania aplikacji mobilnych za pomocą języka JavaScript / C++) | 15.9.28016.0 | Wymagane
Component.OpenJDK | Dystrybucja Microsoft OpenJDK | 15.9.28125.51 | Wymagane
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Wymagane
Component.Android.NDK.R15C | Android NDK (R15C) | 15.2.1 | Zalecane
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Zalecane
Component.MDD.Android | Narzędzia programistyczne C++ Android | 15.0.26606.0 | Zalecane
Component.Android.NDK.R12B | Android NDK (r12b, wersja) | 12.1.10 | Optional
Component.Android.NDK.R12B_3264 | Android NDK (r12b, wersja) (32-bitowa) | 12.1.11 | Optional
Component.Android.NDK.R13B | Android NDK (r13b, wersja) | 13.1.7 | Optional
Component.Android.NDK.R13B_3264 | Android NDK (r13b, wersja) (32-bitowa) | 13.1.8 | Optional
Component.Android.NDK.R15C_3264 | Android NDK (R15C) (32-bitowa) | 15.2.1 | Optional
Component.Google.Android.Emulator.API23.Private | Emulator systemu Google Android (poziom interfejsu API 23) (instalacja lokalna) | 15.6.27413.0 | Optional
Component.HAXM.Private | Intel Hardware Accelerated Execution Menedżera (HAXM) (instalacja lokalna) | 15.6.27413.0 | Optional
Component.Incredibuild | IncrediBuild — przyspieszanie kompilacji | 15.7.27617.1 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Optional
Component.MDD.IOS | Narzędzia programistyczne dla systemu iOS C++ | 15.0.26621.2 | Optional

## <a name="net-core-cross-platform-development"></a>Programowanie dla wielu platform .NET core

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Opis:** Twórz aplikacje dla wielu platform przy użyciu platformy .NET Core, ASP.NET Core, HTML/JavaScript i kontenerów, w tym obsługę platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 15.0.26720.2 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 15.8.27705.0 | Wymagane
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Wymagane
Microsoft.Component.ClickOnce | Publikowania ClickOnce | 15.8.27825.0 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Wymagane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Wymagane
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Wymagane
Microsoft.NetCore.ComponentGroup.Web.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Wymagane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 15.8.27906.1 | Wymagane
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia programistyczne kontenera — narzędzia Build Tools | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.Component.FSharp | F#Obsługa języków | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#Obsługa języka dla projektów sieci web | 15.8.27705.0 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 15.9.28125.51 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.CMDUtils | Narzędzia wiersza polecenia programu SQL Server | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 15.0.26621.2 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Wymagane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 zestawu SDK | 15.0.28218.60 | Wymagane
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 15.9.28219.51 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 15.8.27825.0 | Wymagane
Component.Microsoft.VisualStudio.Web.AzureFunctions | Narzędzia usługi Microsoft Azure WebJobs | 15.7.27617.1 | Zalecane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 15.0.26621.2 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 15.9.28125.51 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Zalecane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Narzędzia usługi Microsoft Azure WebJobs | 15.7.27617.1 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Narzędzia do tworzenia aplikacji internetowych w chmurze | 15.8.27729.1 | Zalecane
Microsoft.Net.Core.Component.SDK | Narzędzia programistyczne programu .NET core 2.0 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | .NET core 1.0 – 1.1 narzędzia programistyczne | 15.6.27406.0 | Optional
Microsoft.NetCore.1x.ComponentGroup.Web | .NET core 1.0 – 1.1 narzędzi programistycznych dla sieci Web | 15.6.27406.0 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Narzędzia programistyczne programu .NET core 2.0 | 15.8.27729.1 | Optional
Microsoft.NetCore.ComponentGroup.Web | Narzędzia programistyczne programu .NET core 2.0 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Obsługa usług IIS w czasie opracowywania | 15.9.28219.51 | Optional

## <a name="mobile-development-with-net"></a>Tworzenie aplikacji mobilnych przy użyciu platformy .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Opis:** Twórz aplikacje Międzyplatformowe dla systemów iOS, Android i Windows za pomocą platformy Xamarin.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Xamarin | Xamarin | 15.8.27906.1 | Wymagane
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 15.6.27323.2 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Wymagane
Microsoft.Net.Core.Component.SDK | Narzędzia programistyczne programu .NET core 2.0 | 15.6.27406.0 | Wymagane
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Narzędzia programistyczne programu .NET core 2.0 | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.FSharp | F#Obsługa języków | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.Merq | Wspólne narzędzia wewnętrzne platformy Xamarin | 15.8.27924.0 | Wymagane
Microsoft.VisualStudio.Component.MonoDebugger | Debuger środowiska mono | 15.0.26720.2 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Aparat szablonów ASP.NET | 15.8.27729.1 | Wymagane
Component.Android.SDK27 | Instalacja zestawu android SDK (poziom 27 interfejsu API) | 15.9.28016.0 | Zalecane
Component.Google.Android.Emulator.API27 | Emulator systemu Google Android (poziom 27 interfejsu API) | 15.9.28016.0 | Zalecane
Component.HAXM | Intel Hardware Accelerated Execution Menedżera (HAXM) (Instalacja globalna) | 15.6.27413.0 | Zalecane
Component.OpenJDK | Dystrybucja Microsoft OpenJDK | 15.9.28125.51 | Zalecane
Component.Xamarin.Inspector | Xamarin Workbooks | 15.0.26606.0 | Optional
Microsoft.Component.ClickOnce | Publikowania ClickOnce | 15.8.27825.0 | Optional
Microsoft.Component.NetFX.Native | Architektura .NET Native | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.Graphics | Obrazów i modeli 3W edytorów | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Narzędzia platformy Windows uniwersalnej dla platformy Xamarin | 15.7.27617.1 | Optional

## <a name="aspnet-and-web-development"></a>ASP.NET i tworzenie aplikacji internetowych

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Opis:** Twórz aplikacje sieci web za pomocą programu ASP.NET, ASP.NET Core, HTML/JavaScript i kontenerów, w tym obsługę platformy Docker.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 15.0.26720.2 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 15.8.27705.0 | Wymagane
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Wymagane
Microsoft.Component.ClickOnce | Publikowania ClickOnce | 15.8.27825.0 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Wymagane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Wymagane
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Wymagane
Microsoft.NetCore.ComponentGroup.Web.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Wymagane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 15.8.27906.1 | Wymagane
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia programistyczne kontenera — narzędzia Build Tools | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.Component.FSharp | F#Obsługa języków | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#Obsługa języka dla projektów sieci web | 15.8.27705.0 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 15.9.28125.51 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.CMDUtils | Narzędzia wiersza polecenia programu SQL Server | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 15.0.26621.2 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Wymagane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 zestawu SDK | 15.0.28218.60 | Wymagane
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 15.9.28219.51 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 15.8.27825.0 | Wymagane
Component.Microsoft.VisualStudio.Web.AzureFunctions | Narzędzia usługi Microsoft Azure WebJobs | 15.7.27617.1 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane funkcje platformy ASP.NET | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 15.8.27825.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 15.0.26621.2 | Zalecane
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 15.9.28125.51 | Zalecane
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.9.28230.55 | Zalecane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 tools | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Narzędzia usługi Microsoft Azure WebJobs | 15.7.27617.1 | Zalecane
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Narzędzia do tworzenia aplikacji internetowych w chmurze | 15.8.27729.1 | Zalecane
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
Microsoft.NetCore.1x.ComponentGroup.Web | .NET core 1.0 – 1.1 narzędzi programistycznych dla sieci Web | 15.6.27406.0 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Narzędzia programistyczne programu .NET core 2.0 | 15.8.27729.1 | Optional
Microsoft.NetCore.ComponentGroup.Web | Narzędzia programistyczne programu .NET core 2.0 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Obsługa usług IIS w czasie opracowywania | 15.9.28219.51 | Optional
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 15.6.27406.0 | Optional

## <a name="nodejs-development"></a>Tworzenia aplikacji node.js

**ID:** Microsoft.VisualStudio.Workload.Node

**Opis:** Tworzenie skalowalnych aplikacji sieciowych przy użyciu platformy Node.js i asynchronicznego oparte na zdarzeniach środowiska uruchomieniowego JavaScript.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 15.9.28125.51 | Wymagane
Microsoft.VisualStudio.Component.Node.Build | Obsługa MSBuild dla środowiska node.js | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.Node.Tools | Obsługa rozwoju oprogramowania node.js | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.TestTools.Core | Podstawowe funkcje narzędzi do testowania | 15.7.27520.0 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 zestawu SDK | 15.0.28218.60 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 w wersji 15.9 v14.16 najnowszych wersji 141 narzędzi | 15.9.28230.55 | Optional

## <a name="officesharepoint-development"></a>Programowanie Office/SharePoint

**ID:** Microsoft.VisualStudio.Workload.Office

**Opis:** Tworzenie dodatków narzędzi VSTO za pomocą pakietu Office i programu SharePoint dodatków oraz rozwiązań programu SharePoint C#, VB i JavaScript.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 15.0.26720.2 | Wymagane
Component.Microsoft.Web.LibraryManager | Library Manager | 15.8.27705.0 | Wymagane
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Wymagane
Microsoft.Component.ClickOnce | Publikowania ClickOnce | 15.8.27825.0 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Wymagane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Wymagane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Wymagane
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 15.8.27906.1 | Wymagane
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia programistyczne kontenera — narzędzia Build Tools | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 15.9.28125.51 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Narzędzia programistyczne dla platformy .NET | 15.7.27625.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 15.8.27924.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.CMDUtils | Narzędzia wiersza polecenia programu SQL Server | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 15.0.26621.2 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Wymagane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 zestawu SDK | 15.0.28218.60 | Wymagane
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.8.27924.0 | Wymagane
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 15.9.28219.51 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools dla pakietu Office (VSTO) | 15.7.27625.0 | Zalecane
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

## <a name="python-development"></a>Programowanie w języku Python

**ID:** Microsoft.VisualStudio.Workload.Python

**Opis:** Edytowanie, debugowanie, opracowywanie interakcyjne oraz kontrola źródła dla języka Python.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.PythonTools | Obsługa języka Python | 15.0.26823.1 | Wymagane
Component.CPython3.x64 | Python 3 64-bitowy (3.6.6) | 3.6.6 | Zalecane
Microsoft.Component.CookiecutterTools | Obsługa szablonów Cookiecutter | 15.0.26621.2 | Zalecane
Microsoft.Component.PythonTools.Web | Obsługa sieci web w języku Python | 15.9.28107.0 | Zalecane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Zalecane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 15.9.28125.51 | Zalecane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 zestawu SDK | 15.0.28218.60 | Zalecane
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 15.8.27825.0 | Zalecane
Component.Anaconda2.x64 | Anaconda2 64-bitowa (5.2.0) | 5.2.0 | Optional
Component.Anaconda2.x86 | Anaconda2 32-bitowa (5.2.0) | 5.2.0 | Optional
Component.Anaconda3.x64 | Anaconda3 64-bitowa (5.2.0) | 5.2.0 | Optional
Component.Anaconda3.x86 | Anaconda3 32-bitowa (5.2.0) | 5.2.0 | Optional
Component.CPython2.x64 | Python 2 64-bitowa (2.7.14) | 2.7.14 | Optional
Component.CPython2.x86 | Python 2 32-bitowa (2.7.14) | 2.7.14 | Optional
Component.CPython3.x86 | Python 3 32-bitowy (3.6.6) | 3.6.6 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Usługi języka razor | 15.0.26720.2 | Optional
Component.Microsoft.Web.LibraryManager | Library Manager | 15.8.27705.0 | Optional
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Optional
Microsoft.Component.ClickOnce | Publikowania ClickOnce | 15.8.27825.0 | Optional
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Optional
Microsoft.Component.NetFX.Native | Architektura .NET Native | 15.0.26208.0 | Optional
Microsoft.Component.PythonTools.UWP | Obsługa IoT w języku Python | 15.0.26606.0 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Zestawu Windows Universal CRT SDK | 15.6.27309.0 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Narzędzia do programowania natywnego języka Python | 15.8.27729.1 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Optional
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulator obliczeń platformy Azure | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulator usługi Azure Storage | 15.9.28125.51 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton | Podstawowe narzędzia usługi Azure Cloud Services | 15.9.28107.0 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Narzędzia do kompilacji usługi Azure Cloud Services | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Projektant klas | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.DockerTools | Narzędzia programistyczne dla kontenerów | 15.8.27906.1 | Optional
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia programistyczne kontenera — narzędzia Build Tools | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.Graphics | Obrazów i modeli 3W edytorów | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla technologii DirectX | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | Windows 8.1 narzędzi graficznych dla zestawu SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Podstawowe składniki dla obciążenia zarządzanego pulpitu | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Optional
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.SQL.CMDUtils | Narzędzia wiersza polecenia programu SQL Server | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | VC ++ 2015.3 14.00 (wersja 140) z zestawu narzędzi dla pulpitu | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Narzędzia profilowania dla języka C++ | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 w wersji 15.9 v14.16 najnowszych wersji 141 narzędzi | 15.9.28230.55 | Optional
Microsoft.VisualStudio.Component.Web | Narzędzia programistyczne programu ASP.NET i sieci web | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | System Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Zestaw SDK systemu Windows 8.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Web | Wymagania wstępne dotyczące narzędzi do programowania dla platformy ASP.NET i sieci web | 15.9.28219.51 | Optional

## <a name="universal-windows-platform-development"></a>Opracowywanie zawartości dla platformy Windows Universal

**ID:** Microsoft.VisualStudio.Workload.Universal

**Opis:** Tworzenie aplikacji uniwersalnych platformy Windows za pomocą C#, VB, JavaScript lub opcjonalnie C++.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Wymagane
Microsoft.Component.ClickOnce | Publikowania ClickOnce | 15.8.27825.0 | Wymagane
Microsoft.Component.NetFX.Native | Architektura .NET Native | 15.0.26208.0 | Wymagane
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Core.Component.SDK.2.1 | Narzędzia programistyczne programu .NET core 2.1 | 15.8.27924.0 | Wymagane
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.Graphics | Obrazów i modeli 3W edytorów | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 15.9.28125.51 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 zestawu SDK | 15.0.28218.60 | Wymagane
Microsoft.VisualStudio.Component.UWP.Support | Narzędzia platformy Windows uniwersalnej | 15.9.28119.51 | Wymagane
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Wymagane
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Narzędzia platformy Windows uniwersalnej dla Cordova | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | Architektura .NET native i .NET Standard | 15.8.27906.1 | Wymagane
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Narzędzia platformy Windows uniwersalnej dla platformy Xamarin | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 15.8.27825.0 | Wymagane
Microsoft.Component.VC.Runtime.OSSupport | Środowisko uruchomieniowe Visual C++ dla platformy uniwersalnej systemu Windows | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Debuger grafiki i profiler procesora GPU dla technologii DirectX | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | Windows 8.1 narzędzi graficznych dla zestawu SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Emulator Windows 10 Mobile (Fall Creators Update) | 15.0.27406.0 | Optional
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Narzędzia platformy Windows uniwersalnej C++ dla architektury ARM64 | 15.0.28125.51 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | Kompilatory języka Visual C++ i bibliotek dla ARM | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Kompilatory języka Visual C++ i bibliotek dla architektury ARM64 | 15.9.28230.55 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 w wersji 15.9 v14.16 najnowszych wersji 141 narzędzi | 15.9.28230.55 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | System Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | System Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | System Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | System Windows 10 SDK (10.0.15063.0) for Desktop C++ [x86 i x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | System Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | System Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | System Windows 10 SDK (10.0.16299.0) for Desktop C++ [x86 i x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | System Windows 10 SDK (10.0.16299.0) for Desktop C++ [ARM i ARM64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | System Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | System Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | System Windows 10 SDK (10.0.17763.0) | 15.9.28218.60 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Połączenie urządzenia USB | 15.7.27625.0 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | C++ Universal Windows Platform tools | 15.9.28107.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | System Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | System Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | Optional

## <a name="visual-studio-extension-development"></a>Programowanie rozszerzeń programu Visual Studio

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Opis:** Twórz dodatki i rozszerzenia dla programu Visual Studio, w tym nowe polecenia, analizatory kodu i okna narzędzi.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publikowania ClickOnce | 15.8.27825.0 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagane
Microsoft.VisualStudio.Component.PortableLibrary | .NET portable Library targeting pack | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Visual Studio rozszerzenia wymagania wstępne dotyczące programowania | 15.7.27625.0 | Wymagane
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 15.8.27729.1 | Zalecane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 15.0.26208.0 | Zalecane
Component.Dotfuscator | Ochrona preEmptive — Dotfuscator | 15.0.26208.0 | Optional
Microsoft.Component.CodeAnalysis.SDK | Zestaw SDK platformy kompilatora .NET | 15.0.27729.1 | Optional
Microsoft.Component.VC.Runtime.OSSupport | Środowisko uruchomieniowe Visual C++ dla platformy uniwersalnej systemu Windows | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Projektant klas | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DslTools | Modeling SDK | 15.0.27005.2 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL dla x86 i x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC dla x86 i x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Podstawowe funkcje programu Visual Studio C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 w wersji 15.9 v14.16 najnowszych wersji 141 narzędzi | 15.9.28230.55 | Optional

## <a name="mobile-development-with-javascript"></a>Tworzenie aplikacji mobilnych za pomocą języka JavaScript

**ID:** Microsoft.VisualStudio.Workload.WebCrossPlat

**Opis:** Twórz aplikacje systemu Android, iOS i platformy uniwersalnej systemu Windows przy użyciu narzędzi Tools for Apache Cordova.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Component.CordovaToolset.6.3.1 | Zestaw narzędzi Cordova 6.3.1 | 15.7.27625.0 | Wymagane
Component.WebSocket | WebSocket4Net | 15.0.26606.0 | Wymagane
Microsoft.VisualStudio.Component.Cordova | Tworzenie aplikacji mobilnych z podstawowymi funkcjami JavaScript | 15.0.26606.0 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostyka JavaScript | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.ProjectSystem | I narzędzia współdzielone JavaScript | 15.0.26606.0 | Wymagane
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Obsługa języków JavaScript i TypeScript | 15.9.28125.51 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.2.3 | TypeScript 2.3 zestawu SDK | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 zestawu SDK | 15.0.28218.60 | Wymagane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i tworzenie aplikacji internetowych | 15.8.27825.0 | Wymagane
Component.Android.SDK23.Private | Instalacja zestawu android SDK (poziom interfejsu API 23) (lokalna instalacja na potrzeby opracowywania aplikacji mobilnych za pomocą języka JavaScript / C++) | 15.9.28016.0 | Optional
Component.Google.Android.Emulator.API23.Private | Emulator systemu Google Android (poziom interfejsu API 23) (instalacja lokalna) | 15.6.27413.0 | Optional
Component.HAXM.Private | Intel Hardware Accelerated Execution Menedżera (HAXM) (instalacja lokalna) | 15.6.27413.0 | Optional
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.6.27406.0 | Optional
Component.OpenJDK | Dystrybucja Microsoft OpenJDK | 15.9.28125.51 | Optional
Microsoft.Component.ClickOnce | Publikowania ClickOnce | 15.8.27825.0 | Optional
Microsoft.Component.NetFX.Native | Architektura .NET Native | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Narzędzia Developer Analytics tools | 15.8.27825.0 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | Narzędzia profilowania dla programu .NET | 15.8.27729.1 | Optional
Microsoft.VisualStudio.Component.Git | Git dla systemu Windows | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Graphics | Obrazów i modeli 3W edytorów | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Phone.Emulator.15254 | Emulator Windows 10 Mobile (Fall Creators Update) | 15.0.27406.0 | Optional
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Narzędzia platformy Windows uniwersalnej dla Cordova | 15.7.27617.1 | Optional

## <a name="unaffiliated-components"></a>Składniki nie podlega

Są to składniki, które nie są uwzględniane przy użyciu dowolnego obciążenia, ale można wybrać jako poszczególnych składników.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
Component.Android.Emulator | Emulator programu Visual Studio dla systemu Android | 15.6.27413.0
Component.Android.NDK.R11C | Android NDK (r11c, wersja) | 11.3.14
Component.Android.NDK.R11C_3264 | Android NDK (r11c, wersja) (32-bitowa) | 11.3.16
Component.Android.SDK23 | Instalacja zestawu android SDK (poziom interfejsu API 23) (Instalacja globalna) | 15.9.28107.0
Component.Android.SDK25 | Instalacja zestawu android SDK (poziom interfejsu API 25) | 15.9.28107.0
Component.GitHub.VisualStudio | Rozszerzenie GitHub dla programu Visual Studio | 2.5.2.2500
Component.Google.Android.Emulator.API23.V2 | Emulator systemu Google Android (poziom interfejsu API 23) (Instalacja globalna) | 15.6.27413.0
Component.Google.Android.Emulator.API25 | Emulator systemu Google Android (poziom interfejsu API 25) | 15.7.27604.0
Microsoft.Component.Blend.SDK.WPF | Program Blend for Visual Studio SDK dla platformy .NET | 15.6.27406.0
Microsoft.Component.HelpViewer | Podgląd pomocy | 15.6.27323.2
Microsoft.VisualStudio.Component.DependencyValidation.Community | Weryfikacja zależności | 15.0.26208.0
Microsoft.VisualStudio.Component.GraphDocument | Edytor DGML | 15.0.27005.2
Microsoft.VisualStudio.Component.LinqToSql | Narzędzi LINQ to SQL | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator | Emulator Windows 10 Mobile (Anniversary Edition) | 15.6.27406.0
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Emulator Windows 10 Mobile (Aktualizacja dla twórców) | 15.6.27406.0
Microsoft.VisualStudio.Component.Runtime.Node.x86.6.4.0 | Środowisko uruchomieniowe dla składników opartych na środowisku Node.js v6.4.0 (x86) | 15.7.27617.1
Microsoft.VisualStudio.Component.Runtime.Node.x86.7.4.0 | Środowisko uruchomieniowe dla składników opartych na środowisku Node.js v7.4.0 (x86) | 15.7.27617.1
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 zestawu SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.8.27729.1
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

* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
* [Podręcznik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
