---
title: Programowe dodawanie obrazów i grafiki programu Word do dokumentów
description: Dowiedz się, jak dodawać obrazy i rysowanie obiektów do dokumentów w czasie projektowania lub w czasie uruchamiania.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 445857200dfb269dd71f7cb3d446d025048cb3ac
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828439"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>How to: Programmatically add pictures and Word Art to documents (2. Programowe dodawanie obrazów i grafiki programu Word do dokumentów)
  Obrazy i rysowanie obiektów można dodawać do dokumentów w czasie projektowania lub w czasie uruchamiania. WordArt umożliwia dodawanie tekstu dekoracyjnych do dokumentów Microsoft Office Word. Te specjalne efekty tekstowe to rysowanie obiektów, które można dostosować i wstawić do dokumentu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="add-a-picture-at-design-time"></a>Dodawanie obrazu w czasie projektowania
 Jeśli opracowujesz dostosowanie na poziomie dokumentu, możesz dodać do dokumentu obraz w czasie projektowania.

### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Aby dodać obraz do dokumentu programu Word w czasie projektowania

1. Umieść kursor w miejscu, w którym chcesz wstawić obraz do dokumentu.

2. Kliknij **kartę Wstawianie** na wstążce.

3. W grupie **Ilustracje** kliknij pozycję **Obraz**.

4. W **oknie dialogowym Wstaw** obraz przejdź do obrazu, który chcesz wstawić, a następnie kliknij pozycję **Wstaw**.

     Obraz zostanie dodany do dokumentu w bieżącej lokalizacji kursora.

## <a name="add-a-picture-at-run-time"></a>Dodawanie obrazu w czasie uruchamiania
 Obraz można wstawić do dokumentu w bieżącej lokalizacji kursora.

### <a name="to-add-a-picture-at-the-cursor-location"></a>Aby dodać obraz w lokalizacji kursora

1. Wywołaj <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> metodę <xref:Microsoft.Office.Interop.Word.InlineShapes> kolekcji i przekaż nazwę pliku.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet108":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet108":::

## <a name="add-wordart-at-design-time"></a>Dodawanie wykresu WordArt w czasie projektowania
 Jeśli opracowujesz dostosowanie na poziomie dokumentu, możesz dodać do dokumentu tekst WordArt w czasie projektowania.

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Aby dodać wykres WordArt do dokumentu programu Word w czasie projektowania

1. Umieść kursor w miejscu, w którym chcesz wstawić wykres WordArt do dokumentu.

2. Kliknij **kartę Wstawianie** na wstążce.

3. W grupie **Tekst** kliknij pozycję **WordArt,** a następnie wybierz styl WordArt.

4. Dodaj tekst, który ma być wyświetlany w dokumencie, do okna dialogowego **Edytowanie tekstu WordArt** i kliknij przycisk **OK.**

     Tekst zostanie dodany do dokumentu z zastosowanym wybranym stylem WordArt.

## <a name="add-wordart-at-run-time"></a>Dodawanie wykresu WordArt w czasie uruchamiania
 Możesz wstawić wykres WordArt do dokumentu w bieżącej lokalizacji kursora. Procedura jest inna w przypadku dostosowań na poziomie dokumentu i dodatków VSTO.

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Aby dodać wykres WordArt w lokalizacji kursora w dostosowywaniu na poziomie dokumentu

1. Pobierz lewą i górną pozycję bieżącej lokalizacji kursora.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet109":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet109":::

2. Wywołaj <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> metodę obiektu w <xref:Microsoft.Office.Interop.Word.Shapes> dokumencie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet110":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet110":::

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Aby dodać wykres WordArt w lokalizacji kursora w dodatku VSTO

1. Pobierz lewą i górną pozycję bieżącej lokalizacji kursora.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet109":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet109":::

2. Wywołaj <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> metodę <xref:Microsoft.Office.Interop.Word.Shapes> obiektu aktywnego dokumentu (lub innego dokumentu, który określisz).

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet110":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet110":::

## <a name="compile-the-code"></a>Kompilowanie kodu

- Obraz o *nazwieSamplePicture.jpg* musi istnieć na dysku C.

## <a name="see-also"></a>Zobacz też
- [Pisano: Programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)
- [How to: Programowe wstawianie tekstu do dokumentów programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [How to: Programowe przywracanie wyborów po wyszukiwaniu](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [How to: Programowe zapisywanie dokumentów](../vsto/how-to-programmatically-save-documents.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
