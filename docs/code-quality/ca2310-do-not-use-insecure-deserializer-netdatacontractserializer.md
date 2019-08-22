---
title: 'CA2310: Nie używaj niezabezpieczonego deserializatora NetDataContractSerializer'
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
ms.openlocfilehash: 09496fd11945ec4d419cc215569a7436f96d71ec
ms.sourcegitcommit: 673b9364fc9a96b027662dcb4cf5d61cab60ef11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69891150"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310: Nie używaj niezabezpieczonego deserializatora NetDataContractSerializer

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerNetDataContractSerializer|
|CheckId|CA2310|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna

<xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> Metoda deserializacji została wywołana lub przywoływana.

## <a name="rule-description"></a>Opis reguły

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Ta zasada umożliwia <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> znalezienie wywołań metod deserializacji lub odwołań. Jeśli chcesz zdeserializować tylko wtedy, gdy <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> właściwość jest ustawiona na ograniczanie typów, wyłącz tę regułę i Włącz w zamian reguły [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) i [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) .

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Jeśli to możliwe, zamiast tego Użyj bezpiecznego serializatora i **nie Zezwalaj osobie atakującej na określenie dowolnego typu do deserializacji**. Niektóre bezpieczniejsze serializacji obejmują:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>— Nigdy nie <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>używaj. Jeśli musisz użyć mechanizmu rozpoznawania typów, Ogranicz typy deserializowane do oczekiwanej listy.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET — Użyj TypeNameHandling. None. Jeśli musisz użyć innej wartości dla TypeNameHandling, Ogranicz typy deserializowane do oczekiwanej listy za pomocą niestandardowego ISerializationBinder.
  - Bufory protokołu
- Przekształć dane serializowane. Po serializacji należy kryptograficznie podpisywać serializowane dane. Przed deserializacji Sprawdź poprawność podpisu kryptograficznego. Ochrona klucza kryptograficznego przed ujawnieniem i projektowaniem na potrzeby rotacji kluczy.
- Ogranicz typy deserializowane. Implementowanie niestandardowego <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Przed deserializacji z <xref:System.Runtime.Serialization.NetDataContractSerializer>należy <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> ustawić właściwość na wystąpienie niestandardowe <xref:System.Runtime.Serialization.SerializationBinder>. W przypadku przesłoniętej <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metody, jeśli typ jest nieoczekiwany, Zgłoś wyjątek, aby zatrzymać deserializacji.
  - W przypadku ograniczenia typów deserializowanych można wyłączyć tę regułę i włączyć reguły [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) i [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md). Reguły [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) i [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) pomagają <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> upewnić się, że właściwość jest zawsze ustawiona przed deserializacji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

### <a name="violation"></a>Krocz

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

[CA2311: Nie wykonuj deserializacji bez wcześniejszego ustawienia NetDataContractSerializer. Binder](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312: Upewnij się, że ustawiono NetDataContractSerializer. Binder przed deserializacji](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
