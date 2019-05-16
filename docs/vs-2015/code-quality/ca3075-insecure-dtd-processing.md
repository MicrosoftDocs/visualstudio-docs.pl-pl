---
title: 'CA3075: Niezabezpieczone przetwarzanie definicji DTD | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 694b72327d8e059fe12a227afdab79219081ef92
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693416"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: Niezabezpieczone przetwarzanie definicji DTD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Jeśli używasz niezabezpieczone <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> wystąpień lub odwołanie do jednostki zewnętrznej źródeł, analizator może akceptować niezaufanych danych wejściowych i ujawnienia poufnych informacji dla osób atakujących.

## <a name="rule-description"></a>Opis reguły
 A [definicji typu dokumentu (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) jest jeden z dwóch sposobów analizatora XML można określić ważności dokumentu, zgodnie z definicją [World Wide Web Consortium (W3C) XML Extensible Markup Language () 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Ta reguła szuka właściwości i wystąpienia, gdzie niezaufanych danych jest akceptowany w celu otrzymania deweloperów o potencjalnych [ujawnienie informacji](https://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) zagrożenia, które mogą prowadzić do [przeprowadzenie ataku typu "odmowa usługi" (DoS)](https://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) ataków. Ta zasada wyzwala, gdy:

- Włączono XmlReaderSettings <xref:System.Xml.XmlReader> wystąpienia, który jest rozpoznawany jako zewnętrzne jednostki XML przy użyciu <xref:System.Xml.XmlUrlResolver>.

- <xref:System.Xml.XmlNode.InnerXml%2A> Ustawiono właściwość w pliku XML.

- <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> wartość właściwości jest równa analizy.

- Niezaufane dane wejściowe zostanie przetworzona przy użyciu <xref:System.Xml.XmlResolver> zamiast <xref:System.Xml.XmlSecureResolver> .

- Element XmlReader.<xref:System.Xml.XmlReader.Create%2A> Metoda jest wywoływana za pomocą niezabezpieczonego <xref:System.Xml.XmlReaderSettings> wystąpienia lub nie wcale.

- <xref:System.Xml.XmlReader> jest tworzona przy użyciu ustawień domyślnych niezabezpieczone lub wartości.

  W każdym z tych przypadków, wynik jest taki sam: zawartość z dowolnego systemu lub sieci udziały plików na komputerze, gdzie jest przetwarzany plik XML, będzie ona widoczna dla osoby atakującej, może być następnie użyta jako wektor systemu DoS.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- CATCH i przetwórz wszystkie wyjątki klasy XmlTextReader poprawnie, aby uniknąć ujawnienia informacji ścieżki.

- Użyj <xref:System.Xml.XmlSecureResolver> do ograniczania zasobów, które mogą uzyskiwać dostęp do klasy XmlTextReader.

- Nie zezwalaj na <xref:System.Xml.XmlReader> otworzyć dowolnych zasobów zewnętrznych, ustawiając <xref:System.Xml.XmlResolver> właściwości **null**.

- Upewnij się, że <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> właściwość <xref:System.Data.DataViewManager> jest przydzielany z zaufanego źródła.

  .NET 3.5 i starszych

- Wyłącz przetwarzanie DTD, jeśli masz do czynienia ze źródeł niezaufanych, ustawiając <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> właściwości **true** .

- Klasy XmlTextReader ma dziedziczenia pełnego zaufania. Zobacz [Inheritancedemand](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) Aby uzyskać więcej informacji.

  .NET 4 i nowsze

- Unikaj włączania XmlReaderSettings, jeśli są zajmujących źródeł niezaufanych, ustawiając właściwość XmlReaderSettings [Zabroń lub Ignoruj](https://msdn.microsoft.com/library/system.xml.dtdprocessing.aspx)

- Upewnij się, że metoda Load() przyjmuje instancję XmlReader we wszystkich przypadkach elementu.

> [!NOTE]
> Ta zasada może raportować pewnych wystąpień z prawidłową XmlSecureResolver wyników fałszywie dodatnich. Pracujemy nad rozwiązywania tego problemu przez mid 2016.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli nie masz pewności, że dane wejściowe jest znany jako z zaufanego źródła, nie Pomijaj reguły z tego ostrzeżenia.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie zasad

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

### <a name="violation"></a>Naruszenie zasad

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

### <a name="violations"></a>Naruszenia

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

### <a name="violation"></a>Naruszenie zasad

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

### <a name="violation"></a>Naruszenie zasad

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

### <a name="violation"></a>Naruszenie zasad

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

### <a name="violations"></a>Naruszenia

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
