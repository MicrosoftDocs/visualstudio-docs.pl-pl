---
title: Programistyczne kopiowanie i wklejanie kształtów w dokumencie programu Visio
description: Dowiedz się, jak można programistycznie kopiować kształty na jednej stronie dokumentu i wklejać je do nowej strony w tym samym dokumencie.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 90a065ec98da440af6e52a191e11f4371575c2d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964228"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Instrukcje: Programowane kopiowanie i wklejanie kształtów w dokumencie programu Visio
  Można programowo skopiować kształty na jednej stronie dokumentu i wkleić je do nowej strony w tym samym dokumencie. Możesz wkleić je do lokalizacji domyślnej (centrum aktywnego okna) lub do tych samych lokalizacji współrzędnych, które znajdowały się na oryginalnej stronie.

## <a name="copy-and-paste-shapes"></a>Kopiowanie i wklejanie kształtów
 Aby uzyskać szczegółowe informacje na temat modelu obiektów, zobacz dokumentację języka VBA dla elementu [Microsoft. Office. Interop. Visio. Shape. DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft. Office. Interop](/office/vba/api/Visio.Shape.DrawOval), Visio. Shape. DrawOval, [Microsoft. Office.](/office/vba/api/Visio.Shape.Copy)Interop. Applications. Shape. Copy i Microsoft. Office. Interop. Visio. [Shape. Past](/office/vba/api/Visio.Shape.Paste) oraz flagę [Microsoft. Office.](/office/vba/api/Visio.viscutcopypastecodes) Interop. Visio. VisCutCopyPasteCodes. visCopyPasteNormal.

### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Aby skopiować kształty do środka innej strony

- W poniższym przykładzie pokazano, jak skopiować kształty z pierwszej strony i wkleić je do środka drugiej strony.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]

## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Kopiowanie i wklejanie kształtów z tymi samymi położeniami
 Aby uzyskać szczegółowe informacje na temat modelu obiektów, zobacz dokumentację języka VBA dla elementu [Microsoft. Office. Interop. Visio. Shape. DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft. Office. Interop](/office/vba/api/Visio.Shape.DrawOval), Visio. Shape. DrawOval, [Microsoft. Office.](/office/vba/api/Visio.Shape.Copy)Interop. Applications. Shape. Copy i Microsoft. Office. Interop. Visio. [Shape. Past](/office/vba/api/Visio.Shape.Paste) oraz flagę [Microsoft. Office.](/office/vba/api/Visio.viscutcopypastecodes) Interop. Visio. VisCutCopyPasteCodes. visCopyPasteNoTranslate.

 Jeśli konieczne jest kontrolowanie formatu wklejanych informacji i (opcjonalnie) nawiązanie linku do pliku źródłowego (na przykład Microsoft Office dokumentu programu Word), należy użyć metody PasteSpecial.

### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Aby skopiować kształty i lokalizacje kształtów na inną stronę

- W poniższym przykładzie pokazano, jak skopiować kształty z pierwszej strony i wkleić je do drugiej strony z oryginalnymi lokalizacjami współrzędnych.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Model obiektów programu Visio — Omówienie](../vsto/visio-object-model-overview.md)
- [Współpraca z kształtami programu Visio](../vsto/working-with-visio-shapes.md)
- [Instrukcje: Programowane dodawanie kształtów do dokumentu programu Visio](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)
