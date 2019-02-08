---
title: 'CA1709: Identyfikatory powinny mieć prawidłową wielkość liter'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f692218cd051338a6bd4e83a07d985bb52f907e6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932082"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Identyfikatory powinny mieć prawidłową wielkość liter

|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Przerywanie — gdy wywołany zestawów, przestrzeni nazw, typów, elementów członkowskich i parametry.<br /><br /> Bez podziału — gdy wywoływane w parametrach typu ogólnego.|

## <a name="cause"></a>Przyczyna
 Nazwa identyfikatora nie jest poprawna.

 \- lub —

 Nazwa identyfikatora zawiera akronim dwuliterowych, a drugi literą jest pisana małymi literami.

 \- lub —

 Nazwa identyfikatora zawiera akronim co najmniej trzech wielkich liter.

## <a name="rule-description"></a>Opis reguły
 Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Ten spójności zmniejsza nauki, wymagana na nowe biblioteki oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.

 Według Konwencji nazwy parametrów używają notacji pisane wielkości liter i przestrzeni nazw, typu i nazwy elementów członkowskich Użyj Pascal wielkość liter w wyrazie. W nazwie formacie camelcase pierwszą literą jest pisana małymi literami, a pierwszą literę wszelkie pozostałe słów w nazwie jest wielką literą. Przykłady formacie camelcase nazw `packetSniffer`, `ioFile`, i `fatalErrorCode`. W nazwie Pascal — z uwzględnieniem wielkości liter pierwszą literą jest wielką literą, a pierwszą literę wszelkie pozostałe słów w nazwie jest wielką literą. Przykłady nazw Pascal — z uwzględnieniem wielkości liter `PacketSniffer`, `IOFile`, i `FatalErrorCode`.

 Ta zasada dzieli nazwę w oparciu o wielkość liter w wyrazie wyrazy i sprawdza, czy wszystkie wyrazy dwuliterowych z listą popularne wyrazy dwuliterowych, takie jak "In" lub "Moje". Jeśli nie zostanie znalezione dopasowanie, wyraz zakłada się, że akronim. Ponadto ta reguła zakłada, że znalazł akronim, gdy nazwa zawiera cztery wielkich liter w wierszu albo trzy wielkich liter w wierszu na końcu nazwy.

 Zgodnie z Konwencją skrótów dwuliterowych Użyj wielkie litery, a akronimów trzech lub więcej znaków Użyj Pascal wielkość liter w wyrazie. W poniższych przykładach używane jest następująca Konwencja nazewnictwa: "DB", "CR", "Cpa" i "Ecma". Poniższe przykłady naruszają Konwencji: "We/wy", "XML" i "DoD", a w przypadku nazw innych parametrów, "xp" i "Panel sterowania".

 'Identyfikator' to specjalny — z uwzględnieniem wielkości liter spowodować naruszenie tej zasady. 'Identyfikator' nie jest akronim, ale stanowi skrót od "Identyfikacja".

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień nazwę, dzięki czemu jest poprawna.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć to ostrzeżenie, jeśli masz konwencje nazewnictwa, czy identyfikator reprezentuje nazwę odpowiedniego, na przykład nazwę firmy lub technologii.

 Można również dodać konkretne terminy, skrótów i akronimów ją do niestandardowego słownika analizy kodu. Terminem do słownika nie spowoduje naruszenie tej zasady. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

## <a name="related-rules"></a>Powiązane reguły
 [CA1708: Identyfikatory powinny różnić się przez więcej niż wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)