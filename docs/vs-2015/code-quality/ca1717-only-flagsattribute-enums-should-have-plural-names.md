---
title: 'CA1717: tylko wyliczenia FlagsAttribute powinny mieć nazwy w liczbie mnogiej | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0c378d419be0d964c27cfcbe523fbe3a33da97b8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669081"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Tylko typy wyliczeniowe FlagsAttribute powinny mieć nazwy w liczbie mnogiej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa widocznego na zewnątrz wyliczenia zostanie zakończona w słowie w liczbie mnogiej, a Wyliczenie nie jest oznaczone atrybutem <xref:System.FlagsAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 Konwencje nazewnictwa wymuszają, że nazwa w liczbie mnogiej dla wyliczenia wskazuje, że można określić więcej niż jedną wartość wyliczenia jednocześnie. @No__t_0 informuje kompilatory, że Wyliczenie powinno być traktowane jako pole bitowe, które włącza operacje bitowe na wyliczeniu.

 Jeśli można określić tylko jedną wartość wyliczenia, nazwa wyliczenia powinna być słowem jednopojedynczym. Na przykład Wyliczenie definiujące dni tygodnia może być przeznaczone do użycia w aplikacji, w której można określić wiele dni. To Wyliczenie powinno mieć <xref:System.FlagsAttribute> i może być nazywane "dniami". Podobne Wyliczenie, które zezwala na określenie tylko jednego dnia, nie ma atrybutu i może być wywołane "Day".

 Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Pozwala to skrócić czas wymagany do nauczenia się nowej biblioteki oprogramowania i zwiększyć zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wprowadź nazwę wyliczenia jako pojedyncze słowo lub Dodaj <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli nazwa zostanie zakończona pojedynczym słowem, można bezpiecznie pominąć ostrzeżenie z reguły.

## <a name="related-rules"></a>Powiązane reguły
 [CA1714: Wyliczenia flag powinny mieć nazwy w liczbie mnogiej](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: Oznacz typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Nie oznaczaj wyliczeń za pomocą atrybutu FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Zobacz też
 [projekt wyliczenia](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545) <xref:System.FlagsAttribute?displayProperty=fullName>
