---
title: Dokumentacja zarządzana (Programowanie Office w Visual Studio)
ms.date: 08/14/2019
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
ms.openlocfilehash: 137031202075d1c646cc7415042dd8d6eab72b78
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985768"
---
# <a name="managed-reference-office-development-in-visual-studio"></a>Dokumentacja zarządzana (Programowanie Office w Visual Studio)
  Ta sekcja zawiera dokumentację referencyjną interfejsu API dla przestrzeni nazw i typów, które są używane w projektach pakietu Office przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](includes/net-v45-md.md)]. Aby uzyskać dokumentację interfejsu API dotyczącą przestrzeni nazw i typów, które są używane w projektach pakietu Office przeznaczonych dla .NET Framework 3,5, zobacz następującą sekcję referencyjną w dokumentacji programu Visual Studio: [informacje zarządzane (Programowanie Office w Visual Studio )](managed-reference-office-development-in-visual-studio.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>W tej sekcji
 <xref:Microsoft.Office.Tools>

 Zawiera klasy wspólne do programowania rozwiązań pakietu Office. Obejmują one klasę bazową dla dodatków narzędzi VSTO, klasy służące do tworzenia niestandardowych okienek zadań w dodatkach narzędzi VSTO, klasy służące do tworzenia tagów inteligentnych w rozwiązaniach Excel i Word oraz klasy służące do tworzenia okienek akcji w dostosowaniach na poziomie dokumentu.

 <xref:Microsoft.Office.Tools.Excel>

 Zawiera kontrolki hosta i elementy hosta, które mogą być używane w rozwiązaniach dla programu Excel.

 <xref:Microsoft.Office.Tools.Excel.Controls>

 Zawiera kontrolki programu Excel i Windows Forms kontrolki, które mogą być używane w rozwiązaniach dla programu Excel.

 <xref:Microsoft.Office.Tools.Outlook>

 Zawiera klasy używane przez dodatki narzędzi VSTO dla programu Outlook, w tym klasy, które są używane do tworzenia niestandardowych regionów formularzy.

 <xref:Microsoft.Office.Tools.Ribbon>

 Zawiera klasy, które są używane do programistycznego modyfikowania dostosowań Wstążki utworzonych przy użyciu projektanta wstążki.

 <xref:Microsoft.Office.Tools.Word>

 Zawiera kontrolki hosta i elementy hosta, które mogą być używane w rozwiązaniach dla programu Word.

 <xref:Microsoft.Office.Tools.Word.Controls>

 Zawiera kontrolki programu Word i kontrolki Windows Forms, które mogą być używane w rozwiązaniach dla programu Word.

 <xref:Microsoft.VisualStudio.Tools.Applications>

 Zawiera klasę <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> i zestaw powiązanych klas danych w pamięci podręcznej. Te klasy mogą służyć do modyfikowania niektórych aspektów dostosowywania na poziomie dokumentu na komputerach, na których nie zainstalowano Microsoft Office.

 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>

 Zawiera interfejs <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> (który można zaimplementować w celu utworzenia *akcji po wdrożeniu* dla rozwiązania pakietu Office), wyjątków, które mogą być zgłaszane podczas instalowania rozwiązania pakietu Office i innych interfejsów API, które są częścią infrastruktury programu Visual Studio.

 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>

 Zawiera większość wyjątków, które mogą być zgłaszane przez [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)], kilka klas, które mogą być używane do buforowania danych w dostosowaniach na poziomie dokumentu oraz inne interfejsy API, które są częścią infrastruktury programu Visual Studio.

 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>

 Zawiera klasy zadań programu MSBuild, które są używane do kompilowania projektów pakietu Office.

## <a name="see-also"></a>Zobacz także
- [Omówienie programu Visual Studio Tools for Office Runtime](visual-studio-tools-for-office-runtime-overview.md)
- [Wprowadzenie &#40;do programowania pakietu Office w programie Visual Studio&#41;](getting-started-office-development-in-visual-studio.md)
- [Przykłady i przewodniki dotyczące programowania pakietu Office](office-development-samples-and-walkthroughs.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](designing-and-creating-office-solutions.md)
