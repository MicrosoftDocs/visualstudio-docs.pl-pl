---
title: 'CA2213: pola jednorazowe powinny zostać usunięte | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8ebeae3e5e367bb2c1a09bc1cb38dcc80d2c3826
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662901"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Pola usuwalne powinny zostać usunięte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName> deklaruje pola, które są typu, które również implementują <xref:System.IDisposable>. Metoda <xref:System.IDisposable.Dispose%2A> pola nie jest wywoływana przez metodę <xref:System.IDisposable.Dispose%2A> typu deklarującego.

## <a name="rule-description"></a>Opis reguły
 Typ jest odpowiedzialny za usuwanie wszystkich zasobów niezarządzanych; jest to realizowane przez implementację <xref:System.IDisposable>. Ta reguła sprawdza, czy typ jednorazowy `T` deklaruje `F` pola, które jest wystąpieniem typu, `FT`. Dla każdego `F` pola reguła próbuje zlokalizować wywołanie do `FT.Dispose`. Reguła przeszukuje metody wywoływane przez `T.Dispose` i niższy poziom (metody wywoływane przez metody wywoływane przez `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, wywołaj <xref:System.IDisposable.Dispose%2A> dla pól, które implementują <xref:System.IDisposable>, jeśli użytkownik jest odpowiedzialny za przydzielanie i zwalnianie zasobów niezarządzanych przechowywanych w polu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli użytkownik nie jest odpowiedzialny za zwolnienie zasobu przechowywanego przez pole lub wywołanie <xref:System.IDisposable.Dispose%2A> występuje na bardziej szczegółowym poziomie niż sprawdzanie reguły, jest bezpieczne.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ `TypeA`, który implementuje <xref:System.IDisposable> (`FT` w poprzedniej dyskusji).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typ `TypeB`, który narusza tę regułę przez zadeklarowanie `aFieldOfADisposableType` pola (`F` w poprzedniej dyskusji) jako typ jednorazowy (`TypeA`) i nie wywoływanie <xref:System.IDisposable.Dispose%2A> w polu. `TypeB` odpowiada `T` w poprzedniej dyskusji.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable?displayProperty=fullName> — [wzorzec usuwania](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
