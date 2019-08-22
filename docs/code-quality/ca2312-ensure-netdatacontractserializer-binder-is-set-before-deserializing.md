---
title: 'CA2312: Upewnij się, że właściwość NetDataContractSerializer.Binder jest ustawiona przed deserializacją'
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
- CA2312
- EnsureNetDataContractSerializerBinderIsSetBeforeDeserializing
ms.openlocfilehash: 38495a3c8d5a2efb5e5e96785cecbd6d50e9cd00
ms.sourcegitcommit: 673b9364fc9a96b027662dcb4cf5d61cab60ef11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69891111"
---
# <a name="ca2312-ensure-netdatacontractserializerbinder-is-set-before-deserializing"></a>CA2312: Upewnij się, że właściwość NetDataContractSerializer.Binder jest ustawiona przed deserializacją

|||
|-|-|
|TypeName|EnsureNetDataContractSerializerBinderIsSetBeforeDeserializing|
|CheckId|CA2312|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna

Metoda deserializacji została wywołana lub ma odwołanie <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> , a właściwość może mieć wartość null. <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType>

## <a name="rule-description"></a>Opis reguły

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Ta zasada umożliwia <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> znalezienie wywołań metod deserializacji lub odwołań, <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> gdy może mieć wartość null. Jeśli chcesz nie zezwalać na deserializacja z <xref:System.Runtime.Serialization.NetDataContractSerializer> niezależnie <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> od właściwości, wyłącz tę regułę i [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md), a następnie Włącz regułę [CA2310](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md).

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
  - Upewnij się, że wszystkie ścieżki kodu <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> mają ustawioną właściwość.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

### <a name="violation"></a>Krocz

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;

[DataContract]
public class BookRecord
{
    [DataMember]
    public string Title { get; set; }

    [DataMember]
    public string Author { get; set; }

    [DataMember]
    public int PageCount { get; set; }

    [DataMember]
    public AisleLocation Location { get; set; }
}

[DataContract]
public class AisleLocation
{
    [DataMember]
    public char Aisle { get; set; }

    [DataMember]
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public NetDataContractSerializer Serializer { get; set; }

    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) this.Serializer.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization

<DataContract()>
Public Class BookRecord
    <DataMember()>
    Public Property Title As String

    <DataMember()>
    Public Property Author As String

    <DataMember()>
    Public Property Location As AisleLocation
End Class

<DataContract()>
Public Class AisleLocation
    <DataMember()>
    Public Property Aisle As Char

    <DataMember()>
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Property Serializer As NetDataContractSerializer

    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(Me.Serializer.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;

public class BookRecordSerializationBinder : SerializationBinder
{
    public override Type BindToType(string assemblyName, string typeName)
    {
        // One way to discover expected types is through testing deserialization
        // of **valid** data and logging the types used.

        ////Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')");

        if (typeName == "BookRecord" || typeName == "AisleLocation")
        {
            return null;
        }
        else
        {
            throw new ArgumentException("Unexpected type", nameof(typeName));
        }
    }
}

[DataContract]
public class BookRecord
{
    [DataMember]
    public string Title { get; set; }

    [DataMember]
    public string Author { get; set; }

    [DataMember]
    public int PageCount { get; set; }

    [DataMember]
    public AisleLocation Location { get; set; }
}

[DataContract]
public class AisleLocation
{
    [DataMember]
    public char Aisle { get; set; }

    [DataMember]
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        serializer.Binder = new BookRecordSerializationBinder();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) serializer.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization

Public Class BookRecordSerializationBinder
    Inherits SerializationBinder

    Public Overrides Function BindToType(assemblyName As String, typeName As String) As Type
        ' One way to discover expected types is through testing deserialization
        ' of **valid** data and logging the types used.

        'Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')")

        If typeName = "BinaryFormatterVB.BookRecord" Or typeName = "BinaryFormatterVB.AisleLocation" Then
            Return Nothing
        Else
            Throw New ArgumentException("Unexpected type", NameOf(typeName))
        End If
    End Function
End Class

<DataContract()>
Public Class BookRecord
    <DataMember()>
    Public Property Title As String

    <DataMember()>
    Public Property Author As String

    <DataMember()>
    Public Property Location As AisleLocation
End Class

<DataContract()>
Public Class AisleLocation
    <DataMember()>
    Public Property Aisle As Char

    <DataMember()>
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        serializer.Binder = New BookRecordSerializationBinder()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(serializer.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

## <a name="related-rules"></a>Powiązane reguły

[CA2310: Nie używaj niezabezpieczonego deserializacji NetDataContractSerializer](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md)

[CA2311: Nie wykonuj deserializacji bez wcześniejszego ustawienia NetDataContractSerializer. Binder](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)
