---
title: Dostosowywanie wstążki do programu Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 035a38abc2285f744841b1d095387f61a21335a7
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671537"
---
# <a name="customize-a-ribbon-for-outlook"></a>Dostosowywanie wstążki do programu Outlook
  Podczas dostosowywania wstążki w programie Microsoft Outlook pakietu Office, należy rozważyć, gdzie Twoje niestandardowa Wstążka pojawią się w aplikacji. Program Outlook wyświetli wstążki w głównej aplikacji interfejsu użytkownika (UI), a w systemie windows, które otwierają, gdy użytkownicy wykonają pewnych zadań, takich jak tworzenie wiadomości e-mail. Tych aplikacji systemu windows są nazywane inspektorzy.  
  
 ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [w jaki sposób użycia I: projektanta wstążki w celu dostosowania wstążki w programie Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Dodaj niestandardowe wstążki do głównego interfejsu użytkownika aplikacji  
 Głównej aplikacji interfejsu użytkownika w programie Outlook jest nazywany Eksploratora. Jeśli używasz **Wstążka (Projektant graficzny)** elementu, można dodać wstążki do Eksploratora, klikając **RibbonType** właściwości wstążki w **właściwości** oknie a następnie wybierając **Microsoft.Outlook.Explorer**.  
  
## <a name="assign-a-ribbon-to-an-inspector"></a>Przypisz wstążki do Inspektor  
 Inspektor, który chcesz dostosować, określając typ wstążki, który odnosi się do klasy wiadomości, aby inspektor możesz zidentyfikować.  
  
 Jeśli używasz **Wstążka (Projektant graficzny)** element, kliknij przycisk **RibbonType** właściwości wstążki w **właściwości** okna, a następnie wybierz co najmniej jedną wstążki identyfikatory z Lista wartości.  
  
 Możesz dodać więcej niż jeden wstążki do projektu. Jeśli więcej niż jeden Wstążka udostępnia identyfikator wstążki, zastępują `CreateRibbonExtensibilityObject` method in Class metoda `ThisAddin` klasy projektu, aby określić, które wstążki do wyświetlenia w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md). Aby uzyskać więcej informacji o każdym typie wstążki, zobacz artykuł techniczny [dostosowania wstążki w programie Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).  
  
## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Określ typ wstążki za pomocą XML wstążki  
 Jeśli używasz **wstążki (XML)** , należy sprawdzić wartość *ribbonID* parametr <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> metody i zwrócenie odpowiedniego wstążki.  
  
 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> Metody jest generowana automatycznie przez program Visual Studio w pliku kodu wstążki. *RibbonID* parametru jest ciąg, który identyfikuje programu Explorer lub określonego typu inspector. Aby uzyskać pełną listę możliwych wartości *ribbonID* parametru, zobacz artykuł techniczny [dostosowania wstążki w programie Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).  
  
 Poniższy przykład kodu demonstruje sposób wyświetlania niestandardowej tylko we wstążce `Microsoft.Outlook.Mail.Compose` inspector. To narzędzie inspector, która zostanie otwarta, gdy użytkownik tworzy nową wiadomość e-mail. Na Wstążce, aby wyświetlić została określona w `GetResourceText()` metody, która jest generowany w **wstążki** klasy. Aby uzyskać więcej informacji na temat **wstążki** klasy, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także  
 [Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Wstążka — omówienie](../vsto/ribbon-overview.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [XML — wstążka](../vsto/ribbon-xml.md)  
  
  