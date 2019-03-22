---
title: 'CA1702: Wyrazy złożone powinny mieć prawidłową wielkość liter | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9f4844431215d952f03ab9acc3f11ab57644abde
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355213"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA1702: Wyrazy złożone powinny mieć prawidłową wielkość liter](https://docs.microsoft.com/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly) w witrynie docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Istotne, kiedy jest uruchamiany na zestawach.<br /><br /> Bez podziału — gdy wywoływane w parametrach typu.|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa identyfikatora zawiera wiele wyrazów i co najmniej jedno ze słów wydaje się wyrazem złożonym, który nie jest poprawna.  
  
## <a name="rule-description"></a>Opis reguły  
 Nazwa identyfikatora jest dzielony na wyrazy, które są oparte na wielkość liter w wyrazie. Kombinacjami word dwóch sąsiadujących jest sprawdzana przez bibliotekę sprawdzania pisowni Microsoft. Jeśli został rozpoznany identyfikator powoduje naruszenie reguły. Przykłady wyrazy złożone, powodujących naruszenie to "CheckSum" i "MultiPart", które powinny być pisane w formie "Checksum" i "Multipart", odpowiednio. Ze względu na poprzednie powszechnie kilkoma wyjątkami są wbudowane w zasady i są oznaczane kilka pojedyncze wyrazy, takie jak "Toolbar" i "Filename", które powinny mieć prawidłową wielkość jako dwa różne wyrazy (w tym przypadku "ToolBar" i "FileName").  
  
 Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to nauki, jest wymagany dla nowe biblioteki oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zmień nazwę, dzięki czemu jest poprawna.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli obie części wyraz złożony są rozpoznawane przez słownik sprawdzania pisowni, a celem jest użycie dwóch słów.  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Identyfikatory powinny różnić się przez więcej niż wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące nazewnictwa](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)   
 [Konwencje dotyczące wielkości liter](http://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
