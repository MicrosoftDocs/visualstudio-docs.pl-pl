---
title: 'CA3075: Niezabezpieczone przetwarzanie definicji DTD'
ms.date: 03/18/2019
ms.topic: reference
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42efb51dfe9c447538fe8f01bdd37c73bf993d8f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237118"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: Niezabezpieczone przetwarzanie definicji DTD

|||
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

W przypadku korzystania z niezabezpieczonych <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> wystąpień lub odwoływania się do zewnętrznych źródeł jednostek Analizator może zaakceptować niezaufane dane wejściowe i ujawnić poufne informacje osobom atakującym.

## <a name="rule-description"></a>Opis reguły

*Definicja typu dokumentu (DTD)* to jeden z dwóch sposobów, przez który parser XML może ustalić ważność dokumentu, zgodnie z definicją [organizacja World Wide Web Consortium (W3C) XML (XML) 1,0](http://www.w3.org/TR/2008/REC-xml-20081126/). Ta reguła umożliwia wyszukiwanie właściwości i wystąpień, w przypadku których dane niezaufane są akceptowane, aby ostrzec deweloperów o potencjalnych zagrożeniach związanych z [ujawnianiem informacji](/dotnet/framework/wcf/feature-details/information-disclosure) lub atakami [typu "odmowa usługi" (DOS)](/dotnet/framework/wcf/feature-details/denial-of-service) . Ta zasada wyzwala następujące wyzwalacze:

- DtdProcessing jest włączona w <xref:System.Xml.XmlReader> wystąpieniu, które rozpoznaje zewnętrzne jednostki XML przy użyciu. <xref:System.Xml.XmlUrlResolver>

- <xref:System.Xml.XmlNode.InnerXml%2A> Właściwość w pliku XML jest ustawiona.

- <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>Właściwość jest ustawiona na wartość Parse.

- Niezaufane dane wejściowe są przetwarzane przy <xref:System.Xml.XmlResolver> użyciu <xref:System.Xml.XmlSecureResolver>zamiast.

- Metoda jest wywoływana z niezabezpieczonym <xref:System.Xml.XmlReaderSettings> wystąpieniem lub bez wystąpienia. <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType>

- <xref:System.Xml.XmlReader>jest tworzony z niezabezpieczonymi domyślnymi ustawieniami lub wartościami.

W każdym z tych przypadków wynik jest taki sam: zawartość z systemu plików lub udziałów sieciowych z komputera, na którym jest przetwarzany kod XML, będzie widoczna dla osoby atakującej lub można użyć przetwarzania DTD jako wektora DoS.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Należy prawidłowo przechwycić i przetworzyć wszystkie wyjątki XmlTextReader, aby uniknąć ujawnienia informacji o ścieżce.

- Użyj, <xref:System.Xml.XmlSecureResolver> aby ograniczyć zasoby, do których XmlTextReader może uzyskać dostęp.

- Nie Zezwalaj <xref:System.Xml.XmlReader> na otwieranie jakichkolwiek zasobów zewnętrznych przez <xref:System.Xml.XmlResolver> ustawienie właściwości na **null**.

- Upewnij się, <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A?displayProperty=nameWithType> że właściwość jest przypisana z zaufanego źródła.

**.NET 3,5 i starsze**

- Wyłącz przetwarzanie DTD w przypadku postępowania z niezaufanymi źródłami, ustawiając <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> właściwość na **wartość true**.

- Klasa XmlTextReader ma pełne żądanie dziedziczenia zaufania.

**.NET 4 i nowsze**

- Unikaj włączania DtdProcessing w przypadku korzystania z niezaufanych źródeł przez ustawienie właściwości <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A?displayProperty=nameWithType> na wartość **Zabroń** lub **Ignoruj**.

- Upewnij się, że metoda Load () przyjmuje wystąpienie elementu XmlReader we wszystkich przypadkach InnerXml.

> [!NOTE]
> Ta reguła może zgłosić fałszywie dodatnie dla niektórych prawidłowych wystąpień XmlSecureResolver.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli nie masz pewności, że dane wejściowe są znane z zaufanego źródła, nie pomijaj reguły z tego ostrzeżenia.

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

### <a name="violation"></a>Krocz

```csharp
using System.IO;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlSchema schema = XmlSchema.Read(tr, null); // warn
            return schema;
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System.IO;
using System.Xml;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlTextReader reader = new XmlTextReader(tr) { DtdProcessing = DtdProcessing.Prohibit };
            XmlSchema schema = XmlSchema.Read(reader , null);
            return schema;
        }
    }
}
```

### <a name="violation"></a>Krocz

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings();
        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);  // warn
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings()
        {
            DtdProcessing = DtdProcessing.Prohibit
        };

        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);
        }
    }
}
```

### <a name="violations"></a>Ze

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseSetInnerXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument() { XmlResolver = null };
            doc.InnerXml = xml; // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseLoadXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument(){ XmlResolver = null };
            doc.LoadXml(xml); // warn
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System.Xml;

public static void TestMethod(string xml)
{
    XmlDocument doc = new XmlDocument() { XmlResolver = null };
    System.IO.StringReader sreader = new System.IO.StringReader(xml);
    XmlReader reader = XmlReader.Create(sreader, new XmlReaderSettings() { XmlResolver = null });
    doc.Load(reader);
}
```

### <a name="violation"></a>Krocz

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            serializer.Deserialize(stream); // warn
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            XmlReader reader = XmlReader.Create(stream, new XmlReaderSettings() { XmlResolver = null });
            serializer.Deserialize(reader );
        }
    }
}
```

### <a name="violation"></a>Krocz

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XPathDocument doc = new XPathDocument(path); // warn
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XmlReader reader = XmlReader.Create(path, new XmlReaderSettings() { XmlResolver = null });
            XPathDocument doc = new XPathDocument(reader);
        }
    }
}
```

### <a name="violation"></a>Krocz

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = new XmlUrlResolver() };
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = null }; // or set to a XmlSecureResolver instance
    }
}
```

### <a name="violations"></a>Ze

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod()
        {
            var reader = XmlTextReader.Create(""doc.xml""); //warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            try {
                XmlTextReader reader = new XmlTextReader(path); // warn
            }
            catch { throw ; }
            finally {}
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings() { XmlResolver = null };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```
