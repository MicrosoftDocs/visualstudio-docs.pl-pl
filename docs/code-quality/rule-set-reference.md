---
title: Odwołanie zestawu reguł analizy kodu
ms.date: 04/04/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da0d70af989d759df94eb2d22606ad90373936ad
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448831"
---
# <a name="code-analysis-rule-set-reference"></a>Odwołanie zestawu reguł analizy kodu

Podczas konfigurowania starszej analizy dla projektów kodu zarządzanego w programie Visual Studio można wybrać jedną z listy wbudowanych *zestawów reguł*. Niektóre reguły są zawarte w więcej niż jednym z wbudowanych zestawów reguł, na przykład zestaw reguł prawidłowości podstawowych reguł poprawności zawiera reguły, które znajdują się w zestawie reguł zarządzanych zalecanych reguł.

> [!NOTE]
> Zestawy reguł w tej sekcji odnoszą się do starszej analizy. Aby uzyskać informacje o zestawach reguł dostępnych dla pakietów analizatora kodu, zobacz [Korzystanie z zestawów reguł z analizami kodu](analyzer-rule-sets.md).

Można użyć jednego z tych wbudowanych zestawów reguł lub [dostosować zestaw reguł](../code-quality/how-to-create-a-custom-rule-set.md) tak, aby odpowiadał wymaganiom projektu. W przypadku dołączania wielu zestawów reguł, które zawierają tę samą regułę w zestawie reguł niestandardowych, ta reguła występuje tylko raz w zestawie reguł niestandardowych.

W tematach w tej sekcji opisano wbudowane zestawy reguł oraz reguły (lub ostrzeżenia), które zawierają.

| Zestaw reguł | Uwzględnione reguły |
| - | - |
| [Wszystkie reguły](all-rules-rule-set.md) | Zawiera wszystkie dostępne reguły zarządzane C++ i |
| [Podstawowe reguły poprawności](basic-correctness-rules-rule-set-for-managed-code.md) | Obejmuje zarządzane zalecane reguły oraz reguły dla błędów logiki i użycia struktury |
| [Rozszerzone reguły poprawności](extended-correctness-rules-rule-set-for-managed-code.md) | Zawiera podstawowe reguły poprawności (w tym zarządzane zalecane reguły) oraz więcej reguł dla błędów logiki i użycia struktury |
| [Podstawowe reguły dotyczące projektowania](basic-design-guideline-rules-rule-set-for-managed-code.md) | Obejmuje zarządzane zalecane reguły oraz reguły zapewniające, że można łatwo odczytywać, zrozumieć i konserwować kod |
| [Reguły rozszerzonej wytyczne dotyczące projektowania](extended-design-guidelines-rules-rule-set-for-managed-code.md) | Zawiera podstawowe reguły dotyczące projektowania (w tym zarządzane zalecane reguły) oraz bardziej szczegółowe reguły, które koncentrują się na nazewnictwie |
| [Reguły globalizacji](globalization-rules-rule-set-for-managed-code.md) | Zawiera reguły dotyczące problemów z globalizacją |
| [Zarządzane reguły minimalne](managed-minimum-rules-rule-set-for-managed-code.md) | Zawiera cztery reguły dotyczące krytycznych problemów z kodem zarządzanym |
| [Zarządzane zalecane reguły](managed-recommended-rules-rule-set-for-managed-code.md) | Obejmuje zarządzane reguły minimalne oraz więcej reguł dotyczących krytycznych problemów z kodem zarządzanym |
| [Mieszane reguły minimalne](mixed-minimum-rules-rule-set.md) | Zawiera reguły dotyczące krytycznych problemów w C++ kodzie dla środowiska CLR |
| [Mieszane zalecane reguły](mixed-recommended-rules-rule-set.md) | Zawiera mieszane reguły minimalne oraz więcej reguł dotyczących krytycznych problemów w C++ kodzie dla środowiska CLR |
| [Natywne reguły minimalne](native-minimum-rules-rule-set.md) | Zawiera reguły dotyczące krytycznych problemów w kodzie natywnym |
| [Zalecane reguły natywne](native-recommended-rules-rule-set.md) | Zawiera natywne reguły minimalne i więcej reguł dotyczących krytycznych problemów w kodzie natywnym |
| [Reguły zabezpieczeń](security-rules-rule-set-for-managed-code.md) | Zawiera reguły dotyczące znajdowania luk w zabezpieczeniach |
