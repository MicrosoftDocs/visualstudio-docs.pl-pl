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
ms.openlocfilehash: 558e205fa37569bfa12d7b93f989d0f8ebabab43
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669061"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Niezabezpieczone wykonywanie skryptu XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Jeśli wykonujesz [rozszerzalne przekształcenia języka (XSLT)](https://support.microsoft.com/kb/313997) w aplikacjach .NET, procesor może [rozpoznać niezaufane odwołania do identyfikatorów URI](https://msdn.microsoft.com/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) , które mogą ujawnić poufne informacje osobom atakującym, prowadząc do odmowy Ataki między usługami i między lokacjami.

## <a name="rule-description"></a>Opis reguły
 [XSLT](https://msdn.microsoft.com/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) jest standardem organizacja World Wide Web Consortium (W3C) do przekształcania danych XML. XSLT jest zwykle używany do pisania arkuszy stylów do przekształcania danych XML w inne formaty, takie jak HTML, tekst o stałej długości, tekst rozdzielony przecinkami lub inny format XML. Chociaż domyślnie zabronione, można je włączyć dla projektu.

 Aby upewnić się, że nie ujawniasz obszaru ataków, ta reguła jest wyzwalana za każdym razem, gdy XslCompiledTransform. <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> odbiera niebezpieczne wystąpienia kombinacji <xref:System.Xml.Xsl.XsltSettings> i <xref:System.Xml.XmlResolver>, co umożliwia przetwarzanie złośliwego skryptu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Zastąp niezabezpieczony argument XsltSettings z XsltSettings. <xref:System.Xml.Xsl.XsltSettings.Default%2A> lub z wystąpieniem, które ma wyłączone funkcje dokumentu i wykonanie skryptu.

- Zastąp argument <xref:System.Xml.XmlResolver> wartością null lub wystąpieniem <xref:System.Xml.XmlSecureResolver>.

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
