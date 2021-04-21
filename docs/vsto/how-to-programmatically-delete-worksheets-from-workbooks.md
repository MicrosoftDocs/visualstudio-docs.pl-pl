---
title: 'How to: Programowe usuwanie arkuszy ze skoroszytów'
description: Dowiedz się, jak programowo usunąć dowolny arkusz w skoroszycie programu Microsoft Excel, na przykład przy użyciu elementu hosta arkusza.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f3413eaf82b323bc23164687dc3ae3ac0b9d3c48
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825943"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>How to: Programowe usuwanie arkuszy ze skoroszytów
  Możesz usunąć dowolny arkusz w skoroszycie. Aby usunąć arkusz, użyj elementu hosta arkusza lub uzyskaj dostęp do arkusza przy użyciu kolekcji arkuszy skoroszytu.

 [!INCLUDE[appliesto_xlalldocapp](includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Używanie elementu hosta arkusza
 Jeśli arkusz został dodany w czasie projektowania w dostosowywaniu na poziomie dokumentu, użyj metody , <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> aby usunąć określony arkusz. Poniższy kod usuwa arkusz ze skoroszytu, odwołując się bezpośrednio do elementu hosta arkusza.

> [!IMPORTANT]
> Ten kod jest uruchamiany tylko w projektach, które tworzysz przy użyciu dowolnego z następujących szablonów projektów:
>
> - Skoroszyt programu Excel 2013
> - Szablon programu Excel 2013
> - Skoroszyt programu Excel 2010
> - Szablon programu Excel 2010
>
>   Jeśli chcesz wykonać to zadanie w dowolnym innym typie projektu, musisz dodać odwołanie do zestawu **Microsoft.Office.Interop.Excel,** a następnie użyć klas z tego zestawu, aby otworzyć skoroszyt i usunąć arkusz. Aby uzyskać więcej informacji, zobacz [Temat Jak kierować](how-to-target-office-applications-through-primary-interop-assemblies.md) aplikacje pakietu Office za pośrednictwem podstawowych zestawów międzyoptykowych oraz Informacje o podstawowym zestawie [międzyoptykowym programu Excel 2010.](office-primary-interop-assemblies.md)

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Aby usunąć arkusz przy użyciu elementu hosta arkusza

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> metodę `Sheet1` .

     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet17":::
     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet17":::

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Korzystanie z kolekcji Arkuszy skoroszytu programu Excel
 Uzyskiwanie dostępu do arkuszy za pośrednictwem Microsoft Office programu Excel <xref:Microsoft.Office.Interop.Excel.Sheets> w następujących przypadkach:

- Chcesz usunąć arkusz w dodatku VSTO.

- Arkusz, który chcesz usunąć, został utworzony w czasie uruchamiania w dostosowywaniu na poziomie dokumentu.

  Poniższy kod usuwa arkusz ze skoroszytu, odwołując się do arkusza za pośrednictwem numeru indeksu **kolekcji Arkusze.** W tym kodzie przyjęto założenie, że nowy arkusz został utworzony programowo.

> [!IMPORTANT]
> Jeśli chcesz wykonać to zadanie w dowolnym innym typie projektu, musisz dodać odwołanie do zestawu **Microsoft.Office.Interop.Excel,** a następnie użyć klas z tego zestawu, aby otworzyć skoroszyt i usunąć arkusz. Aby uzyskać więcej informacji, zobacz [Temat Jak kierować](how-to-target-office-applications-through-primary-interop-assemblies.md) aplikacje pakietu Office za pomocą podstawowych zestawów międzyoptykowych i Informacje o podstawowym zestawie [międzyoptykowym programu Excel 2010.](office-primary-interop-assemblies.md)

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Aby usunąć arkusz przy użyciu kolekcji Arkusze skoroszytu programu Excel

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> metodę <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji .

     :::code language="csharp" source="codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet18":::
     :::code language="vb" source="codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet18":::

## <a name="see-also"></a>Zobacz też
- [Praca z arkuszami](working-with-worksheets.md)
- [How to: Programowe ukrywanie arkuszy](how-to-programmatically-hide-worksheets.md)
- [How to: Programowe przenoszenie arkuszy w obrębie skoroszytów](how-to-programmatically-move-worksheets-within-workbooks.md)
- [How to: Programowe zaznaczanie arkuszy](how-to-programmatically-select-worksheets.md)
- [How to: Programowe dodawanie nowych arkuszy do skoroszytów](how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Element hosta arkusza](worksheet-host-item.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](global-access-to-objects-in-office-projects.md)
- [Programowe ograniczenia elementów hosta i kontrolek hosta](programmatic-limitations-of-host-items-and-host-controls.md)
