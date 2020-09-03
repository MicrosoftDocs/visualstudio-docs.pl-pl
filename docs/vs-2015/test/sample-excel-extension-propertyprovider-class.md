---
title: 'Przykładowe rozszerzenie programu Excel: Klasa PropertyProvider | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ae254f85b00c47ba00250641f7afe0a638ceabc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660419"
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Przykładowe rozszerzenie programu Excel: klasa PropertyProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta wewnętrzna Klasa rozszerza <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> klasę i zapewnia usługi właściwości dla [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] elementów do rejestrowania i odtwarzania testów interfejsu użytkownika (UI).

## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel, Metoda
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A>Metoda zwraca liczbę, która wskazuje poziom wsparcia, który dostawca właściwości może zaoferować dla podanej kontrolki. Im wyższa wartość zwracana, tym bardziej dostawca właściwości może obsługiwać formant. W tym przypadku metoda sprawdza wartość <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> Właściwości podanej kontrolki. Jeśli wartość to "Excel", a jeśli <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> wskazuje `CellElement` , że metoda zwraca najwyższą wartość. w przeciwnym razie zwraca zero, co oznacza, że nie jest dostępna żadna pomoc.

## <a name="getpropertynames-method"></a>GetPropertyNames — Metoda
 Zwraca słownik nazw właściwości i deskryptorów właściwości dla obsługiwanych właściwości kontrolki komórki programu Excel.

## <a name="getpropertydescriptor-method"></a>GetPropertyDescriptor, Metoda
 Ta metoda jest wywoływana przez platformę testową w celu uzyskania wstępnie zdefiniowanego deskryptora właściwości dla podanej nazwy właściwości.

## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>Metody GetPropertyValue i SetPropertyValue
 `GetPropertyValue`Metoda używa `Communicator` klasy tego rozszerzenia do zwrócenia wartości właściwości z programu Excel. `SetPropertyValue`Metoda używa <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> klasy i `Communicator` składnika do ustawiania wartości właściwości. Metody te są wywoływane przez platformę testową.

## <a name="code-generation-customization-methods"></a>Metody dostosowywania generowania kodu
 Te metody nie są zaimplementowane dla tego rozszerzenia. W związku z tym zwracają `null` lub generują <xref:System.NotImplementedException> .

## <a name="see-also"></a>Zobacz też
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>
 [Rozszerzanie zakodowanych testów interfejsu użytkownika i nagrywanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
