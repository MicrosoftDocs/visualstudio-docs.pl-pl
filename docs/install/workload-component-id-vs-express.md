---
title: Obciążenie programu Visual Studio Desktop Express i identyfikatory składników
titleSuffix: ''
description: Używanie obciążeń i identyfikatorów składników do instalowania programu Visual Studio przy użyciu wiersza polecenia lub do określenia jako zależność w manifeście VSIX
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
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
ms.openlocfilehash: 21735c82a318623758f1980a1865a543adde121e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881805"
---
# <a name="visual-studio-desktop-express-component-directory"></a>Katalog składników programu Visual Studio Desktop Express

Tabele na tej stronie wyświetlają identyfikatory, których można użyć do zainstalowania programu Visual Studio przy użyciu wiersza polecenia lub można określić jako zależność w manifeście VSIX. Należy pamiętać, że po udostępnieniu aktualizacji dla programu Visual Studio zostaną dodane dodatkowe składniki.

Należy również zwrócić uwagę na następujące kwestie dotyczące strony:

* Każde obciążenie ma własną sekcję, a następnie identyfikator obciążenia oraz tabelę składników, które są dostępne dla obciążenia.
* Domyślnie **wymagane** składniki zostaną zainstalowane po zainstalowaniu obciążenia.
* Jeśli wybierzesz opcję, możesz również zainstalować **zalecane** i **opcjonalne** składniki.
* Dodaliśmy również sekcję, która zawiera dodatkowe składniki, które nie są powiązane z żadnym obciążeniem.

Podczas ustawiania zależności w manifeście VSIX należy określić tylko identyfikatory składników. Użyj tabel na tej stronie, aby określić nasze minimalne zależności składników. W niektórych scenariuszach może to oznaczać, że należy określić tylko jeden składnik z obciążenia. W innych scenariuszach może oznaczać, że należy określić wiele składników z pojedynczego obciążenia lub wielu składników z wielu obciążeń. Aby uzyskać więcej informacji, zobacz stronę [How to: migruje Projekty rozszerzalności do programu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) .

Aby uzyskać więcej informacji na temat korzystania z tych identyfikatorów, zobacz temat [używanie Command-Line parametrów w celu zainstalowania strony programu Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) . Aby uzyskać listę identyfikatorów obciążeń i składników dla innych produktów, zobacz stronę [obciążenia i identyfikatory składników programu Visual Studio 2017](workload-and-component-ids.md) .

## <a name="express-for-windows-desktop"></a>Express for Windows Desktop

**Identyfikator:** Microsoft. VisualStudio. obciążeni. WDExpress

**Opis:** Twórz aplikacje natywne i zarządzane, takie jak WPF, WinForms i Win32, przy użyciu edycji kodu z rozpoznawaniem składni, kontroli kodu źródłowego i zarządzania elementami roboczymi. Obejmuje obsługę języka C#, Visual Basic i Visual C++.

### <a name="components-included-by-this-workload"></a>Składniki zawarte w tym obciążeniu

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft. Component. ClickOnce | Publikowanie ClickOnce | 15.8.27825.0 | Wymagane
Microsoft. Component. HelpViewer | Podgląd pomocy | 15.6.27323.2 | Wymagane
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft. Component. VC. Runtime. OSSupport | Visual C++ środowisko uruchomieniowe dla platformy UWP | 15.6.27406.0 | Wymagane
Microsoft.Net. Component. 4.5.1. TargetingPack | Pakiet .NET Framework 4.5.1 | 15.6.27406.0 | Wymagane
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 — pakiet docelowy | 15.6.27406.0 | Wymagane
Microsoft.Net. Component. 4.5. TargetingPack | Pakiet docelowy .NET Framework 4,5 | 15.6.27406.0 | Wymagane
Microsoft. NET. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Wymagane
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 | 15.6.27406.0 | Wymagane
Microsoft.Net. Component. 4.6. TargetingPack | Pakiet docelowy .NET Framework 4,6 | 15.6.27406.0 | Wymagane
Microsoft.Net. Component. 4. TargetingPack | Pakiet docelowy .NET Framework 4 | 15.6.27406.0 | Wymagane
Microsoft.Net. Component. DevelopmentPrerequisites | Narzędzia programistyczne .NET Framework 4.6.1 | 15.8.27825.0 | Wymagane
Microsoft.Net. Component. TargetingPacks. Common | .NET Framework 4 — narzędzia deweloperskie 4,6 | 15.6.27406.0 | Wymagane
Microsoft. VisualStudio. Component. Common. Azure. Tools | Narzędzia do łączności i publikowania | 15.9.28107.0 | Wymagane
Microsoft. VisualStudio. Component. CoreEditor | Visual Studio Core Editor | 15.8.27729.1 | Wymagane
Microsoft. VisualStudio. Component. EntityFramework | Narzędzia Entity Framework 6 | 15.6.27406.0 | Wymagane
Microsoft. VisualStudio. Component. NuGet | Menedżer pakietów NuGet | 15.9.28016.0 | Wymagane
Microsoft. VisualStudio. Component. Roslyn. kompilator | Kompilatory języka C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagane
Microsoft. VisualStudio. Component. SQL. ADAL | Środowisko uruchomieniowe ADAL SQL | 15.6.27406.0 | Wymagane
Microsoft. VisualStudio. Component. SQL. CLR | Typy danych CLR dla SQL Server | 15.0.26208.0 | Wymagane
Microsoft. VisualStudio. Component. SQL. CMDUtils | Narzędzia wiersza polecenia SQL Server | 15.0.26208.0 | Wymagane
Microsoft. VisualStudio. Component. SQL. DataSources | Źródła danych na potrzeby obsługi SQL Server | 15.0.26621.2 | Wymagane
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Wymagane
Microsoft. VisualStudio. Component. SQL. NCLI | SQL Server Native Client | 15.0.26208.0 | Wymagane
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Data Tools | 15.9.28107.0 | Wymagane
Microsoft. VisualStudio. Component. static. Analysis. Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft. VisualStudio. Component. TextTemplating | Transformacja szablonu tekstu | 15.0.26208.0 | Wymagane
Microsoft. VisualStudio. Component. VC. CLI. Support | Obsługa języka C++/CLI | 15.6.27309.0 | Wymagane
Microsoft. VisualStudio. Component. VC. Tools. ARM | Visual C++ kompilatory i biblioteki dla usługi ARM | 15.8.27825.0 | Wymagane
Microsoft. VisualStudio. Component. VC. Tools. ARM64 | Visual C++ kompilatory i biblioteki dla ARM64 | 15.9.28230.55 | Wymagane
Microsoft. VisualStudio. Component. VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagane
Microsoft. VisualStudio. Component. Windows10SDK. 14393 | Zestaw SDK systemu Windows 10 (10.0.14393.0) | 15.6.27406.0 | Wymagane
Microsoft. VisualStudio. Component. Windows10SDK. 17134 | Zestaw SDK systemu Windows 10 (10.0.17134.0) | 15.8.27924.0 | Wymagane

## <a name="unaffiliated-components"></a>Niestowarzyszone składniki

Są to składniki, które nie są uwzględnione w obciążeniu, ale mogą być wybierane jako poszczególne składniki.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
nie dotyczy | nie dotyczy | nie dotyczy

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
