---
title: 'Instrukcje: Programowe Włączanie ochrony arkuszy'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93acd8466ae90a6db4d1f25d93460e501335af50
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60062220"
---
# <a name="how-to-programmatically-protect-worksheets"></a>Instrukcje: Programowe Włączanie ochrony arkuszy
  Funkcja ochrony w programie Microsoft Office Excel uniemożliwia użytkownikom i kod modyfikowanie obiektów w arkuszu. Domyślnie wszystkie komórki są blokowane po włączeniu ochrony.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 W dostosowaniach na poziomie dokumentu można chronić arkuszy, za pomocą projektanta programu Excel. Arkusz umożliwia również ochronę programowo w czasie wykonywania w dowolnym typem projektu.

> [!NOTE]
>  Nie można dodać kontrolek formularzy Windows Forms obszary arkusza, które są chronione.

## <a name="use-the-designer"></a>Za pomocą projektanta

### <a name="to-protect-a-worksheet-in-the-designer"></a>Aby chronić arkusz w Projektancie

1. W **zmiany** grupy **przeglądu** kliknij pozycję **Chroń arkusz**.

    **Chroń arkusz** pojawi się okno dialogowe. Można ustawić hasła i opcjonalnie określić pewne akcje, które użytkownicy mogą wykonywać na arkusz, takie jak format komórki lub wstawianie wierszy.

   Możesz również zezwolić użytkownikom edytowanie określonych zakresów w arkuszach chronionych.

### <a name="to-allow-editing-in-specific-ranges"></a>Aby umożliwić edycję w określonych zakresach

1. W **zmiany** grupy **przeglądu** kliknij pozycję **Zezwalanie użytkownikom na edycję zakresów**.

     **Zezwalanie użytkownikom na edycję zakresów** pojawi się okno dialogowe. Można określić zakresy, które są odblokowane, przy użyciu hasła i użytkowników, którzy mogą edytować zakresów, bez użycia hasła.

## <a name="use-code-at-runtime"></a>Użyj kodu w czasie wykonywania
 Poniższy kod ustawia hasło (przy użyciu zmiennej getPasswordFromUser, zawierającą uzyskanych od użytkownika hasła) i umożliwia sortowanie tylko.

### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>Aby chronić arkusz przy użyciu kodu w dostosowaniu na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> metoda arkusza. W tym przykładzie założono, że pracujesz z arkusza o nazwie `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#27)]

### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>Aby chronić arkusz przy użyciu kodu w dodatku narzędzi VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> metoda aktywnego arkusza.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#17)]

## <a name="see-also"></a>Zobacz także
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [Instrukcje: Programowe usuwanie ochrony z arkuszy](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)
- [Instrukcje: Programowe Włączanie ochrony skoroszytów](../vsto/how-to-programmatically-protect-workbooks.md)
- [Instrukcje: Programowe ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
