---
title: 'Instrukcje: Programowe zapisywanie dokumentów'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0e8a4e1c44928663d0d055d84899c60b968f90a0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636466"
---
# <a name="how-to-programmatically-save-documents"></a>Instrukcje: Programowe zapisywanie dokumentów
  Istnieje kilka sposobów, aby zapisać dokumenty Microsoft Word pakietu Office. Można zapisać dokumentu, bez zmiany nazwy dokumentu lub zapisaniu dokumentu pod nową nazwą.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="save-a-document-without-changing-the-name"></a>Zapisywanie dokumentu bez zmiany nazwy

### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Aby zapisać dokument skojarzony z dostosowywania poziomie dokumentu

1.  Wywołaj <xref:Microsoft.Office.Tools.Word.Document.Save%2A> metody <xref:Microsoft.Office.Tools.Word.Document> klasy. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]

### <a name="to-save-the-active-document"></a>Aby zapisać aktywnego dokumentu

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.Save%2A> metodę dla aktywnego dokumentu. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.

    [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
    [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]

   Jeśli nie masz pewności, czy dokument, który ma zostać zapisany jest aktywny dokument, możesz się odwoływać do według jego nazwy.

### <a name="to-save-a-document-specified-by-name"></a>Można zapisać dokumentu, określonego przez nazwę

1.  Użyj nazwy dokumentu jako argument do <xref:Microsoft.Office.Interop.Word.Documents> kolekcji. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]

## <a name="save-a-document-with-a-new-name"></a>Zapisywanie dokumentu pod nową nazwą
 Należy użyć metody Zapisz jako, aby zapisać dokument pod nową nazwą. Można użyć tej metody <xref:Microsoft.Office.Tools.Word.Document> element hosta w projekcie programu Word poziomie dokumentu lub natywny <xref:Microsoft.Office.Interop.Word.Document> obiektu w każdym projekcie programu Word. Ta metoda wymaga, aby określić nową nazwę pliku, ale inne argumenty są opcjonalne.

> [!NOTE]
>  Jeśli wyświetlisz **Zapisz jako** okna dialogowego wewnątrz <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> program obsługi zdarzeń `ThisDocument` i ustaw *anulować* parametr **false**, aplikacja może został nieoczekiwanie zakończony. Jeśli ustawisz *anulować* parametr **true**, wyświetlony komunikat o błędzie wskazujący, że zapisywania został wyłączony.

### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Aby zapisać dokument skojarzony z dostosowania poziomu dokumentu pod nową nazwą

1.  Wywołaj <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> metody `ThisDocument` klasy w projekcie, przy użyciu w pełni kwalifikowaną ścieżkę i nazwę pliku. Jeśli plik o tej nazwie już istnieje w tym folderze, jest zastąpione w trybie dyskretnym. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisDocument` klasy.

    > [!NOTE]
    >  <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> Metoda zgłasza wyjątek, jeśli katalog docelowy nie istnieje, lub jeśli występują inne problemy podczas zapisywania pliku. Jest dobrą praktyką, aby użyć **try... catch** block wokół <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> metody lub wewnątrz wywołania metody.

     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]

### <a name="to-save-a-native-document-with-a-new-name"></a>Można zapisać dokumentu macierzystego pod nową nazwą

1.  Wywołaj <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metody <xref:Microsoft.Office.Interop.Word.Document> , którą chcesz zapisać, przy użyciu w pełni kwalifikowaną ścieżkę i nazwę pliku. Jeśli plik o tej nazwie już istnieje w tym folderze, jest zastąpione w trybie dyskretnym.

     Poniższy przykład kodu Zapisuje aktywny dokument pod nową nazwą. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.

    > [!NOTE]
    >  <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Metoda zgłasza wyjątek, jeśli katalog docelowy nie istnieje, lub jeśli występują inne problemy podczas zapisywania pliku. Jest dobrą praktyką, aby użyć **try... catch** block wokół <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metody lub wewnątrz wywołania metody.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład kodu wymaga następujących elementów:

-   Zapisywanie dokumentu o nazwie, o nazwie dokumentu *NewDocument.doc* muszą istnieć w katalogu o nazwie *testu* na dysku C.

-   Aby zapisać dokument pod nową nazwą, katalog o nazwie *testu* musi istnieć na dysku C.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe zamykanie dokumentów](../vsto/how-to-programmatically-close-documents.md)
- [Instrukcje: Programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)
- [Element hosta dokumentu](../vsto/document-host-item.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
