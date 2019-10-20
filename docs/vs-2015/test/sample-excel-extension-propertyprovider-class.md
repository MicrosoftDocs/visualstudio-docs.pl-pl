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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660419"
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Przykładowe rozszerzenie programu Excel: klasa PropertyProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta wewnętrzna Klasa rozszerza klasę <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> i zapewnia usługi właściwości dla [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] elementów do rejestrowania i odtwarzania testów interfejsu użytkownika (UI).

## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel, Metoda
 Metoda <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> zwraca liczbę wskazującą poziom wsparcia, który dostawca właściwości może zaoferować dla podanej kontrolki. Im wyższa wartość zwracana, tym bardziej dostawca właściwości może obsługiwać formant. W tym przypadku metoda sprawdza wartość właściwości <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> podanej kontrolki. Jeśli wartość to "Excel", a <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> wskazuje, że jest `CellElement`, metoda zwraca najwyższą wartość; w przeciwnym razie zwraca zero, co oznacza, że nie jest dostępna żadna pomoc techniczna.

## <a name="getpropertynames-method"></a>GetPropertyNames — Metoda
 Zwraca słownik nazw właściwości i deskryptorów właściwości dla obsługiwanych właściwości kontrolki komórki programu Excel.

## <a name="getpropertydescriptor-method"></a>GetPropertyDescriptor, Metoda
 Ta metoda jest wywoływana przez platformę testową w celu uzyskania wstępnie zdefiniowanego deskryptora właściwości dla podanej nazwy właściwości.

## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>Metody GetPropertyValue i SetPropertyValue
 Metoda `GetPropertyValue` używa klasy `Communicator` tego rozszerzenia do zwrócenia wartości właściwości z programu Excel. Metoda `SetPropertyValue` używa klasy <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> i składnika `Communicator` do ustawiania wartości właściwości. Metody te są wywoływane przez platformę testową.

## <a name="code-generation-customization-methods"></a>Metody dostosowywania generowania kodu
 Te metody nie są zaimplementowane dla tego rozszerzenia. W związku z tym zwracają `null` lub generują <xref:System.NotImplementedException>.

## <a name="see-also"></a>Zobacz też
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider><xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>
 [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
