---
title: 'CA3075: niezabezpieczone przetwarzanie DTD | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d8cd78b529618504b5f14905a764c369da249fe2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545174"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: Niezabezpieczone przetwarzanie definicji DTD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 W przypadku korzystania z niezabezpieczonych <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> wystąpień lub odwoływania się do zewnętrznych źródeł jednostek Analizator może zaakceptować niezaufane dane wejściowe i ujawnić poufne informacje osobom atakującym.

## <a name="rule-description"></a>Opis reguły
 [Definicja typu dokumentu (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) to jeden z dwóch sposobów, przez który parser XML może ustalić ważność dokumentu, zgodnie z definicją [organizacja World Wide Web Consortium (W3C) XML (XML) 1,0](https://www.w3.org/TR/2008/REC-xml-20081126/). Ta reguła umożliwia wyszukiwanie właściwości i wystąpień, w przypadku których niezaufane dane są akceptowane, aby ostrzec deweloperów o potencjalnych zagrożeniach związanych z [ujawnianiem informacji](https://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) , co może prowadzić do ataków [typu "odmowa usługi" (DOS)](https://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) . Ta zasada wyzwala następujące wyzwalacze:

- DtdProcessing jest włączona w <xref:System.Xml.XmlReader> wystąpieniu, które rozpoznaje zewnętrzne jednostki XML przy użyciu <xref:System.Xml.XmlUrlResolver> .

- <xref:System.Xml.XmlNode.InnerXml%2A>Właściwość w pliku XML jest ustawiona.

- <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>Właściwość jest ustawiona na wartość Parse.

- Niezaufane dane wejściowe są przetwarzane przy użyciu <xref:System.Xml.XmlResolver> zamiast <xref:System.Xml.XmlSecureResolver> .

- Element XmlReader.<xref:System.Xml.XmlReader.Create%2A> Metoda jest wywoływana z niezabezpieczonym <xref:System.Xml.XmlReaderSettings> wystąpieniem lub bez wystąpienia.

- <xref:System.Xml.XmlReader>jest tworzony z niezabezpieczonymi domyślnymi ustawieniami lub wartościami.

  W każdym z tych przypadków wynik jest taki sam: zawartość z systemu plików lub udziałów sieciowych z komputera, na którym jest przetwarzany kod XML, zostanie uwidoczniona dla osoby atakującej, która może być następnie użyta jako wektor DoS.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Należy prawidłowo przechwycić i przetworzyć wszystkie wyjątki XmlTextReader, aby uniknąć ujawnienia informacji o ścieżce.

- Użyj,  <xref:System.Xml.XmlSecureResolver> Aby ograniczyć zasoby, do których XmlTextReader może uzyskać dostęp.

- Nie Zezwalaj na  <xref:System.Xml.XmlReader> otwieranie jakichkolwiek zasobów zewnętrznych przez ustawienie <xref:System.Xml.XmlResolver> właściwości na **null**.

- Upewnij się, że <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> Właściwość <xref:System.Data.DataViewManager> jest przypisana z zaufanego źródła.

  .NET 3,5 i starsze

- Wyłącz przetwarzanie DTD w przypadku postępowania z niezaufanymi źródłami, ustawiając  <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> Właściwość na **wartość true** .

- Klasa XmlTextReader ma pełne żądanie dziedziczenia zaufania. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące dziedziczenia](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) .

  .NET 4 i nowsze

- Unikaj włączania DtdProcessing w przypadku korzystania z niezaufanych źródeł przez ustawienie właściwości DtdProcessing na wartość [Zabroń lub zignoruj](https://msdn.microsoft.com/library/system.xml.dtdprocessing.aspx)

- Upewnij się, że metoda Load () przyjmuje wystąpienie elementu XmlReader we wszystkich przypadkach InnerXml.

> [!NOTE]
> Ta reguła może zgłosić fałszywie dodatnie dla niektórych prawidłowych wystąpień XmlSecureResolver. Pracujemy nad rozwiązaniem tego problemu w witrynie Mid 2016.

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
    XmlTextReader reader = new XmlTextReader(sreader) { DtdProcessing = DtdProcessing.Prohibit };
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
            XmlTextReader reader = new XmlTextReader(stream) { DtdProcessing = DtdProcessing.Prohibit } ;
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
            XmlTextReader reader = new XmlTextReader(path) { DtdProcessing = DtdProcessing.Prohibit };
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
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Parse };
            XmlReader reader = XmlReader.Create(path, settings); // warn
        }
    }
}
```

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
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Prohibit };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```
