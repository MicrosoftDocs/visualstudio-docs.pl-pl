---
title: Weryfikowanie danych po dodaniu nowego wiersza do kontrolki ListObject
description: Dowiedz się, jak za pomocą Visual Studio walidować dane po dodaniu nowego wiersza do kontrolki ListObject.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a7002cdc0787850fc7be5a782f3cf3a2101d7593
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825722"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>How to: Validate data when a new row is added to a ListObject control (Dzieje się tak po dodaniu nowego wiersza do kontrolki ListObject)
  Użytkownicy mogą dodawać nowe wiersze do <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki powiązanej z danymi. Przed zatwierdzeniem zmian w źródle danych możesz zweryfikować dane użytkownika.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>Walidacja danych
 Za każdym razem, gdy wiersz jest dodawany do <xref:Microsoft.Office.Tools.Excel.ListObject> tabeli powiązanej z danymi, <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> zdarzenie jest wywoływane. Możesz obsłużyć to zdarzenie, aby przeprowadzić walidację danych. Jeśli na przykład aplikacja wymaga dodania do źródła danych tylko pracowników w wieku od 18 do 65 lat, przed dodaniem wiersza sprawdź, czy wprowadzony wiek mieści się w tym zakresie.

> [!NOTE]
> Oprócz klienta należy zawsze sprawdzać dane wejściowe użytkownika na serwerze. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie aplikacji klienckich.](/dotnet/framework/data/adonet/secure-client-applications)

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Aby zweryfikować dane po dodaniu nowego wiersza do powiązanego z danymiobiektu ListObject

1. Utwórz zmienne dla identyfikatora i <xref:System.Data.DataTable> na poziomie klasy.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet8":::

2. Utwórz nową i dodaj przykładowe kolumny oraz dane w obsłudze zdarzeń klasy (w projekcie na poziomie dokumentu) lub klasy (w projekcie <xref:System.Data.DataTable> `Startup` `Sheet1` `ThisAddIn` dodatku VSTO).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet9":::

3. Dodaj kod do `list1_BeforeAddDataBoundRow` procedury obsługi zdarzeń, aby sprawdzić, czy wprowadzony wiek mieści się w akceptowalnym zakresie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet10":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 W tym przykładzie kodu założono, że masz istniejącą <xref:Microsoft.Office.Tools.Excel.ListObject> nazwę w `list1` arkuszu, w którym pojawia się ten kod.

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Kontrolki w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie uruchamiania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [ListObject, kontrolka](../vsto/listobject-control.md)
- [Automatyzowanie programu Excel przy użyciu obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [How to: Map ListObject columns to data (Jak mapować kolumny ListObject na dane)](../vsto/how-to-map-listobject-columns-to-data.md)
