---
title: Programistyczne Włączanie ochrony dokumentów i części dokumentów
description: Dowiedz się, jak można dodać ochronę do dokumentów programu Microsoft Word, aby uniemożliwić użytkownikom wprowadzanie zmian w dokumencie.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1dbb001a8c350b376f30047dbafbf747f043e91d
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527767"
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Instrukcje: programowe Włączanie ochrony dokumentów i części dokumentów
  Możesz dodać ochronę do Microsoft Office dokumentów programu Word, aby uniemożliwić użytkownikom wprowadzanie zmian w dokumencie.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Można także oznaczyć niektóre obszary dokumentu jako wyjątki, aby określeni użytkownicy mogli edytować tylko te obszary dokumentu. Na przykład może być konieczne ochrona całego dokumentu z wyjątkiem określonej zakładki. Opcjonalnie możesz dodać hasło, aby użytkownicy nie mogli usunąć ochrony dokumentów, chyba że zna hasło.

> [!NOTE]
> W poniższym przykładzie nie jest używana Ochrona hasłem; Warto jednak rozważyć użycie hasła podczas dodawania ochrony dokumentów. Aby uzyskać więcej informacji, zobacz próbkę funkcji ochrony dokumentów w przykładach [i przewodnikach programistycznych dotyczących pakietu Office](../vsto/office-development-samples-and-walkthroughs.md).

 Za pomocą kontrolek zawartości można również chronić części dokumentów. Aby uzyskać więcej informacji, zobacz [jak: ochrona części dokumentów za pomocą kontrolek zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="protect-a-document-that-is-part-of-a-document-level-customization"></a>Ochrona dokumentu, który jest częścią dostosowania na poziomie dokumentu

### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Aby chronić dokument, który jest częścią dostosowania na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> metodę `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]

### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Aby wykluczyć formant zakładki z ochrony dokumentów

1. Chroń cały dokument przy użyciu <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> metody.

     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]

2. Wyklucz `Bookmark1` z ochrony dokumentów.

     [!code-vb[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#112)]
     [!code-csharp[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#112)]

### <a name="compile-the-code"></a>Kompiluj kod
 Aby użyć tych przykładów kodu, uruchom je z `ThisDocument` klasy w projekcie. W tych przykładach kodu założono, że masz istniejącą <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę o nazwie `Bookmark1` w dokumencie, w którym ten kod pojawia się.

## <a name="protect-a-document-by-using-a-vsto-add-in"></a>Ochrona dokumentu przy użyciu dodatku VSTO

### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>Aby chronić dokument przy użyciu dodatku VSTO na poziomie aplikacji

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> metodę <xref:Microsoft.Office.Interop.Word.Document> , która ma być chroniona.

     Poniższy przykład kodu chroni aktywny dokument. Aby użyć tego przykładu kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#111)]

## <a name="see-also"></a>Zobacz też
- [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)
- [Ochrona hasłem w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)
- [Instrukcje: Zezwalanie na uruchamianie kodu w tle dokumentów z ograniczonymi uprawnieniami](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Instrukcje: Dodawanie kontrolek zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
