---
title: 'CA3076: niezabezpieczone wykonywanie skryptu XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2b3e06bb7a150c4bb07eefc0571818f1127fe460
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545122"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Niezabezpieczone wykonywanie skryptu XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 W przypadku wykonywania [rozszerzalnych arkuszy stylów (XSLT)](https://support.microsoft.com/kb/313997) w aplikacjach .NET w niezabezpieczony sposób procesor może [rozpoznać niezaufane odwołania do identyfikatorów URI](https://msdn.microsoft.com/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) , które mogą ujawnić poufne informacje osobom atakującym, prowadząc do odmowy usługi i ataków między lokacjami.

## <a name="rule-description"></a>Opis reguły
 [XSLT](https://msdn.microsoft.com/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) jest standardem organizacja World Wide Web Consortium (W3C) do przekształcania danych XML. XSLT jest zwykle używany do pisania arkuszy stylów do przekształcania danych XML w inne formaty, takie jak HTML, tekst o stałej długości, tekst rozdzielony przecinkami lub inny format XML. Chociaż domyślnie zabronione, można je włączyć dla projektu.

 Aby upewnić się, że nie ujawniasz obszaru ataków, ta reguła jest wyzwalana za każdym razem, gdy XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> odbiera niezabezpieczone wystąpienia złożone z <xref:System.Xml.Xsl.XsltSettings> i <xref:System.Xml.XmlResolver> , które umożliwiają złośliwe przetwarzanie skryptów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Zastąp niezabezpieczony argument XsltSettings z XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> lub z wystąpieniem, które ma wyłączone funkcje dokumentu i wykonanie skryptu.

- Zastąp <xref:System.Xml.XmlResolver> argument wartością null lub <xref:System.Xml.XmlSecureResolver> wystąpieniem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli nie masz pewności, że dane wejściowe są znane z zaufanego źródła, nie pomijaj reguły z tego ostrzeżenia.

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

### <a name="violation"></a>Krocz

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

### <a name="solution"></a>Rozwiązanie

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

### <a name="violation"></a>Krocz

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

### <a name="solution"></a>Rozwiązanie

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
