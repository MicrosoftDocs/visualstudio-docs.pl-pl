---
title: Dostęp do regionów formularzy w czasie wykonywania
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at runtime
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: f2c1f3e80f5ca4015a19b5eee7f2f4c673dcc615
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304483"
---
# <a name="access-a-form-region-at-runtime"></a>Dostęp do regionów formularzy w czasie wykonywania

|Informacje zawarte w tym artykule dotyczą|  
|----------------|  
|Informacje przedstawione w tym temacie mają zastosowane tylko do poniższych typów projektów i wersji pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [funkcje, które są dostępne przez typ aplikacji i projektów pakietu Office](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Typ projektu**<br /><br /> -Projekty dodatków narzędzi VSTO dla programów<br /><br /> **Wersja Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  

 Użyj `Globals` klasy do regionów formularzy w dostęp z dowolnego miejsca w obrębie projektu programu Outlook. Aby uzyskać więcej informacji na temat `Globals` klasy, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Dostęp do obszarów formularzy, które pojawiają się w określonym oknie inspektora programu Outlook  
 Aby uzyskać dostęp do wszystkich regionów formularzy, które pojawiają się w określonym Inspektor programu Outlook, wywołaj `FormRegions` właściwość `Globals` klasy i przekazać <xref:Microsoft.Office.Interop.Outlook.Inspector> obiekt, który reprezentuje Inspektor.  

 Poniższy przykład pobiera kolekcję regionów formularzy, które są wyświetlane w panelu Inspektor, który aktualnie ma fokus. W tym przykładzie następnie uzyskuje dostęp do regionów formularzy w kolekcji o nazwie `formRegion1` i ustawia tekst, który pojawia się w polu tekstowym, aby `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]  

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Dostęp do obszarów formularzy, które pojawiają się w określonym oknie Eksploratora programu Outlook  
 Aby uzyskać dostęp do wszystkich obszarów formularzy, które pojawiają się w określonym Eksplorator programu Outlook, wywołaj `FormRegions` właściwość `Globals` klasy i przekazać <xref:Microsoft.Office.Interop.Outlook.Explorer> obiekt, który reprezentuje Eksploratora.  

 Poniższy przykład pobiera kolekcję regionów formularza, które są wyświetlane w Eksploratorze, który aktualnie ma fokus. W tym przykładzie następnie uzyskuje dostęp do regionów formularzy w kolekcji o nazwie `formRegion1` i ustawia tekst, który pojawia się w polu tekstowym, aby `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]  

## <a name="access-all-form-regions"></a>Dostęp do wszystkich regionów formularzy  
 Aby uzyskać dostęp do wszystkich regionów formularzy, które pojawiają się na wszystkie eksploratorów i wszystkie inspektorzy, należy wywołać `FormRegions` właściwość `Globals` klasy.  

 Poniższy przykład pobiera kolekcję regionów formularzy, które pojawiają się na wszystkie eksploratorów i wszystkie inspektorzy. W tym przykładzie następnie uzyskuje dostęp do regionu formularza o nazwie `formRegion1` i ustawia tekst, który pojawia się w polu tekstowym, aby `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]  

## <a name="access-controls-on-a-form-region"></a>Kontroli dostępu do regionów formularzy  
 Do kontroli dostępu do regionów formularzy przy użyciu `Globals` klasy, należy formanty dostępny do kodu poza plik kodu regionu formularza.  

### <a name="form-regions-designed-in-the-form-region-designer"></a>Regionów formularzy zaprojektowanych w projektanta regionów formularza  
 Aby uzyskać C#, zmień modyfikator każdy formant, który chcesz uzyskać dostęp. Aby to zrobić, zaznacz każdy formant w projektanta regionów formularza i zmień **Modyfikatory** właściwości **wewnętrzne** lub **publicznych** w **właściwości** okna. Na przykład, jeśli zmienisz **modyfikator** właściwość `textBox1` do **wewnętrzne**, możesz uzyskać dostęp `textBox1` , wpisując `Globals.FormRegions.FormRegion1.textBox1`.  

 Dla języka Visual Basic nie trzeba zmienić modyfikator.  

### <a name="imported-form-regions"></a>Regiony formularzy zaimportowany  
 Po zaimportowaniu regionu formularza zaprojektowanego w programie Outlook, modyfikator dostępu dla każdego formantu na region formularza staje się prywatnych. Ponieważ nie można użyć projektanta regionów formularza do modyfikowania regionu formularza zaimportowane, nie ma możliwości zmiany modyfikator kontrolki w **właściwości** okna.  

 Aby włączyć dostęp do kontrolki z poza plikiem kodu regionu formularza, należy utworzyć właściwość w pliku kodu regionu formularza do zwrócenia tej kontrolki.  

 Aby uzyskać więcej informacji o sposobie tworzenia właściwości w C#, zobacz [porady: deklarowanie i użycie Odczyt, zapis właściwości &#40;C&#35; Podręcznik programowania&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).  

 Aby uzyskać więcej informacji na temat tworzenia właściwości w języku Visual Basic, zobacz [porady: Tworzenie właściwości (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).  

## <a name="see-also"></a>Zobacz także  
 [Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Porady: dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Niestandardowe akcje w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Wskazówki: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Porady: ochrona programu Outlook przed wyświetlaniem regionów formularzy](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)  
