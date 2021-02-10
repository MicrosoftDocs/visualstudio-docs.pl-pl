---
title: Uzyskiwanie dostępu do wstążki w czasie wykonywania
description: Można napisać kod, aby pokazać, ukryć i zmodyfikować Wstążkę oraz umożliwić użytkownikom uruchamianie kodu z kontrolek w niestandardowym okienku zadań, w okienku Akcje lub w regionie formularza programu Outlook.
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
ms.openlocfilehash: 224396d7b4328164c55bc58c746909ada015e02f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965736"
---
# <a name="access-the-ribbon-at-run-time"></a>Uzyskiwanie dostępu do wstążki w czasie wykonywania
  Można napisać kod, aby pokazać, ukryć i zmodyfikować Wstążkę oraz umożliwić użytkownikom uruchamianie kodu z kontrolek w niestandardowym okienku zadań, w okienku Akcje lub w regionie formularza programu Outlook.

 Możesz uzyskać dostęp do wstążki przy użyciu `Globals` klasy. W przypadku projektów programu Outlook można uzyskać dostęp do wstążki, które są wyświetlane w określonym Inspektorze programu Outlook lub oknie Eksploratora programu Outlook.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Dostęp do wstążki przy użyciu klasy Globals
 Możesz użyć klasy, `Globals` Aby uzyskać dostęp do wstążki w projekcie na poziomie dokumentu lub w dodatku VSTO z dowolnego miejsca w projekcie.

 Aby uzyskać więcej informacji na temat `Globals` klasy, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

 Poniższy przykład używa `Globals` klasy w celu uzyskania dostępu do Wstążki niestandardowej o nazwie `Ribbon1` i ustawienia tekstu wyświetlanego w polu kombi na Wstążce `Hello World` .

 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Dostęp do kolekcji wstążki, które pojawiają się w określonym oknie Inspektora programu Outlook
 Możesz uzyskać dostęp do kolekcji wstążki, które są wyświetlane w *inspektorach* programu Outlook. Inspektor to okno otwierane w programie Outlook, gdy użytkownicy wykonują określone zadania, takie jak tworzenie wiadomości e-mail. Aby uzyskać dostęp do wstążki okna inspektora, wywołaj `Ribbons` Właściwość `Globals` klasy i przekaż <xref:Microsoft.Office.Interop.Outlook.Inspector> obiekt, który reprezentuje Inspektor.

 Poniższy przykład pobiera kolekcję wstążki inspektora, który ma aktualnie fokus. Ten przykład następnie uzyskuje dostęp do wstążki o nazwie `Ribbon1` i ustawia tekst, który pojawia się w polu kombi na Wstążce `Hello World` .

 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Dostęp do kolekcji wstążki, które są wyświetlane dla określonego Eksploratora programu Outlook
 Możesz uzyskać dostęp do kolekcji wstążki, które są wyświetlane w *Eksploratorze* programu Outlook. Eksplorator jest głównym interfejsem użytkownika aplikacji (UI) dla wystąpienia programu Outlook. Aby uzyskać dostęp do wstążki okna Eksploratora, wywołaj `Ribbons` Właściwość `Globals` klasy i przekaż <xref:Microsoft.Office.Interop.Outlook.Explorer> obiekt, który reprezentuje Eksploratora.

 Poniższy przykład pobiera kolekcję wstążki Eksploratora, która aktualnie ma fokus. Ten przykład następnie uzyskuje dostęp do wstążki o nazwie `Ribbon1` i ustawia tekst, który pojawia się w polu kombi na Wstążce `Hello World` .

 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]

## <a name="see-also"></a>Zobacz też
- [Omówienie wstążki](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — Wstążka](../vsto/ribbon-xml.md)
- [Omówienie modelu obiektów wstążki](../vsto/ribbon-object-model-overview.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Przewodnik: aktualizowanie kontrolek na Wstążce w czasie wykonywania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Dostęp do regionu formularza w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)
