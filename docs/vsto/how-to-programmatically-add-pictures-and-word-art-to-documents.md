---
title: Programistyczne Dodawanie zdjęć i obiektów WordArt do dokumentów
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: e73473229a35bebb99eac03963fb43f880a39903
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585395"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Instrukcje: programowe Dodawanie zdjęć i rysunków programu Word do dokumentów
  Możesz dodawać obrazy i obiekty rysunkowe do dokumentów w czasie projektowania lub w czasie wykonywania. Obiekt WordArt umożliwia dodawanie dekoracyjnego tekstu do Microsoft Office dokumentów programu Word. Te specjalne efekty tekstowe to obiekty rysunkowe, które można dostosować i wstawić do dokumentu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="add-a-picture-at-design-time"></a>Dodawanie obrazu w czasie projektowania
 Jeśli tworzysz dostosowanie na poziomie dokumentu, możesz dodać obraz do dokumentu w czasie projektowania.

### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Aby dodać obraz do dokumentu programu Word w czasie projektowania

1. Umieść kursor w miejscu, w którym chcesz wstawić obraz do dokumentu.

2. Kliknij kartę **Wstawianie** na Wstążce.

3. W grupie **ilustracje** kliknij pozycję **obraz**.

4. W oknie dialogowym **Wstawianie obrazu** przejdź do obrazu, który chcesz wstawić, a następnie kliknij przycisk **Wstaw**.

     Obraz zostanie dodany do dokumentu w bieżącej lokalizacji kursora.

## <a name="add-a-picture-at-run-time"></a>Dodawanie obrazu w czasie wykonywania
 Możesz wstawić obraz do dokumentu w bieżącej lokalizacji kursora.

### <a name="to-add-a-picture-at-the-cursor-location"></a>Aby dodać obraz w lokalizacji kursora

1. Wywołaj <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> metodę <xref:Microsoft.Office.Interop.Word.InlineShapes> kolekcji i przekaż nazwę pliku.

     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]

## <a name="add-wordart-at-design-time"></a>Dodawanie tekstu WordArt w czasie projektowania
 Jeśli tworzysz dostosowanie na poziomie dokumentu, możesz dodać obiekt WordArt do dokumentu w czasie projektowania.

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Aby dodać obiekt WordArt do dokumentu programu Word w czasie projektowania

1. Umieść kursor w miejscu, w którym chcesz wstawić obiekt WordArt do dokumentu.

2. Kliknij kartę **Wstawianie** na Wstążce.

3. W grupie **tekst** kliknij przycisk **WordArt**, a następnie wybierz styl WordArt.

4. Dodaj tekst, który ma być wyświetlany w dokumencie do okna dialogowego **Edytuj tekst WordArt** , a następnie kliknij przycisk **OK**.

     Tekst zostanie dodany do dokumentu z zastosowaniem wybranego stylu WordArt.

## <a name="add-wordart-at-run-time"></a>Dodaj obiekt WordArt w czasie wykonywania
 Możesz wstawić obiekt WordArt do dokumentu w bieżącej lokalizacji kursora. Procedura różni się w przypadku dostosowań na poziomie dokumentu i dodatków narzędzi VSTO.

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Aby dodać obiekt WordArt w lokalizacji kursora w dostosowaniu na poziomie dokumentu

1. Pobierz lewą i górną pozycję bieżącej lokalizacji kursora.

     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]

2. Wywoływanie <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> metody <xref:Microsoft.Office.Interop.Word.Shapes> obiektu w dokumencie.

     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Aby dodać obiekt WordArt w lokalizacji kursora w dodatku narzędzi VSTO

1. Pobierz lewą i górną pozycję bieżącej lokalizacji kursora.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]

2. Wywoływanie <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> metody <xref:Microsoft.Office.Interop.Word.Shapes> obiektu aktywnego dokumentu (lub innego dokumentu określonego przez użytkownika).

     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]

## <a name="compile-the-code"></a>Kompiluj kod

- Obraz o nazwie *SamplePicture.jpg* musi znajdować się na dysku C.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)
- [Instrukcje: Programowane wstawianie tekstu do dokumentów programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Instrukcje: Programowane przywracanie zaznaczenia po wyszukiwaniu](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Instrukcje: programowe zapisywanie dokumentów](../vsto/how-to-programmatically-save-documents.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
