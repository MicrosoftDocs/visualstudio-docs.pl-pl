---
title: 'CA2105: Pola tablicy nie powinny być tylko odczytu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0969147ce4f454f7720f26f72b46cab6e91c37bf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937982"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: Pola tablicy nie powinny być tylko odczytu

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Pole publiczne lub chronione, który zawiera tablicę jest zadeklarowany tylko do odczytu.

## <a name="rule-description"></a>Opis reguły

Po zastosowaniu `readonly` (`ReadOnly` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) modyfikatora pola, które zawiera tablicę, pola nie można zmienić do odwoływania się do innej tablicy. Można jednak zmienić elementy tablicy, które są przechowywane w polu tylko do odczytu. Kod, który podejmuje decyzje lub wykonuje operacje, które są oparte na elementach tablicy tylko do odczytu, które są publicznie dostępne mogą zawierać luki w zabezpieczeniach kończona.

Należy pamiętać, że mających publiczne pole również narusza regułę projektowania [CA1051: Nie deklaruj widocznych pól wystąpień](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby rozwiązać problem luki w zabezpieczeniach, która jest identyfikowana przez tę regułę, nie należy polegać na zawartości tablicy tylko do odczytu, które są publicznie dostępne. Zdecydowanie zaleca się korzystanie z jednej z następujących procedur:

- Zastąp tablicy silnie typizowaną kolekcją, której nie można zmienić. Aby uzyskać więcej informacji, zobacz <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Zastąp pole publiczne metody, która zwróci klon tablicy prywatnej. Ponieważ kod nie polega na klonie, nie ma ryzyka, jeśli elementy są modyfikowane.

Jeśli została wybrana opcja drugiej metody, nie zastępują pola z właściwością; właściwości zwracające tablice niekorzystnie wpłynąć na wydajność. Aby uzyskać więcej informacji, zobacz [CA1819: Właściwości nie powinny zwracać tablic](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Wykluczenie ostrzeżenie od tej reguły jest zdecydowanie odradzane. Niemal żadnych scenariuszy wystąpić, gdy zawartość pola tylko do odczytu nie są ważne. Jeśli jest to w przypadku danego scenariusza, należy usunąć `readonly` modyfikator zamiast wiadomości z wyjątkiem.

## <a name="example-1"></a>Przykład 1

W tym przykładzie pokazano niebezpieczeństwa naruszenie tej zasady. Pierwsza część zawiera biblioteki przykładu, który ma typ, `MyClassWithReadOnlyArrayField`, która zawiera dwa pola (`grades` i `privateGrades`), które nie są bezpieczne. Pole `grades` publicznej i w związku z tym narażony na dowolny obiekt wywołujący. Pole `privateGrades` jest prywatny, ale jest nadal podatne, ponieważ jest on zwracany do wywoływania przez `GetPrivateGrades` metody. `securePrivateGrades` Pole jest widoczne w bezpieczny sposób przez `GetSecurePrivateGrades` metody. Jest zadeklarowany jako prywatny dobrego projektowania rozwiązań. Druga część zawiera kod, który zmienia wartości przechowywane w `grades` i `privateGrades` elementów członkowskich.

Biblioteka klas przykład pojawia się w następującym przykładzie.

[!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]

## <a name="example-2"></a>Przykład 2

W poniższym kodzie użyto przykład biblioteki klas, aby zilustrować problemy z zabezpieczeniami tablicy tylko do odczytu.

[!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]

Dane wyjściowe z tego przykładu są:

```text
Before tampering: Grades: 90, 90, 90 Private Grades: 90, 90, 90  Secure Grades, 90, 90, 90
After tampering: Grades: 90, 555, 90 Private Grades: 90, 555, 90  Secure Grades, 90, 90, 90
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>