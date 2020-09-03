---
title: Element hosta dokumentu
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ebea0c3a09d08741523deddce94def170d844202
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "71253706"
---
# <a name="document-host-item"></a>Element hosta dokumentu
  <xref:Microsoft.Office.Tools.Word.Document>Element hosta jest typem, który rozszerza <xref:Microsoft.Office.Interop.Word.Document> Typ z podstawowego zestawu międzyoperacyjnego dla programu Word. <xref:Microsoft.Office.Tools.Word.Document>Element hosta zawiera wszystkie te same właściwości, metody i zdarzenia co <xref:Microsoft.Office.Interop.Word.Document> obiekt, ale udostępnia także dodatkowe zdarzenia i działa jako kontener dla formantów hosta i formantów Windows Forms.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 W projektach na poziomie dokumentu istnieje domyślny <xref:Microsoft.Office.Tools.Word.Document> element hosta, który reprezentuje dokument w projekcie. W projektach dodatku VSTO można generować <xref:Microsoft.Office.Tools.Word.Document> elementy hosta w czasie wykonywania.

## <a name="understand-the-document-host-item-in-document-level-projects"></a>Zrozumienie elementu hosta dokumentu w projektach na poziomie dokumentu
 Aby uzyskać dostęp do dokumentu w projekcie, użyj `ThisDocument` klasy. Podczas tworzenia projektu na poziomie dokumentu program Visual Studio generuje `ThisDocument` klasę, która będzie stanowić łącze komunikacyjne między programem Word i kodem dostosowania. `ThisDocument`Klasa umożliwia dostęp do elementów członkowskich <xref:Microsoft.Office.Tools.Word.Document> elementu hosta w celu wykonywania podstawowych zadań w dostosowaniu, takich jak uruchamianie kodu, gdy dokument zostanie otwarty lub zamknięty. Można również użyć klasy, aby dodać kontrolki do dokumentu. Łącząc różne zestawy kontrolek i pisząc kod, można powiązać kontrolki z danymi, zbierać informacje od użytkownika i reagować na akcje użytkownika. Aby uzyskać więcej informacji, zobacz temat [programowe dostosowanie na poziomie dokumentu](../vsto/programming-document-level-customizations.md).

 `ThisDocument`Klasa zawiera lokalizację, w której można rozpocząć pisanie kodu w projekcie. Ponieważ Klasa zawiera wszystkie te same właściwości, metody i zdarzenia co <xref:Microsoft.Office.Interop.Word.Document> obiekt w podstawowym zestawie międzyoperacyjnym dla programu Word, można również użyć `ThisDocument` w celu uzyskania dostępu do modelu obiektów programu Word. Aby uzyskać więcej informacji, zobacz temat [Omówienie modelu obiektów programu Word](../vsto/word-object-model-overview.md).

### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Ograniczenia elementu hosta dokumentu w projektach na poziomie dokumentu
 Projekt na poziomie dokumentu może zawierać tylko jeden <xref:Microsoft.Office.Tools.Word.Document> element hosta (to jest `ThisDocument` Klasa). Nie można dodać nowych <xref:Microsoft.Office.Tools.Word.Document> elementów hosta do projektu w czasie projektowania i nie można utworzyć nowych <xref:Microsoft.Office.Tools.Word.Document> elementów hosta w czasie wykonywania na podstawie dostosowania na poziomie dokumentu.

 Jeśli tworzysz nowy dokument programu Word w czasie wykonywania, będzie on typem <xref:Microsoft.Office.Interop.Word.Document> . Ponieważ nie jest elementem hosta, nie może zawierać żadnych formantów hosta ani formantów Windows Forms. Aby uzyskać więcej informacji na temat tworzenia dokumentów w czasie wykonywania, zobacz [How to: programowe tworzenie nowych dokumentów](../vsto/how-to-programmatically-create-new-documents.md).

## <a name="understand-document-host-items-in-application-level-projects"></a>Zrozumienie elementów hosta dokumentu w projektach na poziomie aplikacji
 W projektach dodatku VSTO można wygenerować <xref:Microsoft.Office.Tools.Word.Document> element hosta w czasie wykonywania dla każdego dokumentu otwartego w programie Word. Możesz użyć <xref:Microsoft.Office.Tools.Word.Document> elementu hosta, aby dodać kontrolki do skojarzonego dokumentu lub obsłużyć zdarzenia, które nie są dostępne w <xref:Microsoft.Office.Interop.Word.Document> obiektach.

 Aby wygenerować <xref:Microsoft.Office.Tools.Word.Document> element hosta, użyj `GetVstoObject` metody. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Zobacz też
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Model obiektów programu Word — omówienie](../vsto/word-object-model-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
