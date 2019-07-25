---
title: Rozwiązywanie problemów z analizą kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b2efecdefb693653ff9916e798d1a11afe44e4a5
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416903"
---
# <a name="troubleshooting-code-analysis-issues"></a>Rozwiązywanie problemów związanych z analizą kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten temat zawiera informacje dotyczące rozwiązywania problemów dotyczących następujących problemów z analizą kodu programu Visual Studio.

- [Zmiany w zestawie reguł programu Visual Studio 2010 nie są odzwierciedlone w poprzednich wersjach programu Visual Studio](#ChildRuleSetChangesInPreviousVersions)

## <a name="ChildRuleSetChangesInPreviousVersions"></a>Zmiany w zestawie reguł programu Visual Studio 2010 nie są odzwierciedlone w poprzednich wersjach programu Visual Studio

Podczas tworzenia zestawu reguł w programie [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] , który zawiera podrzędny zestaw reguł, zmiana podrzędnego zestawu reguł może nie zostać zastosowana w przypadku uruchamiania analizy kodu na komputerach używających wcześniejszej wersji programu Visual Studio. Aby rozwiązać ten problem, należy wymusić ponowne zapisywanie zestawu reguł nadrzędnych, który jest zestawem reguł zawierającym podrzędny zestaw reguł.

1. Otwórz zestaw reguł nadrzędnych w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].

2. Wprowadź zmiany, takie jak dodawanie lub usuwanie reguły, a następnie zapisywanie zestawu reguł.

3. Otwórz ponownie zestaw reguł, Odwróć zmianę, a następnie Zapisz zestaw reguł.

## <a name="see-also"></a>Zobacz także

- [Analizowanie jakości aplikacji](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)
- [Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
- [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
