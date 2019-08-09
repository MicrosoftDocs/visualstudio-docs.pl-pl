---
title: 'Przykładowe rozszerzenie programu Excel: Klasa ActionFilter | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 26eb001de3a8fed7c6bb1d9d1a547aa618e745e8
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871604"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Przykładowe rozszerzenie programu Excel: ActionFilter, klasa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta wewnętrzna Klasa rozszerza klasę [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) i reprezentuje filtr dla akcji [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] testowych dla elementu.

## <a name="simple-properties"></a>Proste właściwości
 Te właściwości tylko do odczytu umożliwiają deweloperowi określenie, w jaki sposób ten filtr akcji testowych ma być wykonywany przez zakodowaną strukturę testowania interfejsu użytkownika. Na przykład `UITestActionFilter.Name` Właściwość zawiera nazwę filtru akcji. Inne właściwości otrzymują `UITestActionFilter.Category` filtr akcji `UITestActionFilter.FilterType`, czyli `UITestActionFilter.Group` nazwę akcji testowych, które są filtrowane przez ten filtr akcji testowej. Inne wskazują, czy `UITestActionFilter.ApplyTimeout` ma być, a także czy Akcja `UITestActionFilter.Enabled`testowa jest.

## <a name="processrule-method"></a>ProcessRule, Metoda
 Ta metoda jest wywoływana przez strukturę testowania kodowanego interfejsu użytkownika i wykonuje filtr w odniesieniu `IUITestActionStack`do podanego elementu. To przesłonięcie powoduje usunięcie przycisku akcji wybierz akcję w komórce, gdy Następna akcja w stosie wysyła naciśnięcia klawiszy do komórki. Następnie zwraca wartość `false`.

## <a name="private-methods"></a>Metody prywatne
 `IsLeftClick` Metoda określa, czy podana akcja reprezentuje kliknięcie lewym przyciskiem myszy. `AreActionsOnSameExcelCell` Metoda określa, czy dwie podane akcje są wykonywane w tej samej komórce w programie Excel.

## <a name="see-also"></a>Zobacz także

- [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
