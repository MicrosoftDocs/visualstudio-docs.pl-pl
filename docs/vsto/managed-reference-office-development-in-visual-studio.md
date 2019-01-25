---
title: Zarządzane odniesienia (Office development w programie Visual Studio)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reference [Office development in Visual Studio], 2007 Microsoft Office system
- Office development in Visual Studio, reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aba08ad315c9e3165728b01c552c888f53c94a62
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871614"
---
# <a name="managed-reference-office-development-in-visual-studio"></a>Zarządzane odniesienia (Office development w programie Visual Studio)
  Ta sekcja zawiera dokumentację referencyjną interfejsu API dla przestrzeni nazw i typy, które są używane w pakiecie Office projekty [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Aby uzyskać dokumentację referencyjną interfejsu API o obszary nazw i typy, które są używane w projektach pakietu Office, przeznaczonych dla programu .NET Framework 3.5, zobacz następującą sekcję informacyjną w dokumentacji programu Visual Studio: [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
> [!NOTE]  
>  Zainteresowanych opracowywaniem rozwiązań, które rozszerzają możliwości pakietu Office w [wiele platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatki pakietu Office mieć o niewielkich rozmiarach, w porównaniu do dodatków narzędzi VSTO dla programów i rozwiązań, a następnie utworzyć je przy użyciu niemal dowolnej technologii, takich jak HTML5, JavaScript, CSS3 i XML programowanie dla sieci web.  
  
## <a name="in-this-section"></a>W tej sekcji  
 <xref:Microsoft.Office.Tools>  
 Zawiera klasy, które są wspólne dla programowania rozwiązań pakietu Office. Należą do klasy bazowej dla dodatków narzędzi VSTO dla programów, klas na potrzeby tworzenia niestandardowych okienek zadań w dodatkach VSTO, klas na potrzeby tworzenia inteligentnych tagów w rozwiązaniach programu Excel i Word i klas na potrzeby tworzenia okienka akcji w dostosowaniach na poziomie dokumentu.  
  
 <xref:Microsoft.Office.Tools.Excel>  
 Zawiera formanty hosta i elementów hosta, których można użyć w przypadku rozwiązań dla programu Excel.  
  
 <xref:Microsoft.Office.Tools.Excel.Controls>  
 Zawiera kontrolki programu Excel i formanty Windows Forms, których można użyć w przypadku rozwiązań dla programu Excel.  
  
 <xref:Microsoft.Office.Tools.Outlook>  
 Zawiera klasy używane przez dodatków narzędzi VSTO dla programu Outlook, w tym klasy, które są używane do tworzenia regionów formularzy niestandardowych.  
  
 <xref:Microsoft.Office.Tools.Ribbon>  
 Zawiera klasy, które są używane do programowego modyfikowania dostosowań Wstążki utworzony przy użyciu projektanta wstążki.  
  
 <xref:Microsoft.Office.Tools.Word>  
 Zawiera formanty hosta i elementów hosta, które mogą służyć w rozwiązaniach programu Word.  
  
 <xref:Microsoft.Office.Tools.Word.Controls>  
 Zawiera formanty programu Word i formanty Windows Forms, których można użyć w przypadku rozwiązań dla programu Word.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications>  
 Zawiera <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy i zestaw powiązanych buforowanych danych klasy. W ramach tych zajęć, może służyć do modyfikowania niektórych aspektów dostosowywania poziomie dokumentu na komputerach, które nie mają zainstalowane w Microsoft Office.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>  
 Zawiera <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interfejsu (które można zaimplementować w celu tworzenia *wpis akcji wdrażania* dla rozwiązań pakietu Office), wyjątki, które mogą zostać zgłoszone podczas instalowania rozwiązania do pakietu Office i innych interfejsów API, które są częścią wizualizacji Infrastruktura Studio.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>  
 Zawiera większość wyjątków, które mogą zostać zgłoszone przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], kilka klas, które mogą służyć do danych w pamięci podręcznej dostosowywane na poziomie dokumentu i innych interfejsów API, które są częścią infrastruktury programu Visual Studio.  
  
 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>  
 Zawiera klasy zadania programu MSBuild, które są używane do tworzenia projektów pakietu Office.  
  
## <a name="see-also"></a>Zobacz także  
 [Visual Studio tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Rozpoczynanie pracy &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office development ― przykłady i przewodniki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)  
