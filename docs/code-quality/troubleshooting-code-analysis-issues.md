---
title: Rozwiązywanie problemów związanych z analizą kodu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 34fce91db15d484b140aee291f9abd915d9399d2
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2018
ms.locfileid: "53738796"
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
 [Analiza jakości aplikacji](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md) [analiza jakości zarządzanego kodu](../code-quality/code-analysis-for-managed-code-overview.md) [korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)