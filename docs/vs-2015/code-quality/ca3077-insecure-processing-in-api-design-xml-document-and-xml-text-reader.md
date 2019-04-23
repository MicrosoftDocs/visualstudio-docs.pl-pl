---
title: 'CA3077: Niezabezpieczone przetwarzanie w projekt interfejsu API, dokumencie XML i czytnik tekstu XML | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a0907c2c73a175d9ec0d1e502e8f14f1ac0604fd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60049805"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: Niezabezpieczone przetwarzanie w elemencie Design interfejsu API, dokumencie XML i czytniku tekstu dla kodu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Podczas projektowania interfejsu API pochodną klasy XMLDocument i klasy XMLTextReader, można w trosce o <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  Za pomocą niezabezpieczonego wystąpień XmlReaderSettings, gdy odwołuje się do rozpoznawania jednostek zewnętrznych źródeł lub ustawiania wartości niebezpieczne w XML może prowadzić do ujawnienia informacji.

## <a name="rule-description"></a>Opis reguły
 A [definicji typu dokumentu (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) jest jeden z dwóch sposobów analizatora XML można określić ważności dokumentu, zgodnie z definicją [World Wide Web Consortium (W3C) XML Extensible Markup Language () 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Ta reguła szuka właściwości i wystąpienia, gdzie niezaufanych danych jest akceptowany w celu otrzymania deweloperów o potencjalnych [ujawnienie informacji](http://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) zagrożenia, które mogą prowadzić do [przeprowadzenie ataku typu "odmowa usługi" (DoS)](http://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) ataków. Ta zasada wyzwala, gdy:

- <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XmlTextReader> klasy używać domyślnego programu rozpoznawania nazw wartości przetwarzanie elementu DTD.

- Żaden konstruktor nie jest zdefiniowany dla obiektu XmlDocument klasy pochodne klasy XmlTextReader lub nie bezpieczne jest wykorzystywana do <xref:System.Xml.XmlResolver>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- CATCH i przetwórz wszystkie wyjątki klasy XmlTextReader poprawnie, aby uniknąć ujawnienia informacji ścieżki.

- Użyj <xref:System.Xml.XmlSecureResolver>zamiast element XmlResolver do ograniczania zasobów, mogą uzyskiwać dostęp do klasy XmlTextReader.

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
