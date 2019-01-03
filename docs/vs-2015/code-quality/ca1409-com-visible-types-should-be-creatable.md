---
title: 'CA1409: Typy widoczne dla modelu COM powinny mieć możliwość utworzenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 11a852cba3283c437d34f43ca354a052859dedd6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985675"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Typy widoczne dla modelu COM powinny mieć możliwość utworzenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ odwołania, który jest specjalnie oznaczony jako widoczny na Component Object Model (COM) zawiera publiczny konstruktor sparametryzowany, ale nie zawiera publicznego domyślnego (bezparametrowego) konstruktora.

## <a name="rule-description"></a>Opis reguły
 Nie można utworzyć typu bez publicznego konstruktora domyślnego przez klientów modelu COM. Jednak typ nadal jest możliwy przez klientów modelu COM. Jeśli inny oznacza, że jest dostępny do utworzenia typu i przekazać go do klienta (na przykład w wyniku wartość zwracaną przez wywołanie metody).

 Reguła ignoruje typy, które są uzyskiwane z <xref:System.Delegate?displayProperty=fullName>.

 Domyślnie widoczny dla modelu COM są następujące: zestawy, typy publiczne, składowe publiczne wystąpienia w publicznych typach i wszystkich elementów członkowskich typów publicznych wartości.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy dodać publicznego konstruktora domyślnego lub usunąć <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> z typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli podano inny sposób utworzyć i przekazać obiekt do klienta COM.

## <a name="related-rules"></a>Powiązane reguły
 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz też
 [Kwalifikowanie typów .NET do międzyoperacyjności](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [współdziałanie z niezarządzanego kodu](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
