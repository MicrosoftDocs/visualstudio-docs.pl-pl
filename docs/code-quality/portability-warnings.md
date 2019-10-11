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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 072858a9faafe312fd7c8314e7f25cf581c40844
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163071"
---
# <a name="portability-warnings"></a>Ostrzeżenia przenośności
Ostrzeżenia dotyczące przenośności obsługują przenośność w różnych systemach operacyjnych.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA1900: Pola typu wartości powinny być przenośne @ no__t-0|Ta reguła sprawdza, czy struktury, które są zadeklarowane za pomocą jawnego atrybutu układu, są wyrównane prawidłowo w przypadku skierowania do kodu niezarządzanego w 64-bitowych systemach operacyjnych.|
|[CA1901: Deklaracje P/Invoke powinny być przenośne @ no__t-0|Ta reguła służy do obliczania rozmiaru każdego parametru oraz wartości zwracanej P/Invoke i sprawdza, czy ich rozmiar jest poprawny w przypadku skierowania do kodu niezarządzanego na 32-bitowych i 64-bitowych systemach operacyjnych.|
|[CA1903: Używaj tylko interfejsu API z platformy Target Framework @ no__t-0|Element członkowski lub typ używa elementu członkowskiego lub typu wprowadzonego w dodatku Service Pack, który nie został uwzględniony razem ze wskazanym środowiskiem docelowym projektu.|
