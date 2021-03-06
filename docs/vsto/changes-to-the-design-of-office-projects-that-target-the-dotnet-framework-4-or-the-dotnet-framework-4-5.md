---
title: Projektuj zmiany w projektach pakietu Office, dla których .NET Framework
description: Dowiedz się więcej o zmianach wprowadzonych w programie Visual Studio do projektu pakietu Office przeznaczonego dla .NET Framework 4 lub nowszego.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio 2010, what's new
- what's new [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2bb8f6064bd2c2df55c7d0cf8fea1e25c513da0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903796"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Zmiany projektu pakietu Office przeznaczone dla .NET Framework 4 lub .NET Framework 4,5
  Począwszy od programu [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] , program Visual Studio wprowadził pewne zmiany do projektu pakietu Office, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub w późniejszym czasie. Jeśli znasz projekty pakietu Office w poprzednich wersjach programu Visual Studio, należy pamiętać o tych zmianach przed rozpoczęciem tworzenia projektów pakietu Office przeznaczonych dla tych wersji .NET Framework 4,0 lub nowszych. Domyślnie wszystkie projekty tworzone przy użyciu Visual Studio 2013 lub później są przeznaczone dla .NET Framework 4,0 lub nowszych.

 W poniższych sekcjach opisano te zmiany projektu programu Office Project.

## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Zapoznaj się z projektowaniem opartym na interfejsie narzędzi Visual Studio 2010 Tools for Office Runtime
 Podczas tworzenia projektu pakietu Office, który jest przeznaczony dla programu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszego, większość typów używanych w programie Visual Studio 2010 Tools for Office Runtime to interfejsy. Jest to istotna zmiana z poprzednich wersji programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , gdzie te typy są klasami. Na przykład, gdy obiektem docelowym jest [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, <xref:Microsoft.Office.Tools.Excel.Worksheet> <xref:Microsoft.Office.Tools.Word.Document> typy i są interfejsami, a nie klasami. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools dla środowiska uruchomieniowego pakietu Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

 Dla dowolnego typu, który można utworzyć bezpośrednio w poprzednich wersjach programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , można teraz użyć metod `Globals.Factory` obiektu do uzyskania wystąpień tych typów. Na przykład aby uzyskać obiekt implementujący <xref:Microsoft.Office.Tools.Excel.SmartTag> interfejs, użyj `Globals.Factory.CreateSmartTag` metody. Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Aktualizowanie projektów programów Excel i Word, które są migrowane do .NET Framework 4 lub .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Aktualizowanie dostosowań wstążki w projektach pakietu Office migrowanych do .NET Framework 4 lub .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Aktualizowanie regionów formularzy w projektach programu Outlook migrowanych do .NET Framework 4 lub .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

### <a name="new-base-classes-in-office-projects"></a>Nowe klasy bazowe w projektach pakietu Office
 Nowy projekt oparty na interfejsie programu Visual Studio 2010 Tools for Office Runtime ma wpływ na wygenerowane klasy w projektach pakietu Office, takich jak `ThisDocument` , `ThisWorkbook` i `ThisAddIn` . W projektach pakietu Office przeznaczonych dla .NET Framework 3,5 i poprzednich wersji platformy te wygenerowane klasy pochodzą z klas w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] takich jak `Microsoft.Office.Tools.Word.Document` , `Microsoft.Office.Tools.Excel.Worksheet` , i `Microsoft.Office.Tools.AddIn` . W projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych, te [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] klasy są teraz interfejsy. W związku z tym wygenerowane klasy w projektach pakietu Office nie mogą już dziedziczyć ich implementacji. Zamiast tego wygenerowane klasy pochodzą z nowych klas podstawowych, takich jak <xref:Microsoft.Office.Tools.Word.DocumentBase> , <xref:Microsoft.Office.Tools.Excel.WorksheetBase> , i <xref:Microsoft.Office.Tools.AddInBase> . Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO](../vsto/programming-vsto-add-ins.md) i [programowe dostosowanie na poziomie dokumentu](../vsto/programming-document-level-customizations.md).

 Klasy podstawowe nie są częścią [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pakietu redystrybucyjnego. Zamiast tego są one zdefiniowane w zestawach narzędzi, które są dołączone do programu Visual Studio. Te zestawy są kopiowane do folderu wyjściowego podczas kompilowania projektów pakietu Office i muszą zostać wdrożone wraz z rozwiązaniem. Aby uzyskać więcej informacji na temat zestawów narzędzi, zobacz [zestawy w Visual Studio Tools dla środowiska uruchomieniowego pakietu Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>Istotne zmiany w projektach pakietu Office, które są przekierowywane do .NET Framework 4
 W poniższej tabeli wymieniono podstawowe zmiany, które można napotkać w projektach pakietu Office, które są przekierowywane do programu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszego. Aby uzyskać więcej informacji, zobacz [Migrowanie rozwiązań pakietu Office do .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

|Zmiana podziału|Konsekwencję|
|---------------------|-----------------|
|<xref:System.Security.SecurityTransparentAttribute>Nie jest już używane ani obsługiwane w projektach pakietu Office.|Należy usunąć ten atrybut z pliku kodu AssemblyInfo w projektach pakietu Office uaktualnianych z programu Visual Studio 2008. Aby uzyskać więcej informacji, zobacz [wymagane zmiany w celu uruchomienia projektów pakietu Office migrowanych do .NET Framework 4 lub .NET Framework 4,5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|**ExcelLocale1033Attribute** nie jest już używana ani nie jest obsługiwana w projektach programu Excel.|Należy usunąć ten atrybut z pliku kodu *AssemblyInfo* w projektach programu Excel. Aby uzyskać więcej informacji, zobacz [Aktualizowanie projektów programów Excel i Word, które zostały zmigrowane do .NET Framework 4 lub .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Model programowania elementów projektu **wstążki (Visual Designer)** został zmieniony.|Należy zmodyfikować plik związany z kodem dla wszystkich elementów wstążki w projekcie. Należy również zmodyfikować każdy kod, który tworzy wystąpienie formantów wstążki w czasie wykonywania, obsługuje zdarzenia wstążki lub ustawia pozycję składnika wstążki programowo. Aby uzyskać więcej informacji, zobacz [Aktualizowanie dostosowań wstążki w projektach pakietu Office migrowanych do .NET Framework 4 lub .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md).|
|Model programowania regionów formularzy programu Outlook został zmieniony.|Należy zmodyfikować plik związany z kodem dla dowolnego regionu formularza w projekcie i dowolny kod, który tworzy wystąpienia niektórych klas regionów formularzy w czasie wykonywania. Aby uzyskać więcej informacji, zobacz temat [Aktualizowanie regionów formularzy w projektach programu Outlook migrowanych do .NET Framework 4 lub .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Model programowania tagów inteligentnych w projektach programu Excel i Word został zmieniony. Tagi inteligentne są przestarzałe w [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] i [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] .|Jeśli rozwiązanie używa tagów inteligentnych, błędy wystąpią podczas kompilowania projektu. Ponieważ Tagi inteligentne są przestarzałe w [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] i [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] , należy usunąć Tagi, zanim będzie można testować i debugować rozwiązanie w [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] lub w późniejszym czasie.|
|Składnia `GetVstoObject` `HasVstoObject` metod i została zmieniona|Należy przekazać `Globals.Factory` obiekt do tych metod, gdy uzyskujesz dostęp do nich w obiektach natywnych z podstawowych zestawów międzyoperacyjnych (zestawów PIA) lub możesz uzyskać dostęp do tych metod na obiekcie, który jest zwracany przez `Globals.Factory` Właściwość w projekcie. Aby uzyskać więcej informacji, zobacz [Aktualizowanie projektów programów Excel i Word, które zostały zmigrowane do .NET Framework 4 lub .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Zdarzenia formantów zawartości programu Word są skojarzone z nowymi delegatami.|Aby określić nowych delegatów, należy zmodyfikować każdy kod, który obsługuje zdarzenia formantów zawartości programu Word. Aby uzyskać więcej informacji, zobacz [Aktualizowanie projektów programów Excel i Word, które zostały zmigrowane do .NET Framework 4 lub .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|`OLEObject` `OLEControl` Nazwy klas i zostały zmienione.|Należy zmodyfikować każdy kod, który używa wystąpień tych klas do użycia <xref:Microsoft.Office.Tools.Excel.ControlSite> obiektów lub <xref:Microsoft.Office.Tools.Word.ControlSite> . Aby uzyskać więcej informacji, zobacz [Aktualizowanie projektów programów Excel i Word, które zostały zmigrowane do .NET Framework 4 lub .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Klasy elementów hosta, takie jak `ThisWorkbook` , `Sheet` *n*, `ThisDocument` i `ThisAddIn` , nie udostępniają już `Dispose` metody, którą można przesłonić.|Należy przenieść dowolny kod w `Dispose` przesłonięciu metody do `Shutdown` procedury obsługi zdarzeń w klasie elementu hosta, na przykład, `ThisAddIn_Shutdown` i usunąć `Dispose` przesłonięcie metody z klasy elementów hosta.|

## <a name="see-also"></a>Zobacz też
- [Migrowanie rozwiązań pakietu Office do .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Nowości w programowaniu pakietu Office](/previous-versions/86bkz018(v=vs.110))
- [Visual Studio Tools dla środowiska uruchomieniowego pakietu Office — omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md)