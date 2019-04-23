---
title: 'Instrukcje: Programowe Dodawanie kształtów do dokumentu programu Visio'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e172ff57fb784d6ae768dde1e705ef645b3f9a9c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117788"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Instrukcje: Programowe Dodawanie kształtów do dokumentu programu Visio
  Pobieranie serwerów głównych ze wzornika i upuszczając kształtów na aktywnej stronie, można dodać kształtów do dokumentu programu Microsoft Visio pakietu Office.

 Aby uzyskać więcej informacji, zobacz dokumentację referencyjną VBA [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) metody [Microsoft.Office.Interop.Visio.Application.ActivePage](/office/vba/api/Visio.Application.ActivePage) właściwości i [Microsoft.Office.Interop.Visio.Page.Drop](/office/vba/api/Visio.Page.Drop) metody.

## <a name="add-shapes-to-a-visio-document"></a>Dodawanie kształtów do dokumentu programu Visio

### <a name="to-add-shapes-to-a-visio-document"></a>Dodawanie kształtów do dokumentu programu Visio

- Od aktywnego dokumentu Pobierz wzorce z kolekcji Documents.Masters i upuść kształty w aktywnym dokumencie. Wzorzec można pobrać przy użyciu indeksu lub wzorca nazwy.

     Poniższy przykład kodu tworzy pusty dokument programu Visio, a następnie go otwiera **kształtów podstawowych** wzornika zadokowany. Kod następnie pobiera kilku kształtów i umieszcza je na aktywnej stronie.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>Zobacz także
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)
- [Praca z dokumentami Visio shapes](../vsto/working-with-visio-shapes.md)
- [Instrukcje: Programowe kopiowanie i wklejanie kształtów w dokumencie programu Visio](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)
