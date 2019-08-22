---
title: 'CA2301: Nie wywołuj metody BinaryFormatter.Deserialize bez uprzedniego ustawienia właściwości BinaryFormatter.Binder'
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
- CA2301
- DoNotCallBinaryFormatterDeserializeWithoutFirstSettingBinaryFormatterBinder
ms.openlocfilehash: 0291aa4d8130cfdc9b919e0c8430e56ef0f95296
ms.sourcegitcommit: 673b9364fc9a96b027662dcb4cf5d61cab60ef11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69891194"
---
# <a name="ca2301-do-not-call-binaryformatterdeserialize-without-first-setting-binaryformatterbinder"></a>CA2301: Nie wywołuj metody BinaryFormatter.Deserialize bez uprzedniego ustawienia właściwości BinaryFormatter.Binder

|||
|-|-|
|TypeName|DoNotCallBinaryFormatterDeserializeWithoutFirstSettingBinaryFormatterBinder|
|CheckId|CA2301|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna

Metoda deserializacji została wywołana lub ma <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> odwołanie bez zestawu właściwości. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType>

## <a name="rule-description"></a>Opis reguły

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Ta zasada umożliwia <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> znalezienie wywołań metod deserializacji lub odwołań, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> gdy nie ma <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> ustawionej wartości. Jeśli chcesz nie zezwalać na deserializacja z <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> niezależnie <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> od właściwości, wyłącz tę regułę i [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md), a następnie Włącz regułę [CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md).

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

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

### <a name="violation"></a>Krocz

```csharp
using System;
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

[Serializable]
public class BookRecord
{
    public string Title { get; set; }
    public string Author { get; set; }
    public int PageCount { get; set; }
    public AisleLocation Location { get; set; }
}

[Serializable]
public class AisleLocation
{
    public char Aisle { get; set; }
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) formatter.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization.Formatters.Binary

<Serializable()>
Public Class BookRecord
    Public Property Title As String
    Public Property Author As String
    Public Property Location As AisleLocation
End Class

<Serializable()>
Public Class AisleLocation
    Public Property Aisle As Char
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(formatter.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;
using System.Runtime.Serialization.Formatters.Binary;

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

[Serializable]
public class BookRecord
{
    public string Title { get; set; }
    public string Author { get; set; }
    public int PageCount { get; set; }
    public AisleLocation Location { get; set; }
}

[Serializable]
public class AisleLocation
{
    public char Aisle { get; set; }
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        formatter.Binder = new BookRecordSerializationBinder();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) formatter.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization
Imports System.Runtime.Serialization.Formatters.Binary

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

<Serializable()>
Public Class BookRecord
    Public Property Title As String
    Public Property Author As String
    Public Property Location As AisleLocation
End Class

<Serializable()>
Public Class AisleLocation
    Public Property Aisle As Char
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        formatter.Binder = New BookRecordSerializationBinder()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(formatter.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

## <a name="related-rules"></a>Powiązane reguły

[CA2300: Nie używaj niezabezpieczonego deserializacji BinaryFormatter](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)

[CA2302: Upewnij się, że ustawiono BinaryFormatter. Binder przed wywołaniem BinaryFormatter. deserializacji](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)