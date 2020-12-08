---
title: Globalny dostęp do obiektów w projektach pakietu Office
description: Dowiedz się, jak można użyć klasy Globals, aby uzyskać dostęp do kilku różnych elementów projektu w czasie wykonywania z dowolnego kodu w projekcie.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument_Shutdown
- ThisDocument_Startup
- Globals class, object global access
- worksheets [Office development in Visual Studio], global access
- documents [Office development in Visual Studio], global access
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- application-level addins [Office development in Visual Studio]
- addins [Office development in Visual Studio], events
- workbooks [Office development in Visual Studio], global access
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio]
- Startup event
- Shutdown event
- projects [Office development in Visual Studio], global access
- Office documents [Office development in Visual Studio, global access
- ThisAddin_Startup
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e2653f314edf07c4dcca6d3afc74af64c548af35
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846392"
---
# <a name="global-access-to-objects-in-office-projects"></a>Globalny dostęp do obiektów w projektach pakietu Office
  Podczas tworzenia projektu pakietu Office Program Visual Studio automatycznie generuje klasę o nazwie `Globals` w projekcie. Można użyć klasy, `Globals` Aby uzyskać dostęp do kilku różnych elementów projektu w czasie wykonywania z dowolnego kodu w projekcie.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="how-to-use-the-globals-class"></a>Jak używać klasy Globals
 `Globals` jest klasą statyczną, która zachowuje odwołania do określonych elementów w projekcie. Korzystając z `Globals` klasy, można uzyskać dostęp do następujących elementów z dowolnego kodu w projekcie w czasie wykonywania:

- `ThisWorkbook`Klasy i `Sheet` *n* w skoroszycie programu Excel lub w projekcie szablonu. Dostęp do tych obiektów można uzyskać przy użyciu `Globals.ThisWorkbook` `Sheet` *n* właściwości i.

- `ThisDocument`Klasa w dokumencie programu Word lub projekcie szablonu. Dostęp do tego obiektu można uzyskać przy użyciu `Globals.ThisDocument` właściwości.

- `ThisAddIn`Klasa w projekcie dodatku VSTO. Dostęp do tego obiektu można uzyskać przy użyciu `Globals.ThisAddIn` właściwości.

- Wszystkie wstążki w projekcie, które zostały dostosowane przy użyciu projektanta wstążki. Możesz uzyskać dostęp do wstążki przy użyciu `Globals.Ribbons` właściwości. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md).

- Wszystkie regiony formularzy programu Outlook w projekcie dodatku VSTO programu Outlook. Możesz uzyskać dostęp do regionów formularza przy użyciu `Globals.FormRegions` właściwości. Aby uzyskać więcej informacji, zobacz [dostęp do regionu formularza w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md).

- Obiekt fabryki, który umożliwia tworzenie kontrolek wstążki i elementów hosta w czasie wykonywania w projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Dostęp do tego obiektu można uzyskać przy użyciu `Globals.Factory` właściwości. Ten obiekt jest wystąpieniem klasy implementującej jeden z następujących interfejsów:

  - [Microsoft. Office. Tools. Factory](xref:Microsoft.Office.Tools.Factory)

  - [Microsoft. Office. Tools. Excel. Factory](xref:Microsoft.Office.Tools.Excel.Factory)

  - [Microsoft. Office. Tools. Outlook. Factory](xref:Microsoft.Office.Tools.Outlook.Factory)

  - [Microsoft. Office. Tools. Word. Factory](xref:Microsoft.Office.Tools.Word.Factory)

  Na przykład można użyć `Globals.Sheet1` właściwości, aby wstawić tekst do <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki, `Sheet1` gdy użytkownik kliknie przycisk w okienku Akcje w projekcie na poziomie dokumentu dla programu Excel.

  [!code-vb[Trin_VstcoreProgramming#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#1)]
  [!code-csharp[Trin_VstcoreProgramming#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#1)]

 Kod, który próbuje użyć `Globals` klasy przed zainicjowaniem dokumentu lub dodatku VSTO może zgłosić wyjątek czasu wykonywania. Na przykład użycie `Globals` podczas deklarowania zmiennej na poziomie klasy może się nie powieść, ponieważ `Globals` Klasa może nie zostać zainicjowana z odwołaniami do wszystkich elementów hosta przed wystąpieniem zadeklarowanego obiektu.

> [!NOTE]
> `Globals`Klasa nigdy nie została zainicjowana w czasie projektowania, ale instancje sterujące są tworzone przez projektanta. Oznacza to, że w przypadku utworzenia kontrolki użytkownika, która używa właściwości `Globals` klasy z wewnątrz klasy kontrolki użytkownika, należy sprawdzić, czy właściwość zwraca **wartość null** przed podjęciem próby użycia zwracanego obiektu.

## <a name="see-also"></a>Zobacz także
- [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Dostęp do regionu formularza w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Element hosta dokumentu](../vsto/document-host-item.md)
- [Element hosta skoroszytu](../vsto/workbook-host-item.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
