---
title: Identyfikatory obciążenia i składników programu Visual Studio Desktop Express
titleSuffix: ''
description: Używanie identyfikatorów obciążenia i składników do instalowania programu Visual Studio przy użyciu wiersza polecenia lub określania zależności w manifeście vsix
keywords: ''
author: ornellaalt
ms.author: ornella
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
open_to_public_contributors: false
ms.openlocfilehash: 1e24f90f24921bee9a6132ccc047c0b9da37fc90
ms.sourcegitcommit: 22deb247ad951e4971f27fdab413b158415d0584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81276295"
---
# <a name="visual-studio-desktop-express-component-directory"></a>Katalog składników programu Visual Studio Desktop Express

Tabele na tej stronie listy identyfikatorów, których można użyć do zainstalowania programu Visual Studio przy użyciu wiersza polecenia lub które można określić jako zależność w manifeście VSIX. Należy zauważyć, że dodamy dodatkowe składniki podczas wydawania aktualizacji programu Visual Studio.

Zwróć również uwagę na następujące informacje na temat strony:

* Każde obciążenie ma własną sekcję, a następnie identyfikator obciążenia i tabelę składników, które są dostępne dla obciążenia.
* Domyślnie **wymagane** składniki zostaną zainstalowane podczas instalowania obciążenia.
* W tym przypadku można również zainstalować składniki **Zalecane** i **Opcjonalne.**
* Dodaliśmy również sekcję zawierającą listę dodatkowych składników, które nie są powiązane z żadnym obciążeniem.

Po ustawieniu zależności w manifeście VSIX należy określić tylko identyfikatory składników. Użyj tabel na tej stronie, aby określić nasze minimalne zależności składników. W niektórych scenariuszach może to oznaczać, że można określić tylko jeden składnik z obciążenia. W innych scenariuszach może to oznaczać, że można określić wiele składników z jednego obciążenia lub wiele składników z wielu obciążeń. Aby uzyskać więcej informacji, zobacz [how to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) page.

Aby uzyskać więcej informacji na temat używania tych identyfikatorów, zobacz Instalowanie strony [programu Visual Studio 2017 za pomocą parametrów wiersza polecenia.](use-command-line-parameters-to-install-visual-studio.md) Aby uzyskać listę identyfikatorów obciążenia i składników dla innych produktów, zobacz stronę [Obciążenia i identyfikatory składników programu Visual Studio 2017.](workload-and-component-ids.md)

## <a name="express-for-windows-desktop"></a>Express dla pulpitu systemu Windows

**Identyfikator:** Microsoft.VisualStudio.Workload.WDExpress

**Opis:** Tworzenie aplikacji natywnych i zarządzanych, takich jak WPF, WinForms i Win32 z edycji kodu obsługujących składnię, kontroli kodu źródłowego i zarządzania elementami pracy. Zawiera obsługę języka C#, Visual Basic i Visual C++.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Składnik Microsoft.ClickOnce | Kliknij publikowanieonce | 15.8.27825.0 | Wymagany
Microsoft.Component.HelpViewer | Podgląd pomocy | 15.6.27323.2 | Wymagany
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagany
Microsoft.Component.VC.Runtime.OSSport | Środowisko wykonawcze Visual C++ dla platformy uniwersalnej systemu i platformy uniwersalnej | 15.6.27406.0 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.5.1.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.1 | 15.6.27406.0 | Wymagany
Pakiet targetingpakingu microsoft.net.component.4.5.2.TargetingPack | Pakiet targetowania programu .NET Framework 4.5.2 | 15.6.27406.0 | Wymagany
Pakiet targeting firmy Microsoft.Net.Component.4.5.TargetingPack | Pakiet targetowania programu .NET Framework 4.5 | 15.6.27406.0 | Wymagany
Składnik Microsoft.Net.4.6.1.SDK | Plik SDK programu .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Pakiet targetingu firmy Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet kierowania .NET Framework 4.6.1 | 15.6.27406.0 | Wymagany
Pakiet targeting firmy Microsoft.Net.Component.4.6.TargetingPack | Pakiet targetowania programu .NET Framework 4.6 | 15.6.27406.0 | Wymagany
Pakiet docelowy firmy Microsoft.Net.Component.4.TargetingPack | Pakiet targetowania programu .NET Framework 4 | 15.6.27406.0 | Wymagany
Microsoft.Net.ComponentGroup.DevelopmentZamagasy wstępne | Narzędzia programistyczne .NET Framework 4.6.1 | 15.8.27825.0 | Wymagany
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 narzędzia programistyczne | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 15.9.28107.0 | Wymagany
Microsoft.VisualStudio.Component.CoreEditor | Edytor podstawowy programu Visual Studio | 15.8.27729.1 | Wymagany
Microsoft.VisualStudio.Component.EntityFramework | Narzędzia entity Framework 6 | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagany
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
Pomoc techniczna aplikacji Microsoft.VisualStudio.Component.VC.CLI.Support | Obsługa języka C++/CLI | 15.6.27309.0 | Wymagany
Microsoft.VisualStudio.Component.VC.Tools.ARM | Kompilatory i biblioteki visual C++ dla ARM | 15.8.27825.0 | Wymagany
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Kompilatory i biblioteki visual c++ dla ARM64 | 15.9.28230.55 | Wymagany
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Wymagany

## <a name="unaffiliated-components"></a>Składniki niepowiązane

Są to składniki, które nie są dołączone do żadnego obciążenia, ale mogą być wybrane jako pojedynczy składnik.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
Nie dotyczy | Nie dotyczy | Nie dotyczy

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
