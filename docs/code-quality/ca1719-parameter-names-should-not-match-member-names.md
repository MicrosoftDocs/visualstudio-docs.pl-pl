---
title: 'CA1719: Nazwy parametrów nie powinny być zgodne z nazwami składowych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b3e34bec0e199e1eb0b49a88517e9551b9b13cd
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921626"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Nazwy parametrów nie powinny być zgodne z nazwami składowych

|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Nazwa elementu członkowskiego widocznego na zewnątrz, w porównaniu z uwzględnieniem wielkości liter, nazwa jednego z jego parametrów.

## <a name="rule-description"></a>Opis reguły
Nazwa parametru powinna przekazywać znaczenie parametru, a nazwa elementu członkowskiego — znaczenie elementu członkowskiego. W projekcie rzadko są one takie same. Nazywanie parametru tak samo jak nazwa jego elementu członkowskiego jest nieintuicyjne i utrudnia korzystanie z biblioteki.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Wybierz nazwę parametru, która nie jest zgodna z nazwą elementu członkowskiego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
W przypadku nowych rozwiązań nie występują żadne znane scenariusze, w których należy pominąć ostrzeżenie z tej reguły. W przypadku bibliotek wysyłkowych może być konieczne pominięcie ostrzeżenia z tej reguły.

## <a name="related-rules"></a>Powiązane reguły
[CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

[CA1708 Identyfikatory powinny różnić się więcej niż wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

[CA1707 Identyfikatory nie powinny zawierać podkreśleń](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)