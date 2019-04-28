---
title: Element hosta skoroszytu
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel workbooks
- Workbook host items
- host items [Office development in Visual Studio], Workbook
- workbooks, Excel
- Workbook host items, events
- workbooks
- Excel [Office development in Visual Studio], workbooks
- workbooks, events
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e30ab9ce498134426caa35e0c3c9f9652f683535
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445533"
---
# <a name="workbook-host-item"></a>Element hosta skoroszytu
  <xref:Microsoft.Office.Tools.Excel.Workbook> Hosta elementu to typ, który rozszerza <xref:Microsoft.Office.Interop.Excel.Workbook> typu na podstawie podstawowego zestawu międzyoperacyjnego dla programu Excel. <xref:Microsoft.Office.Tools.Excel.Workbook> Element hosta zawiera wszystkie właściwości, metody i zdarzenia jako <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu, ale udostępnia także dodatkowe funkcje.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 W projektach na poziomie dokumentu jest domyślnie <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta, która reprezentuje skoroszyt w projekcie. W projektach dodatku narzędzi VSTO dla programów, można wygenerować <xref:Microsoft.Office.Tools.Excel.Workbook> hosta elementy w czasie wykonywania.

## <a name="understand-the-workbook-host-item-in-document-level-projects"></a>Zrozumienie element hosta skoroszytu w projektach na poziomie dokumentu
 Aby uzyskać dostęp do skoroszytu w projekcie, należy użyć `ThisWorkbook` klasy. `ThisWorkbook` Klasy daje dostęp do elementów członkowskich <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta do wykonywania podstawowych zadań w dostosowaniu, takie jak uruchamianie kodu, gdy otwarcie lub zamknięcie skoroszytu. Aby uzyskać więcej informacji, zobacz [Program dostosowań poziomu dokumentu](../vsto/programming-document-level-customizations.md).

 `ThisWorkbook` Klasa udostępnia miejsce, w którym można zacząć pisać kod w projekcie. Ponieważ klasa oferuje wszystkie właściwości, metody i zdarzenia jako <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu podstawowego zestawu międzyoperacyjnego dla programu Excel, można również użyć `ThisWorkbook` dostępu do modelu obiektów programu Excel. Aby uzyskać więcej informacji, zobacz [model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).

 Kliknij dwukrotnie **ThisWorkbook** elementu projektu w **Eksploratora rozwiązań** do wyświetlania Projektant skoroszytów i wyświetlić właściwości i zdarzenia skoroszytu w **właściwości**okna.

### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>Ograniczenia element hosta skoroszytu w projektach na poziomie dokumentu
 Projekt poziomu dokumentu może zawierać tylko jeden <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta (czyli `ThisWorkbook` klasy). Nie można dodać nowego <xref:Microsoft.Office.Tools.Excel.Workbook> hosta elementy do projektu w czasie projektowania i nie można utworzyć nowego <xref:Microsoft.Office.Tools.Excel.Workbook> hosta elementy w czasie wykonywania z dostosowywania poziomie dokumentu.

 Jeśli tworzysz nowy skoroszyt programu Excel w czasie wykonywania, będą typu <xref:Microsoft.Office.Interop.Excel.Workbook>. Ponieważ nie jest element hosta, nie może zawierać wszystkie formanty hosta lub kontrolek formularzy Windows Forms. Aby uzyskać więcej informacji o tworzeniu skoroszytów w czasie wykonywania, zobacz [jak: Programowe tworzenie nowych skoroszytów](../vsto/how-to-programmatically-create-new-workbooks.md).

 <xref:Microsoft.Office.Tools.Excel.Workbook> Element hosta nie działa jako kontener dla kontrolki hosta. Dlatego nie można dodać żadnych widocznych kontrolek w skoroszycie, ale można dodać składniki, takie jak <xref:System.Data.DataSet>, dzięki czemu składniki mogą być współużytkowane przez wszystkie arkusze. W projekcie na poziomie dokumentu, następujące składniki do skoroszytu można znaleźć w **składnika** karcie **danych** karcie i **wszystkie formularze Windows** karcie  **Przybornik**.

> [!NOTE]
> Narzędzi programistycznych pakietu Office w programie Visual Studio nie obsługują skoroszytów udostępnionych.

## <a name="understand-workbook-host-items-in-vsto-add-in-projects"></a>Omówienie elementów hosta skoroszytu w projektach dodatku narzędzi VSTO
 W projektach dodatku narzędzi VSTO dla programów, można wygenerować <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta w czasie wykonywania dla dowolnego skoroszytu, która jest otwarta w programie Excel. Aby wygenerować <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta, użyj `GetVstoObject` metody. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Zobacz także
- [Office development ― przykłady i przewodniki](../vsto/office-development-samples-and-walkthroughs.md)
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
