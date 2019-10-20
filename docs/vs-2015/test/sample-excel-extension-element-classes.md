---
title: 'Przykładowe rozszerzenie programu Excel: klasy elementów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21c7777be710f0175708629eb9507b34f0d70be2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660453"
---
# <a name="sample-excel-extension-element-classes"></a>Przykładowe rozszerzenie programu Excel: klasy elementów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozszerzenie używa klas, które pochodzą z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> i reprezentują kontrolkę arkusz i kontrolkę komórka w [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].

 Element podstawowy dla tego rozszerzenia jest `ExcelElement`. Klasa `ExcelWorksheetElement` i Klasa `ExcelCellElement` dziedziczą z tego elementu

## <a name="element-and-elementinformation-classes"></a>Klasy elementów i ElementInformation
 @No__t_0 jest klasą bazową dla wszystkich elementów interfejsu użytkownika dla rozszerzenia programu Excel i dziedziczy z klasy <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>. `ElementInformation` jest klasą bazową dla klas informacji o elementach w przykładzie i nie ma żadnych elementów członkowskich.

#### <a name="simple-properties-and-methods"></a>Proste właściwości i metody
 Te elementy członkowskie zwracają proste wartości, takie jak wartość właściwości `Name` lub wartość właściwości `ClassName`, a kod jest jasno i czytelny. Niektóre wartości są zwracane przy użyciu klasy `Utility`, która została omówiona w dalszej części. Inne zwracają `null`, ponieważ nie są one istotne w tym przykładowym rozszerzeniu. Dwa elementy członkowskie są bardziej interesujące niż pozostałe: Właściwość <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> i Metoda <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A>.

#### <a name="queryid-property"></a>Właściwość QueryId
 Ta właściwość zwraca warunek składający się z par nazwa-wartość właściwości, które jednoznacznie identyfikują kontrolkę podczas odtwarzania. Dla każdej klasy formantów pochodnych Deweloper musi zastąpić tę właściwość w celu zwrócenia obiektu <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>, który może być używany przez platformę do znajdowania formantu w interfejsie użytkownika.

#### <a name="cacheproperties-method"></a>CacheProperties, Metoda
 Ta metoda jest wywoływana przez strukturę testowania podczas procesu rejestrowania, aby poinformować element, aby zapisać migawkę ważnych właściwości. Pozwala to zachować dostęp do właściwości nawet wtedy, gdy rzeczywista kontrolka interfejsu użytkownika nie jest już na ekranie.

## <a name="worksheetelement-and-worksheetinformation-classes"></a>I klasy WorksheetInformation
 Klasa `WorksheetElement` reprezentuje arkusz programu Excel w środowisku testowym i dziedziczy z klasy bazowej `Element`. Trzy właściwości są zastępowane w celu zapewnienia określonych informacji o obiekcie arkusza programu Excel: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> i <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.

 @No__t_0 jest również stosowana do tej klasy, aby była widoczna dla modelu COM.

 Klasa `WorksheetInformation` reprezentuje informacje o arkuszu programu Excel. Ma tylko jeden element członkowski, właściwość `SheetName`, która jest wystarczająca dla tego przykładu.

## <a name="cellelement-and-cellinformation-classes"></a>Cells i klasy CellInformation
 Klasa `CellElement` reprezentuje komórkę programu Excel i dziedziczy z klasy bazowej `Element`. Jedynym przesłoniętym elementem członkowskim jest właściwość <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>, która zwraca <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>, która używa właściwości `RowIndex` i `ColumnIndex` do identyfikowania komórki.

## <a name="utilities-and-excelutilities-classes"></a>Narzędzia i klasy ExcelUtilities
 Wewnętrzna klasa `ExcelUtilities` zapewnia pewne wartości stałe, takie jak nazwa technologii i metoda, która określa, czy podane dojście okna reprezentuje arkusz programu Excel.

 Klasa `Utilities` ma metody pomocnika, które zwracają różne informacje o interfejsie użytkownika. Niektóre metody używają bezpośrednich wywołań do zewnętrznych bibliotek DLL systemu, takich jak **User32. DLL** i **OLEACC. DLL**, aby uzyskać uchwyty okna z interfejsu użytkownika<strong>.</strong>

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.InteropServices.ComVisibleAttribute><xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>
 [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
