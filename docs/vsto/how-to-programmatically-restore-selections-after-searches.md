---
title: 'Instrukcje: Programowane przywracanie zaznaczenia po wyszukiwaniu'
description: Dowiedz się, jak używać programu Visual Studio do programistycznego przywracania wybranych elementów po przeszukiwaniu w dokumencie programu Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 493f736ce899a0d90332418ca37a5b2825dd2d7b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897512"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Instrukcje: Programowane przywracanie zaznaczenia po wyszukiwaniu
  Jeśli odnajdziesz i zastąpisz tekst w dokumencie, możesz chcieć przywrócić oryginalny wybór użytkownika po zakończeniu wyszukiwania.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Kod w przykładowej procedurze używa dwóch <xref:Microsoft.Office.Interop.Word.Range> obiektów. Jeden z nich przechowuje bieżącą <xref:Microsoft.Office.Interop.Word.Selection> , a jeden ustawia cały dokument do użycia jako zakres wyszukiwania.

## <a name="to-restore-the-users-original-selection-after-a-search"></a>Aby przywrócić pierwotny wybór użytkownika po wyszukiwaniu

1. Utwórz <xref:Microsoft.Office.Interop.Word.Range> obiekty dla dokumentu i bieżące zaznaczenie.

    [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
    [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]

2. Wykonaj operację wyszukiwania i zamieniania.

    [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
    [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]

3. Wybierz zakres początkowy, aby przywrócić oryginalny wybór użytkownika.

    [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
    [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]

   Poniższy przykład przedstawia metodę Complete.

## <a name="example"></a>Przykład
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: programowe wyszukiwanie i zastępowanie tekstu w dokumentach](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Instrukcje: Programowane Ustawianie opcji wyszukiwania w programie Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Instrukcje: programowe przechodzenie w pętli poprzez znalezione elementy w dokumentach](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
