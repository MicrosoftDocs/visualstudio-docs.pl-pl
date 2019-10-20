---
title: Rozwiązywanie problemów z analizą kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4eee70b3184496e8dbb7d784501a5cac2aac00ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672116"
---
# <a name="troubleshooting-code-analysis-issues"></a>Rozwiązywanie problemów związanych z analizą kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten temat zawiera informacje dotyczące rozwiązywania problemów dotyczących następujących problemów z analizą kodu programu Visual Studio.

- [Zmiany w zestawie reguł programu Visual Studio 2010 nie są odzwierciedlone w poprzednich wersjach programu Visual Studio](#ChildRuleSetChangesInPreviousVersions)

## <a name="ChildRuleSetChangesInPreviousVersions"></a>Zmiany w zestawie reguł programu Visual Studio 2010 nie są odzwierciedlone w poprzednich wersjach programu Visual Studio

Podczas tworzenia zestawu reguł w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], który zawiera podrzędny zestaw reguł, zmiana podrzędnego zestawu reguł może nie zostać zastosowana w przypadku uruchamiania analizy kodu na komputerach korzystających ze starszej wersji programu Visual Studio. Aby rozwiązać ten problem, należy wymusić ponowne zapisywanie zestawu reguł nadrzędnych, który jest zestawem reguł zawierającym podrzędny zestaw reguł.

1. Otwórz zestaw reguł nadrzędnych w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].

2. Wprowadź zmiany, takie jak dodawanie lub usuwanie reguły, a następnie zapisywanie zestawu reguł.

3. Otwórz ponownie zestaw reguł, Odwróć zmianę, a następnie Zapisz zestaw reguł.

## <a name="see-also"></a>Zobacz także

- [Analizowanie jakości aplikacji](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)
- [Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
- [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
