---
title: 'CA3076: Niezabezpieczone wykonywanie skryptu XSLT'
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c6c5df0109a8cff3cefcc308ea27077ef0fbe03
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237078"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Niezabezpieczone wykonywanie skryptu XSLT

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Jeśli wykonasz rozszerzalne przekształcenia języka (XSLT) w aplikacjach .NET, procesor może rozpoznać niezaufane odwołania do identyfikatorów URI, które mogą ujawnić poufne informacje osobom atakującym, prowadząc do odmowy usługi i wielu lokacji ataków. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń XSLT (Przewodnik po sieci)](/dotnet/standard/data/xml/xslt-security-considerations).

## <a name="rule-description"></a>Opis reguły

**XSLT** jest standardem organizacja World Wide Web Consortium (W3C) do przekształcania danych XML. XSLT jest zwykle używany do pisania arkuszy stylów do przekształcania danych XML w inne formaty, takie jak HTML, tekst o stałej długości, tekst rozdzielony przecinkami lub inny format XML. Chociaż domyślnie zabronione, można je włączyć dla projektu.

Aby upewnić się, że nie ujawniasz obszaru ataków, ta reguła jest wyzwalana za każdym razem, gdy XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> odbiera niezabezpieczone wystąpienia złożone z <xref:System.Xml.Xsl.XsltSettings> i <xref:System.Xml.XmlResolver>, które umożliwiają złośliwe przetwarzanie skryptów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Zastąp niezabezpieczony argument XsltSettings z XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> lub z wystąpieniem, które ma wyłączone funkcje dokumentu i wykonanie skryptu.

- <xref:System.Xml.XmlSecureResolver> Zastąp <xref:System.Xml.XmlResolver> argument wartością null lub wystąpieniem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli nie masz pewności, że dane wejściowe są znane z zaufanego źródła, nie pomijaj reguły z tego ostrzeżenia.

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

### <a name="violation-that-uses-xsltsettingstrustedxslt"></a>Naruszenie używające XsltSettings. TrustedXslt

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

### <a name="solution-that-uses-xsltsettingsdefault"></a>Rozwiązanie używające XsltSettings. default

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

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>Funkcja&mdash;dokumentu naruszenia i wykonywanie skryptu nie są wyłączone

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

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Rozwiązanie&mdash;Wyłącz funkcję dokumentu i wykonanie skryptu

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

- [Zagadnienia dotyczące zabezpieczeń XSLT (Przewodnik po sieci)](/dotnet/standard/data/xml/xslt-security-considerations)