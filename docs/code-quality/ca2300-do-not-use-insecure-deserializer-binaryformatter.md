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
ms.openlocfilehash: 4ca4990308ceab21e2c6e256770ff37a3ca9a6fc
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237945"
---
# <a name="ca2300-do-not-use-insecure-deserializer-binaryformatter"></a>CA2300: Nie używaj niezabezpieczonego deserializatora BinaryFormatter

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerBinaryFormatter|
|CheckId|CA2300|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> Metoda deserializacji została wywołana lub przywoływana.

## <a name="rule-description"></a>Opis reguły

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Ta zasada umożliwia <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> znalezienie wywołań metod deserializacji lub odwołań. Jeśli chcesz zdeserializować tylko wtedy, gdy <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> właściwość jest ustawiona na ograniczanie typów, wyłącz tę regułę i Włącz w zamian reguły [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) i [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) .

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Jeśli to możliwe, zamiast tego Użyj bezpiecznego serializatora i **nie Zezwalaj osobie atakującej na określenie dowolnego typu do deserializacji**. Niektóre bezpieczniejsze serializacji obejmują:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>— Nigdy nie <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>używaj. Jeśli musisz użyć mechanizmu rozpoznawania typów, Ogranicz typy deserializowane do oczekiwanej listy.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET — Użyj TypeNameHandling. None. Jeśli musisz użyć innej wartości dla TypeNameHandling, Ogranicz typy deserializowane do oczekiwanej listy za pomocą niestandardowego ISerializationBinder.
  - Bufory protokołu
- Przekształć dane serializowane. Po serializacji należy kryptograficznie podpisywać serializowane dane. Przed deserializacji Sprawdź poprawność podpisu kryptograficznego. Ochrona klucza kryptograficznego przed ujawnieniem i projektowaniem na potrzeby rotacji kluczy.
- Ogranicz typy deserializowane. Implementowanie niestandardowego <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Przed deserializacji z <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>należy <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> ustawić właściwość na wystąpienie niestandardowe <xref:System.Runtime.Serialization.SerializationBinder>. W przypadku przesłoniętej <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metody, jeśli typ jest nieoczekiwany, Zgłoś wyjątek, aby zatrzymać deserializacji.
  - W przypadku ograniczenia typów deserializowanych można wyłączyć tę regułę i włączyć reguły [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) i [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md). Reguły [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) i [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) pomagają <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> upewnić się, że właściwość jest zawsze ustawiona przed deserializacji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

### <a name="violation"></a>Krocz

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

[CA2301: Nie wywołuj BinaryFormatter. deserializacji bez wcześniejszego ustawienia BinaryFormatter. Binder](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)

[CA2302: Upewnij się, że ustawiono BinaryFormatter. Binder przed wywołaniem BinaryFormatter. deserializacji](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)