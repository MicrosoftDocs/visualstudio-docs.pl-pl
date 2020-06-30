---
title: 'CA1409: typy widoczne dla modelu COM powinny być możliwe do utworzenia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 180a8d6bbc7f035fa0ae2eeafaa4e2c884cddc8d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547332"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Typy widoczne dla modelu COM powinny mieć możliwość utworzenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ referencyjny, który jest jawnie oznaczony jako widoczny dla Component Object Model (COM) zawiera publiczny, sparametryzowany Konstruktor, ale nie zawiera publicznego domyślnego (bezparametrowego) konstruktora.

## <a name="rule-description"></a>Opis reguły
 Nie można utworzyć typu bez publicznego konstruktora domyślnego przez klientów modelu COM. Jednak dla klientów modelu COM można nadal uzyskać dostęp do tego typu, jeśli jest dostępny inny sposób tworzenia typu i przekazywania go do klienta (na przykład za pośrednictwem wartości zwracanej wywołania metody).

 Reguła ignoruje typy, które są wyprowadzane z <xref:System.Delegate?displayProperty=fullName> .

 Domyślnie następujące elementy są widoczne dla modelu COM: zestawy, typy publiczne, składowe wystąpienia publicznego w typach publicznych oraz wszystkie elementy członkowskie publicznych typów wartości.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Dodaj publiczny Konstruktor domyślny lub Usuń <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> z tego typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli istnieją inne sposoby tworzenia i przekazywania obiektu do klienta COM, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="related-rules"></a>Powiązane reguły
 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz też
 [Kwalifikowanie typów .NET do](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [współdziałania z kodem niezarządzanym](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
