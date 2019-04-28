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
ms.openlocfilehash: a6a3557cffec60de91da46f60040ec675c866cbf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825328"
---
# <a name="portability-warnings"></a>Ostrzeżenia przenośności
Ostrzeżenia przenośności obsługuje przenośności w różnych systemach operacyjnych.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA1900: Pola typu wartości powinny być przenośne](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Ta reguła sprawdza, czy struktury, które są zadeklarowane za pomocą atrybutu jawnego układu, zostaną prawidłowo wyrównane podczas przekazywania do kodu niezarządzanego w 64-bitowych systemach operacyjnych.|
|[CA1901: Deklaracje P/Invoke powinny być przenośne](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Ta reguła oblicza rozmiar każdego parametru oraz wartość zwracaną metody P/Invoke i sprawdza, czy ich rozmiar jest poprawny podczas przekazywania do kodu niezarządzanego w 32-bitowych i 64-bitowych systemach operacyjnych.|
|[CA1903: Używaj tylko interfejsu API platformy docelowej](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Element członkowski lub typ używa elementu członkowskiego lub typu wprowadzonego w dodatku Service Pack, który nie został uwzględniony razem ze wskazanym środowiskiem docelowym projektu.|