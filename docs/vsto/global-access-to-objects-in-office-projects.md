---
title: Globalny dostęp do obiektów w projektach pakietu Office
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 843eba9cceefb2360ed24284a80f4359d092fd89
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909076"
---
# <a name="global-access-to-objects-in-office-projects"></a>Globalny dostęp do obiektów w projektach pakietu Office
  Podczas tworzenia projektu pakietu Office program Visual Studio automatycznie generuje klasę o nazwie `Globals` w projekcie. Możesz użyć `Globals` klasy, aby mieć dostęp do kilku elementów inny projekt, w czasie wykonywania z dowolnego kodu w projekcie.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="how-to-use-the-globals-class"></a>Jak używać klasy globalne  
 `Globals` jest klasą statyczną, który utrzymuje odwołania do określonych elementów w projekcie. Za pomocą `Globals` klasy, są dostępne następujące elementy w projekcie kodu w czasie wykonywania:  
  
- `ThisWorkbook` i `Sheet` *n* klasy w projekcie skoroszytem lub szablonem programu Excel. Dostęp do tych obiektów za pomocą `Globals.ThisWorkbook` i `Sheet` *n* właściwości.  
  
- `ThisDocument` Klasy w projekcie dokumentem lub szablonem programu Word. Dostęp do obiektu za pomocą `Globals.ThisDocument` właściwości.  
  
- `ThisAddIn` Klasy w projekcie dodatku narzędzi VSTO. Dostęp do obiektu za pomocą `Globals.ThisAddIn` właściwości.  
  
- Wszystkie taśmy w projekcie, który można dostosować przy użyciu projektanta wstążki. Dostęp do wstążki przy użyciu `Globals.Ribbons` właściwości. Aby uzyskać więcej informacji, zobacz [dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md).  
  
- Wszystkie regiony formularza programu Outlook w projekcie dodatku narzędzi VSTO dla programu Outlook. Dostęp do regionów formularzy przy użyciu `Globals.FormRegions` właściwości. Aby uzyskać więcej informacji, zobacz [dostępu do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md).  
  
- Obiekt fabryki, która pozwala na tworzenie formantów wstążki, a następnie Hostuj elementy w czasie wykonywania w projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Dostęp do obiektu za pomocą `Globals.Factory` właściwości. Ten obiekt jest wystąpieniem klasy, która implementuje jedną następujących interfejsów:  
  
  -   <xref:Microsoft.Office.Tools.Factory>  
  
  -   <xref:Microsoft.Office.Tools.Excel.Factory>  
  
  -   <xref:Microsoft.Office.Tools.Outlook.Factory>  
  
  -   <xref:Microsoft.Office.Tools.Word.Factory>  
  
  Na przykład, można użyć `Globals.Sheet1` właściwość Wstawianie tekstu do <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolować na `Sheet1` kiedy użytkownik kliknie przycisk w okienku akcji w projekcie na poziomie dokumentu dla programu Excel.  
  
  [!code-vb[Trin_VstcoreProgramming#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#1)]
  [!code-csharp[Trin_VstcoreProgramming#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#1)]  
  
## <a name="initialize-the-globals-class"></a>Inicjowanie klasy globalne  
 Kod, który próbuje użyć `Globals` klasy przed zainicjowaniem jest dokument lub dodatku narzędzi VSTO może zgłosić wyjątek czasu wykonywania. Na przykład za pomocą `Globals` podczas deklarowania zmienną na poziomie klasy może się nie powieść ponieważ `Globals` klasy może nie być zainicjowana za pomocą odwołania do wszystkich elementów hosta przed utworzeniem wystąpienia deklarowanego obiektu.  
  
> [!NOTE]  
>  `Globals` Klasy nigdy nie został zainicjowany w czasie projektowania, ale wystąpienia kontrolki są tworzone przez projektanta. Oznacza to, że jeśli utworzysz formant użytkownika, który korzysta z właściwością `Globals` klasy z wewnątrz klasy formantu użytkownika, należy najpierw, czy właściwość ta zwraca **null** przed podjęciem próby użycia zwróconego obiektu.  
  
## <a name="see-also"></a>Zobacz także  
 [Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Dostęp do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Element hosta dokumentu](../vsto/document-host-item.md)   
 [Element hosta skoroszytu](../vsto/workbook-host-item.md)   
 [Element hosta arkusza](../vsto/worksheet-host-item.md)   
 [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)  
