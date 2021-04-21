---
title: 'How to: Programowe przenoszenie arkuszy w obrębie skoroszytów'
description: Dowiedz się, jak programowo zmienić położenie arkuszy względem innych arkuszy w skoroszycie programu Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd05dcb39c295d4d1ebb39d933c643f61c6d921c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827295"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>How to: Programowe przenoszenie arkuszy w obrębie skoroszytów
  Można programowo zmienić położenie arkuszy względem innych arkuszy w skoroszycie. Jeśli nie określisz lokalizacji dla przeniesionego arkusza, program Excel utworzy nowy skoroszyt, który będzie go zawierał.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Aby przenieść arkusz w dostosowywaniu na poziomie dokumentu

1. Przypisz łączną liczbę arkuszy w skoroszycie do zmiennej, a następnie przenieś pierwszy arkusz tak, aby stał się ostatnim.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet24":::

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>Aby przenieść arkusz w dodatku VSTO

1. Przypisz łączną liczbę arkuszy w skoroszycie do zmiennej, a następnie przenieś pierwszy arkusz tak, aby stał się ostatnim.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet16":::

## <a name="see-also"></a>Zobacz też
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [How to: Programowe ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)
- [How to: Programowe usuwanie arkuszy ze skoroszytów](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [How to: Programmatically protect arkusze](../vsto/how-to-programmatically-protect-worksheets.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
