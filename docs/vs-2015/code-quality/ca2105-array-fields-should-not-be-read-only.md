---
title: 'CA2105: pola tablicy nie powinny być tylko do odczytu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: db52bf869642a5bdcc28eeb0792b295ae314a508
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538674"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: Pola tablicy nie powinny być tylko do odczytu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Pole publiczne lub chronione, które przechowuje tablicę, jest zadeklarowane jako tylko do odczytu.

## <a name="rule-description"></a>Opis reguły
 Po zastosowaniu `readonly` `ReadOnly` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] modyfikatora (in) do pola, które zawiera tablicę, pola nie można zmienić, aby odwoływać się do innej tablicy. Można jednak zmienić elementy tablicy, które są przechowywane w polu tylko do odczytu. Kod, który podejmuje decyzje lub wykonuje operacje oparte na elementach tablicy tylko do odczytu, które mogą być dostępne publicznie, może zawierać lukę w zabezpieczeniach.

 Należy pamiętać, że posiadanie pola publicznego narusza także reguły projektowania [CA1051: Nie deklaruj widocznych pól wystąpień](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić lukę w zabezpieczeniach, która jest identyfikowana przez tę regułę, nie należy polegać na zawartości tablicy tylko do odczytu, która jest dostępna publicznie. Zdecydowanie zaleca się użycie jednej z następujących procedur:

- Zastąp tablicę kolekcją o jednoznacznie określonym typie, której nie można zmienić. Aby uzyskać więcej informacji, zobacz <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Zastąp pole publiczne metodą zwracającą klon tablicy prywatnej. Ponieważ kod nie bazuje na klonie, nie ma żadnych zagrożeń, jeśli elementy są modyfikowane.

  W przypadku wybrania drugiego podejścia nie należy zamieniać pola na Właściwość; Właściwości, które zwracają tablice, mają negatywny wpływ na wydajność. Aby uzyskać więcej informacji, zobacz [CA1819: właściwości nie powinny zwracać tablic](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Wyłączenie ostrzeżenia z tej reguły jest zdecydowanie odradzane. Niemal nie występują żadne scenariusze, w których zawartość pola tylko do odczytu nie jest ważna. W takim przypadku w scenariuszu Usuń `readonly` modyfikator zamiast wykluczania komunikatu.

## <a name="example"></a>Przykład
 Ten przykład pokazuje zagrożenie naruszenia tej reguły. Pierwsza część pokazuje przykładową bibliotekę, która ma typ, `MyClassWithReadOnlyArrayField` który zawiera dwa pola ( `grades` i), `privateGrades` które nie są bezpieczne. Pole `grades` jest publiczne i dlatego jest narażone na dowolnego wywołującego. Pole `privateGrades` jest prywatne, ale jest nadal podatne na ataki, ponieważ jest zwracane do wywoływania przez `GetPrivateGrades` metodę. `securePrivateGrades`Pole jest udostępniane w sposób bezpieczny przez `GetSecurePrivateGrades` metodę. Jest on zadeklarowany jako prywatny do przestrzegania dobrych praktyk projektowania. Druga część pokazuje kod, który zmienia wartości przechowywane w `grades` i `privateGrades` elementów członkowskich.

 Przykładowa Biblioteka klas zostanie wyświetlona w poniższym przykładzie.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>Przykład
 Poniższy kod używa przykładowej biblioteki klas do zilustrowania problemów z zabezpieczeniami tablicy tylko do odczytu.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 Dane wyjściowe z tego przykładu to:

 **Przed manipulacją: klasy: 90, 90, 90 prywatne klasy: 90, 90, 90 bezpieczne klasy, 90, 90, 90** 
 **Po manipulowaniu: klasy: 90, 555, 90 prywatne klasy: 90, 555, 90 Secure klasy, 90, 90, 90**
## <a name="see-also"></a>Zobacz też
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
