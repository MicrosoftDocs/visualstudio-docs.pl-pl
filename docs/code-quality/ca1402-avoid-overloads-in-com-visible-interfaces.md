---
title: 'CA1402: Unikaj przeciążeń w interfejsach widocznych dla modelu COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3f1bd825d2e2a74178c9ec03a0abc51d3385ba29
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546560"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: Unikaj przeciążeń w interfejsach widocznych dla modelu COM

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Component Object Model (COM) deklaruje widoczne interfejsu przeciążone metody.

## <a name="rule-description"></a>Opis reguły
 Gdy przeciążone metody są udostępniane klientom COM, tylko pierwsze przeciążenie metody zachowuje swoją nazwę. Kolejne przeciążenia są jednoznacznie nazywane przez dołączenie do nazwy znaku podkreślenia "_" i liczba całkowita, która odpowiada kolejności deklaracji przeciążeń przeciążeń. Na przykład należy wziąć pod uwagę następujące metody:

```csharp
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

Te metody są widoczne dla klientów modelu COM jako poniżej.

```csharp
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

Klienci Visual Basic 6 COM nie może implementować metody interfejsu za pomocą znaku podkreślenia w nazwie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić nazwy przeciążonych metod, aby nazwy są unikatowe. Alternatywnie ukrywanie interfejs dla modelu COM, zmieniając ułatwień dostępu do `internal` (`Friend` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) lub przez zastosowanie <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> ustawioną wartość atrybutu `false`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy kod przedstawia interfejs, który narusza regułę określającą, a interfejsem, który spełnia reguły.

 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Unikaj statycznych elementów członkowskich w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz także

- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
- [Long, typ danych](/dotnet/visual-basic/language-reference/data-types/long-data-type)