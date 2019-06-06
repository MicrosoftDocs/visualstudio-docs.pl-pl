---
title: 'CA1303: Nie przekazuj literałów jako zlokalizowanych parametrów'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cc32db1aea9c5514a7548bc889b65463de3de3d5
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714699"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Nie przekazuj literałów jako zlokalizowanych parametrów

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Metoda przekazuje ciąg literału jako parametr .NET konstruktora lub metody, a ciąg powinien być możliwy do zlokalizowania.

To ostrzeżenie jest zgłaszane, gdy literał ciągu jest przekazywany jako wartość parametru lub właściwość dotyczy co najmniej jeden z następujących przypadkach:

- <xref:System.ComponentModel.LocalizableAttribute> Atrybut parametru lub właściwość jest ustawiona na wartość true.

- Nazwa parametru lub właściwości zawiera "Text", "Message" lub "Podpis".

- Nazwa parametru ciągu, który jest przekazywany do metody Console.Write — lub elementu Console.WriteLine jest "value" lub "format".

## <a name="rule-description"></a>Opis reguły

Literały ciągów, które są osadzone w kodzie źródłowym są trudne do zlokalizowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Zamień literał ciągu pobierane w drodze wystąpienie <xref:System.Resources.ResourceManager> klasy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli nie jest lokalizowany biblioteki kodu lub jeśli ciąg nie jest uwidaczniana, aby użytkownik końcowy lub deweloperem, za pomocą biblioteki kodu.

Użytkownikom można wyeliminować szumu względem metody, które nie powinny być przekazywane zlokalizowanych ciągów, albo zmieniając nazwę parametru lub właściwości lub oznaczając te elementy jako warunkowe.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia metodę, która zgłasza wyjątek, gdy jeden z dwóch argumentów są poza zakresem. Dla pierwszego argumentu konstruktora wyjątków jest przekazywany ciąg literału, który narusza tę regułę. Drugi argument Konstruktor poprawnie jest przekazywany ciąg, który został pobrany <xref:System.Resources.ResourceManager>.

[!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
[!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
[!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>Zobacz także

- [Zasoby w aplikacjach klasycznych](/dotnet/framework/resources/index)