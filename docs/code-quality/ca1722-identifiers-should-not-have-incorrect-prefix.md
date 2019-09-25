---
title: 'CA1722: Identyfikatory nie powinny mieć nieprawidłowych prefiksów'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb41f2ad4548933d10137e7f72cae59643d33043
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233878"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Identyfikatory nie powinny mieć nieprawidłowych prefiksów

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Kategoria|Microsoft.Naming|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Identyfikator ma nieprawidłowy prefiks.

## <a name="rule-description"></a>Opis reguły
Zgodnie z konwencją, tylko niektóre elementy programowania mają nazwy rozpoczynające się od określonego prefiksu.

Nazwy typów nie mają określonego prefiksu i nie powinny być poprzedzone znakiem "C". Ta reguła zgłasza naruszenia dla nazw typów, takich jak "CMyClass" i nie zgłasza naruszeń dla nazw typów, takich jak "Cache".

Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Ta spójność zmniejsza krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Usuń prefiks z identyfikatora.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="related-rules"></a>Powiązane reguły
[CA1715 Identyfikatory powinny mieć poprawny prefiks](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)