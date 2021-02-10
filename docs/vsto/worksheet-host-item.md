---
title: Element hosta arkusza
description: Dowiedz się, że element hosta arkusza jest typem, który rozszerza typ arkusza z podstawowego zestawu międzyoperacyjnego dla programu Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host items [Office development in Visual Studio], Worksheet
- Excel [Office development in Visual Studio], worksheets
- Worksheet host items
- worksheets, events
- Worksheet host items, events
- Excel worksheets
- worksheets, Excel
- worksheets
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 12dc0823f1c7d1eb78867cb3529f955851f45b66
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955739"
---
# <a name="worksheet-host-item"></a>Element hosta arkusza
  <xref:Microsoft.Office.Tools.Excel.Worksheet>Element hosta jest typem, który rozszerza <xref:Microsoft.Office.Interop.Excel.Worksheet> Typ z podstawowego zestawu międzyoperacyjnego dla programu Excel. <xref:Microsoft.Office.Tools.Excel.Worksheet>Element hosta zawiera wszystkie te same właściwości, metody i zdarzenia co <xref:Microsoft.Office.Interop.Excel.Worksheet> obiekt, ale udostępnia także dodatkowe zdarzenia i działa jako kontener dla formantów hosta i formantów Windows Forms.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 W projektach na poziomie dokumentu można dodawać <xref:Microsoft.Office.Tools.Excel.Worksheet> elementy hosta do projektu w czasie projektowania. W projektach dodatku VSTO można generować <xref:Microsoft.Office.Tools.Excel.Worksheet> elementy hosta w czasie wykonywania.

## <a name="understand-worksheet-host-items-in-document-level-projects"></a>Zrozumienie elementów hosta arkusza w projektach na poziomie dokumentu
 Po utworzeniu projektu na poziomie dokumentu dla programu Excel program Visual Studio automatycznie tworzy trzy <xref:Microsoft.Office.Tools.Excel.Worksheet> elementy hosta w projekcie. Domyślne nazwy arkuszy to `Sheet1` , `Sheet2` , i `Sheet3` . W przypadku utworzenia projektu opartego na istniejącym skoroszycie liczba elementów hosta zależy od liczby arkuszy w skoroszycie.

 Te klasy arkuszy zapewniają dostęp do elementów członkowskich elementów <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta w celu wykonywania podstawowych zadań w dostosowaniu, takich jak modyfikowanie zawartości arkusza. Można również użyć tych klas do dodawania formantów do arkuszy. Łącząc różne zestawy kontrolek i pisząc kod, można powiązać kontrolki z danymi, zbierać informacje od użytkownika i reagować na akcje użytkownika. Aby uzyskać więcej informacji, zobacz temat [programowe dostosowanie na poziomie dokumentu](../vsto/programming-document-level-customizations.md).

 Klasy arkusza zapewniają lokalizację, w której można rozpocząć pisanie kodu w projekcie. Ponieważ Klasa zawiera wszystkie te same właściwości, metody i zdarzenia co <xref:Microsoft.Office.Interop.Excel.Worksheet> obiekt w podstawowym zestawie międzyoperacyjnym dla programu Excel, można także użyć tych klas do uzyskania dostępu do modelu obiektów programu Excel. Aby uzyskać więcej informacji, zobacz [model obiektów programu Excel — Omówienie](../vsto/excel-object-model-overview.md).

 W projektach na poziomie dokumentu można dodać kolejne <xref:Microsoft.Office.Tools.Excel.Worksheet> elementy hosta do projektu w czasie projektowania, dodając nowy arkusz do skoroszytu w projektancie.

### <a name="rename-worksheets"></a>Zmień nazwy arkuszy
 W projekcie na poziomie dokumentu można zmienić nazwy arkuszy w projektancie programu Visual Studio, ale tylko zmiana nazwy wyświetlanej arkusza. Nazwa programowa jest nadal domyślną nazwą arkusza. Jeśli zmienisz nazwę arkusza w oknie **Właściwości** , tylko nazwa programowa zostanie zmieniona.

### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Ograniczenia elementu hosta arkusza w projektach na poziomie dokumentu
 Nie można tworzyć nowych <xref:Microsoft.Office.Tools.Excel.Worksheet> elementów hosta w czasie wykonywania w projekcie na poziomie dokumentu. Jeśli tworzysz nowy arkusz programu Excel w czasie wykonywania, będzie on typem <xref:Microsoft.Office.Interop.Excel.Worksheet> . Ponieważ nie jest elementem hosta, nie może zawierać żadnych formantów hosta ani formantów Windows Forms. Aby uzyskać więcej informacji na temat tworzenia dokumentów w czasie wykonywania, zobacz [How to: programowe Dodawanie nowych arkuszy do skoroszytów](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

## <a name="understand-worksheet-host-items-in-vsto-add-in-projects"></a>Omówienie elementów hosta arkusza w projektach dodatku VSTO
 W projektach na poziomie aplikacji można wygenerować <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta w czasie wykonywania dla dowolnego arkusza, który jest otwarty w programie Excel. Możesz użyć <xref:Microsoft.Office.Tools.Excel.Worksheet> elementu hosta, aby dodać kontrolki do skojarzonego arkusza lub obsłużyć zdarzenia, które nie są dostępne w <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektach.

 Aby wygenerować <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta, użyj `GetVstoObject` metody. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Zobacz też
- [Przykłady i przewodniki dotyczące programowania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Element hosta skoroszytu](../vsto/workbook-host-item.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
