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
ms.openlocfilehash: 887600bad0c3d05ff78050aa4449cf49dc882027
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534579"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Pola możliwe do likwidacji należy likwidować
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName> deklarowane pola, które są typu, które również implementują <xref:System.IDisposable> . <xref:System.IDisposable.Dispose%2A>Metoda pola nie jest wywoływana przez <xref:System.IDisposable.Dispose%2A> metodę typu deklarującego.

## <a name="rule-description"></a>Opis reguły
 Typ jest odpowiedzialny za usuwanie wszystkich zasobów niezarządzanych; jest to realizowane przez implementację <xref:System.IDisposable> . Ta reguła sprawdza, czy typ jednorazowy `T` deklaruje pole `F` , które jest wystąpieniem typu jednorazowego `FT` . Dla każdego pola `F` reguła próbuje zlokalizować wywołanie `FT.Dispose` . Reguła przeszukuje metody wywoływane przez `T.Dispose` , i niższy poziom (metody wywoływane przez metody wywoływane przez `FT.Dispose` ).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, wywołaj <xref:System.IDisposable.Dispose%2A> pola należące do typów, które implementują, <xref:System.IDisposable> Jeśli użytkownik jest odpowiedzialny za przydzielanie i zwalnianie niezarządzanych zasobów przechowywanych w polu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli użytkownik nie ponosi odpowiedzialności za zwolnienie zasobu przechowywanego przez pole lub jeśli wywołanie <xref:System.IDisposable.Dispose%2A> wystąpi na bardziej szczegółowym poziomie wywoływania niż sprawdzanie reguły, jest bezpieczne.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ `TypeA` , który implementuje <xref:System.IDisposable> ( `FT` w poprzedniej dyskusji).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typ `TypeB` , który narusza tę regułę przez zadeklarowanie pola `aFieldOfADisposableType` ( `F` w poprzedniej dyskusji) jako typ jednorazowy ( `TypeA` ) i nie wywoływanie <xref:System.IDisposable.Dispose%2A> dla tego pola. `TypeB`odpowiada `T` w poprzedniej dyskusji.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable?displayProperty=fullName>Usuń [wzorzec](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
