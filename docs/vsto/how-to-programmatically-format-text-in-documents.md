---
title: 'Instrukcje: Programowe formatowanie tekstu w dokumentach'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 66ca84d2246a3335aa3a1bbc0900ca6f48f59f01
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630694"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Instrukcje: Programowe formatowanie tekstu w dokumentach
  Możesz użyć <xref:Microsoft.Office.Interop.Word.Range> obiektu, aby sformatować tekst w dokumencie programu Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Poniższy przykład wybiera pierwszy akapit w dokumencie i zmienia rozmiar czcionki, nazwa czcionki oraz wyrównanie. Następnie wybiera zakres i wyświetla okno komunikatu, aby wstrzymać przed wykonaniem następnej sekcji kodu. Następna sekcja wywołuje metodę cofania <xref:Microsoft.Office.Tools.Word.Document> element hosta (dla dostosowania poziomu dokumentu) lub <xref:Microsoft.Office.Interop.Word.Document> klasy (w przypadku dodatku narzędzi VSTO) trzy razy. On zastosowany styl normalne wcięcie i wyświetla okno komunikatu, aby wstrzymać kodu. Następnie kod wywołuje <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> raz, metody i wyświetla okno komunikatu.

## <a name="document-level-customization-example"></a>Przykład dostosowania na poziomie dokumentu

### <a name="to-format-text-using-a-document-level-customization"></a>Aby sformatować tekst przy użyciu dostosowywania poziomie dokumentu

1.  Poniższy przykład może służyć w dostosowaniu na poziomie dokumentu. Aby użyć tego kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]

## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO

### <a name="to-format-text-using-a-vsto-add-in"></a>Aby sformatować tekst przy użyciu dodatku narzędzi VSTO

1.  Poniższy przykład może służyć w dodatku VSTO. W tym przykładzie użyto aktywnego dokumentu. Aby użyć tego kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Instrukcje: Programowe Wstawianie tekstu w dokumentach programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Instrukcje: Programowe wyszukiwanie i zastępowanie tekstu w dokumentach](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
