---
title: Projekty pakietu Office w środowisku programu Visual Studio
description: Dowiedz się, w jaki sposób projekty Microsoft Office mają środowisko programistyczne podobne do innych typów projektów w programie Visual Studio, takich jak projekty Windows Forms.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.WordDocument
- VST.ProjectItem.ExcelWorkbook
- VST.ProjectItem.ExcelTemplate
- VST.ProjectItem.ExcelSheet
- VST.ProjectItem.BlueprintCode
- VST.ProjectItem.Word
- VST.ProjectItem.Excel
- VST.ProjectItem.AddinProject
- Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner
- VST.ProjectItem.ExtendedBluePrint
- VST.ProjectItem.WordTemplate
- Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner
- VST.Designer.ExcelVST.Designer.Word
- VST.ProjectItem.ExtendedBlueprintCode
- VST.ProjectItem.BluePrint
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- hidden files [Office development in Visual Studio]
- project files [Office development in Visual Studio], hidden
- Office development in Visual Studio, documents in Visual Studio
- design view, Excel
- designers, Office development in Visual Studio
- Office documents [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], about documents in Visual Studio
- designers [Office development in Visual Studio]
- Word designer
- Word [Office development in Visual Studio], Word designer
- Visual Studio, Office documents in
- worksheets [Office development in Visual Studio]
- VST.Designer.ExcelVST.Designer.Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 88abd7294a96b4fe4989630753253b16f036ab7c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892011"
---
# <a name="office-projects-in-the-visual-studio-environment"></a>Projekty pakietu Office w środowisku programu Visual Studio
  Dla projektów pakietu Microsoft Office przygotowano środowisko programistyczne podobne jak do innych typów projektów w programie, np. projektów interfejsu Windows Forms. Po utworzeniu lub otwarciu projektu pakietu Office elementy projektu są wyświetlane w **Eksplorator rozwiązań**. W projektach na poziomie dokumentu dokument (tzn. dokument programu Word lub skoroszyt programu Excel) jest otwierany w programie Visual Studio i zachowuje się jak projektant wizualny.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="project-items-in-solution-explorer"></a>Elementy projektu w Eksplorator rozwiązań
 W projekcie na poziomie dokumentu **Eksplorator rozwiązań** wyświetla następujące domyślne elementy:

- Węzły dla dokumentu, skoroszytu i arkuszy, które są dostosowywane przez projekt. Węzły te pełnią rolę kontenerów na pliki kodu skojarzone z dokumentem, skoroszytem i arkuszami.

- Pliki kodu skojarzone z dokumentem, skoroszytem i arkuszami, które są dostosowywane przez projekt. W projektach programu Word pliki kodu są powiązane z dokumentem lub szablonem programu Word. W projektach programu Excel pliki kodu są skojarzone ze skoroszytem lub szablonem programu Excel oraz z każdym arkuszem i arkuszem wykresu w skoroszycie lub szablonie.

- Ukryte pliki projektu, które nie są przeznaczone do bezpośredniej edycji. Aby uzyskać więcej informacji, zobacz [ukryte pliki projektu](#hiddenfiles).

  W projekcie dodatku VSTO **Eksplorator rozwiązań** wyświetla następujące domyślne elementy:

- Węzeł aplikacji. Ten węzeł ma taką samą nazwę jak aplikacja hosta, taka jak **Word**, **Excel** lub **Outlook**. Węzeł aplikacji zawiera plik kodu ThisAddIn. Udostępnia również **przestrzeń nazw dla właściwości element hosta** . Aby uzyskać więcej informacji na temat tej właściwości, zobacz [właściwości w projektach pakietu Office](../vsto/properties-in-office-projects.md).

- Plik kodu ThisAddIn. Ten plik zawiera wygenerowaną `ThisAddIn` klasę dla dodatku VSTO. Aby uzyskać więcej informacji na temat tej klasy, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

- Ukryte pliki projektu, które nie są przeznaczone do bezpośredniej edycji. Aby uzyskać więcej informacji, zobacz [ukryte pliki projektu](#hiddenfiles).

### <a name="temporary-certificates"></a>Tymczasowe certyfikaty
 Projekty pakietu Office zawierają również tymczasowy certyfikat o nazwie *projekt* _TemporaryKey. pfx. Certyfikat służy do podpisywania manifestów aplikacji i wdrażania projektu w trakcie programowania. Aby uzyskać więcej informacji, zobacz [udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md) i [bezpiecznych rozwiązań pakietu Office](../vsto/securing-office-solutions.md).

### <a name="hidden-project-files"></a><a name="hiddenfiles"></a> Ukryte pliki projektu
 Niektóre pliki projektu są domyślnie ukryte. Pliki te są generowane przez program Visual Studio i różnią się w zależności od typu projektu. Aby wyświetlić ukryte pliki, kliknij przycisk **Pokaż wszystkie pliki** w **Eksplorator rozwiązań**.

 Nie wolno modyfikować ukrytych plików projektu. Bezpośrednia edycja tych plików nie jest obsługiwana i może spowodować uszkodzenie projektu. Ukryte pliki projektu są generowane każdorazowo po wprowadzeniu pewnych zmian w dokumencie. Ręczna modyfikacja ukrytego pliku projektu spowoduje utratę tych zmian podczas ponownego generowania pliku.

## <a name="document-designer-in-document-level-projects"></a>Projektant dokumentów w projektach na poziomie dokumentu
 W projektach na poziomie dokumentu dla programów Excel i Word jest dostępny projektant, który hostuje dokument skojarzony z projektem w programie Visual Studio. Projektant umożliwia modyfikowanie dokumentu bez konieczności wychodzenia poza środowisko Visual Studio.

 Aby otworzyć dokument w projektancie, kliknij dwukrotnie plik kodu w **Eksplorator rozwiązań** , który jest skojarzony z dokumentem. Na przykład, aby otworzyć arkusz **Arkusz1** w projektancie w projekcie programu Excel, kliknij dwukrotnie plik kodu **Arkusz1** .

 Podczas modyfikowania dokumentu w projektancie można wykorzystać macierzystą funkcjonalność aplikacji pakietu Office. Na przykład można wpisać tekst w dokumencie lub arkuszu albo za pomocą Wstążki wykonać zadania takie jak dodanie tabeli lub wykresu. Domyślnie mapowania skrótów klawiaturowych są takie same jak w programie Visual Studio. Aby zamiast tego użyć mapowań skrótów klawiaturowych pakietu Office, należy zmienić ustawienia w węźle **Ustawienia klawiatury Microsoft Office** w oknie dialogowym **Opcje** w menu **Narzędzia** .

### <a name="controls-on-documents"></a>Formanty w dokumentach
 Można przeciągać *formanty hosta* i Windows Forms kontrolki z **przybornika** programu Visual Studio na powierzchnię projektu dokumentu. Formanty hosta to specjalistyczne wersje obiektów pakietu Office, takie jak formanty zawartości programu Word i zakresy programu Excel, których można używać w projektach pakietu Office utworzonych przy użyciu programu Visual Studio. Formanty hosta mają dodatkowe funkcje nieobecne w odnośnych obiektach pakietu Office, np. tworzenie powiązań danych czy większy zbiór zdarzeń.

 Aby uzyskać więcej informacji, zobacz [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md) oraz [kontrolek Windows Forms w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md).

### <a name="excel-worksheets-and-workbooks-in-the-designer"></a>Arkusze i skoroszyty programu Excel w projektancie
 Po otwarciu arkusza w projektancie można go modyfikować tak samo, jak po otwarciu bezpośrednio w programie Excel. Dwukrotne kliknięcie komórki spowoduje przełączenie jej do trybu edycji. Po dwukrotnym kliknięciu komórki zawierającej formant hosta zostanie otwarty Edytor kodu, a program Visual Studio wygeneruje domyślny program obsługi zdarzeń dla formantu. Aby przechodzić do innych arkuszy, możesz klikać karty arkuszy u dołu projektanta.

 Po otwarciu skoroszytu w projektancie nie widać żadnej powierzchni projektowej. Widok projektu skoroszytu to duży zasobnik elementów, który wypełnia projektanta.

 Skoroszyt i każdy arkusz w skoroszycie mają powiązane pliki kodu. Każdy plik kodu zawiera wygenerowaną klasę *elementu hosta* , która reprezentuje skoroszyt lub arkusz. Aby uzyskać więcej informacji, zobacz [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md).

### <a name="word-documents-in-the-designer"></a>Dokumenty programu Word w projektancie
 Po otwarciu dokumentu w projektancie można go modyfikować tak samo, jak po otwarciu bezpośrednio w programie Word. Dwukrotne kliknięcie wyrazu w dokumencie spowoduje jego zaznaczenie. Jeśli jednak wyraz znajduje się wewnątrz formantu hosta, zostanie otwarty edytor kodu, a program Visual Studio wygeneruje domyślny program obsługi zdarzeń dla formantu.

 Dokument ma skojarzony plik kodu. Plik kodu zawiera wygenerowaną klasę *elementu hosta* , która reprezentuje dokument. Aby uzyskać więcej informacji, zobacz [dokument element hosta](../vsto/document-host-item.md).

### <a name="design-mode-vs-runtime-mode"></a>Tryb projektowania a tryb środowiska uruchomieniowego
 Gdy dokument jest otwarty w środowisku programu Visual Studio, jest zawsze w *trybie projektowania*. Niektóre zadania, takie jak przeciągnięcie formantu hosta na powierzchnię dokumentu, można wykonywać tylko w trybie projektowania.

 Aby wyświetlić dokument w *trybie środowiska uruchomieniowego*, należy otworzyć aplikację i dokument poza programem Visual Studio. Można również skompilować i uruchomić projekt. Wtedy dokument i aplikacja będą automatycznie otwierane poza środowiskiem Visual Studio.

## <a name="code-editor"></a>Edytor kodu
 Edytor kodu umożliwia wyświetlanie i modyfikowanie widocznych plików kodu w rozwiązaniu. Pliki te zawierają kod, który definiuje zachowanie rozwiązania.

 Aby uzyskać więcej informacji na temat edytora kodu, zobacz [pisanie kodu w edytorze kodu i tekstu](../ide/writing-code-in-the-code-and-text-editor.md). Aby uzyskać więcej informacji na temat pisania kodu w projektach pakietu Office, zobacz [pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).

## <a name="properties-window"></a>Okno właściwości
 W oknie **Właściwości** są wyświetlane właściwości elementów projektu, które są wybrane w **Eksplorator rozwiązań** i dla elementów interfejsu użytkownika wybranych w projektancie, takich jak formanty czy dokument w projekcie na poziomie dokumentu. Niektóre właściwości są specyficzne dla aplikacji i dokumentu, a inne takie same we wszystkich projektach.

## <a name="data-sources-window"></a>Data Sources — Okno
 Możesz użyć okna **źródła danych** w projektach pakietu Office na poziomie dokumentu, aby przeciągnąć źródło danych do dokumentu i utworzyć formant, który jest powiązany ze źródłem danych. Aby uzyskać więcej informacji, zobacz [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też

- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Właściwości w projektach pakietu Office](../vsto/properties-in-office-projects.md)
