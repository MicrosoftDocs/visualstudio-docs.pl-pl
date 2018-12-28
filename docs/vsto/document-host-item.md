---
title: Element hosta dokumentu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: ea85d0f0f9435795abf75973373e6f0ae7e3a949
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647355"
---
# <a name="document-host-item"></a>Element hosta dokumentu
  <xref:Microsoft.Office.Tools.Word.Document> Hosta elementu to typ, który rozszerza <xref:Microsoft.Office.Interop.Word.Document> typu na podstawie podstawowego zestawu międzyoperacyjnego dla programu Word. <xref:Microsoft.Office.Tools.Word.Document> Element hosta zawiera wszystkie właściwości, metody i zdarzenia jako <xref:Microsoft.Office.Interop.Word.Document> obiektu, ale również udostępnia dodatkowe zdarzenia i działa jako kontener dla formantów hosta i kontrolek formularzy Windows Forms.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 W projektach na poziomie dokumentu jest domyślnie <xref:Microsoft.Office.Tools.Word.Document> element hosta, która reprezentuje dokument w projekcie. W projektach dodatku narzędzi VSTO dla programów, można wygenerować <xref:Microsoft.Office.Tools.Word.Document> hosta elementy w czasie wykonywania.  
  
## <a name="understand-the-document-host-item-in-document-level-projects"></a>Zrozumienie element hosta dokumentu w projektach na poziomie dokumentu  
 Aby uzyskać dostęp do dokumentów w swoim projekcie, należy użyć `ThisDocument` klasy. Podczas tworzenia projektów dokumentów programu Visual Studio generuje `ThisDocument` klasa ma pełnić rolę łącza komunikacyjnego między programów Word i dostosowywania kodu. `ThisDocument` Klasy daje dostęp do elementów członkowskich <xref:Microsoft.Office.Tools.Word.Document> element hosta do wykonywania podstawowych zadań w dostosowaniu, takie jak uruchomienie kodu po otwarciu lub zamknięciu dokumentu. Klasa umożliwia również dodawanie formantów do dokumentu. Łączenie różnych zestawów kontrolek i napisanie kodu, można powiązać formanty z danymi, zbiera informacje o użytkowniku i reagować na działania użytkownika. Aby uzyskać więcej informacji, zobacz [Program dostosowań poziomu dokumentu](../vsto/programming-document-level-customizations.md).  
  
 `ThisDocument` Klasa udostępnia miejsce, w którym można zacząć pisać kod w projekcie. Ponieważ klasa oferuje wszystkie właściwości, metody i zdarzenia jako <xref:Microsoft.Office.Interop.Word.Document> obiektu podstawowego zestawu międzyoperacyjnego dla programu Word, możesz również użyć `ThisDocument` dostępu do modelu obiektów programu Word. Aby uzyskać więcej informacji, zobacz [model obiektu Word — omówienie](../vsto/word-object-model-overview.md).  
  
### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Ograniczenia element hosta dokumentu w projektach na poziomie dokumentu  
 Projekt poziomu dokumentu może zawierać tylko jeden <xref:Microsoft.Office.Tools.Word.Document> element hosta (czyli `ThisDocument` klasy). Nie można dodać nowego <xref:Microsoft.Office.Tools.Word.Document> hosta elementy do projektu w czasie projektowania i nie można utworzyć nowego <xref:Microsoft.Office.Tools.Word.Document> hosta elementy w czasie wykonywania z dostosowywania poziomie dokumentu.  
  
 Jeśli tworzysz nowy dokument programu Word w czasie wykonywania, będą typu <xref:Microsoft.Office.Interop.Word.Document>. Ponieważ nie jest element hosta, nie może zawierać wszystkie formanty hosta lub kontrolek formularzy Windows Forms. Aby uzyskać więcej informacji na temat tworzenia dokumentów w czasie wykonywania, zobacz [jak: Programowe tworzenie nowych dokumentów](../vsto/how-to-programmatically-create-new-documents.md).  
  
## <a name="understand-document-host-items-in-application-level-projects"></a>Omówienie elementów hosta dokumentu w projektach na poziomie aplikacji  
 W projektach dodatku narzędzi VSTO dla programów, można wygenerować <xref:Microsoft.Office.Tools.Word.Document> element hosta w czasie wykonywania dla dowolnego dokumentu, który jest otwarty w programie Word. Możesz użyć <xref:Microsoft.Office.Tools.Word.Document> element hosta, aby dodać formanty do skojarzonego dokumentu lub do obsługi zdarzeń, które nie są dostępne na <xref:Microsoft.Office.Interop.Word.Document> obiektów.  
  
 Aby wygenerować <xref:Microsoft.Office.Tools.Word.Document> element hosta, użyj `GetVstoObject` metody. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  