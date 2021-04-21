---
title: 'How to: Programowe przywracanie wyborów po wyszukiwaniu'
description: Dowiedz się, jak za pomocą Visual Studio programowo przywrócić wybrane opcje po wyszukiwaniu w dokumencie programu Microsoft Word.
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
ms.openlocfilehash: 2a9f804e218ec9dfa0e0550501dec0c1aa8388ff
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824019"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>How to: Programowe przywracanie wyborów po wyszukiwaniu
  Jeśli znajdziesz i zastąpisz tekst w dokumencie, możesz przywrócić oryginalny wybór użytkownika po zakończeniu wyszukiwania.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Kod w przykładowej procedurze korzysta z dwóch <xref:Microsoft.Office.Interop.Word.Range> obiektów. Jeden przechowuje bieżący , a jeden ustawia cały dokument do <xref:Microsoft.Office.Interop.Word.Selection> użycia jako zakres wyszukiwania.

## <a name="to-restore-the-users-original-selection-after-a-search"></a>Aby przywrócić oryginalny wybór użytkownika po wyszukiwaniu

1. Utwórz <xref:Microsoft.Office.Interop.Word.Range> obiekty dla dokumentu i bieżące zaznaczenie.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet83":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet83":::

2. Wykonaj operację wyszukiwania i zastępowania.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet84":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet84":::

3. Wybierz zakres startowy, aby przywrócić oryginalny wybór użytkownika.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet85":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet85":::

   W poniższym przykładzie pokazano kompletną metodę .

## <a name="example"></a>Przykład
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet82":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet82":::

## <a name="see-also"></a>Zobacz także
- [How to: Programowe wyszukiwanie i zastępowanie tekstu w dokumentach](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Jak programowo ustawić opcje wyszukiwania w programie Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [How to: Programmatically loop through found items in documents](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
