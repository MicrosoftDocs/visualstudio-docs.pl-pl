---
title: 'CA2236: Wywołuj metody klasy bazowej typu ISerializable | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4ec8c14da5c691f6f9740c6df86cb38aeb9fac5e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60057644"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Wywołuj metody klasy bazowej dla typów ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ pochodzi od typu, który implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejsu i jeden z następujących warunków jest spełniony:

- Typ implementuje konstruktora serializacji, to znaczy konstruktora o <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> podpis parametru, ale nie wywołuje konstruktor serializacji typu podstawowego.

- Typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metody, ale nie mogą wywoływać <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody typu podstawowego.

## <a name="rule-description"></a>Opis reguły
 W procesie serializacji niestandardowej typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody do wykonywania serializacji jej pola i Konstruktor serializacji, aby deserializować pola. Jeśli typ pochodzi z typu, który implementuje <xref:System.Runtime.Serialization.ISerializable> interfejs, typ podstawowy <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody i serializacja konstruktora powinna być wywoływana do serializacji/cofania-serialize pola typu podstawowego. W przeciwnym razie typu nie można serializować i deserializowany poprawnie. Jeśli typ pochodny nie dodasz nowe pola, typ musi implementować <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metoda ani konstruktora serializacji lub zadzwoń odpowiedniki typu podstawowego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy wywołać typu podstawowego <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metoda lub Konstruktor serializacji z odpowiadającej pochodne typu metoda lub Konstruktor.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ pochodny spełniającego reguły przez wywołanie konstruktora serializacji i <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody klasy bazowej.

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2240: Poprawnie zaimplementuj interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Poprawnie Implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Oznacz wszystkie pola nieprzeznaczone do](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Udostępnij metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)
