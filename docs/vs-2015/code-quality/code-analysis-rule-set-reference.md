---
title: Odwołanie do zestawu reguł analizy kodu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a1f91b352da5a41ec2ef81fb6067976073c787ef
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786643"
---
# <a name="code-analysis-rule-set-reference"></a>Odwołanie zestawu reguł analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas konfigurowania analizy kodu dla zarządzanych projektów kodu w [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], lub [!INCLUDE[vsPro](../includes/vspro-md.md)]zostanie wyświetlona lista wbudowanej *zestawów reguł*. Można użyć jednego z zestawów reguł standar lub można dostosować zestaw reguł, aby zgodnie z wymaganiami projektu.  
  
## <a name="available-rule-sets"></a>Zestawy reguł dostępne  
 W poniższej tabeli wymieniono domyślne zestawy reguł:  
  
|||  
|-|-|  
|[Zestaw reguł Wszystkie reguły](../code-quality/all-rules-rule-set.md)|Ten zestaw reguł zawiera wszystkie reguły. Uruchamianie tego zestawu reguł może skutkować dużą liczbę ostrzeżeń. Użyj ten zestaw reguł, aby uzyskać kompleksowy przegląd wszystkich problemów w kodzie. To może pomóc w podjęciu decyzji, które reguły ściślejszych zestawów są najbardziej odpowiednie do uruchamiania dla projektów.|  
|[Zestaw podstawowych reguł poprawności dla kodu zarządzanego](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Te reguły dotyczą błędów logicznych i typowych pomyłek popełnianych framework interfejsów API. Obejmują ten zestaw reguł, aby rozszerzyć listę ostrzeżeń zgłaszanych przez minimalne zalecane reguły.|  
|[Zestaw podstawowych reguł wytycznych projektowych dla kodu zarządzanego](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Te reguły dotyczą wymuszanie najlepszych rozwiązań, aby sprawić, że kod jest łatwy do zrozumienia i użycia. Obejmują tej reguły, jeśli projekt zawiera kod biblioteki lub jeśli chcesz wymuszać najlepsze rozwiązania dla kodu łatwego w obsłudze.|  
|[Zestaw rozszerzonych reguł poprawności dla kodu zarządzanego](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Te reguły rozszerzają podstawowe reguły poprawności w celu zmaksymalizowania błędy użycia logiki i struktury, które są zgłaszane. Dodatkowy nacisk jest kładziony na określone scenariusze, takie jak aplikacje COM międzyoperacyjności i na urządzeniach przenośnych. Należy rozważyć dołączenie tego zestawu, jeśli jeden z tych scenariuszy dotyczy projektu lub w celu znalezienia dodatkowych problemów w projekcie reguł.|  
|[Zestaw rozszerzonych reguł wytycznych projektowych dla kodu zarządzanego](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Te reguły rozszerzają reguły wskazówek dotyczących podstawowy projekt, aby zmaksymalizować użytecznością i utrzymaniem problemy, które są zgłaszane. Dodatkowy nacisk jest kładziony na wskazówki dotyczące nazewnictwa. Należy rozważyć dołączenie tego zestawu, jeśli projekt zawiera kod biblioteki lub jeśli chcesz wymusić najwyższych standardów tworzenia kodu łatwego w utrzymaniu reguł.|  
|[Zestaw reguł globalizacji dla kodu zarządzanego](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Te reguły dotyczą problemów, które uniemożliwiają dane w aplikacji z prawidłowo wyświetlane, gdy są używane w różnych językach, ustawień regionalnych i kultur. Obejmują tej reguły, jeśli aplikacja jest lokalizowana lub globalizowana.|  
|[Zarządzany minimalny zestaw reguł dla kodu zarządzanego](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Te reguły dotyczą najpoważniejszych problemów w kodzie, dla którego jest najbardziej dokładna analiza kodu.  Te reguły to niewielka liczba i są przeznaczone do uruchamiania tylko w ograniczonej wersji programu Visual Studio.  Należy używać elementu MinimumRecommendedRules.ruleset w innych wersjach programu Visual Studio.|  
|[Zarządzany zalecany zestaw reguł dla kodu zarządzanego](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Te reguły dotyczą najpoważniejszych problemów w kodzie, w tym potencjalnych luk w zabezpieczeniach, awarii aplikacji i inne istotne błędy logiki i projektowania. Należy dołączyć ten zestaw reguł każdego niestandardowego zestawu reguł tworzonego dla projektów.|  
|[Mieszany minimalny zestaw reguł](../code-quality/mixed-minimum-rules-rule-set.md)|Te reguły dotyczą najpoważniejszych problemów w projektach C++ obsługujących środowisko uruchomieniowe języka wspólnego, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Należy dołączyć ten zestaw reguł każdego niestandardowego zestawu reguł tworzonego dla projektów C++ obsługujących środowisko uruchomieniowe języka wspólnego.|  
|[Mieszany zalecany zestaw reguł](../code-quality/mixed-recommended-rules-rule-set.md)|Te reguły dotyczą najczęstszych i najpoważniejszych problemów w projektach C++ obsługujących środowisko uruchomieniowe języka wspólnego, w tym potencjalnych luk w zabezpieczeniach, awarii aplikacji i inne istotne błędy logiki i projektowania. Należy dołączyć ten zestaw reguł każdego niestandardowego zestawu reguł tworzonego dla projektów C++ obsługujących środowisko uruchomieniowe języka wspólnego.  Ten zestaw reguł został zaprojektowany do skonfigurowania za pomocą programu Visual Studio w wersji Professional lub nowszy.|  
|[Natywny minimalny zestaw reguł](../code-quality/native-minimum-rules-rule-set.md)|Te reguły dotyczą najpoważniejszych problemów w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Należy dołączyć ten zestaw reguł każdego niestandardowego zestawu reguł tworzonego dla projektów natywnych.|  
|[Natywny zalecany zestaw reguł](../code-quality/native-recommended-rules-rule-set.md)|Te reguły dotyczą i najpoważniejszych problemów w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji.  Należy dołączyć ten zestaw reguł każdego niestandardowego zestawu reguł tworzonego dla projektów natywnych.  Ten zestaw reguł jest przeznaczona do pracy z Visual Studio Professional edition lub nowszy.|  
|[Zestaw reguł zabezpieczeń dla kodu zarządzanego](../code-quality/security-rules-rule-set-for-managed-code.md)|Ten zestaw reguł zawiera wszystkie reguły zabezpieczeń firmy Microsoft. Obejmują ten zestaw reguł, aby zmaksymalizować liczbę potencjalnych problemów z zabezpieczeniami, które są zgłaszane.|
