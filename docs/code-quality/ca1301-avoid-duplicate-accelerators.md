---
title: 'CA1301: Unikaj duplikowania akceleratorów'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f50be12f4d601161ec20659bbb6b710e5a7cf24
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235161"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Unikaj duplikowania akceleratorów

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Kategoria|Microsoft. Globalizacja|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Typ rozszerza <xref:System.Windows.Forms.Control?displayProperty=fullName> i zawiera dwie lub więcej formantów najwyższego poziomu, które mają identyczne klucze dostępu, które są przechowywane w pliku zasobów.

## <a name="rule-description"></a>Opis reguły

Klucz dostępu, znany również jako akcelerator, umożliwia dostęp z klawiatury do kontrolki za pomocą klawisza **Alt** . Gdy wiele kontrolek ma ten sam klucz dostępu, zachowanie klucza dostępu nie jest dobrze zdefiniowane. Użytkownik może nie mieć dostępu do zamierzonej kontroli przy użyciu klucza dostępu, a kontrolka inna niż ta, która jest zamierzona, może być włączona.

Bieżąca implementacja tej reguły ignoruje elementy menu. Jednak elementy menu w tym samym podmenu nie powinny mieć identycznych kluczy dostępu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, zdefiniuj unikatowe klucze dostępu dla wszystkich kontrolek.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
W poniższym przykładzie pokazano minimalną postać zawierającą dwie kontrolki, które mają identyczne klucze dostępu. Klucze są przechowywane w pliku zasobów, który nie jest wyświetlany. Jednak ich wartości są wyświetlane w `checkBox.Text` wierszach z komentarzem. Zachowanie zduplikowanych akceleratorów może być badane przez wymianę `checkBox.Text` wierszy z ich komentarzem. Jednak w tym przypadku przykład nie spowoduje wygenerowania ostrzeżenia z reguły.

[!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Zasoby w aplikacjach klasycznych](/dotnet/framework/resources/index)