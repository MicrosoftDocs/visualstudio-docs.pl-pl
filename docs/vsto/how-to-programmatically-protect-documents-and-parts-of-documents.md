---
title: Programowe zabezpieczanie dokumentów i ich części
description: Dowiedz się, jak dodać ochronę do dokumentów programu Microsoft Word, aby uniemożliwić użytkownikom edytowanie dokumentu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af3cc1d9c34bf0d6dc503ca2aabe35de5848265c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827607"
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Jak programowo chronić dokumenty i ich części
  Możesz dodać ochronę do dokumentów programu Microsoft Office Word, aby uniemożliwić użytkownikom edytowanie dokumentu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Niektóre obszary dokumentu można również oznaczyć jako wyjątki, aby określoni użytkownicy mogą edytować tylko te obszary dokumentu. Na przykład możesz chcieć chronić cały dokument z wyjątkiem konkretnej zakładki. Opcjonalnie możesz dodać hasło, aby użytkownicy nie byli w stanie usunąć ochrony dokumentów, chyba że znają hasło.

> [!NOTE]
> Poniższy przykład nie korzysta z ochrony hasłem; Warto jednak rozważyć użycie hasła podczas dodawania ochrony dokumentów. Aby uzyskać więcej informacji, zobacz przykład funkcji ochrony dokumentów w [przykładach i przewodnikach](../vsto/office-development-samples-and-walkthroughs.md)dotyczących rozwoju pakietu Office.

 Do ochrony części dokumentów można również używać kontrolek zawartości. Aby uzyskać więcej informacji, [zobacz Jak chronić części dokumentów za pomocą kontrolek zawartości.](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)

## <a name="protect-a-document-that-is-part-of-a-document-level-customization"></a>Ochrona dokumentu, który jest częścią dostosowania na poziomie dokumentu

### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Aby chronić dokument, który jest częścią dostosowania na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> metodę klasy w `ThisDocument` projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet111":::

### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Aby wykluczyć kontrolkę zakładki z ochrony dokumentów

1. Chroń cały dokument przy użyciu <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> metody .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet111":::

2. `Bookmark1`Wyklucz z ochrony dokumentów.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet112":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet112":::

### <a name="compile-the-code"></a>Kompilowanie kodu
 Aby użyć tych przykładów kodu, uruchom je z `ThisDocument` klasy w projekcie. W tych przykładach kodu założono, że masz istniejącą <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę o nazwie `Bookmark1` w dokumencie, w którym ten kod jest wyświetlany.

## <a name="protect-a-document-by-using-a-vsto-add-in"></a>Ochrona dokumentu za pomocą dodatku VSTO

### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>Aby chronić dokument przy użyciu dodatku VSTO na poziomie aplikacji

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> metodę metody , którą chcesz <xref:Microsoft.Office.Interop.Word.Document> chronić.

     Poniższy przykład kodu chroni aktywny dokument. Aby użyć tego przykładu kodu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet111":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet111":::

## <a name="see-also"></a>Zobacz też
- [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)
- [Ochrona hasłem w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)
- [How to: Permit code to run behind documents with restricted permissions (Jak zezwolić na uruchamianie kodu za dokumentami z ograniczonymi uprawnieniami)](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [How to: Add Bookmark controls to Word documents (Jak dodać kontrolki zakładek do dokumentów programu Word)](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
