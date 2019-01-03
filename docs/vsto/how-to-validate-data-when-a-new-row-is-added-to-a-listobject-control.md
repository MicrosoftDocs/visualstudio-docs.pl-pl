---
title: 'Instrukcje: Walidacja danych po dodaniu nowego rzędu do kontrolki ListObject'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1f6fd03238f9b477f7530353b8b10afb71a41edd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989844"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Instrukcje: Walidacja danych po dodaniu nowego rzędu do kontrolki ListObject
  Użytkownicy mogą dodawać nowe wiersze do <xref:Microsoft.Office.Tools.Excel.ListObject> formant, który jest powiązany z danymi. Możesz walidować dane użytkownika przed zatwierdzeniem zmian w źródle danych.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="data-validation"></a>Sprawdzanie poprawności danych  
 Zawsze, gdy wiersz zostanie dodany do <xref:Microsoft.Office.Tools.Excel.ListObject> , jest powiązany z danymi, <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> zdarzenie jest wywoływane. Może obsługiwać to zdarzenie, aby wykonać walidację danych. Na przykład jeśli aplikacja wymaga, że tylko pracownicy między w wieku od 18 i 65 można dodać do źródła danych, sprawdź, czy wiek wprowadzono mieści się w zakresie przed dodaniem wiersza.  
  
> [!NOTE]  
>  Należy zawsze sprawdzić dane wejściowe użytkownika na serwerze, oprócz klienta. Aby uzyskać więcej informacji, zobacz [zabezpieczanie aplikacje klienckich](/dotnet/framework/data/adonet/secure-client-applications).  
  
### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Aby sprawdzić poprawność danych, gdy nowy wiersz jest dodawany do powiązanych z danymi ListObject  
  
1.  Tworzenie zmiennych dla Identyfikatora i <xref:System.Data.DataTable> na poziomie klasy.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]  
  
2.  Utwórz nową <xref:System.Data.DataTable> i dodawanie przykładowe kolumny i dane w `Startup` program obsługi zdarzeń `Sheet1` klasy (w projekcie poziomie dokumentu) lub `ThisAddIn` klasy (w projekcie dodatku narzędzi VSTO).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]  
  
3.  Dodaj kod, aby `list1_BeforeAddDataBoundRow` program obsługi zdarzeń, aby sprawdzić, czy wiek wprowadzono mieści się w dopuszczalnym zakresem.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]  
  
## <a name="compile-the-code"></a>Skompilować kod  
 W tym przykładzie kodu założono, że istniejące <xref:Microsoft.Office.Tools.Excel.ListObject> o nazwie `list1` w arkuszu, w której występuje ten kod.  
  
## <a name="see-also"></a>Zobacz także  
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ListObject — formant](../vsto/listobject-control.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Instrukcje: Mapowanie kolumn ListObject do danych](../vsto/how-to-map-listobject-columns-to-data.md)  
