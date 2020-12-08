---
title: Automatyzowanie programu Word za pomocą obiektów rozszerzonych
description: Dowiedz się, jak używać elementów hosta i kontrolek hosta w rozwiązaniach podczas opracowywania rozwiązań programu Word w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 39ac9d50d0f75f595568c66b02bda1c5ed46a3d6
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844455"
---
# <a name="automate-word-by-using-extended-objects"></a>Automatyzowanie programu Word za pomocą obiektów rozszerzonych
  Podczas opracowywania rozwiązań programu Word w programie Visual Studio można używać *elementów hosta* i *kontrolek hosta* w swoich rozwiązaniach. Są to obiekty, które rozszerzają niektóre często używane obiekty w modelu obiektów programu Word (czyli model obiektów, który jest udostępniany przez podstawowy zestaw międzyoperacyjny dla programu Word), taki <xref:Microsoft.Office.Interop.Word.Document> jak <xref:Microsoft.Office.Interop.Word.ContentControl> obiekty i. Obiekty rozszerzone zachowują się jak obiekty programu Word, na których się opierają, ale dodają do obiektów dodatkowe zdarzenia i możliwości powiązania danych.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Elementy hosta i formanty hosta są dostępne zarówno dla dodatków VSTO, jak i dostosowań na poziomie dokumentu, chociaż kontekst, w którym mogą być używane, różni się w zależności od typu rozwiązania. Aby uzyskać więcej informacji, zobacz [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md).

## <a name="document-host-item"></a>Element hosta dokumentu
 Projekty programu Word umożliwiają dostęp do <xref:Microsoft.Office.Tools.Word.Document> elementu hosta. <xref:Microsoft.Office.Tools.Word.Document>Element hosta działa jako kontener dla innych kontrolek, w tym formantów hosta i kontrolek Windows Forms, i utrzymuje informacje o kontrolkach na jego powierzchni. <xref:Microsoft.Office.Tools.Word.Document>Element hosta zapewnia również większość elementów członkowskich <xref:Microsoft.Office.Interop.Word.Document> , które są w klasie, która jest odpowiednią klasą w modelu obiektów programu Word.

 Aby uzyskać więcej informacji, zobacz [dokument element hosta](../vsto/document-host-item.md).

## <a name="word-host-controls"></a>formanty hosta programu Word
 Istnieje kilka kontrolek hosta dla programu Word, które ułatwiają tworzenie, organizowanie i automatyzowanie dokumentów. Większość ich funkcji obejmuje importowanie, prezentowanie i ochronę danych. Te kontrolki hosta zapewniają zdarzenia i możliwości powiązań danych, których odpowiedniki w modelu obiektów natywnego programu Word nie mają.

 W projektach na poziomie dokumentu można dodać dowolny formant hosta do dokumentu w czasie projektowania lub dodać kontrolki zawartości i kontrolki zakładki w czasie wykonywania. W projektach dodatku VSTO można dodać kontrolki zawartości i kontrolki zakładki do dowolnego otwartego dokumentu w czasie wykonywania.

 Aby uzyskać więcej informacji na temat kontrolek hosta, których można używać w projektach programu Word, zobacz następujące tematy:

- [Kontrolki zawartości](../vsto/content-controls.md)

- [Kontrolka zakładki](../vsto/bookmark-control.md)

- [XMLNode — formant](../vsto/xmlnode-control.md)

- [Formant XMLNodes](../vsto/xmlnodes-control.md)

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Instrukcje: Dodawanie kontrolek zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Instrukcje: Dodawanie formantów XMLNode do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Instrukcje: Dodawanie kontrolek XMLNodes do dokumentów programu Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Instrukcje: zmiana rozmiaru kontrolek zakładek](../vsto/how-to-resize-bookmark-controls.md)
- [Przewodnik: Tworzenie szablonu za pomocą kontrolek zawartości](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)
- [Wskazówki: powiązywanie kontrolek zawartości z niestandardowymi częściami XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)
- [Przewodnik: Tworzenie menu skrótów dla zakładek](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Rozwiązania programu Word](../vsto/word-solutions.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
