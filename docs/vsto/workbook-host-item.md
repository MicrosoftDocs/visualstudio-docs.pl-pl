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
ms.openlocfilehash: 797f1a55ec7632114e411bf0ba08e7f4e0cc146e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255086"
---
# <a name="workbook-host-item"></a>Element hosta skoroszytu
  <xref:Microsoft.Office.Tools.Excel.Workbook>Element hosta jest typem, który rozszerza <xref:Microsoft.Office.Interop.Excel.Workbook> Typ z podstawowego zestawu międzyoperacyjnego dla programu Excel. <xref:Microsoft.Office.Tools.Excel.Workbook>Element hosta zawiera wszystkie te same właściwości, metody i zdarzenia co <xref:Microsoft.Office.Interop.Excel.Workbook> obiekt, ale udostępnia także dodatkowe funkcje.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 W projektach na poziomie dokumentu istnieje domyślny <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta, który reprezentuje skoroszyt w projekcie. W projektach dodatku VSTO można generować <xref:Microsoft.Office.Tools.Excel.Workbook> elementy hosta w czasie wykonywania.

## <a name="understand-the-workbook-host-item-in-document-level-projects"></a>Zrozumienie elementu hosta skoroszytu w projektach na poziomie dokumentu
 Aby uzyskać dostęp do skoroszytu w projekcie, użyj `ThisWorkbook` klasy. `ThisWorkbook`Klasa umożliwia dostęp do elementów członkowskich <xref:Microsoft.Office.Tools.Excel.Workbook> elementu hosta w celu wykonywania podstawowych zadań w dostosowaniu, takich jak uruchamianie kodu, gdy skoroszyt zostanie otwarty lub zamknięty. Aby uzyskać więcej informacji, zobacz temat [programowe dostosowanie na poziomie dokumentu](../vsto/programming-document-level-customizations.md).

 `ThisWorkbook`Klasa zawiera lokalizację, w której można rozpocząć pisanie kodu w projekcie. Ponieważ Klasa zawiera wszystkie te same właściwości, metody i zdarzenia co <xref:Microsoft.Office.Interop.Excel.Workbook> obiekt w podstawowym zestawie międzyoperacyjnym dla programu Excel, można również użyć `ThisWorkbook` w celu uzyskania dostępu do modelu obiektów programu Excel. Aby uzyskać więcej informacji, zobacz [model obiektów programu Excel — Omówienie](../vsto/excel-object-model-overview.md).

 Kliknij dwukrotnie element projektu **ThisWorkbook** w **Eksplorator rozwiązań** , aby wyświetlić projektanta skoroszytów i wyświetlić właściwości i zdarzenia skoroszytu w oknie **Właściwości** .

### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>Ograniczenia elementu hosta skoroszytu w projektach na poziomie dokumentu
 Projekt na poziomie dokumentu może zawierać tylko jeden <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta (to jest `ThisWorkbook` Klasa). Nie można dodać nowych <xref:Microsoft.Office.Tools.Excel.Workbook> elementów hosta do projektu w czasie projektowania i nie można utworzyć nowych <xref:Microsoft.Office.Tools.Excel.Workbook> elementów hosta w czasie wykonywania na podstawie dostosowania na poziomie dokumentu.

 Jeśli tworzysz nowy skoroszyt programu Excel w czasie wykonywania, będzie on miał typ <xref:Microsoft.Office.Interop.Excel.Workbook> . Ponieważ nie jest elementem hosta, nie może zawierać żadnych formantów hosta ani formantów Windows Forms. Aby uzyskać więcej informacji na temat tworzenia skoroszytów w czasie wykonywania, zobacz [How to: programowe tworzenie nowych skoroszytów](../vsto/how-to-programmatically-create-new-workbooks.md).

 <xref:Microsoft.Office.Tools.Excel.Workbook>Element hosta nie działa jako kontener dla kontrolek hosta. W związku z tym nie można dodać żadnych widocznych kontrolek do skoroszytu, ale można dodać składniki, takie jak <xref:System.Data.DataSet> , tak aby składniki mogły być współużytkowane przez wszystkie arkusze. W projekcie na poziomie dokumentu składniki dostępne dla skoroszytu znajdują się na karcie **składnika** , na karcie **dane** i na karcie **wszystkie Windows Forms** w **przyborniku**.

> [!NOTE]
> Narzędzia programistyczne pakietu Office w programie Visual Studio nie obsługują skoroszytów udostępnionych.

## <a name="understand-workbook-host-items-in-vsto-add-in-projects"></a>Zrozumienie elementów hosta skoroszytów w projektach dodatku narzędzi VSTO
 W projektach dodatku VSTO można wygenerować <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta w czasie wykonywania dla każdego skoroszytu otwartego w programie Excel. Aby wygenerować <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta, użyj `GetVstoObject` metody. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Zobacz też
- [Przykłady i przewodniki dotyczące programowania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
