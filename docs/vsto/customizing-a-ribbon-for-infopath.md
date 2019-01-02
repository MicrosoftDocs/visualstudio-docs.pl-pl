---
title: Dostosowywanie wstążki do InfoPath
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: c69ef50662bd1b98e896d1b8d3933d23be26123c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837267"
---
# <a name="customize-a-ribbon-for-infopath"></a>Dostosowywanie wstążki do InfoPath
  Podczas dostosowywania wstążki w programie Microsoft InfoPath pakietu Office, należy rozważyć, gdzie Twoje niestandardowa Wstążka pojawią się w aplikacji. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] może wyświetlać wstążki w trzech następujących rodzajów InfoPath aplikacji systemu windows:  
  
- Windows, wyświetlające szablonu formularza, który jest otwierany w trybie projektowania.  
  
- Windows, do wyświetlania formularza, który jest oparty na szablonie formularza.  
  
- Okno podglądu wydruku.  
  
  **Dotyczy:** Informacje przedstawione w tym temacie dotyczą projektów dodatku VSTO dla programu InfoPath 2010. Aby uzyskać więcej informacji, zobacz [funkcje, które są dostępne przez typ aplikacji i projektów pakietu Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
  Użytkownicy i projektanci Otwórz szablon formularza w trybie projektowania, aby zmodyfikować wygląd i układ szablonu. Użytkownicy otworzyć formularze, które opierają się w szablonie formularza, aby dodać zawartość.  
  
  Okno podglądu wydruku umożliwia projektantów i użytkowników wyświetlić podgląd strony formularza lub szablonu formularza, przed ich drukowanie.  
  
> [!NOTE]  
>  **AddIns** karta nie pojawi się w oknie Podgląd wydruku. Jeśli chcesz, aby niestandardowej karty pojawią się w oknie Podgląd wydruku, upewnij się, że **OfficeId** nie ustawiono właściwości karty **TabAddIns**.  
  
 Należy określić typ wstążki każdego okna, w którym chcesz Wstążkę w taki sposób, w celu są wyświetlane.  
  
## <a name="specify-the-ribbon-type-in-the-ribbon-designer"></a>Określ typ Wstążkę w Projektancie wstążki  
 Jeśli używasz **Wstążka (Projektant graficzny)** element, kliknij przycisk **RibbonType** właściwości wstążki w **właściwości** okna, a następnie wybierz dowolną identyfikatorów wstążki opisane w poniższej tabeli.  
  
|Identyfikator wstążki|Okno, w którym wstążce pojawi się po uruchomieniu projektu|  
|---------------|---------------------------------------------------------------------|  
|**Microsoft.InfoPath.Designer**|Windows, wyświetlające szablonu formularza, który jest otwierany w trybie projektowania.|  
|**Microsoft.InfoPath.Editor**|Windows, do wyświetlania formularza, który jest oparty na szablonie formularza.|  
|**Microsoft.InfoPath.PrintPreview**|Okno podglądu wydruku.|  
  
 Możesz dodać więcej niż jeden wstążki do projektu. Jeśli więcej niż jeden wstążki udostępnić identyfikator wstążki, zastępują `CreateRibbonExtensibilityObject` method in Class metoda `ThisAddin` klasy projektu, aby określić, które wstążki do wyświetlenia w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Określ typ wstążki za pomocą XML wstążki  
 Jeśli używasz **wstążki (XML)** , należy sprawdzić wartość *ribbonID* parametr <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> metody i zwrócenie odpowiedniego wstążki.  
  
 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> Metody jest generowana automatycznie przez program Visual Studio w pliku kodu wstążki. *RibbonID* parametru jest ciąg, który identyfikuje typ okna programu InfoPath, które jest otwierane.  
  
 Poniższy przykład kodu demonstruje sposób wyświetlania niestandardowa Wstążka tylko w oknie, który wyświetla szablonu formularza w trybie projektowania. Na Wstążce, aby wyświetlić została określona w `GetResourceText()` metody, która jest generowany w klasie wstążki. Aby uzyskać więcej informacji o klasie wstążki, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]  
  
## <a name="see-also"></a>Zobacz także  
 [Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Wstążka — omówienie](../vsto/ribbon-overview.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [XML — wstążka](../vsto/ribbon-xml.md)  
