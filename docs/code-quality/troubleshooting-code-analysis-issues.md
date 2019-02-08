---
title: Rozwiązywanie problemów związanych z analizą kodu
ms.date: 11/04/2016
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e309015eda874e73213e78e90e953862d23fbe61
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55956249"
---
# <a name="troubleshooting-code-analysis-issues"></a>Rozwiązywanie problemów związanych z analizą kodu
Ten temat zawiera informacje dotyczące rozwiązywania problemów dla następujących problemów z analizą kodu programu Visual Studio.

-   [Zmiany w Visual Studio 2010 reguły zestawu są nie zostaną uwzględnione w poprzednich wersjach programu Visual Studio](#ChildRuleSetChangesInPreviousVersions)

##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Zmiany w Visual Studio 2010 reguły zestawu są nie zostaną uwzględnione w poprzednich wersjach programu Visual Studio
 Po utworzeniu zestaw reguł w [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] zawierającą podrzędny zestaw reguł, zmiany do zestawu reguł podrzędne mogą nie zostać zastosowane w przebiegi analizy kodu na komputerach, które korzystają z wcześniejszej wersji programu Visual Studio. Aby rozwiązać ten problem, możesz wymusić nadpisania zestaw reguł nadrzędnego, który jest zestaw reguł, który zawiera zestaw reguł podrzędnych.

1. Otwórz zestaw reguł nadrzędnego, [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].

2. Wprowadź zmiany, takie jak dodawanie lub usuwanie reguły, a następnie Zapisz zestaw reguł.

3. Otwórz zestaw reguł, odwrócić zmiany, a następnie zapisz ponownie zestaw reguł.

## <a name="see-also"></a>Zobacz też

- [Analizowanie jakości aplikacji](../code-quality/code-analysis-for-managed-code-overview.md)
- [Analiza jakości zarządzanego kodu](../code-quality/code-analysis-for-managed-code-overview.md)
- [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)