---
title: 'CA3076: Niezabezpieczone wykonywanie skryptu XSLT'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e162f5e883fb6c54eecc8afbbdf1c466138861fb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947793"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Niezabezpieczone wykonywanie skryptu XSLT

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Jeżeli insecurely wykonać Extensible arkuszy stylów języka przekształcenia (XSLT) w aplikacjach platformy .NET, procesor może zostać rozwiązany niezaufanych odwołań do identyfikatora URI, które można ujawnić poufne informacje do osoby atakujące, co prowadzi do "odmowa usługi" i Cross-Site ataki. Aby uzyskać więcej informacji, zobacz [Considerations(.NET Guide) zabezpieczeń XSLT](/dotnet/standard/data/xml/xslt-security-considerations).

## <a name="rule-description"></a>Opis reguły

**XSLT** jest standardem World Wide Web Consortium (W3C) do przekształcania danych XML. XSLT zazwyczaj używany do zapisywania arkuszy stylów do przekształcania danych XML do innych formatów, takich jak HTML, tekst o stałej długości, tekst rozdzielany przecinkami lub w innym formacie XML. Mimo że będzie to zabronione przez domyślne, można ją włączyć dla Twojego projektu.

Aby upewnić się, nie jest ujawniany obszar narażony na ataki, ta zasada wyzwala zawsze, gdy XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> odbiera wystąpień kombinacji niezabezpieczone <xref:System.Xml.Xsl.XsltSettings> i <xref:System.Xml.XmlResolver>, która pozwala na przetwarzanie złośliwy skrypt.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Zastąp niezabezpieczone argument XsltSettings XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> lub z wystąpieniem, wyłączył możliwość wykonywania funkcji i skryptów dokumentu.

- Zastąp <xref:System.Xml.XmlResolver> argumentu o wartości null lub <xref:System.Xml.XmlSecureResolver> wystąpienia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli nie masz pewności, że dane wejściowe jest znany jako z zaufanego źródła, nie Pomijaj reguły z tego ostrzeżenia.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation-that-uses-xsltsettingstrustedxslt"></a>Naruszenia zasad, która używa XsltSettings.TrustedXslt

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
         void TestMethod()
        {
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
        }
    }
}
```

### <a name="solution-that-uses-xsltsettingsdefault"></a>Rozwiązanie, które używa XsltSettings.Default

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>Naruszenie&mdash;dokumentu wykonanie funkcji i skryptów, nie jest wyłączone

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Rozwiązanie&mdash;wyłączyć wykonywanie funkcji i skryptów dokumentu

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```

## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące zabezpieczeń XSLT (Przewodnik platformy .NET)](/dotnet/standard/data/xml/xslt-security-considerations)