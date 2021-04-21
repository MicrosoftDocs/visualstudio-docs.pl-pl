---
title: Jak programowo dodawać kształty do dokumentu programu Visio
description: Dowiedz się, jak dodawać kształty do dokumentu Microsoft Office Visio, pobierania wzorców ze wzornika i upuszczania kształtów na aktywnej stronie.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f5eabd18ac915e6cc10ff05de3d13d0263fa1eee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828413"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Jak programowo dodawać kształty do dokumentu programu Visio
  Kształty można dodawać do dokumentu Microsoft Office Visio, pobierania wzorców ze wzornika i upuszczania kształtów na aktywnej stronie.

 Aby uzyskać więcej informacji, zobacz dokumentację referencyjną dotyczącąMicrosoft.Office.Interop.Visio.Doc[VBA. Dodaj](/office/vba/api/Visio.Documents.Add) metodę, [właściwość Microsoft.Office.Interop.Visio.Application.ActivePage](/office/vba/api/Visio.Application.ActivePage) i [metodę Microsoft.Office.Interop.Visio.Page.Drop.](/office/vba/api/Visio.Page.Drop)

## <a name="add-shapes-to-a-visio-document"></a>Dodawanie kształtów do dokumentu programu Visio

### <a name="to-add-shapes-to-a-visio-document"></a>Aby dodać kształty do dokumentu programu Visio

- Gdy dokument jest aktywny, pobierz wzorce z kolekcji Documents.Masters i upuść kształty w aktywnym dokumencie. Wzorzec można pobrać przy użyciu indeksu lub nazwy głównej.

     Poniższy przykład kodu tworzy pusty dokument programu Visio, a następnie otwiera go zadokowany wzornik **Podstawowe** kształty. Następnie kod pobiera kilka kształtów i porzuca je na aktywnej stronie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Omówienie modelu obiektów programu Visio](../vsto/visio-object-model-overview.md)
- [Praca z kształtami programu Visio](../vsto/working-with-visio-shapes.md)
- [Jak programowo kopiować i wklejać kształty w dokumencie programu Visio](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)
