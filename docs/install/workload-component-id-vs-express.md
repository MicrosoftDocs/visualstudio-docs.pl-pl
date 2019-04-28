---
title: Visual Studio Express pulpitu identyfikatory obciążeń i składników
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
ms.assetid: a3c0cc76-e3ce-435c-a1af-a6318b5a4dbe
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
ms.openlocfilehash: 2447f0eab7ee3931df70f503519f3f110f4ba272
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62818963"
---
# <a name="visual-studio-desktop-express-component-directory"></a>Visual Studio Express pulpitu składników katalogu

Tabele na tej stronie listy identyfikatorów, w której można zainstalować program Visual Studio przy użyciu wiersza polecenia lub można określić jako zależności w manifestu VSIX. Należy pamiętać, że dodamy dodatkowe składniki, jak wydaniu aktualizacji do programu Visual Studio.

Ponadto należy pamiętać, że informacje o stronie:

* Każde obciążenie ma osobny rozdział, następuje identyfikator obciążenia i tabeli składników, które są dostępne dla obciążenia.
* Domyślnie **wymagane** składniki zostaną zainstalowane po zainstalowaniu obciążenia.
* Jeśli chcesz, możesz także zainstalować **zalecane** i **opcjonalnie** składników.
* Dodaliśmy również sekcję, która zawiera listę dodatkowych składników, które nie są powiązane z dowolnych obciążeń.

Po ustawieniu współzależności w manifeście VSIX tylko należy określić identyfikatory składników. Użyj tabel na tej stronie, aby określić nasze zależności minimalnej składnika. W niektórych scenariuszach to oznaczać, że należy określić tylko jeden składnik z obciążenia. W innych przypadkach może oznaczać, możesz określić wiele składników z pojedynczego obciążenia lub wielu składników z wielu obciążeń. Aby uzyskać więcej informacji, zobacz [jak: Migrowanie projektów rozszerzalności do programu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) strony.

Aby uzyskać więcej informacji na temat używania tych identyfikatorów, zobacz [Użyj parametry wiersza polecenia, aby zainstalować program Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) strony. I dla listy, obciążenie i identyfikatorów składników dla innych produktów, zobacz [Visual Studio 2017 obciążenia i identyfikatory składnika](workload-and-component-ids.md) strony.

## <a name="express-for-windows-desktop"></a>Express for Windows Desktop

**ID:** Microsoft.VisualStudio.Workload.WDExpress

**Opis:** Twórz aplikacje natywne i zarządzane, takie jak WPF, WinForms i Win32 edytowania kodu uwzględniającej składnię, kontroli kodu źródłowego i zarządzania elementami roboczymi. Obejmuje obsługę języka C#, Visual Basic i Visual C++.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publikowania ClickOnce | 15.8.27825.0 | Wymagane
Microsoft.Component.HelpViewer | Podgląd pomocy | 15.6.27323.2 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Component.VC.Runtime.OSSupport | Środowisko uruchomieniowe Visual C++ dla platformy uniwersalnej systemu Windows | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Wymagane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Wymagane
Microsoft.VisualStudio.Component.CoreEditor | Edytor rdzeni programu Visual Studio | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 tools | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagane
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
Microsoft.VisualStudio.Component.VC.CLI.Support | C + +/ interfejsu wiersza polecenia | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.VC.Tools.ARM | Kompilatory języka Visual C++ i bibliotek dla ARM | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Kompilatory języka Visual C++ i bibliotek dla architektury ARM64 | 15.9.28230.55 | Wymagane
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK.14393 | System Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Wymagane

## <a name="unaffiliated-components"></a>Składniki nie podlega

Są to składniki, które nie są uwzględniane przy użyciu dowolnego obciążenia, ale można wybrać jako poszczególnych składników.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
n/d | n/d | n/d

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
* [Podręcznik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
