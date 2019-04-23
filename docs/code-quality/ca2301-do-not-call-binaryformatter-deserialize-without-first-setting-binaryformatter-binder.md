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
ms.openlocfilehash: d90ed71c1d5ca4cbfdcf8e500e1d176519a2fdff
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60037599"
---
# <a name="ca2301-do-not-call-binaryformatterdeserialize-without-first-setting-binaryformatterbinder"></a>CA2301: Nie wywołuj metody BinaryFormatter.Deserialize bez uprzedniego ustawienia właściwości BinaryFormatter.Binder

|||
|-|-|
|TypeName|DoNotCallBinaryFormatterDeserializeWithoutFirstSettingBinaryFormatterBinder|
|CheckId|CA2301|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

A <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> metody deserializacji został o nazwie lub do których odwołuje się bez <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> zestawu właściwości.

## <a name="rule-description"></a>Opis reguły

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Ta reguła umożliwia znalezienie <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> deserializacji wywołania metody lub odwołania, gdy <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> nie ma jej <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> Ustaw. Jeśli chcesz uniemożliwić wszelkie deserializacja przy użyciu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> niezależnie od tego <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> właściwości, wyłącz tę regułę i [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)i włączyć regułę [CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Jeśli to możliwe, Użyj bezpiecznego serializator, i **nie można określić dowolny typ do deserializacji osobie atakującej**. Niektóre bezpieczniejsze serializatory obejmują:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Nigdy nie używaj <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Jeśli musisz użyć typu program rozpoznawania nazw, ograniczyć typy po deserializacji do oczekiwanej listy.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - NewtonSoft Json.NET — Użyj TypeNameHandling.None. Jeśli musisz użyć innej wartości dla TypeNameHandling, ograniczyć po deserializacji typów do oczekiwanej listy przy użyciu niestandardowych ISerializationBinder.
  - Protocol Buffers
- Należy odporne serializowanych danych. Po serializacji podpisać kryptograficznie serializowanych danych. Przed deserializacji należy zweryfikować podpisu kryptograficznego. Ochrona klucza kryptograficznego zostały ujawnione i projektowania dla wymiany kluczy.
- Ograniczenia typów po deserializacji. Implementowanie niestandardowego <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Przed deserializacji za pomocą <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>ustaw <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> właściwości wystąpienia niestandardowego <xref:System.Runtime.Serialization.SerializationBinder>. W zgodnym z przesłoniętą <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metody, jeśli typ jest nieoczekiwany następnie zgłoszenie wyjątku.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie zasad

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

[CA2300: Nie używaj niezabezpieczonych Deserializator elementu](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)

[CA2302: Upewnij się, że ustawiono BinaryFormatter.Binder przed wywołaniem BinaryFormatter.Deserialize](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)