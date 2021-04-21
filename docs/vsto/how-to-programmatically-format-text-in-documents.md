---
title: Jak programowo sformatować tekst w dokumentach
description: Dowiedz się, jak używać obiektu Range do programowego formatowania tekstu w dokumencie programu Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b91486c193b7b3fdba3b4c5cbbe86f58ffa7f06c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827880"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Jak programowo sformatować tekst w dokumentach
  Obiektu można użyć <xref:Microsoft.Office.Interop.Word.Range> do formatowania tekstu w dokumencie Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Poniższy przykład wybiera pierwszy akapit w dokumencie i zmienia rozmiar czcionki, nazwę czcionki i wyrównanie. Następnie wybiera zakres i wyświetla okno komunikatu do wstrzymania przed wykonaniem następnej sekcji kodu. W następnej sekcji trzykrotnie wywołuje się metodę Undo elementu hosta (w celu dostosowania na poziomie dokumentu) lub klasy (dla dodatku <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Interop.Word.Document> VSTO). Stosuje ona styl normalnego wcięcia i wyświetla okno komunikatu w celu wstrzymania kodu. Następnie kod wywołuje metodę <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> raz i wyświetla okno komunikatu.

## <a name="document-level-customization-example"></a>Przykład dostosowywania na poziomie dokumentu

### <a name="to-format-text-using-a-document-level-customization"></a>Aby sformatować tekst przy użyciu dostosowania na poziomie dokumentu

1. Poniższy przykład może służyć do dostosowywania na poziomie dokumentu. Aby użyć tego kodu, uruchom go z `ThisDocument` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet62":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet62":::

## <a name="vsto-add-in-example"></a>Przykład dodatku VSTO

### <a name="to-format-text-using-a-vsto-add-in"></a>Aby sformatować tekst przy użyciu dodatku VSTO

1. W poniższym przykładzie można użyć dodatku VSTO. W tym przykładzie jest używany aktywny dokument. Aby użyć tego kodu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet62":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet62":::

## <a name="see-also"></a>Zobacz też
- [Jak programowo definiować i wybierać zakresy w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [How to: Programowe wstawianie tekstu do dokumentów programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [How to: Programowe wyszukiwanie i zastępowanie tekstu w dokumentach](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
