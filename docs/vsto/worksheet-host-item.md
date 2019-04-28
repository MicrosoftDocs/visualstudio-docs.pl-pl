---
title: Element hosta arkusza
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e4a5287648d515d1aca340ab55d5f21b494610b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62814734"
---
# <a name="worksheet-host-item"></a>Element hosta arkusza
  <xref:Microsoft.Office.Tools.Excel.Worksheet> Hosta elementu to typ, który rozszerza <xref:Microsoft.Office.Interop.Excel.Worksheet> typu na podstawie podstawowego zestawu międzyoperacyjnego dla programu Excel. <xref:Microsoft.Office.Tools.Excel.Worksheet> Element hosta zawiera wszystkie właściwości, metody i zdarzenia jako <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu, ale również udostępnia dodatkowe zdarzenia i działa jako kontener dla formantów hosta i kontrolek formularzy Windows Forms.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 W projektach na poziomie dokumentu, można dodać <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta elementy do projektu w czasie projektowania. W projektach dodatku narzędzi VSTO dla programów, można wygenerować <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta elementy w czasie wykonywania.

## <a name="understand-worksheet-host-items-in-document-level-projects"></a>Omówienie elementów arkusza hosta w projektach na poziomie dokumentu
 Po utworzeniu projektu na poziomie dokumentu dla programu Excel, programu Visual Studio automatycznie tworzy trzy <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta elementy w projekcie. Domyślne nazwy arkuszy są `Sheet1`, `Sheet2`, i `Sheet3`. Jeśli tworzysz projektu, w oparciu o istniejący skoroszyt, liczba elementów hosta zależy od liczby arkuszy w skoroszycie.

 W ramach tych zajęć arkusza udzielić Ci dostępu do elementów członkowskich <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta do wykonywania podstawowych zadań w swojej dostosowania, takie jak modyfikowanie zawartości arkusza. W ramach tych zajęć umożliwia również dodawanie formantów do arkuszy. Łączenie różnych zestawów kontrolek i napisanie kodu, można powiązać formanty z danymi, zbiera informacje o użytkowniku i reagować na działania użytkownika. Aby uzyskać więcej informacji, zobacz [Program dostosowań poziomu dokumentu](../vsto/programming-document-level-customizations.md).

 Klas arkusza podania lokalizacji, w którym można zacząć pisać kod w projekcie. Ponieważ klasa oferuje wszystkie właściwości, metody i zdarzenia jako <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu podstawowego zestawu międzyoperacyjnego dla programu Excel, można również użyć tych klas dostępu do modelu obiektów programu Excel. Aby uzyskać więcej informacji, zobacz [model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).

 W projektach na poziomie dokumentu, możesz dodać dodatkowe <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta elementy do projektu w czasie projektowania, dodając nowy arkusz do skoroszytu w projektancie.

### <a name="rename-worksheets"></a>Zmiana nazwy arkuszy
 W projekcie na poziomie dokumentu można zmienić nazwy arkuszy w Projektancie Visual Studio, ale spowoduje to zmianę tylko nazwa wyświetlana arkusza. Nazwą programową nadal jest domyślna nazwa arkusza. Jeśli zmienisz nazwę arkusza w **właściwości** okna, nazwą programową zostanie zmieniony.

### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Ograniczenia element hosta arkusza w projektach na poziomie dokumentu
 Nie można utworzyć nowego <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta elementy w czasie wykonywania w projekcie na poziomie dokumentu. Jeśli tworzysz nowy arkusz programu Excel w czasie wykonywania, będą typu <xref:Microsoft.Office.Interop.Excel.Worksheet>. Ponieważ nie jest element hosta, nie może zawierać wszystkie formanty hosta lub kontrolek formularzy Windows Forms. Aby uzyskać więcej informacji na temat tworzenia dokumentów w czasie wykonywania, zobacz [jak: Programowe Dodawanie nowych arkuszy do skoroszytu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

## <a name="understand-worksheet-host-items-in-vsto-add-in-projects"></a>Omówienie elementów arkusza hosta w projektach dodatku narzędzi VSTO
 W projektach na poziomie aplikacji, można wygenerować <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta w czasie wykonywania dla dowolnego arkusza, która jest otwarta w programie Excel. Możesz użyć <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta na dodawanie formantów do arkusza skojarzone lub do obsługi zdarzeń, które nie są dostępne na <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektów.

 Aby wygenerować <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta, użyj `GetVstoObject` metody. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Zobacz także
- [Office development ― przykłady i przewodniki](../vsto/office-development-samples-and-walkthroughs.md)
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
- [Element hosta skoroszytu](../vsto/workbook-host-item.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
