---
title: 'CA1301: Unikaj zduplikowanych akceleratorów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 647fef2968971cddb6a14cc19e53eed979b9c151
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661518"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Należy unikać duplikowania akceleratorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Kategoria|Microsoft. Globalizacja|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ rozszerza <xref:System.Windows.Forms.Control?displayProperty=fullName> i zawiera co najmniej dwie kontrolki najwyższego poziomu, które mają identyczne klucze dostępu, które są przechowywane w pliku zasobów.

## <a name="rule-description"></a>Opis reguły
 Klucz dostępu, znany również jako akcelerator, umożliwia dostęp z klawiatury do formantu za pomocą klawisza ALT. Kiedy wiele formantów ma zduplikowany klucz dostępu, jego zachowanie nie jest dobrze zdefiniowane. Użytkownik może nie mieć dostępu do zamierzonej kontroli przy użyciu klucza dostępu, a kontrolka inna niż ta, która jest zamierzona, może być włączona.

 Bieżąca implementacja tej reguły ignoruje elementy menu. Jednak elementy menu w tym samym podmenu nie powinny mieć identycznych kluczy dostępu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, zdefiniuj unikatowe klucze dostępu dla wszystkich kontrolek.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano minimalną postać zawierającą dwie kontrolki, które mają identyczne klucze dostępu. Klucze są przechowywane w pliku zasobów, który nie jest wyświetlany; jednak ich wartości są wyświetlane w wierszach z komentarzem `checkBox.Text`. Zachowanie zduplikowanych akceleratorów można sprawdzić przez wymianę wierszy `checkBox.Text` z ich komentarzem. Jednak w tym przypadku przykład nie spowoduje wygenerowania ostrzeżenia z reguły.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>Zobacz też
 [zasoby <xref:System.Resources.ResourceManager?displayProperty=fullName> w aplikacjach klasycznych](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
