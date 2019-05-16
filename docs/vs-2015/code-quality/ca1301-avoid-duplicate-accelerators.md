---
title: 'CA1301: Unikaj duplikowania akceleratorów | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a2e992cfb648b9b7f84032abab2f96d3f7cb410d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686858"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Unikaj duplikowania akceleratorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Rozszerza typ <xref:System.Windows.Forms.Control?displayProperty=fullName> i zawiera co najmniej dwóch kontrolki najwyższego poziomu, które mają identyczne klawiszy, które są przechowywane w pliku zasobów.

## <a name="rule-description"></a>Opis reguły
 Klucz dostępu, znany również jako akcelerator, umożliwia dostęp z klawiatury do formantu za pomocą klawisza ALT. Kiedy wiele formantów ma zduplikowany klucz dostępu, jego zachowanie nie jest dobrze zdefiniowane. Użytkownik może być mogli korzystać z zamierzonym kontroli przy użyciu klucza dostępu i może być włączona kontrola innym niż ten, który jest przeznaczony.

 Bieżąca implementacja parametru ta zasada powoduje ignorowanie elementów menu. Jednak elementy menu, w tym samym podmenu nie powinna mieć identyczny klawiszy.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy określić klucze dostępu unikatowe dla wszystkich kontrolek.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje minimalny formularz, który zawiera dwa formanty, które mają identyczne klawiszy. Klucze są przechowywane w pliku zasobów, który nie jest pokazany; jednak ich wartości są wyświetlane w skomentowanej się `checkBox.Text` wierszy. Zachowanie duplikowania akceleratorów można sprawdzić przez wymianę `checkBox.Text` wiersze z ich odpowiedniki skomentowanej out. Jednak w takim przypadku przykład nie wygeneruje ostrzeżenia z reguły.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Zasoby w aplikacjach klasycznych](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
