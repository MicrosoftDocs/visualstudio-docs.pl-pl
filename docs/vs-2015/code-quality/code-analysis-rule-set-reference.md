---
title: Odwołanie do zestawu reguł analizy kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3c0b347f186c5adee6cf86a0e1720ebfa80f253
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670112"
---
# <a name="code-analysis-rule-set-reference"></a>Odwołanie zestawu reguł analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas konfigurowania analizy kodu dla projektów kodu zarządzanego w [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] lub [!INCLUDE[vsPro](../includes/vspro-md.md)]you są prezentowane z listą wbudowanych *zestawów reguł*. Można użyć jednego z zestawów reguł standar lub dostosować zestaw reguł, aby odpowiadał wymaganiom projektu.

## <a name="available-rule-sets"></a>Dostępne zestawy reguł
 Poniższa tabela zawiera listę domyślnych zestawów reguł:

|||
|-|-|
|[Zestaw reguł Wszystkie reguły](../code-quality/all-rules-rule-set.md)|Ten zestaw reguł zawiera wszystkie reguły. Uruchomienie tego zestawu reguł może spowodować zgłoszenie dużej liczby ostrzeżeń. Użyj tego zestawu reguł, aby uzyskać kompleksowy obraz wszystkich problemów w kodzie. Może to ułatwić podjęcie decyzji o tym, które z bardziej ukierunkowanych zestawów reguł są najbardziej odpowiednie do uruchomienia dla projektów.|
|[Zestaw podstawowych reguł poprawności dla kodu zarządzanego](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Reguły te koncentrują się na błędach logiki i typowych pomyłkach związanych z użyciem interfejsów API platformy. Uwzględnij ten zestaw reguł, aby rozwinąć listę ostrzeżeń raportowanych przez minimalne zalecane reguły.|
|[Zestaw podstawowych reguł wytycznych projektowych dla kodu zarządzanego](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Te reguły koncentrują się na wymuszeniu najlepszych praktyk, aby ułatwić zrozumienie i używanie kodu. Uwzględnij ten zestaw reguł, jeśli projekt zawiera kod biblioteki lub jeśli chcesz wymusić najlepsze rozwiązania w zakresie łatwego w obsłudze kodu.|
|[Zestaw rozszerzonych reguł poprawności dla kodu zarządzanego](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Te reguły rozszerzają podstawowe reguły poprawności w celu zmaksymalizowania raportowanych błędów logiki i użycia struktury. Dodatkowy nacisk jest umieszczany w określonych scenariuszach, takich jak międzyoperacyjność modelu COM i aplikacje mobilne. Rozważ uwzględnienie tego zestawu reguł, jeśli jeden z tych scenariuszy ma zastosowanie do Twojego projektu lub aby znaleźć dodatkowe problemy w projekcie.|
|[Zestaw rozszerzonych reguł wytycznych projektowych dla kodu zarządzanego](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Te reguły rozszerzają podstawowe reguły dotyczące wytycznych projektowych w celu zmaksymalizowania raportowanych problemów z użytecznością i konserwacją. Dodatkowy nacisk jest umieszczany w wytycznych dotyczących nazewnictwa. Rozważ uwzględnienie tego zestawu reguł, jeśli projekt zawiera kod biblioteki lub chcesz wymusić najwyższy poziom standardów do pisania kodu, który można obsługiwać.|
|[Zestaw reguł globalizacji dla kodu zarządzanego](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Te reguły koncentrują się na problemach, które uniemożliwiają poprawne wyświetlanie danych w aplikacji, gdy są używane w różnych językach, ustawieniach regionalnych i kulturach. Dołącz ten zestaw reguł, jeśli aplikacja jest zlokalizowana lub globalna.|
|[Zarządzany minimalny zestaw reguł dla kodu zarządzanego](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Te reguły koncentrują się na najważniejszych problemach w kodzie, dla których analiza kodu jest najbardziej dokładna.  Te reguły są małe i są przeznaczone tylko do uruchamiania w ograniczonej wersji programu Visual Studio.  Użyj MinimumRecommendedRules. zestaw reguł z innymi wersjami programu Visual Studio.|
|[Zarządzany zalecany zestaw reguł dla kodu zarządzanego](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Te reguły koncentrują się na najważniejszych problemach w kodzie, w tym potencjalnych luk w zabezpieczeniach, awarii aplikacji oraz innych istotnych błędach dotyczących logiki i projektowania. Ten zestaw reguł powinien być dołączany do każdego niestandardowego zestawu reguł tworzonego dla projektów.|
|[Mieszany minimalny zestaw reguł](../code-quality/mixed-minimum-rules-rule-set.md)|Te reguły koncentrują się na najważniejszych problemach w C++ projektach, które obsługują środowisko uruchomieniowe języka wspólnego, w tym potencjalne luki w zabezpieczeniach i awarie aplikacji. Ten zestaw reguł powinien być dołączany do każdego niestandardowego zestawu reguł tworzonego dla C++ projektów, które obsługują środowisko uruchomieniowe języka wspólnego.|
|[Mieszany zalecany zestaw reguł](../code-quality/mixed-recommended-rules-rule-set.md)|Te reguły koncentrują się na typowych i krytycznych problemach w C++ projektach, które obsługują środowisko uruchomieniowe języka wspólnego, w tym potencjalne luki w zabezpieczeniach, awarie aplikacji oraz inne ważne błędy logiki i projektowania. Ten zestaw reguł powinien być dołączany do każdego niestandardowego zestawu reguł tworzonego dla C++ projektów, które obsługują środowisko uruchomieniowe języka wspólnego.  Ten zestaw reguł został zaprojektowany tak, aby można go było skonfigurować przy użyciu wersji Visual Studio Professional lub nowszej.|
|[Natywny minimalny zestaw reguł](../code-quality/native-minimum-rules-rule-set.md)|Te reguły koncentrują się na najważniejszych problemach w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Ten zestaw reguł powinien być dołączany do każdego niestandardowego zestawu reguł tworzonego dla projektów natywnych.|
|[Natywny zalecany zestaw reguł](../code-quality/native-recommended-rules-rule-set.md)|Te reguły koncentrują się na najważniejszych i typowych problemach w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji.  Ten zestaw reguł powinien być dołączany do każdego niestandardowego zestawu reguł tworzonego dla projektów natywnych.  Ten zestaw reguł jest przeznaczony do pracy z Visual Studio Professional Edition lub nowszym.|
|[Zestaw reguł zabezpieczeń dla kodu zarządzanego](../code-quality/security-rules-rule-set-for-managed-code.md)|Ten zestaw reguł zawiera wszystkie reguły zabezpieczeń firmy Microsoft. Uwzględnij ten zestaw reguł, aby zmaksymalizować liczbę raportowanych potencjalnych problemów z zabezpieczeniami.|
