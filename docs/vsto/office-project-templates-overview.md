---
title: Szablony projektów pakietu Office — omówienie
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], about project templates
- Excel Workbook project template
- Word Template project template
- Excel [Office development in Visual Studio], project templates
- Project [Office development in Visual Studio], project templates
- project templates [Office development in Visual Studio]
- project templates, Word
- InfoPath [Office development in Visual Studio], project templates
- Excel Template project template
- project templates, 2007 Microsoft Office system
- project templates, Excel
- PowerPoint [Office development in Visual Studio], project templates
- Word [Office development in Visual Studio], Word project templates
- Office projects [Office development in Visual Studio], templates
- Excel projects in Visual Studio
- Word Document project template
- Visio [Office development in Visual Studio], project templates
- Word projects in Visual Studio
- Outlook [Office development in Visual Studio], project templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d83b04795386cfec80a8a309a9a84da04f6df105
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68926599"
---
# <a name="office-project-templates-overview"></a>Szablony projektów pakietu Office — omówienie
  Narzędzia deweloperskie Microsoft Office w programie Visual Studio zawierają szablony projektów służące do tworzenia następujących typów rozwiązań pakietu Office:

- [Dostosowania na poziomie dokumentów](#DocLevel)

- [Dodatki narzędzi VSTO](#AppLevel)

  Aby zapoznać się ze szczegółowym porównaniem tych typów rozwiązań pakietu Office, zobacz temat [programowanie rozwiązań pakietu Office — omówienie &#40;narzędzi VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

  Szablony projektów pakietu Office są dostępne w oknie dialogowym **Nowy projekt** , w obszarze węzła **Office** w węzłach języka **Visual C#** i **Visual Basic** . Każdy szablon generuje projekt o konfiguracji odpowiedniej dla aplikacji docelowej, razem z odwołaniami do zestawów i ustawieniami debugowania.

  Każdy projekt zawiera pliki i kod źródłowy niezbędne do rozpoczęcia tworzenia określonego typu rozwiązania. Kod generowany dla każdego projektu obejmuje programy obsługi zdarzeń uruchamiania i zamykania. Do programów obsługi można dodać kod, który będzie inicjował rozwiązanie podczas jego ładowania, a czyścił je podczas usuwania z pamięci. Aby uzyskać więcej informacji, zobacz [projekty pakietu Office w środowisku programu Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md) i [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

> [!NOTE]
> Narzędzia programistyczne pakietu Office są dołączane do niektórych wydań programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

## <a name="document-level-customizations"></a><a name="DocLevel"></a> Dostosowania na poziomie dokumentu
 Węzeł **Office** w oknie dialogowym **Nowy projekt** zawiera następujące szablony projektów umożliwiające rozpoczęcie tworzenia dostosowań na poziomie dokumentu dla programów Word i Excel:

- **Dokument narzędzia VSTO dla programów Word 2013 i 2016**

- **Szablon narzędzia VSTO dla programów Word 2013 i 2016**

- **Skoroszyt narzędzi VSTO dla programu Excel 2013 i 2016**

- **Szablon narzędzia VSTO dla programów Excel 2013 i 2016**

- **Dokument narzędzia VSTO programu Word 2010**

- **Szablon narzędzi VSTO programu Word 2010**

- **Skoroszyt narzędzi VSTO dla programu Excel 2010**

- **Szablon narzędzi VSTO programu Excel 2010**

  Szablony projektów dokumentów programu Word i skoroszytów programu Excel zawierają kod źródłowy, który pomoże rozpocząć tworzenie rozwiązania opartego na konkretnym dokumencie lub skoroszycie. W tego typu rozwiązaniach kod działa tylko wtedy, gdy powiązany dokument zostanie otwarty w programie Word lub Excel.

  Szablony projektów programów Word i Excel zachowują się identycznie jak szablony projektów dokumentów programu Word i skoroszytów programów Excel. Jednak szablony projektów programów Word i Excel bardzo ułatwiają użytkownikom tworzenie nowych spersonalizowanych lokalnych kopii dokumentów lub skoroszytów w rozwiązaniu. Funkcje w rozwiązaniu są dostępne z nowego dokumentu, który użytkownik utworzył na podstawie szablonu.

> [!NOTE]
> Szablony programu Word, które odwołują się do rozszerzeń kodu zarządzanego, nie mogą być używane jako globalne dodatki narzędzi VSTO. Zestaw nie jest wywoływany, jeśli szablon jest ładowany z katalogu uruchamiania programu Word. Aby uzyskać więcej informacji, zobacz [ograniczenia szablonów globalnych i dodatków programu Excel (pliki. xla)](#Limitations).

 Informacje na temat rozpoczynania pracy z tego typu projektami znajdują się w następujących tematach:

- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)

- [Rozwiązania programu Word](../vsto/word-solutions.md)

- [Rozwiązania programu Excel](../vsto/excel-solutions.md)

- [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)

- [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)

## <a name="vsto-add-ins"></a><a name="AppLevel"></a> Dodatki narzędzi VSTO
 Węzeł **Office/SharePoint** w oknie dialogowym **Nowy projekt** zawiera następujące szablony projektów umożliwiające rozpoczęcie tworzenia dodatków narzędzi VSTO.

- **Dodatek narzędzi VSTO dla programów Excel 2013 i 2016**

- **Dodatek narzędzi VSTO dla programu InfoPath 2013**

- **Dodatek VSTO dla programów Outlook 2013 i 2016**

- **Dodatek programu PowerPoint 2013 i 2016**

- **Dodatek Project 2013 i 2016**

- **Dodatek programu Visio 2013 i 2016**

- **Dodatek do programów Word 2013 i 2016**

- **Dodatek programu Excel 2010**

- **Dodatek programu InfoPath 2010**

- **Dodatek programu Outlook 2010**

- **Dodatek programu PowerPoint 2010**

- **Dodatek projektu 2010**

- **Dodatek programu Visio 2010**

- **Dodatek programu Word 2010**

  W projekcie opartym na jednym z tych szablonów projektu kod w rozwiązaniu jest uruchamiany po otwarciu powiązanej aplikacji. W przeciwieństwie do projektów na poziomie dokumentu kod nie jest kojarzony z jednym dokumentem.

  Więcej informacji na temat rozpoczynania pracy z tego typu projektami znajdują się w następujących tematach:

- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)

- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)

- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla projektu](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

## <a name="document-vs-template-solutions"></a>Rozwiązania dokumentów i szablonów
 Projektując rozwiązanie w oparciu o dokument programu Word lub skoroszyt programu Excel, należy wybrać najlepszy sposób udostępnienia tego dokumentu użytkownikom.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Czasami trzeba dać każdemu użytkownikowi osobną kopię. W takich przypadkach należy utworzyć rozwiązanie na bazie projektu dokumentu programu Excel lub Word.

 Innym razem lepiej udostępnić szablon na serwerze, tak aby każdy użytkownik mógł otworzyć szablon i zapisać lokalną kopię jako dokument. W takich przypadkach należy utworzyć rozwiązanie na bazie projektu szablonu programu Excel lub Word.

## <a name="comparison"></a>Porównanie
 W poniższej tabeli przedstawiono różnice między dokumentami a szablonami.

|Dokumenty|Szablony|
|---------------|---------------|
|Użytkownicy mogą otwierać i modyfikować dokument, chyba że ma on ustawiony atrybut tylko do odczytu. Wszelkie zapisane zmiany są przechowywane w oryginale.|Użytkownicy mogą otworzyć szablon, aby utworzyć kopię lokalną jako nowy dokument. Nie mogą oni modyfikować oryginału, chyba że otrzymają specjalne uprawnienia.|
|Po otwarciu dokument zgłasza <xref:Microsoft.Office.Tools.Word.Document.Open> zdarzenie.|Po otwarciu szablon zgłasza <xref:Microsoft.Office.Tools.Word.Document.New> zdarzenie.|

## <a name="limitations-of-global-templates-and-excel-add-ins-xla-files"></a><a name="Limitations"></a> Ograniczenia szablonów globalnych i dodatków programu Excel (pliki. xla)
 Dokumenty, skoroszyty i szablony mogą nie funkcjonować poprawnie jako szablony globalne lub dodatki narzędzi VSTO programu Excel (pliki. xla).

## <a name="word-templates"></a>Szablony programu Word
 Jeśli szablon programu Microsoft Office Word zawiera rozszerzenia kodu zarządzanego, a szablon jest dołączony jako szablon globalny lub ładowany z katalogu Startup programu Word, nie dochodzi do wywołania zestawu projektu. Ponadto dokument nie rozpoznaje formatu szablonu będącego częścią rozwiązania utworzonego dla pakietu Office.

## <a name="excel-add-ins-xla-files"></a>Dodatki programu Excel (pliki. xla)
 Brak projektu pakietu Office do tworzenia dodatku narzędzi VSTO programu Excel (plik *. xla* ). Istnieje możliwość zapisania skoroszytu jako pliku .xla, jednak operacja ta nie jest obsługiwana i jej nie zalecamy. Jeśli zapiszesz skoroszyt zawierający rozszerzenia kodu zarządzanego jako **Microsoft Office plik dodatku programu Excel ( \* . xla)** , możesz go wybrać w oknie dialogowym **dodatków** , aby zastosować go do innego skoroszytu. W niektórych przypadkach kod zostanie uruchomiony w skoroszycie docelowym po zastosowaniu dodatku VSTO, ale takie użycie rozwiązania pakietu Office nie jest obsługiwane.

## <a name="see-also"></a>Zobacz też
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
