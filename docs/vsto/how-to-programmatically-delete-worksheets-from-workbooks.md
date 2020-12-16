---
title: 'Instrukcje: programowe usuwanie arkuszy ze skoroszytów'
description: Dowiedz się, jak można programowo usunąć dowolny arkusz w skoroszycie programu Microsoft Excel przy użyciu elementu hosta arkusza, na przykład.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e9d1330c454e0b9b9f5ad4624c18e4ed1055343d
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527780"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Instrukcje: programowe usuwanie arkuszy ze skoroszytów
  Możesz usunąć dowolny arkusz w skoroszycie. Aby usunąć arkusz, użyj elementu hosta arkusza lub uzyskaj dostęp do arkusza przy użyciu kolekcji arkusze skoroszytu.

 [!INCLUDE[appliesto_xlalldocapp](includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Użyj elementu hosta arkusza
 Jeśli arkusz został dodany w czasie projektowania w dostosowaniu na poziomie dokumentu, użyj <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> metody, aby usunąć określony arkusz. Poniższy kod usuwa arkusz ze skoroszytu, odwołując się bezpośrednio do elementu hosta arkusza.

> [!IMPORTANT]
> Ten kod jest uruchamiany tylko w projektach utworzonych przy użyciu dowolnego z następujących szablonów projektu:
>
> - Skoroszyt programu Excel 2013
> - Szablon programu Excel 2013
> - Skoroszyt programu Excel 2010
> - Szablon programu Excel 2010
>
>   Jeśli chcesz wykonać to zadanie w dowolnym innym typie projektu, musisz dodać odwołanie do zestawu **Microsoft. Office. Interop. Excel** , a następnie należy użyć klas z tego zestawu, aby otworzyć skoroszyt i usunąć arkusz. Aby uzyskać więcej informacji, zobacz [jak: docelowa aplikacja pakietu Office za poorednictwem zestawów podstawowych międzyoperacyjnych](how-to-target-office-applications-through-primary-interop-assemblies.md) i [odwołania do podstawowego zestawu międzyoperacyjnego programu Excel 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Aby usunąć arkusz przy użyciu elementu hosta arkusza

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> metodę `Sheet1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#17](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Korzystanie z kolekcji arkuszy skoroszytu programu Excel
 Dostęp do arkuszy za pomocą kolekcji programu Excel Microsoft Office <xref:Microsoft.Office.Interop.Excel.Sheets> w następujących przypadkach:

- Chcesz usunąć arkusz w dodatku narzędzi VSTO.

- Arkusz, który ma zostać usunięty, został utworzony w czasie wykonywania w dostosowaniu na poziomie dokumentu.

  Poniższy kod usuwa arkusz ze skoroszytu, odwołując się do arkusza za pośrednictwem numeru indeksu kolekcji **arkuszy** . W tym kodzie założono, że nowy arkusz został utworzony programowo.

> [!IMPORTANT]
> Jeśli chcesz wykonać to zadanie w dowolnym innym typie projektu, musisz dodać odwołanie do zestawu **Microsoft. Office. Interop. Excel** , a następnie należy użyć klas z tego zestawu, aby otworzyć skoroszyt i usunąć arkusz. Aby uzyskać więcej informacji, zobacz [jak: docelowa aplikacja pakietu Office za poorednictwem zestawów podstawowych międzyoperacyjnych](how-to-target-office-applications-through-primary-interop-assemblies.md) i [odwołania do podstawowego zestawu międzyoperacyjnego programu Excel 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Aby usunąć arkusz przy użyciu kolekcji arkuszy skoroszytu programu Excel

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> metodę <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji.

     [!code-csharp[Trin_VstcoreExcelAutomation#18](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]

## <a name="see-also"></a>Zobacz też
- [Pracuj z arkuszami](working-with-worksheets.md)
- [Instrukcje: programowe ukrywanie arkuszy](how-to-programmatically-hide-worksheets.md)
- [Instrukcje: Programowane przenoszenie arkuszy w skoroszytach](how-to-programmatically-move-worksheets-within-workbooks.md)
- [Instrukcje: Programowane Wybieranie arkuszy](how-to-programmatically-select-worksheets.md)
- [Instrukcje: Programowane dodawanie nowych arkuszy do skoroszytów](how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Element hosta arkusza](worksheet-host-item.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](global-access-to-objects-in-office-projects.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](programmatic-limitations-of-host-items-and-host-controls.md)
