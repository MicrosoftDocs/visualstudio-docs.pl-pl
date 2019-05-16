---
title: 'CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 38d8195baa540c2c212c71938b6266e28df49101
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683064"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Ciąg zasobu zawiera wyraz złożony, który nie ma mieć prawidłową wielkość liter.

## <a name="rule-description"></a>Opis reguły
 Każdego wyrazu w ciągu zasobu jest podzielony na tokeny, które są oparte na wielkość liter w wyrazie. Każda ciągła kombinacja dwóch tokenów jest sprawdzana przez bibliotekę sprawdzania pisowni firmy Microsoft. Jeżeli zostanie rozpoznana, dane słowo powoduje naruszenie reguły. Przykłady wyrazy złożone, powodujących naruszenie to "CheckSum" i "MultiPart", które powinny być pisane w formie "Checksum" i "Multipart", odpowiednio. Ze względu na poprzednie powszechnie kilkoma wyjątkami są wbudowane w zasady i są oznaczane kilka pojedyncze wyrazy, takie jak "Toolbar" i "Filename", które powinny być pisane w formie dwóch unikatowych słów. W tym przykładzie zostanie oznaczony "ToolBar" i "FileName".

 Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to nauki, jest wymagany dla nowe biblioteki oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień litery słowo, dzięki czemu jest poprawna.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli obie części wyraz złożony są rozpoznawane przez słownik sprawdzania pisowni, a celem jest użycie dwóch słów.

 Możesz również dodać wyrazy złożone do słownika niestandardowego sprawdzania pisowni. Wyrazy do słownika nie powodują naruszenia. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Powiązane reguły
 [CA1702: Wyrazy złożone powinny mieć prawidłową wielkość liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identyfikatory powinny różnić się przez więcej niż wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Zobacz też
 [Konwencje dotyczące wielkości liter](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d) [wskazówki dotyczące nazewnictwa](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)
