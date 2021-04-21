---
title: Tworzyć programowo nowe skoroszyty
description: Dowiedz się, jak programowo utworzyć nowy skoroszyt programu Microsoft Excel przy użyciu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8a0a6e0b7b81c472ce03b1255c2c6899df0389da
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825982"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Tworzyć programowo nowe skoroszyty
  Gdy tworzysz skoroszyt programowo, jest to obiekt <xref:Microsoft.Office.Interop.Excel.Workbook> natywny, a nie element <xref:Microsoft.Office.Tools.Excel.Workbook> hosta.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Element hosta dla <xref:Microsoft.Office.Tools.Excel.Workbook> obiektu można wygenerować w <xref:Microsoft.Office.Interop.Excel.Workbook> projekcie dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Extend Word documents and Excel workbooks in VSTO Add-ins at run time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)(Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania).

## <a name="to-create-a-new-workbook"></a>Aby utworzyć nowy skoroszyt

1. Użyj <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> metody <xref:Microsoft.Office.Interop.Excel.Workbooks> kolekcji .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet1":::

    > [!NOTE]
    > Skoroszyt można utworzyć na podstawie szablonu innego niż szablon domyślny: przekaż szablon, którego chcesz użyć jako parametru, do <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> metody .

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Praca ze skoroszytami](../vsto/working-with-workbooks.md)
- [How to: Programmatically open workbooks (2017: Programowe otwieranie skoroszytów)](../vsto/how-to-programmatically-open-workbooks.md)
- [How to: Programmatically save workbooks (2017: Programowe zapisywanie skoroszytów)](../vsto/how-to-programmatically-save-workbooks.md)
- [2019: Programowe zamykanie skoroszytów](../vsto/how-to-programmatically-close-workbooks.md)
- [Programowe ograniczenia elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
