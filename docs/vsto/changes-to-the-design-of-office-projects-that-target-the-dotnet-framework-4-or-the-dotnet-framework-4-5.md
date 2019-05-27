---
title: Projektowanie zmian w projektach pakietu Office przeznaczonych dla platformy .NET Framework
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7f2c4176c0aab4340648feee0b709f9dfd472ca0
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177588"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Zmienia się na projekt projektów Office obiektu docelowego .NET Framework 4 lub .NET Framework 4.5
  Począwszy od [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], Visual Studio wprowadzone pewne zmiany do projekt projektów Office obiektu docelowego [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej. Jeśli jesteś zaznajomiony z projektów pakietu Office w poprzednich wersjach programu Visual Studio, należy pamiętać o tych zmianach przed opracowywanie projektach dla pakietu Office przeznaczonych dla tych wersji programu .NET Framework 4.0 lub nowszego. Domyślnie wszystkie projekty, które tworzysz przy użyciu programu Visual Studio 2013 lub nowszy dla środowiska .NET Framework 4.0 lub nowszy.

 W poniższych sekcjach opisano te zmiany projektu projektu pakietu Office.

## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Zrozumienie projektu na podstawie interfejsu programu Visual Studio 2010 Tools dla pakietu Office runtime
 Po utworzeniu projektu pakietu Office, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej, większość typów używanych w Visual Studio 2010 Tools dla pakietu Office runtime to interfejsy. Jest to istotne zmiany z poprzednich wersji [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], gdzie te typy są klasy. Na przykład kiedy środowiskiem docelowym [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, <xref:Microsoft.Office.Tools.Excel.Worksheet> i <xref:Microsoft.Office.Tools.Word.Document> typy są interfejsami zamiast klasami. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md).

 Dla wszystkich typów, które można utworzyć wystąpienia bezpośrednio w poprzednich wersjach [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], możesz teraz używać metod `Globals.Factory` obiektu można pobrać wystąpień tych typów. Na przykład, aby pobrać obiekt, który implementuje <xref:Microsoft.Office.Tools.Excel.SmartTag> interfejsu, należy użyć `Globals.Factory.CreateSmartTag` metody. Więcej informacji znajduje się w następujących tematach:

- [Zaktualizuj projekty programu Excel i Word, są migrowane do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Aktualizowanie dostosowań Wstążki w projektach pakietu Office, które przenoszonych do oprogramowania .NET Framework 4 lub .NET Framework 4.5](/visualstudio/vsto/update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5)

- [Aktualizowanie regionów formularzy w projektach programu Outlook, są migrowane do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

### <a name="new-base-classes-in-office-projects"></a>Nowe klasy bazowe w projektach pakietu Office
 Nowy projekt na podstawie interfejsu programu Visual Studio 2010 Tools dla pakietu Office runtime ma wpływ na wygenerowanych klas w projektach pakietu Office, takich jak `ThisDocument`, `ThisWorkbook`, i `ThisAddIn`. W projektach pakietu Office, których platformą docelową jest program .NET Framework 3.5 i wcześniejszymi wersjami programu framework tych wygenerowanych klas pochodzić od klasy w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] takich jak `Microsoft.Office.Tools.Word.Document`, `Microsoft.Office.Tools.Excel.Worksheet`, i `Microsoft.Office.Tools.AddIn`. W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, te [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] klasy są teraz interfejsy. W związku z tym wygenerowanych klas w projektach pakietu Office nie może pochodzić ich implementacji, które z nich. Zamiast tego wygenerowanych klas pochodzić od nowych klas podstawowych takich jak <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase>, i <xref:Microsoft.Office.Tools.AddInBase>. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md) i [Program dostosowań poziomu dokumentu](../vsto/programming-document-level-customizations.md).

 Klasy bazowe nie są częścią [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do dystrybucji. Zamiast tego są definiowane w zestawach narzędzi, które są dołączone do programu Visual Studio. Te zestawy są kopiowane do folderu wyjściowego podczas kompilowania projektów pakietu Office i musi zostać wdrożony za pomocą rozwiązania. Aby uzyskać więcej informacji na temat zestawów narzędzi, zobacz [zestawy w Visual Studio Tools for Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>Istotne zmiany w projektach pakietu Office, które są ukierunkowany na .NET Framework 4
 W poniższej tabeli wymieniono główne przełomowych zmianach, mogą wystąpić w projektach pakietu Office, które są ukierunkowany na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej. Aby uzyskać więcej informacji, zobacz [Migrowanie rozwiązań pakietu Office do wersji programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

|Zmiana powodująca niezgodność|Konsekwencją|
|---------------------|-----------------|
|<xref:System.Security.SecurityTransparentAttribute> Nie jest już używana lub obsługiwane w projektach pakietu Office.|Ten atrybut należy usunąć z pliku AssemblyInfo kodu w projektach pakietu Office, uaktualniani z programu Visual Studio 2008. Aby uzyskać więcej informacji, zobacz [wymagane zmiany w celu uruchamiania projektów pakietu Office, które przenoszonych do oprogramowania .NET Framework 4 lub .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|**ExcelLocale1033Attribute** nie jest już używana lub obsługiwane w projektach programu Excel.|Należy usunąć ten atrybut z *AssemblyInfo* plik kodu w projektach programu Excel. Aby uzyskać więcej informacji, zobacz [aktualizacji programu Excel i Word projektów, które przenoszonych do oprogramowania .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Model programowania **Wstążka (Projektant graficzny)** elementy projektu została zmieniona.|Należy zmodyfikować plik CodeBehind dla wszelkich elementów wstążki w projekcie. Musisz także zmodyfikować każdy kod, który tworzy formantów wstążki w czasie wykonywania, obsługi zdarzeń Wstążki lub programowo Ustawia położenie składnika wstążki. Aby uzyskać więcej informacji, zobacz [dostosowań Wstążki aktualizacji w projektach pakietu Office, które przenoszonych do oprogramowania .NET Framework 4 lub .NET Framework 4.5](/visualstudio/vsto/update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5).|
|Model programowania w regionach formularzy programu Outlook został zmieniony.|Należy zmodyfikować plik CodeBehind dla dowolnego regionów formularza w projekcie i wszelki kod, który tworzy wystąpienie niektórych klas regionu formularza w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [aktualizowanie regionów formularzy w projektach programu Outlook, są migrowane do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Zmienił się model programowania tagów inteligentnych w projektach programu Excel i Word. Tagi inteligentne są przestarzałe w [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] i [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Jeśli Twoje rozwiązanie używa inteligentnych tagów, wystąpią błędy podczas kompilowania projektu. Ponieważ tagi inteligentne są przestarzałe w [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] i [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)], należy usunąć tagów, przed przeprowadzeniem testu i debugowania rozwiązań w [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] lub nowszej.|
|Składnia `GetVstoObject` i `HasVstoObject` metody została zmieniona.|Należy przekazać `Globals.Factory` obiektu tych metod, gdy dostęp do natywnych obiektów z podstawowych zestawów międzyoperacyjnych (PIA) lub możesz uzyskać dostęp tych metod w obiekcie, który jest zwracany przez `Globals.Factory` właściwość w projekcie. Aby uzyskać więcej informacji, zobacz [aktualizacji programu Excel i Word projektów, które przenoszonych do oprogramowania .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Zdarzenia formanty zawartości programu Word są skojarzone z nowych delegatów.|Należy zmodyfikować każdy kod, który obsługuje zdarzenia formanty zawartości programu Word, aby określić nowych delegatów. Aby uzyskać więcej informacji, zobacz [aktualizacji programu Excel i Word projektów, które przenoszonych do oprogramowania .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|`OLEObject` i `OLEControl` zmieniono nazwy klasy.|Należy zmodyfikować każdy kod, korzystającą z wystąpieniami tych klas w celu użycia <xref:Microsoft.Office.Tools.Excel.ControlSite> lub <xref:Microsoft.Office.Tools.Word.ControlSite> zamiast niego obiekty. Aby uzyskać więcej informacji, zobacz [aktualizacji programu Excel i Word projektów, które przenoszonych do oprogramowania .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Hostowanie klas elementów, takich jak `ThisWorkbook`, `Sheet` *n*, `ThisDocument`, i `ThisAddIn`, nie zapewniają już `Dispose` metodę, którą można przesłonić.|Należy przenieść każdy kod w `Dispose` zastąpienie metody `Shutdown` programu obsługi zdarzeń w klasie elementu hosta, na przykład `ThisAddIn_Shutdown`i Usuń `Dispose` metoda przesłania z klasy elementu host.|

## <a name="see-also"></a>Zobacz także
- [Migrowanie rozwiązań pakietu Office do wersji programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [What's new in Office development](https://msdn.microsoft.com/library/bf054af2-c896-4723-aa15-6381145b14bb)
- [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md)
