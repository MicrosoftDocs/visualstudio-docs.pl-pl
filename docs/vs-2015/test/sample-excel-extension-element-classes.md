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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660453"
---
# <a name="sample-excel-extension-element-classes"></a>Przykładowe rozszerzenie programu Excel: klasy elementów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozszerzenie używa klas, które pochodzą z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> i reprezentują kontrolkę arkusz i kontrolkę komórki w [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .

 Podstawowym elementem tego rozszerzenia jest `ExcelElement` . `ExcelWorksheetElement`Klasa i `ExcelCellElement` Klasa dziedziczą z tego elementu

## <a name="element-and-elementinformation-classes"></a>Klasy elementów i ElementInformation
 `Element`Jest klasą bazową dla wszystkich elementów interfejsu użytkownika dla rozszerzenia programu Excel i dziedziczy z <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> klasy. `ElementInformation` jest klasą bazową dla klas informacji o elementach w przykładzie i nie ma żadnych elementów członkowskich.

#### <a name="simple-properties-and-methods"></a>Proste właściwości i metody
 Te elementy członkowskie zwracają proste wartości, takie jak wartość `Name` właściwości lub wartość `ClassName` właściwości, a kod jest jasno i czytelny. Niektóre wartości są zwracane przy użyciu `Utility` klasy, która została omówiona w dalszej części. Inne zwracają inne osoby, `null` ponieważ nie są one istotne w tym przykładowym rozszerzeniu. Dwa elementy członkowskie są bardziej interesujące niż pozostałe: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> Właściwość i <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A> Metoda.

#### <a name="queryid-property"></a>Właściwość QueryId
 Ta właściwość zwraca warunek składający się z par nazwa-wartość właściwości, które jednoznacznie identyfikują kontrolkę podczas odtwarzania. Dla każdej klasy formantów pochodnych Deweloper musi zastąpić tę właściwość w celu zwrócenia <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> obiektu, który może być używany przez platformę do znajdowania formantu w interfejsie użytkownika.

#### <a name="cacheproperties-method"></a>CacheProperties, Metoda
 Ta metoda jest wywoływana przez strukturę testowania podczas procesu rejestrowania, aby poinformować element, aby zapisać migawkę ważnych właściwości. Pozwala to zachować dostęp do właściwości nawet wtedy, gdy rzeczywista kontrolka interfejsu użytkownika nie jest już na ekranie.

## <a name="worksheetelement-and-worksheetinformation-classes"></a>I klasy WorksheetInformation
 `WorksheetElement`Klasa reprezentuje arkusz programu Excel w środowisku testowym i dziedziczy z `Element` klasy bazowej. Trzy właściwości są zastępowane w celu zapewnienia określonych informacji o obiekcie arkusza programu Excel: <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A> , <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> i <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A> .

 <xref:System.Runtime.InteropServices.ComVisibleAttribute>Jest również stosowana do tej klasy, aby była widoczna dla modelu com.

 `WorksheetInformation`Klasa reprezentuje informacje o arkuszu programu Excel. Ma tylko jeden element członkowski, `SheetName` Właściwość, która jest wystarczająca dla tego przykładu.

## <a name="cellelement-and-cellinformation-classes"></a>Cells i klasy CellInformation
 `CellElement`Klasa reprezentuje komórkę programu Excel i dziedziczy z `Element` klasy bazowej. Jedynym przesłoniętym elementem członkowskim jest <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> Właściwość, która zwraca wartość, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> która `RowIndex` używa `ColumnIndex` właściwości i do identyfikowania komórki.

## <a name="utilities-and-excelutilities-classes"></a>Narzędzia i klasy ExcelUtilities
 Wewnętrzna `ExcelUtilities` Klasa zawiera pewne wartości stałe, takie jak nazwa technologii i Metoda określająca, czy podane dojście okna reprezentuje arkusz programu Excel.

 `Utilities`Klasa ma metody pomocnika, które zwracają różne informacje o interfejsie użytkownika. Niektóre metody używają bezpośrednich wywołań do zewnętrznych bibliotek DLL systemu, takich jak **USER32.DLL** i **OLEACC.DLL**, aby uzyskać uchwyty okna z interfejsu użytkownika<strong>.</strong>

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>
 [Rozszerzanie zakodowanych testów interfejsu użytkownika i nagrywanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
