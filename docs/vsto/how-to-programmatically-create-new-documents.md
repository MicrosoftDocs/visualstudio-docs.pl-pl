---
title: Jak programowo tworzyć nowe dokumenty
description: Dowiedz się, jak programowo tworzyć nowe dokumenty w programie Microsoft Word przy użyciu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4ba9aed0194804354af62fb1fd582b8ea12ac6b1
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825189"
---
# <a name="how-to-programmatically-create-new-documents"></a>Jak programowo tworzyć nowe dokumenty
  Podczas programowego tworzenia dokumentu nowy dokument jest obiektem <xref:Microsoft.Office.Interop.Word.Document> natywnym. Ten obiekt nie ma dodatkowych zdarzeń i możliwości powiązania danych elementu <xref:Microsoft.Office.Tools.Word.Document> hosta. Aby uzyskać więcej informacji, zobacz [Programowe ograniczenia elementów hosta i kontrolek hosta.](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Podczas opracowywania projektu na poziomie dokumentu nie można programowo dodawać elementów hosta <xref:Microsoft.Office.Tools.Word.Document> do projektu. W projekcie dodatku VSTO można przekonwertować dowolny obiekt na <xref:Microsoft.Office.Interop.Word.Document> element hosta w czasie <xref:Microsoft.Office.Tools.Word.Document> uruchamiania. Aby uzyskać więcej informacji, zobacz [Extend Word documents and Excel workbooks in VSTO Add-ins at run time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)(Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania).

## <a name="to-create-a-new-document-based-on-the-normal-template"></a>Aby utworzyć nowy dokument na podstawie szablonu Normalnego

- Użyj <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Documents> kolekcji , aby utworzyć nowy dokument na podstawie szablonu Normalny. Aby użyć tego przykładu kodu, uruchom go z `ThisDocument` klasy lub `ThisAddIn` w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet1":::

## <a name="use-custom-templates"></a>Używanie szablonów niestandardowych
 Metoda ma opcjonalny argument Template w celu utworzenia nowego dokumentu na podstawie szablonu <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> innego niż szablon Normalny.  Należy podać nazwę pliku i w pełni kwalifikowaną ścieżkę szablonu.

### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Aby utworzyć nowy dokument na podstawie szablonu niestandardowego

- Wywołaj <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metodę <xref:Microsoft.Office.Interop.Word.Documents> kolekcji i określ ścieżkę do szablonu. Aby użyć tego przykładu kodu, uruchom go z `ThisDocument` klasy lub `ThisAddIn` w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet2":::

## <a name="see-also"></a>Zobacz też
- [Pisano: Programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Programowe ograniczenia elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
