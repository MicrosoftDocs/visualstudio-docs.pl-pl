---
title: Zestawy w Visual Studio Tools for Office runtime
titleSuffix: ''
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: a992621bc3311fa6dd9ca2703c00aa06d5998494
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838862"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Zestawy w Visual Studio Tools for Office runtime
  Podczas tworzenia projektu pakietu Office, Visual Studio automatycznie dodaje odwołania do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zestawów, które są używane dla tego typu projektu oraz docelowego środowiska .NET Framework projektu. Istnieją różne zestawy w rozszerzeniach pakietu Office, programu .NET Framework 3.5 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], i [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Aby uzyskać więcej informacji na temat rozszerzeń pakietu Office, zobacz [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>Zestawów w rozszerzeniach pakietu Office dla programu .NET Framework 4 i [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 Poniższa tabela zawiera listę zestawów, które są zawarte w rozszerzeniach pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Dokumentacja przestrzeni nazw i typów w zestawach, te informacje, zobacz [zarządzana dokumentacja dotycząca &#40;programowanie Office w Visual Studio&#41;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Nazwa zestawu|Opis|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|Zawiera następujące typy:<br /><br /> -Typów w celu utworzenia dostosowań Wstążki i tagi inteligentne. **Uwaga:**      Tagi inteligentne są przestarzałe w [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] i [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Typów w celu utworzenia okienka akcji w dostosowaniach na poziomie dokumentu i niestandardowych okienek zadań w dodatków narzędzi VSTO.|  
|Microsoft.Office.Tools.Excel.dll|Udostępnia interfejsy, które reprezentują elementów hosta i kontrolek hosta dla projektów programu Excel i obsługi typów. Aby uzyskać więcej informacji, zobacz [automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Zawiera typy używane do tworzenia regionów formularza niestandardowego w dodatków narzędzi VSTO dla programu Outlook.|  
|Microsoft.Office.Tools.Word.dll|Udostępnia interfejsy, które reprezentują elementów hosta i kontrolek hosta dla projektów programu Word i obsługi typów. Aby uzyskać więcej informacji, zobacz [automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Zawiera następujące typy:<br /><br /> -Wyjątki, które mogą zostać zgłoszone przez Visual Studio Tools for Office runtime.<br />-Atrybuty, których można użyć podczas tworzenia programu Outlook regionów formularza.|  
|Microsoft.Office.Tools.dll|Zawiera typy, które są częścią Visual Studio Tools for Office runtime infrastruktury i nie są przeznaczone do użycia bezpośrednio w kodzie.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Zawiera następujące typy:<br /><br /> <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Atrybutu i <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfejs, który służy do obiektów danych w pamięci podręcznej w dostosowaniu na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [dane z pamięci podręcznej](../vsto/caching-data.md).<br /><xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> Interfejs, który można zaimplementować tak, aby uruchomić dodatkowe czynności instalacyjne jako ostatni krok Instalatora ClickOnce dla rozwiązań pakietu Office. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-Wyjątki, które mogą zostać zgłoszone przez Visual Studio Tools for Office runtime.<br />-Innych typów, które są częścią Visual Studio Tools for Office runtime infrastruktury i nie są przeznaczone do użycia bezpośrednio w kodzie.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Zawiera następujące typy:<br /><br /> <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasy, która umożliwia dołączanie zestawy dostosowywania do dokumentów i uzyskiwać dostęp do pamięci podręcznej w dokumentach. Aby uzyskać więcej informacji, zobacz [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Kilka klas, które reprezentują hierarchii buforowanych danych w dostosowaniu na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 Projekty przeznaczone [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] także odwoływać się do następujących zestawów. Te zestawy nie są częścią [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do dystrybucji. Zamiast tego są one zależne zestawy, które musi zostać wdrożony za pomocą rozwiązania. Domyślnie są kopiowane do folderu wyjściowego kompilacji projektu ( **Kopiuj lokalnie** właściwość te zestawy są ustawione na **True**). Jeśli projekt jest wdrożony przy użyciu technologii ClickOnce, te zestawy są objęte wygenerowany pakiet.  
  
|Nazwa zestawu|Opis|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Udostępnia podstawowe klasy dla wygenerowanej `ThisAddIn` klasy w projektach dodatku narzędzi VSTO dla programów i generowanej klasie wstążki we wszystkich projektach.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Zawiera następujące typy:<br /><br /> -Podstawowej klasy dla wygenerowanej `ThisWorkbook` i `Sheet` klas w poziomie dokumentu projektów dla programu Excel.<br />-Kontrolki formularzy Windows używanych w arkuszach w projektach programu Excel.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Udostępnia klasy bazowej dla wygenerowany `ThisAddIn` i tworzą region klas w projektach programu Outlook.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Zawiera następujące typy:<br /><br /> -Podstawowej klasy dla wygenerowanej `ThisDocument` klasy w projektów na poziomie dokumentu dla programu Word.<br />-Kontrolki formularzy Windows używanych w dokumentach w projektach programu Word.|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Zestawów w rozszerzeniach pakietu Office dla programu .NET Framework 3.5  
 Poniższa tabela zawiera listę zestawów, które znajdują się w rozszerzeniach pakietu Office dla programu .NET Framework 3.5. Aby uzyskać dokumentację na temat przestrzenie nazw i klas w tych zestawach, zobacz następującą sekcję informacyjną w dokumentacji programu Visual Studio 2008: [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Nazwa zestawu|Opis|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Zawiera następujące typy:<br /><br /> -Microsoft.Office.Tools.AddIn klasę bazową dla dodatków narzędzi VSTO.<br />-Klas na potrzeby tworzenia dostosowań Wstążki i tagi inteligentne. **Uwaga:**      Tagi inteligentne są przestarzałe w [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] i [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Klas na potrzeby tworzenia okienka akcji w dostosowaniach na poziomie dokumentu i niestandardowych okienek zadań w dodatkach VSTO.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Udostępnia elementów hosta i kontrolek hosta dla rozwiązania programu Excel. Aby uzyskać więcej informacji, zobacz [automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Udostępnia klasy, które umożliwiają tworzenie regionów formularzy niestandardowych dodatków narzędzi VSTO dla programu Outlook na.|  
|Microsoft.Office.Tools.Word.v9.0.dll|Udostępnia elementów hosta i kontrolek hosta dla rozwiązania programu Word. Aby uzyskać więcej informacji, zobacz [automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v9.0.dll|Zawiera następujące typy:<br /><br /> [RemoteBindableComponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) klasy, która dostarcza możliwości wiązania danych dla kontrolki hosta w poziomie dokumentu dostosowań.<br />-Innych typów, które są częścią Visual Studio Tools for Office runtime infrastruktury i nie są przeznaczone do użycia bezpośrednio w kodzie.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Zawiera następujące typy:<br /><br /> <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Atrybutu i <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfejs, który służy do obiektów danych w pamięci podręcznej w dostosowaniu na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [dane z pamięci podręcznej](../vsto/caching-data.md).<br />-Wyjątki, które mogą zostać zgłoszone przez Visual Studio Tools for Office runtime.<br />-Innych typów, które są częścią Visual Studio Tools for Office runtime infrastruktury i nie są przeznaczone do użycia bezpośrednio w kodzie.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Udostępnia <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interfejs, który można zaimplementować tak, aby uruchomić dodatkowe czynności instalacyjne jako ostatni krok Instalatora ClickOnce dla rozwiązań pakietu Office. Aby uzyskać więcej informacji, zobacz [wdrażaniem rozwiązań Office zaawansowane](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Zawiera następujące typy:<br /><br /> <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasy, która umożliwia programowe dołączanie zestawy dostosowywania do dokumentów i uzyskiwać dostęp do pamięci podręcznej w dokumentach. Aby uzyskać więcej informacji, zobacz [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Kilka klas, które reprezentują hierarchii buforowanych danych w dostosowaniu na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Zawiera następujące typy:<br /><br /> -Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry i Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList klas, których można użyć do utworzenia użytkownika włączenia wpisów na liście udzielenia zaufania do pakietu Office rozwiązania przeznaczone dla programu .NET Framework 3.5.<br />-Innych typów, które są częścią Visual Studio Tools for Office runtime infrastruktury i nie są przeznaczone do użycia bezpośrednio w kodzie.|  
  
## <a name="see-also"></a>Zobacz także  
 [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Visual Studio Tools dla pakietu Office Runtime ― scenariusze instalacji](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
