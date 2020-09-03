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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f48cef7ffaf08fc26566fdd04bee15a3e3e1b85f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "78167576"
---
# <a name="portability-warnings"></a>Ostrzeżenia przenośności
Ostrzeżenia dotyczące przenośności obsługują przenośność w różnych systemach operacyjnych.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA1900: Pola typu wartości powinny być przenośne](../code-quality/ca1900.md)|Ta reguła sprawdza, czy struktury, które są zadeklarowane za pomocą jawnego atrybutu układu, są wyrównane prawidłowo w przypadku skierowania do kodu niezarządzanego w 64-bitowych systemach operacyjnych.|
|[CA1901: deklaracje P/Invoke powinny być przenośne](../code-quality/ca1901.md)|Ta reguła służy do obliczania rozmiaru każdego parametru oraz wartości zwracanej P/Invoke i sprawdza, czy ich rozmiar jest poprawny w przypadku skierowania do kodu niezarządzanego na 32-bitowych i 64-bitowych systemach operacyjnych.|
|[CA1903: Używaj tylko interfejsu API platformy docelowej](../code-quality/ca1903.md)|Element członkowski lub typ używa elementu członkowskiego lub typu wprowadzonego w dodatku Service Pack, który nie został uwzględniony razem ze wskazanym środowiskiem docelowym projektu.|
