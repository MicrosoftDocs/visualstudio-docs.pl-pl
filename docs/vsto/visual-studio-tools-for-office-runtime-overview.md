---
title: Visual Studio Tools dla środowiska uruchomieniowego pakietu Office — omówienie
description: Narzędzia Visual Studio 2010 Tools for Office Runtime muszą być zainstalowane na komputerach użytkowników końcowych w celu uruchamiania rozwiązań utworzonych przy użyciu narzędzi deweloperskich Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio], about Office runtime
- VSTOLoader.dll
- runtime loader [Office development in Visual Studio]
- Office runtime [Office development in Visual Studio], assemblies
- Office runtime [Office development in Visual Studio]
- runtime [Office development in Visual Studio], assemblies
- vstoee.dll
- Visual Studio Tools for Office runtime
- Office solutions [Office development in Visual Studio], runtime
- solutions [Office development in Visual Studio], runtime
- versions [Office development in Visual Studio], runtime
- assemblies [Office development in Visual Studio], runtime
- runtime [Office development in Visual Studio], about VSTO runtime
- solution loader [Office development in Visual Studio]
- runtime [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 16431a9ba2fe56b88f9f6b7f2c874c75bfad61c3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526266"
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Visual Studio Tools dla środowiska uruchomieniowego pakietu Office — omówienie
  Do uruchamiania rozwiązań utworzonych przy użyciu narzędzi deweloperskich Microsoft Office w programie Visual Studio, należy zainstalować narzędzia Visual Studio 2010 Tools for Office Runtime na komputerach użytkowników końcowych. Aby uzyskać więcej informacji, zobacz [How to: Install the Visual Studio Tools for Office Runtime redystrybucyjny](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). Narzędzia Visual Studio 2010 Tools for Office Runtime składają się z dwóch głównych składników:

- Rozszerzenia pakietu Office dla środowiska .NET Framework. To zarządzane zestawy tworzące warstwę komunikacji między rozwiązaniem a aplikacją pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [Opis rozszerzeń pakietu Office dla .NET Framework](#officeextensions).

- Moduł ładujący rozwiązanie dla pakietu Office. To zestaw niezarządzanych bibliotek DLL, przy użyciu których aplikacje pakietu Office ładują środowisko uruchomieniowe i rozwiązanie. Aby uzyskać więcej informacji, zobacz [Omówienie modułu ładującego rozwiązania pakietu Office](#UnmanagedLoader).

  Środowisko uruchomieniowe można zainstalować na kilka różnych sposobów. Składniki środowiska dodawane podczas jego instalacji zależą od konfiguracji komputera. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools scenariuszy instalacji pakietu Office Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

## <a name="understand-the-office-extensions-for-the-net-framework"></a><a name="officeextensions"></a> Informacje na temat rozszerzeń pakietu Office dla .NET Framework
 Visual Studio 2010 Tools for Office Runtime obejmuje rozszerzenia pakietu Office dla .NET Framework 3,5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i nowszych. Rozwiązania przeznaczone dla poszczególnych wersji środowiska .NET Framework używają rozszerzeń odpowiednich dla danej wersji.

 Rozszerzenia te składają się z zestawów, przy użyciu których rozwiązania automatyzują aplikacje pakietu Office i poszerzają ich funkcjonalność. Podczas tworzenia projektu pakietu Office program Visual Studio automatycznie dodaje odwołania do zestawów używanych dla typu projektu oraz docelowego środowiska .NET Framework projektu. Aby uzyskać więcej informacji na temat zestawów w rozszerzeniach pakietu Office, zobacz [zestawy w Visual Studio Tools dla środowiska uruchomieniowego pakietu Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

### <a name="design-differences-in-the-office-extensions"></a>Różnice projektowe w rozszerzeniach pakietu Office
 Większość typów używanych w rozszerzeniach pakietu Office dla środowiska .NET Framework 3.5 to klasy. Są to te same klasy, które zostały uwzględnione w poprzednich wersjach programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Z kolei większość typów używanych w rozszerzeniach pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych są interfejsami. Na przykład, gdy obiektem docelowym jest [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, <xref:Microsoft.Office.Tools.Excel.Worksheet> <xref:Microsoft.Office.Tools.Word.Document> typy i są interfejsami, a nie klasami.

 W większości przypadków kod napisany w rozwiązaniach pakietu Office jest taki sam, niezależnie od tego, czy rozwiązanie jest przeznaczone dla .NET Framework 3,5 czy [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Jednak niektóre funkcje wymagają kodu dopasowanego do cech wersji środowiska .NET Framework. Aby uzyskać więcej informacji, zobacz [Migrowanie rozwiązań pakietu Office do .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>Interfejsy w rozszerzeniach pakietu Office dla .NET Framework 4 lub nowszego
 Większość interfejsów w rozszerzeniach pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych nie jest przeznaczona do implementacji przez kod użytkownika. Jedyne interfejsy, które można zaimplementować, mają nazwy zaczynające się od litery **I**, np <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension> ..

 Wszystkie interfejsy, które nie zaczynają się od litery **I** są implementowane wewnętrznie przez program Visual Studio 2010 Tools for Office Runtime, a te interfejsy mogą ulec zmianie w przyszłych wersjach. Aby utworzyć obiekty, które implementują te interfejsy, należy użyć metod dostarczonych przez `Globals.Factory` obiekt w projekcie. Na przykład aby uzyskać obiekt implementujący <xref:Microsoft.Office.Tools.Excel.SmartTag> interfejs, użyj `Globals.Factory.CreateSmartTag` metody. Aby uzyskać więcej informacji na temat `Globals.Factory` , zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="enable-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>Włączanie równoważności typów i typów osadzonych w projektach przeznaczonych dla .NET Framework 4 lub nowszych
 Ponieważ model obiektów rozszerzeń pakietu Office dla programu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszego bazuje na interfejsach, można użyć funkcji równoważności typu w Visual C# i Visual Basic w programie Visual Studio, aby osadzić informacje o typie z [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do rozwiązania. Ta funkcja umożliwia niezależne korzystanie z rozwiązań pakietu Office oraz [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do wersji programu. Na przykład jeśli rozwiązanie używa <xref:Microsoft.Office.Tools.Word.Document> interfejsu jako typu osadzonego, a następna wersja środowiska uruchomieniowego dodaje członków do <xref:Microsoft.Office.Tools.Word.Document> interfejsu, Twoje rozwiązanie będzie nadal działało z następną wersją środowiska uruchomieniowego. Jeśli rozwiązanie nie korzysta z <xref:Microsoft.Office.Tools.Word.Document> interfejsu jako typu osadzonego, rozwiązanie przestanie działać z następną wersją środowiska uruchomieniowego.

 Domyślnie funkcja równoważności typów nie jest włączona podczas tworzenia projektu pakietu Office, który jest przeznaczony dla lub w [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] późniejszym czasie. Jeśli chcesz włączyć tę funkcję, ustaw właściwość **Osadź typy** współdziałania dowolnego z następujących odwołań do zestawów w projekcie na **wartość true**:

- Microsoft.Office.Tools.dll

- Microsoft.Office.Tools.Common.dll

- Microsoft.Office.Tools.Excel.dll

- Microsoft.Office.Tools.Outlook.dll

- Microsoft.Office.Tools.Word.dll

  Wprowadzenie tej zmiany spowoduje, że informacje o typie dla wszystkich typów środowisk uruchomieniowych używanych w projekcie zostaną podczas kompilowania projektu osadzane w zestawie rozwiązania. Informacje o typie osadzonym, a nie informacje o typie w przywoływanych zestawach, są używane przez rozwiązanie w czasie wykonywania.

## <a name="understand-the-office-solution-loader"></a><a name="UnmanagedLoader"></a> Informacje na temat modułu ładującego rozwiązania pakietu Office
 Visual Studio Tools pakietu Office Runtime zawiera kilka niezarządzanych bibliotek DLL, których aplikacje pakietu Office używają do ładowania środowiska uruchomieniowego i rozwiązań pakietu Office. Nigdy nie powinna zajść konieczność bezpośredniej pracy z tymi bibliotekami, jednak wiedza o ich przeznaczeniu może pomóc lepiej zrozumieć architekturę rozwiązań opartych na pakiecie Office.

 Aby uzyskać informacje o tym, jak te składniki są używane w procesie ładowania, zobacz [architektury dostosowań na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md) i [architektury dodatków VSTO](../vsto/architecture-of-vsto-add-ins.md).

### <a name="vstoeedll"></a>VSTOEE.dll
 Gdy użytkownik otwiera dostosowanie na poziomie dokumentu lub uruchamia dodatek narzędzi VSTO, aplikacja pakietu Office wywołuje do *VSTOEE.dll* wykonywania zadań wymaganych do załadowania [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

 *VSTOEE.dll* upewnić się, że poprawna wersja programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] jest załadowana do rozwiązania i zainstalowanej wersji pakietu Office. Mimo że wiele wersji programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] można zainstalować na tym samym komputerze, tylko jedno wystąpienie *VSTOEE.dll* jest instalowane w danym momencie. Jest to *VSTOEE.dll* , który został uwzględniony w najnowszej wersji środowiska uruchomieniowego zainstalowanej na komputerze. Aby uzyskać więcej informacji na temat różnych wersji programu, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] które mogą być używane w innych rozwiązaniach, zobacz temat [Uruchamianie rozwiązań w różnych wersjach Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

### <a name="vstoloaderdll"></a>VSTOLoader.dll
 Po załadowaniu przez *VSTOEE.dll* odpowiedniej wersji programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] *VSTOLoader.dll* wykonuje większość pracy wymaganej do załadowania zestawu rozwiązań. *VSTOLoader.dll* wykonuje kilka czynności:

- Tworzy domenę aplikacji dla każdego zestawu rozwiązania.

- Wykonuje zbiór testów kontrolnych zabezpieczeń w celu sprawdzenia, czy zestaw rozwiązania ma pozwolenie na działanie.

- Ładuje wersje rozszerzeń pakietu Office dla środowiska .NET Framework wymaganego przez rozwiązanie.

  *VSTOLoader.dll* wykonuje także kilka czynności, które są specyficzne dla dodatków narzędzi VSTO:

- Implementuje <xref:Extensibility.IDTExtensibility2> interfejs. <xref:Extensibility.IDTExtensibility2> jest interfejsem COM, który musi implementować wszystkie dodatki narzędzi VSTO dla aplikacji Microsoft Office. Ten interfejs definiuje metody, które aplikacja wywołuje w celu komunikowania się z dodatkiem narzędzi VSTO.

- Implementuje interfejs IManagedAddin —. Ten interfejs jest używany przez aplikacje pakietu Office w celu ułatwienia ładowania dodatków narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [IManagedAddin — Interface](../vsto/imanagedaddin-interface.md).

## <a name="understand-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Poznaj 32-bitowe i 64-bitowe wersje środowiska uruchomieniowego
 Istnieją oddzielne wersje 64-bitowe i 32-bitowe narzędzi Visual Studio 2010 Tools for Office Runtime. Te wersje środowiska uruchomieniowego są używane do uruchamiania rozwiązań w pakiecie 64-bitowym i 32-bitowym. W poniższej tabeli przedstawiono, która wersja środowiska uruchomieniowego jest wymagana dla każdej kombinacji systemu Windows i pakietu Office.

|Wydanie systemu Windows|Wydanie pakietu Microsoft Office|Wymagana wersja środowiska Visual Studio Tools for Office Runtime|
|------------------------|---------------------------------|--------------------------------------------------------------------|
|32-bitowa|32-bitowa|32-bitowa|
|64-bitowa|32-bitowa|64-bitowa|
|64-bitowa|64-bitowa|64-bitowa|

 Podczas instalowania pakietu Office wymagana wersja programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] jest instalowana wraz z pakietem Office. Na przykład po zainstalowaniu 64-bitowej wersji pakietu Office w 64-bitowej wersji systemu Windows jest również zainstalowana wersja 64-bit [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Aby uzyskać więcej informacji o instalowaniu programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] z pakietem Office, zobacz [Visual Studio Tools scenariusze instalacji środowiska uruchomieniowego pakietu Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

 W 64-bitowej wersji pakietu Office można również uruchamiać rozwiązania pakietu Office, które zostały utworzone przy użyciu szablonów projektów dla systemu 2007 Microsoft Office w programie Visual Studio 2008. Nie obsługują one jednak rozwiązań dla pakietu Office utworzonych przy użyciu szablonów projektów programu Microsoft Office 2003 w środowisku Visual Studio 2008 ani rozwiązań dla pakietu Office utworzonych w programie Visual Studio 2005. Aby uzyskać więcej informacji, zobacz [Uruchamianie rozwiązań w różnych wersjach Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

## <a name="repair-the-visual-studio-2010-tools-for-office-runtime"></a>Naprawa narzędzi Visual Studio 2010 Tools for Office Runtime
 Jeśli musisz naprawić środowisko uruchomieniowe, Otwórz aplet **programy i funkcje** lub **Dodaj lub usuń programy** w panelu sterowania, wybierz pozycję **Microsoft Visual Studio 2010 Tools for Office Runtime** na liście programów, a następnie kliknij przycisk **Odinstaluj**. Zostanie uruchomiony program instalacyjny, który umożliwi naprawę środowiska. Jeśli klikniesz pozycję **Zmień**, nie będziesz mieć możliwości naprawy środowiska uruchomieniowego.

## <a name="see-also"></a>Zobacz też
- [Visual Studio Tools dla scenariuszy instalacji środowiska uruchomieniowego pakietu Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Zestawy w Visual Studio Tools dla środowiska uruchomieniowego pakietu Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
- [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektura dostosowań na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Uaktualnianie i migrowanie rozwiązań pakietu Office](../vsto/upgrading-and-migrating-office-solutions.md)
