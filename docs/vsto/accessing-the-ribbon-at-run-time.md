---
title: Dostęp do wstążki w czasie wykonywania
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9a20297ee0d60173cbd0513f3d34e12f12388bdb
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304626"
---
# <a name="access-the-ribbon-at-runtime"></a>Dostęp do wstążki w czasie wykonywania
  Można napisać kod, aby pokazać, ukrywanie i modyfikowania Wstążki i umożliwienie użytkownikom uruchomić kod z kontrolek w niestandardowego okienka zadań, okienka akcji lub region formularza programu Outlook.  

 Dostęp do wstążki przy użyciu `Globals` klasy. Dla projektów programu Outlook można uzyskać dostęp do taśmy, które pojawiają się w określonym oknie inspektora programu Outlook lub Outlook Eksploratora.  

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Dostęp do wstążki przy użyciu klasy globalne  
 Możesz użyć `Globals` klasy dostępu do wstążki w projektach na poziomie dokumentu lub projekt dodatku narzędzi VSTO dla programów w dowolnym miejscu w projekcie.  

 Aby uzyskać więcej informacji na temat `Globals` klasy, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  

 W poniższym przykładzie użyto `Globals` klasy w celu dostępu do wstążki niestandardowej o nazwie `Ribbon1` i Ustaw tekst, który pojawia się w polu kombi na Wstążce aby `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]  

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Dostępu do kolekcji wstążek, które pojawiają się w określonym oknie inspektora programu Outlook  
 Możesz uzyskać dostęp zbiór wstążek, które są wyświetlane w programie Outlook *inspektorzy*. Inspektor jest oknem, która zostanie otwarta w programie Outlook, gdy użytkownicy wykonają pewnych zadań, takich jak tworzenie wiadomości e-mail. Aby uzyskać dostęp do wstążki oknie Inspektora, należy wywołać `Ribbons` właściwość `Globals` klasy i przekazać <xref:Microsoft.Office.Interop.Outlook.Inspector> obiekt, który reprezentuje Inspektor.  

 Poniższy przykład pobiera kolekcję wstążki Inspector, który aktualnie ma fokus. W tym przykładzie następnie uzyskuje dostęp do wstążki o nazwie `Ribbon1` i ustawia tekst, który pojawia się w polu kombi na Wstążce aby `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]  

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Dostępu do kolekcji wstążek, które są wyświetlane dla określonych Eksplorator programu Outlook  
 Możesz uzyskać dostęp zbiór wstążek, które są wyświetlane w programie Outlook *Explorer*. Eksplorator jest głównej aplikacji interfejsu użytkownika (UI) dla wystąpienia programu Outlook. Aby uzyskać dostęp do wstążki okno Eksploratora, należy wywołać `Ribbons` właściwość `Globals` klasy i przekazać <xref:Microsoft.Office.Interop.Outlook.Explorer> obiekt, który reprezentuje Eksploratora.  

 Poniższy przykład pobiera kolekcję wstążki Explorer, który aktualnie ma fokus. W tym przykładzie następnie uzyskuje dostęp do wstążki o nazwie `Ribbon1` i ustawia tekst, który pojawia się w polu kombi na Wstążce aby `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]  

## <a name="see-also"></a>Zobacz także  
 [Wstążka — omówienie](../vsto/ribbon-overview.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [XML — Wstążka](../vsto/ribbon-xml.md)   
 [Model obiektu Wstążka ― omówienie](../vsto/ribbon-object-model-overview.md)   
 [Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Wskazówki: Aktualizowanie kontrolek na Wstążce w czasie wykonywania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Dostęp do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)  
