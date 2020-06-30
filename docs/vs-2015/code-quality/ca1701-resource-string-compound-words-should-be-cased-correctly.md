---
title: 'CA1701: wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7c1c3b0fd6cf3a25d5db9e3039d4dc5d8364a18e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544108"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Ciąg zasobu zawiera wyraz złożony, który nie jest wyświetlany w przypadku poprawnego wielkości liter.

## <a name="rule-description"></a>Opis reguły
 Każdy wyraz w ciągu zasobu jest podzielony na tokeny, które są oparte na wielkości liter. Każda ciągła kombinacja dwóch tokenów jest sprawdzana przez bibliotekę sprawdzania pisowni firmy Microsoft. Jeżeli zostanie rozpoznana, dane słowo powoduje naruszenie reguły. Przykładami wyrazów złożonych, które powodują naruszenie, są "CheckSum" i "wieloczęściowa", które powinny być odpowiednio określone jako "Checksum" i "wieloczęściowa". Ze względu na poprzednie typowe użycie, kilka wyjątków jest wbudowanych w regułę, a kilka pojedynczych wyrazów jest oflagowanych, takich jak "Toolbar" i "filename", które powinny być uwzględniane w przypadku dwóch odrębnych wyrazów. W tym przykładzie "ToolBar" i "FileName" byłyby oflagowane.

 Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zmniejsza to krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień słowo tak, aby była uwzględniana wielkość liter.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli obie części wyrazu złożonego są rozpoznawane przez słownik pisowni, można bezpiecznie pominąć ostrzeżenie z tej reguły, a zamiarem jest użycie dwóch wyrazów.

 Możesz również dodać wyrazy złożone do słownika niestandardowego dla narzędzia sprawdzania pisowni. Słowa w słowniku niestandardowym nie powodują naruszeń. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Powiązane reguły
 [CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Zobacz też
 [Wskazówki dotyczące nazewnictwa](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) [Konwencji wielką literą](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
