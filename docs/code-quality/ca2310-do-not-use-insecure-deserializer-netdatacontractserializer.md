---
title: 'CA2310: Do not use insecure deserializer NetDataContractSerializer'
ms.date: 05/01/2019
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
- CA2310
- DoNotUseInsecureDeserializerNetDataContractSerializer
ms.openlocfilehash: e4af6bbfbd7e14b99f39ffa0adb5d1117c200d9a
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65135558"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310: Do not use insecure deserializer NetDataContractSerializer

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerNetDataContractSerializer|
|CheckId|CA2310|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

A <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> metody deserializacji został o nazwie lub odwołania.

## <a name="rule-description"></a>Opis reguły

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Ta reguła umożliwia znalezienie <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> deserializacji wywołania metody lub odwołania. Jeśli chcesz wykonać deserializacji tylko wtedy, gdy <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> właściwość jest ustawiona na ograniczenia typów, wyłącz tę regułę i włączyć reguły [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) i [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) zamiast tego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Jeśli to możliwe, Użyj bezpiecznego serializator, i **nie można określić dowolny typ do deserializacji osobie atakującej**. Niektóre bezpieczniejsze serializatory obejmują:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Nigdy nie używaj <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Jeśli musisz użyć typu program rozpoznawania nazw, ograniczyć typy po deserializacji do oczekiwanej listy.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET — Użyj TypeNameHandling.None. Jeśli musisz użyć innej wartości dla TypeNameHandling, ograniczyć po deserializacji typów do oczekiwanej listy przy użyciu niestandardowych ISerializationBinder.
  - Protocol Buffers
- Należy odporne serializowanych danych. Po serializacji podpisać kryptograficznie serializowanych danych. Przed deserializacji należy zweryfikować podpisu kryptograficznego. Ochrona klucza kryptograficznego zostały ujawnione i projektowanie pod kątem wymiany kluczy.
- Ograniczenia typów po deserializacji. Implementowanie niestandardowego <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Przed deserializacji za pomocą <xref:System.Runtime.Serialization.NetDataContractSerializer>ustaw <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> właściwości wystąpienia niestandardowego <xref:System.Runtime.Serialization.SerializationBinder>. W zgodnym z przesłoniętą <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metody, jeśli typ jest nieoczekiwana i zgłosić wyjątek.
- Można ograniczyć typy po deserializacji, możesz chcieć wyłączyć tę regułę, a następnie włącz reguły [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) i [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md). Reguły [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) i [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) pomoc, aby upewnić się, że <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> właściwość ma zawsze wartość przed deserializacji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie zasad

```csharp
using System.IO;
using System.Runtime.Serialization;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        return serializer.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        Return serializer.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>Powiązane reguły

[CA2311: Nie wykonać deserializacji bez uprzedniego ustawienia NetDataContractSerializer.Binder](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312: Upewnij się, że NetDataContractSerializer.Binder jest ustawione przed deserializacji](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
