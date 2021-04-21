---
title: Jak programowo ukrywać tekst w dokumentach
description: Dowiedz się, jak ukryć tekst w dokumencie programu Microsoft Word, ustawiając właściwość Hidden czcionki dla określonego zakresu tekstu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 04ea6b56519656782a3e408892235fa177eef755
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826489"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Jak programowo ukrywać tekst w dokumentach
  Tekst w dokumencie można ukryć, ustawiając właściwość <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> obiektu dla określonego zakresu <xref:Microsoft.Office.Interop.Word.Range.Font%2A> tekstu.

 Na przykład można tymczasowo ukryć tekst w obrębie (w dostosowywaniu na poziomie dokumentu) lub (w dodatku VSTO) przed wysłaniem dokumentu <xref:Microsoft.Office.Tools.Word.Bookmark> <xref:Microsoft.Office.Interop.Word.Bookmark> do drukarki.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Aby ukryć tekst w kontrolce Zakładka podczas drukowania dokumentu

1. Utwórz procedurę ukrywania całego tekstu w określonym zakresie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet105":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet105":::

2. Utwórz procedurę, która odkryje cały tekst w określonym zakresie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet106":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet106":::

3. Przekaż zakres zakładki do metody , wydrukuj dokument, a następnie przekaż ten `HideText` sam zakres do metody `UnhideText` .

     Poniższy przykład kodu może służyć do dostosowywania na poziomie dokumentu. Aby użyć tego przykładu, uruchom go z `ThisDocument` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet107":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet107":::

     Poniższy przykład kodu może być używany w dodatku VSTO. W tym przykładzie jest używany aktywny dokument. Aby użyć przykładu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet107":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet107":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 W tym przykładzie kodu przyjęto założenie, że dokument zawiera kontrolkę (w dostosowywaniu na poziomie dokumentu) lub kontrolkę (w dodatku <xref:Microsoft.Office.Tools.Word.Bookmark> <xref:Microsoft.Office.Interop.Word.Bookmark> VSTO) o nazwie `bookmark1` .

## <a name="see-also"></a>Zobacz też
- [Jak programowo drukować dokumenty](../vsto/how-to-programmatically-print-documents.md)
- [Jak programowo definiować i wybierać zakresy w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [How to: Programowe resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Jak programowo zaktualizować tekst zakładki](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
