---
title: Ostrzeżenia przenośności
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3e1959066f81663d66e8af2af8039080d8cace6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649127"
---
# <a name="portability-warnings"></a>Ostrzeżenia przenośności
Ostrzeżenia dotyczące przenośności obsługują przenośność w różnych systemach operacyjnych.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA1900: Pola typu wartości powinny być przenośne](../code-quality/ca1900.md)|Ta reguła sprawdza, czy struktury, które są zadeklarowane za pomocą jawnego atrybutu układu, są wyrównane prawidłowo w przypadku skierowania do kodu niezarządzanego w 64-bitowych systemach operacyjnych.|
|[CA1901: Deklaracje P/Invoke powinny być przenośne](../code-quality/ca1901.md)|Ta reguła służy do obliczania rozmiaru każdego parametru oraz wartości zwracanej P/Invoke i sprawdza, czy ich rozmiar jest poprawny w przypadku skierowania do kodu niezarządzanego na 32-bitowych i 64-bitowych systemach operacyjnych.|
|[CA1903: Używaj tylko interfejsu API platformy docelowej](../code-quality/ca1903.md)|Element członkowski lub typ używa elementu członkowskiego lub typu wprowadzonego w dodatku Service Pack, który nie został uwzględniony razem ze wskazanym środowiskiem docelowym projektu.|
