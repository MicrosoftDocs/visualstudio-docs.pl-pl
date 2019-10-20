---
title: 'CA1402: Unikaj przeciążeń w interfejsach widocznych dla modelu COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 258b7ba1444cd990c3ec68ebfd5faccc945439e8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661348"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: Unikaj przeciążeń w interfejsach widocznych dla modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Interfejs widoczny dla Component Object Model (COM) deklaruje przeciążone metody.

## <a name="rule-description"></a>Opis reguły
 Gdy przeciążone metody są udostępniane klientom COM, tylko pierwsze przeciążenie metody zachowuje swoją nazwę. Kolejne przeciążenia mają unikatowe nazwy przez dołączenie do nazwy znaku podkreślenia "_" i liczby całkowitej odpowiadającej kolejności deklaracji przeciążenia. Rozważmy na przykład następujące metody.

```
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

 Te metody są udostępniane klientom modelu COM w następujący sposób.

```
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

 Klienci Visual Basic 6 COM nie mogą implementować metod interfejsu przy użyciu znaku podkreślenia w nazwie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień nazwy przeciążonych metod tak, aby nazwy były unikatowe. Alternatywnie, aby interfejs był niewidoczny dla modelu COM, należy zmienić dostępność na `internal` (`Friend` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) lub stosując atrybut <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> ustawiony na `false`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje interfejs, który narusza regułę i interfejs, który spełnia regułę.

 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/cs/FxCop.Interoperability.OverloadsInterface.cs#1)]
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/vb/FxCop.Interoperability.OverloadsInterface.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Unikaj składowych statycznych w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz też
 [Współdziałanie z niezarządzanym](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [typem danych long](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516) Code
