---
title: 'Instrukcje: Programowe Dodawanie zdjęć i WordArt do dokumentów'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f805153a35517c473e95beb871ae7d12a2776bd4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967611"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Instrukcje: Programowe Dodawanie zdjęć i WordArt do dokumentów
  Obrazy i obiekty można dodać do dokumentów w czasie projektowania lub w czasie wykonywania. WordArt umożliwia dodawanie dekoracyjne tekstu do dokumentów programu Microsoft Office Word. Te efekty specjalne tekstowe są Rysowanie obiektów, które można dostosować i wstawić do dokumentu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="add-a-picture-at-design-time"></a>Dodawanie obrazu w czasie projektowania
 Jeśli tworzysz dostosowywania poziomie dokumentu, możesz dodać obraz do dokumentu w czasie projektowania.

### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Aby dodać obraz do dokumentu programu Word w czasie projektowania

1. Umieść kursor w miejscu, w którym chcesz wstawić obrazu w dokumencie.

2. Kliknij przycisk **Wstaw** karty wstążki.

3. W **ilustracje** grupy, kliknij przycisk **obraz**.

4. W **Wstaw obraz** okno dialogowe, przejdź do obrazu, który chcesz wstawić, a następnie kliknij przycisk **Wstaw**.

     Obraz jest dodawany do dokumentu w bieżącej lokalizacji kursora.

## <a name="add-a-picture-at-runtime"></a>Dodawanie obrazu w czasie wykonywania
 Można wstawić obrazu do dokumentu w bieżącej lokalizacji kursora.

### <a name="to-add-a-picture-at-the-cursor-location"></a>Aby dodać obraz w lokalizacji kursora

1. Wywołaj <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> metody <xref:Microsoft.Office.Interop.Word.InlineShapes> zbierania i nazwę pliku.

     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]

## <a name="add-wordart-at-design-time"></a>Dodawanie obiektów WordArt w czasie projektowania
 Jeśli tworzysz dostosowywania poziomie dokumentu można dodać obiektów WordArt do dokumentów w czasie projektowania.

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Można dodać obiektów WordArt do dokumentów programu Word w czasie projektowania

1. Umieść kursor w miejscu, w którym chcesz wstawić tekst WordArt w dokumencie.

2. Kliknij przycisk **Wstaw** karty wstążki.

3. W **tekstu** grupy, kliknij przycisk **WordArt**, a następnie wybierz styl WordArt.

4. Dodaj tekst, który ma być wyświetlany w dokumencie, aby **edytowanie tekstu WordArt** dialogowym i kliknij przycisk **OK**.

     Tekst zostanie dodany do dokumentu za pomocą wybranego zastosowanego stylu WordArt.

## <a name="add-wordart-at-runtime"></a>Dodawanie obiektów WordArt w czasie wykonywania
 Można wstawić obiektów WordArt do dokumentów w bieżącej lokalizacji kursora. Procedura różni się dla dostosowywania poziomie dokumentu i dodatków narzędzi VSTO.

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Aby dodać WordArt w lokalizacji kursora w dostosowaniu na poziomie dokumentu

1. Pobierz położenie lewym i górnym bieżąca lokalizacja kursora.

     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]

2. Wywołaj <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> metody <xref:Microsoft.Office.Interop.Word.Shapes> obiektu w dokumencie.

     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Aby dodać WordArt w lokalizacji kursora w dodatku narzędzi VSTO

1. Pobierz położenie lewym i górnym bieżąca lokalizacja kursora.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]

2. Wywołaj <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> metody <xref:Microsoft.Office.Interop.Word.Shapes> obiektu aktywnego dokumentu (lub innego dokumentu, który określisz).

     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]

## <a name="compile-the-code"></a>Skompilować kod

- Obraz o nazwie *SamplePicture.jpg* musi istnieć na dysku C.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)
- [Instrukcje: Programowe Wstawianie tekstu w dokumentach programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Instrukcje: Programowe Przywracanie zaznaczenia po wyszukiwaniu](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Instrukcje: Programowe zapisywanie dokumentów](../vsto/how-to-programmatically-save-documents.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
