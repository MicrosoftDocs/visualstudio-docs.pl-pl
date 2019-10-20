---
title: 'CA1714: wyliczenia flag powinny mieć nazwy w liczbie mnogiej | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ca3709411f50d0b65f33bb8eed6457cfd1325ff6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669139"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Typy wyliczeniowe flag powinny mieć nazwy w liczbie mnogiej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Publiczne Wyliczenie ma <xref:System.FlagsAttribute?displayProperty=fullName> i jego nazwa nie kończy się znakiem ".

## <a name="rule-description"></a>Opis reguły
 Typy, które są oznaczone <xref:System.FlagsAttribute> mają nazwy, które są w liczbie mnogiej, ponieważ atrybut wskazuje, że można określić więcej niż jedną wartość. Na przykład Wyliczenie definiujące dni tygodnia może być przeznaczone do użycia w aplikacji, w której można określić wiele dni. To Wyliczenie powinno mieć <xref:System.FlagsAttribute> i może być nazywane "dniami". Podobne Wyliczenie, które zezwala na określenie tylko jednego dnia, nie ma atrybutu i może być wywołane "Day".

 Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zmniejsza to krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień nazwę wyliczenia na słowo w liczbie mnogiej lub usuń atrybut <xref:System.FlagsAttribute>, jeśli nie można jednocześnie określić wielu wartości wyliczenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli nazwa jest słowem w liczbie mnogiej, ale nie kończy się znakiem ", można bezpiecznie pominąć naruszenie. Na przykład, jeśli Wyliczenie wielodniowe, które zostało opisane wcześniej miało nazwę "DaysOfTheWeek", spowoduje to naruszenie logiki reguły, ale nie jej potrzeby. Takie naruszenia powinny być pomijane.

## <a name="related-rules"></a>Powiązane reguły
 [CA1027: Oznacz typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Nie oznaczaj wyliczeń za pomocą atrybutu FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz też
 [projekt wyliczenia](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545) <xref:System.FlagsAttribute?displayProperty=fullName>
