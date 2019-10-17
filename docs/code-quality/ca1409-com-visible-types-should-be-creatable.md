---
title: 'CA1409: Typy widoczne dla modelu COM powinny być możliwe do utworzenia'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 402ce13b55921045f8e06d99bbe6b1e3918e457a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440280"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Typy widoczne dla modelu COM powinny być możliwe do utworzenia

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Kategoria|Microsoft. współdziałanie|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Typ referencyjny, który jest jawnie oznaczony jako widoczny dla Component Object Model (COM) zawiera publiczny, sparametryzowany Konstruktor, ale nie zawiera publicznego domyślnego (bezparametrowego) konstruktora.

## <a name="rule-description"></a>Opis reguły
Nie można utworzyć typu bez publicznego konstruktora domyślnego przez klientów modelu COM. Jednak dla klientów modelu COM można nadal uzyskać dostęp do tego typu, jeśli jest dostępny inny sposób tworzenia typu i przekazywania go do klienta (na przykład za pośrednictwem wartości zwracanej wywołania metody).

Reguła ignoruje typy pochodzące z <xref:System.Delegate?displayProperty=fullName>.

Domyślnie następujące elementy są widoczne dla modelu COM: zestawy, typy publiczne, składowe wystąpienia publicznego w typach publicznych oraz wszystkie elementy członkowskie publicznych typów wartości.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Dodaj publiczny Konstruktor domyślny lub Usuń <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> z typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Jeśli istnieją inne sposoby tworzenia i przekazywania obiektu do klienta COM, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="related-rules"></a>Powiązane reguły
[CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz także

- [Kwalifikowanie typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
