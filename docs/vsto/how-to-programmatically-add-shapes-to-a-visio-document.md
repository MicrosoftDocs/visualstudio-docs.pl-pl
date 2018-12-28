---
title: 'Instrukcje: Programowe Dodawanie kształtów do dokumentu programu Visio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 09bc0ca6d0c84f87a1a1621c9028c3a147373bc5
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802666"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Instrukcje: Programowe Dodawanie kształtów do dokumentu programu Visio
  Pobieranie serwerów głównych ze wzornika i upuszczając kształtów na aktywnej stronie, można dodać kształtów do dokumentu programu Microsoft Visio pakietu Office.  
  
 Aby uzyskać więcej informacji, zobacz dokumentację referencyjną VBA [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) metody [Microsoft.Office.Interop.Visio.Application.ActivePage](/office/vba/api/Visio.Application.ActivePage) właściwości i [Microsoft.Office.Interop.Visio.Page.Drop](/office/vba/api/Visio.Page.Drop) metody.  
  
## <a name="add-shapes-to-a-visio-document"></a>Dodawanie kształtów do dokumentu programu Visio  
  
### <a name="to-add-shapes-to-a-visio-document"></a>Dodawanie kształtów do dokumentu programu Visio  
  
-   Od aktywnego dokumentu Pobierz wzorce z kolekcji Documents.Masters i upuść kształty w aktywnym dokumencie. Wzorzec można pobrać przy użyciu indeksu lub wzorca nazwy.  
  
     Poniższy przykład kodu tworzy pusty dokument programu Visio, a następnie go otwiera **kształtów podstawowych** wzornika zadokowany. Kod następnie pobiera kilku kształtów i umieszcza je na aktywnej stronie.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwiązania programu Visio](../vsto/visio-solutions.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Praca z dokumentami Visio shapes](../vsto/working-with-visio-shapes.md)   
 [Instrukcje: Programowe kopiowanie i wklejanie kształtów w dokumencie programu Visio](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  