---
title: Automatyzowanie programu Word za pomocą obiektów rozszerzonych
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], automating
- extended objects [Office development in Visual Studio], Word
- automation [Office development in Visual Studio], Word
- host items [Office development in Visual Studio], Word
- automating Word
- controls [Office development in Visual Studio], Word host controls
- host controls, Word
- host controls [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8244aec25b0179c22e88f91b4577d2fa78c119f3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950150"
---
# <a name="automate-word-by-using-extended-objects"></a>Automatyzowanie programu Word za pomocą obiektów rozszerzonych
  Podczas opracowywania rozwiązań programu Word w programie Visual Studio, możesz użyć *hostować elementy* i *kontrolki hosta*s w posiadanych rozwiązaniach. Są to obiekty, które rozszerzają niektóre powszechnie używane obiekty w modelu obiektów programu Word (oznacza to, że model obiektu, który jest udostępniany przez podstawowy zestaw międzyoperacyjny dla programu Word), takie jak <xref:Microsoft.Office.Interop.Word.Document> i <xref:Microsoft.Office.Interop.Word.ContentControl> obiektów. Obiekty rozszerzone zachowują się jak obiekty programu Word, w których są one oparte na, ale dodają dodatkowe zdarzenia i możliwości wiązania danych do obiektów.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Elementów hosta i kontrolek hosta są dostępne zarówno w przypadku dodatków narzędzi VSTO dla programów, jak i dostosowań na poziomie dokumentu, ale kontekst, w którym mogą one być używane jest inna dla każdego typu rozwiązania. Aby uzyskać więcej informacji, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="document-host-item"></a>Element hosta dokumentu  
 Word projektów zapewniają dostęp do <xref:Microsoft.Office.Tools.Word.Document> element hosta. <xref:Microsoft.Office.Tools.Word.Document> Element hosta działa jako kontener dla innych kontrolek, łącznie z kontrolki hosta i kontrolek Windows Forms i utrzymuje informacji na temat formantów na powierzchni. <xref:Microsoft.Office.Tools.Word.Document> Element hosta zawiera także większość tych samych elementów członkowskich jako <xref:Microsoft.Office.Interop.Word.Document> klasy, która jest odpowiadającą klasę w modelu obiektów programu Word.  
  
 Aby uzyskać więcej informacji, zobacz [element hosta dokumentu](../vsto/document-host-item.md).  
  
## <a name="word-host-controls"></a>kontrolki hosta programu Word  
 Istnieje kilka hosta formantów dla programu Word, które ułatwiają tworzenie, organizowanie i automatyzowanie dokumentów. Większość ich funkcji obejmuje importowania, prezentowania i ochrony danych. Te kontrolki hosta zapewniają zdarzenia oraz funkcje wiązania danych, które nie mają ich odpowiedników w macierzystym modelu obiektów programu Word.  
  
 W projektach na poziomie dokumentu można dodać dowolną kontrolkę hosta do dokumentu w czasie projektowania lub można dodać kontrolki zawartości oraz zakładki, które znajdują się w czasie wykonywania. W projektach dodatku narzędzi VSTO można dodać formanty zawartości i formantów zakładek do dowolnego otwartego dokumentu w czasie wykonywania.  
  
 Aby uzyskać informacje o kontrolkach hosta, którego można używać w projektach programu Word zobacz następujące tematy:  
  
-   [Formanty zawartości](../vsto/content-controls.md)  
  
-   [BOOKMARK, kontrolka](../vsto/bookmark-control.md)  
  
-   [Formant XMLNode](../vsto/xmlnode-control.md)  
  
-   [Formant XMLNodes](../vsto/xmlnodes-control.md)  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Instrukcje: Dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Instrukcje: Dodawanie formantów XMLNode do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Instrukcje: Dodawanie formantów XMLNodes do dokumentów programu Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Instrukcje: Zmiana rozmiaru formantów zakładki](../vsto/how-to-resize-bookmark-controls.md)   
 [Przewodnik: Tworzenie szablonu za pomocą formantów zawartości](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Przewodnik: Powiązywanie kontrolek zawartości do niestandardowych części XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)   
 [Przewodnik: Tworzenie menu skrótów dla zakładek](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Rozwiązania programu Word](../vsto/word-solutions.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
