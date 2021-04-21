---
title: Jak programowo chronić arkusze
description: Dowiedz się, jak za pomocą funkcji ochrony w programie Microsoft Excel uniemożliwić użytkownikom i kodowi modyfikowanie obiektów w arkuszu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 31c0184cbf8f29db6d33d135cf295f8277b55f2e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827102"
---
# <a name="how-to-programmatically-protect-worksheets"></a>Jak programowo chronić arkusze
  Funkcja ochrony w programie Microsoft Office Excel pomaga uniemożliwić użytkownikom i kodowi modyfikowanie obiektów w arkuszu. Domyślnie wszystkie komórki są blokowane po włączeniu ochrony.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 W dostosowaniach na poziomie dokumentu można chronić arkusze przy użyciu projektanta programu Excel. Arkusz można również chronić programowo w czasie uruchamiania w dowolnym typie projektu.

> [!NOTE]
> Nie można Windows Forms kontrolek do chronionych obszarów arkusza.

## <a name="use-the-designer"></a>Korzystanie z projektanta

### <a name="to-protect-a-worksheet-in-the-designer"></a>Aby chronić arkusz w projektancie

1. W grupie **Zmiany** na karcie **Przegląd** kliknij pozycję **Chroń arkusz**.

    Zostanie **wyświetlone okno dialogowe** Chroń arkusz. Można ustawić hasło i opcjonalnie określić pewne akcje, które użytkownicy mogą wykonywać za pomocą arkusza, takie jak formatowanie komórek lub wstawianie wierszy.

   Można również zezwolić użytkownikom na edytowanie określonych zakresów w chronionych arkuszach.

### <a name="to-allow-editing-in-specific-ranges"></a>Aby umożliwić edytowanie w określonych zakresach

1. W grupie **Zmiany** na karcie **Przegląd** kliknij pozycję **Zezwalaj użytkownikom na edytowanie zakresów.**

     Zostanie **wyświetlone okno dialogowe Zezwalaj użytkownikom na edytowanie** zakresów. Możesz określić zakresy, które są odblokowane przy użyciu hasła, oraz użytkowników, którzy mogą edytować zakresy bez hasła.

## <a name="use-code-at-run-time"></a>Korzystanie z kodu w czasie uruchamiania
 Poniższy kod ustawia hasło (przy użyciu zmiennej getPasswordFromUser, która zawiera hasło uzyskane od użytkownika) i umożliwia tylko sortowanie.

### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>Aby chronić arkusz przy użyciu kodu w dostosowywaniu na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> metodę arkusza. W tym przykładzie przyjęto założenie, że pracujesz z arkuszem o nazwie `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet27":::

### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>Aby chronić arkusz przy użyciu kodu w dodatku VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> metodę aktywnego arkusza.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet17":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet17":::

## <a name="see-also"></a>Zobacz też
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [How to: Programmatically remove protection from worksheets (2.01.2017: Programowe usuwanie ochrony z arkuszy)](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)
- [Jak programowo chronić skoroszyty](../vsto/how-to-programmatically-protect-workbooks.md)
- [How to: Programowe ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
