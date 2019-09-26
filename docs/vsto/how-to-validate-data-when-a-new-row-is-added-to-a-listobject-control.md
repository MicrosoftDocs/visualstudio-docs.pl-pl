---
title: Sprawdź poprawność danych po dodaniu nowego wiersza do kontrolki ListObject
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f65bbc374c1d0ec2a940ff98fcc6f04e5391b2db
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255681"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Porady: Sprawdź poprawność danych po dodaniu nowego wiersza do kontrolki ListObject
  Użytkownicy mogą dodawać nowe wiersze do <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki, która jest powiązana z danymi. Możesz sprawdzić poprawność danych użytkownika przed zatwierdzeniem zmian w źródle danych.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>Sprawdzanie poprawności danych
 Po każdym dodaniu wiersza do elementu <xref:Microsoft.Office.Tools.Excel.ListObject> , który jest powiązany z danymi <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> , zdarzenie jest zgłaszane. To zdarzenie można obsłużyć w celu przeprowadzenia walidacji danych. Na przykład, jeśli aplikacja wymaga, aby do źródła danych można było dodać tylko pracowników między 18 a 65, sprawdź, czy wprowadzony wiek znajduje się w tym zakresie przed dodaniem wiersza.

> [!NOTE]
> Oprócz klienta należy zawsze sprawdzać dane wejściowe użytkownika na serwerze. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie aplikacji klienckich](/dotnet/framework/data/adonet/secure-client-applications).

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Aby sprawdzić poprawność danych po dodaniu nowego wiersza do elementu ListObject powiązanego z danymi

1. Utwórz zmienne dla identyfikatora i <xref:System.Data.DataTable> na poziomie klasy.

     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]

2. Utwórz nowe <xref:System.Data.DataTable> i Dodaj przykładowe kolumny i dane `Startup` do procedury obsługi `Sheet1` zdarzeń klasy (w projekcie na poziomie dokumentu) lub `ThisAddIn` klasy (w projekcie dodatku VSTO).

     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]

3. Dodaj kod do `list1_BeforeAddDataBoundRow` programu obsługi zdarzeń, aby sprawdzić, czy wprowadzony wiek mieści się w dopuszczalnym zakresie.

     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]

## <a name="compile-the-code"></a>Skompilować kod
 W tym przykładzie kodu założono, że masz <xref:Microsoft.Office.Tools.Excel.ListObject> istniejącą `list1` nazwę w arkuszu, w którym występuje ten kod.

## <a name="see-also"></a>Zobacz także
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [ListObject — formant](../vsto/listobject-control.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Instrukcje: Mapowanie kolumn ListObject na dane](../vsto/how-to-map-listobject-columns-to-data.md)
