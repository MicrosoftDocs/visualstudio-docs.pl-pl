---
title: 'CA2300: Nie używaj niezabezpieczonego deserializatora BinaryFormatter'
ms.date: 04/05/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
f1_keywords:
- CA2300
- DoNotUseInsecureDeserializerBinaryFormatter
ms.openlocfilehash: 13b50e9eba49ff3457aff41d59448f1a0dfc2ea7
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65083886"
---
# <a name="ca2300-do-not-use-insecure-deserializer-binaryformatter"></a>CA2300: Nie używaj niezabezpieczonego deserializatora BinaryFormatter

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerBinaryFormatter|
|CheckId|CA2300|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

A <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> metody deserializacji został o nazwie lub odwołania.

## <a name="rule-description"></a>Opis reguły

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Ta reguła umożliwia znalezienie <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> deserializacji wywołania metody lub odwołania. Jeśli chcesz wykonać deserializacji tylko wtedy, gdy <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> właściwość jest ustawiona na ograniczenia typów, wyłącz tę regułę i włączyć reguły [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) i [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) zamiast tego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Jeśli to możliwe, Użyj bezpiecznego serializator, i **nie można określić dowolny typ do deserializacji osobie atakującej**. Niektóre bezpieczniejsze serializatory obejmują:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Nigdy nie używaj <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Jeśli musisz użyć typu program rozpoznawania nazw, ograniczyć typy po deserializacji do oczekiwanej listy.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET — Użyj TypeNameHandling.None. Jeśli musisz użyć innej wartości dla TypeNameHandling, ograniczyć po deserializacji typów do oczekiwanej listy przy użyciu niestandardowych ISerializationBinder.
  - Protocol Buffers
- Należy odporne serializowanych danych. Po serializacji podpisać kryptograficznie serializowanych danych. Przed deserializacji należy zweryfikować podpisu kryptograficznego. Ochrona klucza kryptograficznego zostały ujawnione i projektowanie pod kątem wymiany kluczy.
- Ograniczenia typów po deserializacji. Implementowanie niestandardowego <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Przed deserializacji za pomocą <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>ustaw <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> właściwości wystąpienia niestandardowego <xref:System.Runtime.Serialization.SerializationBinder>. W zgodnym z przesłoniętą <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metody, jeśli typ jest nieoczekiwana i zgłosić wyjątek.
- Można ograniczyć typy po deserializacji, możesz chcieć wyłączyć tę regułę, a następnie włącz reguły [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) i [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md). Reguły [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) i [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) pomoc, aby upewnić się, że <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> właściwość ma zawsze wartość przed deserializacji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie zasad

```csharp
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        return formatter.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization.Formatters.Binary

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        Return formatter.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>Powiązane reguły

[CA2301: Nie wywołuj BinaryFormatter.Deserialize bez uprzedniego ustawienia BinaryFormatter.Binder](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)

[CA2302: Upewnij się, że ustawiono BinaryFormatter.Binder przed wywołaniem BinaryFormatter.Deserialize](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)