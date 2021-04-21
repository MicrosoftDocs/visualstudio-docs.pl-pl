---
title: Uzyskiwanie dostępu do regionu formularza w czasie uruchamiania
description: Dowiedz się, jak uzyskać dostęp do regionu formularza w różnych typach projektów i wersjach Microsoft Office w czasie uruchamiania.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at run time
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: dbd60f5773392af2066e4693751dd6fff99128b9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827971"
---
# <a name="access-a-form-region-at-run-time"></a>Uzyskiwanie dostępu do regionu formularza w czasie uruchamiania

|Dotyczy|
|----------------|
|Informacje przedstawione w tym temacie mają zastosowane tylko do poniższych typów projektów i wersji pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [Funkcje dostępne dla aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Typ projektu**<br /><br /> - Projekty dodatków VSTO<br /><br /> **Microsoft Office wersji**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|

 Użyj klasy `Globals` , aby uzyskać dostęp do regionów formularzy z dowolnego miejsca w projekcie programu Outlook. Aby uzyskać więcej informacji na temat `Globals` klasy , zobacz Globalny dostęp do obiektów w [projektach pakietu Office.](../vsto/global-access-to-objects-in-office-projects.md)

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Uzyskiwanie dostępu do regionów formularzy, które są wyświetlane w określonym oknie inspektora programu Outlook
 Aby uzyskać dostęp do wszystkich regionów formularzy, które są wyświetlane w określonym inspektorze programu Outlook, wywołaj właściwość klasy i przekaż obiekt `FormRegions` `Globals` <xref:Microsoft.Office.Interop.Outlook.Inspector> reprezentujący inspektora.

 Poniższy przykład pobiera kolekcję regionów formularzy, które są wyświetlane w inspektorze, który ma obecnie fokus. Następnie ten przykład uzyskuje dostęp do regionu formularza w kolekcji o nazwie i ustawia tekst wyświetlany `formRegion1` w polu tekstowym na `Hello World` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet2":::

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Uzyskiwanie dostępu do regionów formularzy, które są wyświetlane w określonym oknie eksploratora programu Outlook
 Aby uzyskać dostęp do wszystkich regionów formularzy, które są wyświetlane w określonym eksploratorze programu Outlook, wywołaj właściwość klasy i przekaż obiekt `FormRegions` `Globals` <xref:Microsoft.Office.Interop.Outlook.Explorer> reprezentujący eksploratora.

 Poniższy przykład pobiera kolekcję regionów formularzy, które są wyświetlane w Eksploratorze, który ma obecnie fokus. Następnie ten przykład uzyskuje dostęp do regionu formularza w kolekcji o nazwie i ustawia tekst wyświetlany `formRegion1` w polu tekstowym na `Hello World` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet3":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet3":::

## <a name="access-all-form-regions"></a>Dostęp do wszystkich regionów formularzy
 Aby uzyskać dostęp do wszystkich regionów formularzy, które są wyświetlane we wszystkich eksploratorach i wszystkich inspektorach, wywołaj `FormRegions` właściwość `Globals` klasy .

 Poniższy przykład pobiera kolekcję regionów formularzy, które są wyświetlane we wszystkich eksploratorach i wszystkich inspektorach. Następnie ten przykład uzyskuje dostęp do regionu formularza o nazwie i ustawia tekst wyświetlany `formRegion1` w polu tekstowym na `Hello World` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet1":::

## <a name="access-controls-on-a-form-region"></a>Kontrole dostępu w regionie formularza
 Aby uzyskać dostęp do kontrolek w regionie formularza przy użyciu klasy , należy udostępnić kontrolki kodowi poza plikiem kodu `Globals` regionu formularza.

### <a name="form-regions-designed-in-the-form-region-designer"></a>Regiony formularzy zaprojektowane w projektancie regionów formularzy
 W przypadku języka C# zmień modyfikator każdej kontrolki, do której chcesz uzyskać dostęp. W tym celu zaznacz każdą kontrolkę w projektancie regionu  formularza i zmień właściwość **Modyfikatory** na Wewnętrzna lub Publiczna **w** **oknie** Właściwości. Jeśli na przykład zmienisz właściwość **Modyfikator** na Wewnętrzne, możesz uzyskać `textBox1`  `textBox1` dostęp, wpisując `Globals.FormRegions.FormRegion1.textBox1` .

 W Visual Basic nie trzeba zmieniać modyfikatora.

### <a name="imported-form-regions"></a>Zaimportowane regiony formularzy
 Podczas importowania regionu formularza, który został zaprojektowany w programie Outlook, modyfikator dostępu każdej kontrolki w regionie formularza staje się prywatny. Ponieważ nie można użyć projektanta regionów formularzy do modyfikowania zaimportowanych obszarów formularzy, nie ma możliwości zmiany modyfikatora kontrolki w **oknie** Właściwości.

 Aby włączyć dostęp do kontrolki spoza pliku kodu regionu formularza, utwórz właściwość w pliku kodu regionu formularza, aby zwrócić tę kontrolkę.

 Aby uzyskać więcej informacji na temat tworzenia właściwości w języku C#, zobacz How [to: Declare and use read write properties &#40;C&#35; programming guide ](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties)&#41;.

 Aby uzyskać więcej informacji na temat tworzenia właściwości w Visual Basic, zobacz Jak [utworzyć właściwość (Visual Basic).](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property)

## <a name="see-also"></a>Zobacz też
- [Wskazówki dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Przewodnik: projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Jak dodać region formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Akcje niestandardowe w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Kojarzenie regionu formularza z klasą komunikatów programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Przewodnik: importowanie regionu formularza zaprojektowanego w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [How to: Prevent Outlook from displaying a form region (Jak zapobiec wyświetlaniu regionu formularza w programie Outlook)](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Uzyskiwanie dostępu do wstążki w czasie uruchamiania](../vsto/accessing-the-ribbon-at-run-time.md)
