---
title: 'CA1401: wywołanie P-Invoke nie powinno być widoczne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3f867f14f7a2eca4482f1f8d5fb48149f02f43f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661357"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invokes nie powinny być widoczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda publiczna lub chroniona w typie publicznym ma atrybut <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> (również zaimplementowany przez słowo kluczowe `Declare` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="rule-description"></a>Opis reguły
 Metody, które są oznaczone atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> (lub metodami, które są zdefiniowane za pomocą słowa kluczowego `Declare` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), używają usług wywołania platformy w celu uzyskania dostępu do kodu niezarządzanego. Takie metody nie powinny być udostępniane. Utrzymując te metody w trybie prywatnym lub wewnętrznym, upewnij się, że biblioteka nie może zostać użyta w celu naruszenia zabezpieczeń przez umożliwienie wywołujących dostępu do niezarządzanych interfejsów API, które nie mogły ich wywołać w przeciwnym razie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień poziom dostępu metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład deklaruje metodę, która narusza tę regułę.

 [!code-csharp[FxCop.Interoperability.DllImports#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/cs/FxCop.Interoperability.DllImports.cs#1)]
 [!code-vb[FxCop.Interoperability.DllImports#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/vb/FxCop.Interoperability.DllImports.vb#1)]
