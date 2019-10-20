---
title: 'Przykładowe rozszerzenie programu Excel: Klasa ActionFilter | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c286f25159f3ee1934a27d2242e97482f7ec424
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672180"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Przykładowe rozszerzenie programu Excel: klasa ActionFilter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta wewnętrzna Klasa rozszerza klasę [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) i reprezentuje filtr dla akcji testowych dla elementu [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].

## <a name="simple-properties"></a>Proste właściwości
 Te właściwości tylko do odczytu umożliwiają deweloperowi określenie, w jaki sposób ten filtr akcji testowych ma być wykonywany przez zakodowaną strukturę testowania interfejsu użytkownika. Na przykład właściwość `UITestActionFilter.Name` zawiera nazwę filtru akcji. Inne właściwości otrzymują `UITestActionFilter.Category` filtru akcji, `UITestActionFilter.FilterType`, nazwę `UITestActionFilter.Group` dla akcji testowych, które są filtrowane przez ten filtr akcji testu. Inne wskazują, czy `UITestActionFilter.ApplyTimeout`, a także czy akcja testowa jest `UITestActionFilter.Enabled`.

## <a name="processrule-method"></a>ProcessRule, Metoda
 Ta metoda jest wywoływana przez strukturę testowania kodowanego interfejsu użytkownika i wykonuje filtr względem podanej `IUITestActionStack`. To przesłonięcie powoduje usunięcie przycisku akcji wybierz akcję w komórce, gdy Następna akcja w stosie wysyła naciśnięcia klawiszy do komórki. Następnie zwraca `false`.

## <a name="private-methods"></a>Metody prywatne
 Metoda `IsLeftClick` określa, czy podana akcja reprezentuje kliknięcie lewym przyciskiem myszy. Metoda `AreActionsOnSameExcelCell` określa, czy dwie dostarczone akcje są wykonywane w tej samej komórce w programie Excel.

## <a name="see-also"></a>Zobacz także

- [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
