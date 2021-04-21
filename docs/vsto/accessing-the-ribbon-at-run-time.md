---
title: Uzyskiwanie dostępu do wstążki w czasie uruchamiania
description: Możesz napisać kod, aby pokazać, ukryć i zmodyfikować wstążkę, a także umożliwić użytkownikom uruchamianie kodu z kontrolek w niestandardowym okienku zadań, okienku akcji lub regionie formularza programu Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e20c9a54d2fa352c51d5ae5383f5c5b7861e0fdf
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825228"
---
# <a name="access-the-ribbon-at-run-time"></a>Uzyskiwanie dostępu do wstążki w czasie uruchamiania
  Możesz napisać kod, aby pokazać, ukryć i zmodyfikować wstążkę, a także umożliwić użytkownikom uruchamianie kodu z kontrolek w niestandardowym okienku zadań, okienku akcji lub regionie formularza programu Outlook.

 Dostęp do wstążki można uzyskać przy użyciu `Globals` klasy . W przypadku projektów programu Outlook można uzyskać dostęp do wstążek, które są wyświetlane w określonym oknie programu Outlook Inspector lub Eksploratora programu Outlook.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Uzyskiwanie dostępu do wstążki przy użyciu klasy Globals
 Możesz użyć klasy , aby uzyskać dostęp do wstążki w projekcie na poziomie dokumentu lub projektu dodatku `Globals` VSTO z dowolnego miejsca w projekcie.

 Aby uzyskać więcej informacji na temat `Globals` klasy , zobacz Globalny dostęp do obiektów w [projektach pakietu Office.](../vsto/global-access-to-objects-in-office-projects.md)

 W poniższym przykładzie użyto klasy , aby uzyskać dostęp do niestandardowej wstążki o nazwie i ustawić tekst wyświetlany w polu kombi `Globals` `Ribbon1` na wstążce na wartość `Hello World` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet4":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet4":::

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Uzyskiwanie dostępu do kolekcji wstążek, które są wyświetlane w określonym oknie Inspektor programu Outlook
 Możesz uzyskać dostęp do kolekcji wstążek, które są wyświetlane w *inspektorach programu* Outlook. Inspector to okno, które jest otwierane w programie Outlook, gdy użytkownicy wykonują pewne zadania, takie jak tworzenie wiadomości e-mail. Aby uzyskać dostęp do wstążki okna Inspector (Inspektor), wywołaj właściwość klasy i przekaż obiekt `Ribbons` `Globals` <xref:Microsoft.Office.Interop.Outlook.Inspector> reprezentujący inspektora.

 Poniższy przykład pobiera kolekcję wstążki inspektora, który ma obecnie fokus. Następnie ten przykład uzyskuje dostęp do wstążki o nazwie i ustawia tekst wyświetlany w polu kombi `Ribbon1` na wstążce na . `Hello World`

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet5":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet5":::

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Uzyskiwanie dostępu do kolekcji wstążek, które są wyświetlane dla określonego eksploratora programu Outlook
 Możesz uzyskać dostęp do kolekcji wstążek, które są wyświetlane w *eksploratorze* programu Outlook. Eksplorator to główny interfejs użytkownika aplikacji dla wystąpienia programu Outlook. Aby uzyskać dostęp do wstążki okna eksploratora, wywołaj właściwość klasy i przekaż obiekt `Ribbons` `Globals` <xref:Microsoft.Office.Interop.Outlook.Explorer> reprezentujący eksploratora.

 Poniższy przykład pobiera kolekcję wstążki eksploratora, który ma obecnie fokus. Następnie ten przykład uzyskuje dostęp do wstążki o nazwie i ustawia tekst wyświetlany w polu kombi `Ribbon1` na wstążce na `Hello World` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet6":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet6":::

## <a name="see-also"></a>Zobacz też
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — Wstążka](../vsto/ribbon-xml.md)
- [Omówienie modelu obiektów wstążki](../vsto/ribbon-object-model-overview.md)
- [Przewodnik: tworzenie karty niestandardowej przy użyciu Projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Przewodnik: aktualizowanie kontrolek na wstążce w czasie uruchamiania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Uzyskiwanie dostępu do regionu formularza w czasie uruchamiania](../vsto/accessing-a-form-region-at-run-time.md)
