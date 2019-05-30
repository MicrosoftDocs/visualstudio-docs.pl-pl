---
title: Programowe ochrony dokumentów i części dokumentów
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 30cb3d0b9ad04a3a0195f3b58ba5856de94d09d4
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402189"
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Instrukcje: Programowe Włączanie ochrony dokumentów i części dokumentów
  Można dodać ochrony do dokumentów programu Microsoft Office Word, aby uniemożliwić użytkownikom wprowadzanie żadnych zmian w dokumencie.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Niektóre obszary dokumentu można również oznaczyć jako wyjątki, aby określeni użytkownicy mogą edytować tylko te części dokumentu. Na przykład można chronić całego dokumentu, z wyjątkiem określonym zakładki. Możesz opcjonalnie dodać hasła, tak aby użytkownicy nie mogli usunąć ochronę dokumentu, chyba że hasło, które znają.

> [!NOTE]
> Poniższy przykład nie korzysta z ochrony haseł. Jednak warto wziąć pod uwagę przy użyciu hasła, podczas dodawania ochrony dokumentu. Aby uzyskać więcej informacji, zobacz przykład ochrony dokumentu w [Office development ― przykłady i wskazówki dotyczące](../vsto/office-development-samples-and-walkthroughs.md).

 Formanty zawartości umożliwia również ochrona części dokumentów. Aby uzyskać więcej informacji, zobacz [jak: Ochrona części dokumentów za pomocą formantów zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="protect-a-document-that-is-part-of-a-document-level-customization"></a>Chroń dokument, który jest częścią dostosowywania poziomie dokumentu

### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Aby chronić dokument, który jest częścią dostosowywania poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> metody `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]

### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Aby wykluczyć kontrolka zakładki z ochrony dokumentu

1. Ochrona za pomocą całego dokumentu <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> metody.

     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]

2. Wyklucz `Bookmark1` z ochrony dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#112)]
     [!code-csharp[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#112)]

### <a name="compile-the-code"></a>Skompilować kod
 Aby wykorzystać te przykłady kodu, należy uruchomić je z `ThisDocument` klasy w projekcie. Te przykłady kodu założono, że istniejące <xref:Microsoft.Office.Tools.Word.Bookmark> formantu o nazwie `Bookmark1` w dokumencie, w której występuje ten kod.

## <a name="protect-a-document-by-using-a-vsto-add-in"></a>Ochrona dokumentu przy użyciu dodatku narzędzi VSTO

### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>Aby chronić dokument za pomocą dodatku narzędzi VSTO dla dodatku poziomu aplikacji

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> metody <xref:Microsoft.Office.Interop.Word.Document> , którą chcesz chronić.

     Poniższy kod chroni aktywnego dokumentu. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#111)]

## <a name="see-also"></a>Zobacz także
- [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)
- [Ochrona za pomocą hasła w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)
- [Instrukcje: Zezwalanie kodu do uruchamiania w tle dokumentów z ograniczonymi uprawnieniami](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Instrukcje: Dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
