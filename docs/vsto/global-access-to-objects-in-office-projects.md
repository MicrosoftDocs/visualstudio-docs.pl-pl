---
title: Globalny dostęp do obiektów w projektach pakietu Office
description: Dowiedz się, jak za pomocą klasy Globals uzyskać dostęp do kilku różnych elementów projektu w czasie uruchamiania z dowolnego kodu w projekcie.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b939131f388642b452445e0afee0f5e38d2a5195
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825540"
---
# <a name="global-access-to-objects-in-office-projects"></a>Globalny dostęp do obiektów w projektach pakietu Office
  Podczas tworzenia projektu pakietu Office program Visual Studio automatycznie generuje klasę o nazwie `Globals` w projekcie. Możesz użyć klasy , aby uzyskać dostęp do kilku różnych elementów projektu w czasie `Globals` uruchamiania z dowolnego kodu w projekcie.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="how-to-use-the-globals-class"></a>Jak używać klasy Globals
 `Globals` jest klasą statyczną, która przechowuje odwołania do niektórych elementów w projekcie. Przy użyciu klasy można uzyskać dostęp do następujących elementów z dowolnego kodu w `Globals` projekcie w czasie uruchamiania:

- Klasy `ThisWorkbook` i `Sheet` *n* w skoroszycie programu Excel lub projekcie szablonu. Dostęp do tych obiektów można uzyskać za pomocą `Globals.ThisWorkbook` właściwości `Sheet` *i n.*

- Klasa `ThisDocument` w projekcie dokumentu lub szablonu programu Word. Dostęp do tego obiektu można uzyskać za pomocą `Globals.ThisDocument` właściwości .

- Klasa `ThisAddIn` w projekcie dodatku VSTO. Dostęp do tego obiektu można uzyskać za pomocą `Globals.ThisAddIn` właściwości .

- Wszystkie wstążki w projekcie dostosowane przy użyciu Projektanta wstążki. Dostęp do wstążek można uzyskać za pomocą `Globals.Ribbons` właściwości . Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do wstążki w czasie uruchamiania.](../vsto/accessing-the-ribbon-at-run-time.md)

- Wszystkie regiony formularzy programu Outlook w projekcie dodatku VSTO programu Outlook. Dostęp do regionów formularzy można uzyskać przy użyciu `Globals.FormRegions` właściwości . Aby uzyskać więcej informacji, zobacz [Access a form region at run time (Uzyskiwanie dostępu do regionu formularza w czasie uruchamiania).](../vsto/accessing-a-form-region-at-run-time.md)

- Obiekt fabryki, który umożliwia tworzenie kontrolek wstążki i hostuje elementy w czasie uruchamiania w projektach docelowych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Dostęp do tego obiektu można uzyskać za pomocą `Globals.Factory` właściwości . Ten obiekt jest wystąpieniem klasy, która implementuje jeden z następujących interfejsów:

  - [Microsoft.Office.Tools.Factory](xref:Microsoft.Office.Tools.Factory)

  - [Microsoft.Office.Tools.Excel.Factory](xref:Microsoft.Office.Tools.Excel.Factory)

  - [Microsoft.Office.Tools.Outlook.Factory](xref:Microsoft.Office.Tools.Outlook.Factory)

  - [Microsoft.Office.Tools.Word.Factory](xref:Microsoft.Office.Tools.Word.Factory)

  Na przykład możesz użyć właściwości , aby wstawić tekst do kontrolki, gdy użytkownik kliknie przycisk w okienku akcji w projekcie na poziomie dokumentu `Globals.Sheet1` <xref:Microsoft.Office.Tools.Excel.NamedRange> dla programu `Sheet1` Excel.

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet1":::
  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs" id="Snippet1":::

 Kod, który próbuje użyć klasy przed zainicjowanie dokumentu lub dodatku VSTO, może zgłosić `Globals` wyjątek czasu uruchomienia. Na przykład użycie funkcji podczas deklarowania zmiennej na poziomie klasy może się nie powieść, ponieważ klasa może nie zostać zainicjowana z odwołaniami do wszystkich elementów hosta przed zainicjowanym zadeklarowanym `Globals` `Globals` obiektem.

> [!NOTE]
> Klasa `Globals` nigdy nie jest inicjowana w czasie projektowania, ale wystąpienia kontrolne są tworzone przez projektanta. Oznacza to, że w przypadku utworzenia kontrolki użytkownika, która używa właściwości klasy z wewnątrz klasy kontroli użytkownika, przed podjęciem próby użycia zwróconego obiektu należy sprawdzić, czy właściwość zwraca wartość `Globals` **null.**

## <a name="see-also"></a>Zobacz też
- [Uzyskiwanie dostępu do wstążki w czasie uruchamiania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Uzyskiwanie dostępu do regionu formularza w czasie uruchamiania](../vsto/accessing-a-form-region-at-run-time.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Element hosta dokumentu](../vsto/document-host-item.md)
- [Element hosta skoroszytu](../vsto/workbook-host-item.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
