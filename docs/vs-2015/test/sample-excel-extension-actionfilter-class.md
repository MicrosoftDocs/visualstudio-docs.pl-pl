---
title: 'Przykładowe rozszerzenie programu Excel: Klasa ActionFilter | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86c1dda46ed0e62649a576a12c9f9e48561ec891
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158164"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Przykładowe rozszerzenie programu Excel: ActionFilter, klasa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Klasa wewnętrznego rozszerza <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> klasy i reprezentuje filtr akcji testowych na [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] elementu.  
  
## <a name="simple-properties"></a>Proste właściwości  
 Te właściwości tylko do odczytu włączone dla deweloperów określić, jak ten filtr akcji testu jest wykonywane przez kodowanych testów interfejsu użytkownika. Na przykład <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> właściwość zawiera nazwę filtru akcji. Inne właściwości get <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> filtr akcji <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> nazwę dla akcji testów, które są filtrowane według tego testu filtru akcji. Niektóre wskazują czy <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> i tego, czy akcja testu jest także <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.  
  
## <a name="processrule-method"></a>Metoda ProcessRule  
 Ta metoda jest wywoływana przez kodowanych testów interfejsu użytkownika i wykonuje filtr względem dostarczonego <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>. To zastąpienie określonego usuwa myszy wybierz akcję, komórkę, podczas następnej akcji w stosie wysyła naciśnięcia klawiszy do komórki. Następnie zwraca `false`.  
  
## <a name="private-methods"></a>Metody prywatne  
 `IsLeftClick` Metoda określa, czy podana Akcja reprezentuje kliknięcie lewym przyciskiem myszy kursora myszy. `AreActionsOnSameExcelCell` Metoda określa, czy podane dwie akcje są wykonywane w tej samej komórki w programie Excel.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
