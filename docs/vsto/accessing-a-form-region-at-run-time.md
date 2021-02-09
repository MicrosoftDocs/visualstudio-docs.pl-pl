---
title: Dostęp do regionu formularza w czasie wykonywania
description: Dowiedz się, jak uzyskać dostęp do regionu formularza w różnych typach projektów i wersjach Microsoft Office w czasie wykonywania.
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
ms.openlocfilehash: 62d8236b987afbb7dc9d5e4462b79ffb4fe00bc5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928877"
---
# <a name="access-a-form-region-at-run-time"></a>Dostęp do regionu formularza w czasie wykonywania

|Dotyczy|
|----------------|
|Informacje przedstawione w tym temacie mają zastosowane tylko do poniższych typów projektów i wersji pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [dostępność funkcji według aplikacji pakietu Office i typów projektów](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Typ projektu**<br /><br /> — Projekty dodatków narzędzi VSTO<br /><br /> **Wersja Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|

 Użyj `Globals` klasy, aby uzyskać dostęp do regionów formularzy z dowolnego miejsca w projekcie programu Outlook. Aby uzyskać więcej informacji na temat `Globals` klasy, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Obszary formularzy dostępu, które są wyświetlane w określonym oknie Inspektora programu Outlook
 Aby uzyskać dostęp do wszystkich regionów formularzy, które są wyświetlane w określonym Inspektorze programu Outlook, wywołaj `FormRegions` Właściwość `Globals` klasy i przekaż <xref:Microsoft.Office.Interop.Outlook.Inspector> obiekt, który reprezentuje Inspektor.

 Poniższy przykład pobiera kolekcję regionów formularza, które są wyświetlane w Inspektorze, który aktualnie ma fokus. Ten przykład następnie uzyskuje dostęp do regionu formularza w kolekcji o nazwie `formRegion1` i ustawia tekst, który pojawia się w polu tekstowym `Hello World` .

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Obszary formularzy dostępu, które są wyświetlane w określonym oknie Eksploratora programu Outlook
 Aby uzyskać dostęp do wszystkich regionów formularzy, które są wyświetlane w określonym Eksploratorze programu Outlook, wywołaj `FormRegions` Właściwość `Globals` klasy i przekaż <xref:Microsoft.Office.Interop.Outlook.Explorer> obiekt, który reprezentuje Eksploratora.

 Poniższy przykład pobiera kolekcję regionów formularza, które są wyświetlane w Eksploratorze, który ma aktualnie fokus. Ten przykład następnie uzyskuje dostęp do regionu formularza w kolekcji o nazwie `formRegion1` i ustawia tekst, który pojawia się w polu tekstowym `Hello World` .

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]

## <a name="access-all-form-regions"></a>Dostęp do wszystkich regionów formularzy
 Aby uzyskać dostęp do wszystkich regionów formularzy, które są wyświetlane we wszystkich Explorer i wszystkich inspektorach, należy wywołać `FormRegions` Właściwość `Globals` klasy.

 Poniższy przykład pobiera kolekcję regionów formularza, które są wyświetlane we wszystkich Explorer i wszystkich inspektorach. Ten przykład następnie uzyskuje dostęp do regionu formularza o nazwie `formRegion1` i ustawia tekst, który pojawia się w polu tekstowym `Hello World` .

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]

## <a name="access-controls-on-a-form-region"></a>Kontrola dostępu w regionie formularza
 Aby uzyskać dostęp do formantów w regionie formularza przy użyciu `Globals` klasy, należy udostępnić kontrolki dostęp do kodu spoza pliku kodu regionu formularza.

### <a name="form-regions-designed-in-the-form-region-designer"></a>Regiony formularzy zaprojektowane w projektancie regionów formularza
 Dla języka C# Zmień modyfikator każdej kontrolki, do której chcesz uzyskać dostęp. W tym celu zaznacz każdy formant w projektancie regionów formularza i zmień właściwość **Modyfikatory** na **Internal** lub **publiczny** w oknie **Właściwości** . Na przykład, jeśli zmienisz Właściwość **modyfikatora** `textBox1` na **Internal**, możesz uzyskać dostęp, `textBox1` wpisując `Globals.FormRegions.FormRegion1.textBox1` .

 W przypadku Visual Basic nie trzeba zmieniać modyfikatora.

### <a name="imported-form-regions"></a>Zaimportowane regiony formularzy
 Podczas importowania regionu formularza, który został zaprojektowany w programie Outlook, modyfikator dostępu dla każdej kontrolki w regionie formularza zostaje prywatny. Ponieważ nie można użyć projektanta regionów formularza do zmodyfikowania regionu formularza zaimportowanego, nie ma możliwości zmiany modyfikatora kontrolki w oknie **Właściwości** .

 Aby umożliwić dostęp do formantu spoza pliku kodu regionu formularza, Utwórz właściwość w pliku kodu regionu formularza, aby zwrócić tę kontrolkę.

 Aby uzyskać więcej informacji o sposobach tworzenia właściwości w języku C#, zobacz [How to: DECLARE and use Read Write properties &#40;C&#35; Przewodnik programowania&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).

 Aby uzyskać więcej informacji na temat sposobu tworzenia właściwości w Visual Basic, zobacz [How to: Create a Property (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).

## <a name="see-also"></a>Zobacz też
- [Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Przewodnik: Projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Niestandardowe akcje w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Instrukcje: zapobieganie wyświetlaniu regionu formularza przez program Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
