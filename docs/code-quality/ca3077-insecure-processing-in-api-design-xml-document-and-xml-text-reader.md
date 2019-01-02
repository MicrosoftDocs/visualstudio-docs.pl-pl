---
title: 'CA3077: Niezabezpieczone przetwarzanie w projekt interfejsu API, dokumencie XML i czytnik tekstu XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33c6aaea4cdc7de1c81338eb4861d56d73cb5909
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841281"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: Niezabezpieczone przetwarzanie w projekt interfejsu API, dokumencie XML i czytnik tekstu XML

|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Podczas projektowania interfejsu API pochodną klasy XMLDocument i klasy XMLTextReader, można w trosce o <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  Za pomocą niezabezpieczonego wystąpień XmlReaderSettings, gdy odwołuje się do rozpoznawania jednostek zewnętrznych źródeł lub ustawiania wartości niebezpieczne w XML może prowadzić do ujawnienia informacji.

## <a name="rule-description"></a>Opis reguły
 A *definicji typu dokumentu (DTD)* jest jeden z dwóch sposobów analizatora XML można określić ważności dokumentu, zgodnie z definicją [World Wide Web Consortium (W3C) XML Extensible Markup Language () 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Ta reguła szuka właściwości i wystąpienia, gdzie niezaufanych danych jest akceptowany w celu otrzymania deweloperów o potencjalnych [ujawnienie informacji](/dotnet/framework/wcf/feature-details/information-disclosure) zagrożenia, które mogą prowadzić do [przeprowadzenie ataku typu "odmowa usługi" (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) ataków. Ta zasada wyzwala, gdy:

- <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XmlTextReader> klasy używać domyślnego programu rozpoznawania nazw wartości przetwarzanie elementu DTD.

- Żaden konstruktor nie jest zdefiniowany dla obiektu XmlDocument klasy pochodne klasy XmlTextReader lub nie bezpieczne jest wykorzystywana do <xref:System.Xml.XmlResolver>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- CATCH i przetwórz wszystkie wyjątki klasy XmlTextReader poprawnie, aby uniknąć ujawnienia informacji ścieżki.

- Użyj <xref:System.Xml.XmlSecureResolver>zamiast element XmlResolver do ograniczania zasobów, mogą uzyskiwać dostęp do klasy XmlTextReader.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli nie masz pewności, że dane wejściowe jest znany jako z zaufanego źródła, nie Pomijaj reguły z tego ostrzeżenia.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violation"></a>Naruszenie zasad

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass () {} // warn
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2() // warn
        {
        }
    }
}
```

### <a name="solution"></a>Rozwiązanie

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass ()
        {
            XmlResolver = null;
        }
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2()
        {
               XmlResolver = null;
        }
    }
}
```