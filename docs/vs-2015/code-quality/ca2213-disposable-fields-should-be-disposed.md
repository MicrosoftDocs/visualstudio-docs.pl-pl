---
title: 'CA2213: Pola możliwe do rozporządzania należy rozporządzać | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 680a956f96599e2f12c14f4fc1eac828e57a57d7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53928982"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Pola możliwe do rozporządzania należy rozporządzać
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName> deklaruje pola, które są typami, które implementują także <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Metody pól nie jest wywoływany przez <xref:System.IDisposable.Dispose%2A> metody typu deklarującego.

## <a name="rule-description"></a>Opis reguły
 Typ jest odpowiedzialny za usuwanie wszystkich jej zasobów niezarządzanych; jest to realizowane poprzez implementację <xref:System.IDisposable>. Ta reguła sprawdza, czy typu usuwalnego `T` deklaruje pole `F` oznacza to wystąpienie typu usuwalnego `FT`. Dla każdego pola `F`, reguła próbuje zlokalizować wywołanie `FT.Dispose`. Reguła wyszukuje metody wywoływane przez `T.Dispose`, a jeden poziom w dół (metody wywoływane przez metody wywołane `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy wywołać <xref:System.IDisposable.Dispose%2A> w polach, które są typami, które implementują <xref:System.IDisposable> Jeżeli jesteś odpowiedzialny za przydzielanie i zwalniania niezarządzanych zasobów przechowywanych przez pole.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Bezpiecznie Pomijaj ostrzeżeń dla tej reguły, jeśli nie jesteś odpowiedzialny dla przy zwalnianiu zasobów przechowywanych przez pole lub jeśli wywołanie <xref:System.IDisposable.Dispose%2A> występuje dokładniejsze wywoływania niż sprawdzanie reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano typu `TypeA` implementującej <xref:System.IDisposable> (`FT` w poprzednim dyskusji).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano typu `TypeB` który narusza tę regułę przez zadeklarowanie pola `aFieldOfADisposableType` (`F` w poprzednim dyskusji) jako możliwe do rozporządzania typ (`TypeA`) i nie wywołuje metody <xref:System.IDisposable.Dispose%2A> pola. `TypeB` odnosi się do `T` w poprzednim dyskusji.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable?displayProperty=fullName> [Wzorzec Dispose](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
