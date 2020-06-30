---
title: 'CA1709: Identyfikatory powinny mieć prawidłową wielkość liter | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 14c50ed94f05401cc5575af9f8b98472c35b261d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544004"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Identyfikatory powinny mieć prawidłową wielkość liter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly).

|Element|Wartość|
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Przerywanie — gdy jest wywoływany dla zestawów, przestrzeni nazw, typów, elementów członkowskich i parametrów.<br /><br /> Rozdzielenie — w przypadku uruchomienia parametrów typu ogólnego.|

## <a name="cause"></a>Przyczyna
 Nazwa identyfikatora nie ma poprawnej wielkości liter.

 \-oraz

 Nazwa identyfikatora zawiera dwuliterowy akronim, a druga litera jest małymi literami.

 \-oraz

 Nazwa identyfikatora zawiera akronim trzech lub więcej wielkich liter.

## <a name="rule-description"></a>Opis reguły
 Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zmniejsza to krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

 Według Konwencji nazwy parametrów używają notacji CamelCase wielkości liter; nazwy przestrzeni nazw, typów i elementów członkowskich używają wielkości liter w języku Pascal. W nazwie notacji CamelCase, pierwsza litera jest małymi literami, a pierwsza litera dowolnego wyrazu w nazwie jest wielką literą. Przykłady nazw notacji CamelCase — "packetSniffer", "ioFile" i "fatalErrorCode". W nazwie z wielkością liter w języku Pascal pierwsza litera jest wielką literą, a pierwsza litera dowolnego wyrazu w nazwie jest wielką literą. Przykłady nazw z wielkością liter w języku Pascala to "PacketSniffer", "IOFile" i "FatalErrorCode".

 Ta reguła dzieli nazwę na wyrazy w oparciu o wielkość liter i sprawdza wszystkie dwuliterowe słowa w odniesieniu do listy typowych wyrazów dwuliterowych, takich jak "in" lub "my". Jeśli dopasowanie nie zostanie znalezione, przyjmuje się, że słowo jest akronimem. Ponadto ta reguła zakłada, że znaleziono akronim, gdy nazwa zawiera cztery wielkie litery w wierszu lub trzy wielkie litery w wierszu na końcu nazwy.

 Zgodnie z Konwencją, dwuliterowe akronimy używają wszystkich wielkich liter i akronimów trzech lub więcej znaków używają wielkości liter w Pascalu. W poniższych przykładach użyto tej konwencji nazewnictwa: "DB", "CR", "CPA" i "ECMA". Poniższe przykłady naruszają Konwencję: "IO", "XML" i "DoD" oraz dla nazw nieparametrów, "XP" i "cpl".

 Wartość "ID" jest specjalną wielkością liter, aby spowodować naruszenie tej reguły. Element "ID" nie jest akronimem, ale jest skrótem dla elementu "Identification".

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień nazwę tak, aby była uwzględniana wielkość liter.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 W przypadku posiadania własnych konwencji nazewnictwa można bezpiecznie pominąć to ostrzeżenie lub, jeśli identyfikator reprezentuje poprawną nazwę, na przykład nazwę firmy lub technologię.

 Możesz również dodać określone terminy, skróty i akronimy do słownika niestandardowego analizy kodu. Warunki określone w słowniku niestandardowym nie spowodują naruszeń tej reguły. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

## <a name="related-rules"></a>Powiązane reguły
 [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
