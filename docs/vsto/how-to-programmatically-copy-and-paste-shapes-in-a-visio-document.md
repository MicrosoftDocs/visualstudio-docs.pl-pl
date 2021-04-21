---
title: Programowe kopiowanie i wklejanie kształtów w dokumencie programu Visio
description: Dowiedz się, jak programowo kopiować kształty na jednej stronie dokumentu i wklejać je do nowej strony w tym samym dokumencie.
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
ms.openlocfilehash: b7cda46330967ef2b2b08db2109a030bbef8cace
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828556"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Jak programowo kopiować i wklejać kształty w dokumencie programu Visio
  Możesz programowo skopiować kształty na jednej stronie dokumentu i wkleić je na nowej stronie w tym samym dokumencie. Możesz wkleić je w domyślnej lokalizacji (w środku aktywnego okna) lub w tych samych lokalizacjach współrzędnych, które miały na oryginalnej stronie.

## <a name="copy-and-paste-shapes"></a>Kopiowanie i wklejanie kształtów
 Aby uzyskać szczegółowe informacje o modelu obiektów, zobacz dokumentację VBA dla metod [Microsoft.Office.Interop.Visio.Shape.DrawRectangle,](/office/vba/api/Visio.Shape.DrawRectangle) [Microsoft.Office.Interop.Visio.Shape.DrawOval,](/office/vba/api/Visio.Shape.DrawOval) [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)i [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) oraz [flagi Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal.](/office/vba/api/Visio.viscutcopypastecodes)

### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Aby skopiować kształty na środek innej strony

- W poniższym przykładzie pokazano, jak skopiować kształty z pierwszej strony i wkleić je w środku drugiej strony.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet14":::

## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Kopiowanie i wklejanie kształtów z tym samym położeniem
 Aby uzyskać szczegółowe informacje o modelu obiektów, zobacz dokumentację VBA dla metod [Microsoft.Office.Interop.Visio.Shape.DrawRectangle,](/office/vba/api/Visio.Shape.DrawRectangle) [Microsoft.Office.Interop.Visio.Shape.DrawOval,](/office/vba/api/Visio.Shape.DrawOval) [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)i [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) oraz [flagi Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate.](/office/vba/api/Visio.viscutcopypastecodes)

 Jeśli musisz kontrolować format wklejonych informacji i (opcjonalnie) ustanowić link do pliku źródłowego (na przykład dokumentu programu Microsoft Office Word), użyj metody PasteSpecial.

### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Aby skopiować kształty i lokalizacje kształtów na inną stronę

- W poniższym przykładzie pokazano, jak skopiować kształty z pierwszej strony i wkleić je do drugiej strony z ich oryginalnymi lokalizacjami współrzędnych.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet15":::

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Omówienie modelu obiektów programu Visio](../vsto/visio-object-model-overview.md)
- [Praca z kształtami programu Visio](../vsto/working-with-visio-shapes.md)
- [Jak programowo dodawać kształty do dokumentu programu Visio](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)
