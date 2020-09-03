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
ms.openlocfilehash: 74e93a9644f365120117bd247d2ea8b9d43608cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548190"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Publiczne Wyliczenie ma, <xref:System.FlagsAttribute?displayProperty=fullName> a jego nazwa nie kończy się znakiem ".

## <a name="rule-description"></a>Opis reguły
 Typy oznaczone nazwą <xref:System.FlagsAttribute> mają nazwy, które są w liczbie mnogiej, ponieważ atrybut wskazuje, że można określić więcej niż jedną wartość. Na przykład Wyliczenie definiujące dni tygodnia może być przeznaczone do użycia w aplikacji, w której można określić wiele dni. To Wyliczenie powinno mieć wartość <xref:System.FlagsAttribute> i może być nazywane "dniami". Podobne Wyliczenie, które zezwala na określenie tylko jednego dnia, nie ma atrybutu i może być wywołane "Day".

 Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zmniejsza to krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień nazwę wyliczenia na słowo w liczbie mnogiej lub usuń atrybut, <xref:System.FlagsAttribute> Jeśli nie można jednocześnie określić wielu wartości wyliczenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli nazwa jest słowem w liczbie mnogiej, ale nie kończy się znakiem ", można bezpiecznie pominąć naruszenie. Na przykład, jeśli Wyliczenie wielodniowe, które zostało opisane wcześniej miało nazwę "DaysOfTheWeek", spowoduje to naruszenie logiki reguły, ale nie jej potrzeby. Takie naruszenia powinny być pomijane.

## <a name="related-rules"></a>Powiązane reguły
 [CA1027: Oznacz typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Nie oznaczaj typów wyliczeniowych atrybutem Flags](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.FlagsAttribute?displayProperty=fullName>[Projekt wyliczenia](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
