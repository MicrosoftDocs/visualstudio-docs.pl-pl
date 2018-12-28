---
title: 'Instrukcje: Ukrywanie formantów w arkuszu podczas drukowania'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 322c314a768545996f343526367de44c667ce89b
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646802"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Instrukcje: Ukrywanie formantów w arkuszu podczas drukowania
  Podczas drukowania dokument programu Microsoft Office Excel, który zawiera formanty Windows Forms, formanty są widoczne na drukowanego arkusza. Można ukryć formantów podczas drukowania arkusza.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Jeżeli ukrywanie formantów, które wyświetlają dane, takie jak <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, nie są widoczne w arkuszu drukowanych danych w formancie.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Ukrywanie formantów podczas arkusz zostanie wydrukowany  
  
1.  Utwórz lub Otwórz projekt programu Excel w programie Visual Studio i upewnij się, że **Arkusz1** jest widoczne w projektancie. Aby dowiedzieć się, jak tworzenie projektów, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Z **wspólnych formantów** karcie **przybornika**, przeciągnij <xref:Microsoft.Office.Tools.Excel.Controls.Button> kontrolować do komórki na `Sheet1`.  
  
3.  W **właściwości** oknie <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> właściwości **False**.  
  
## <a name="see-also"></a>Zobacz także  
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Formanty Windows Forms na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Instrukcje: Dodawanie kontrolek formularzy Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Instrukcje: Zmiana rozmiaru formantów w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  