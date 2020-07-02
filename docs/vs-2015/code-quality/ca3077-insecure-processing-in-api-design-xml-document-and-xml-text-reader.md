---
title: 'CA3077: niezabezpieczone przetwarzanie w projekcie interfejsu API, dokument XML i czytnik tekstu XML | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c0d6a6f6ab42d69d4503741f6625627c46d4ef77
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545109"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: Niezabezpieczone przetwarzanie w elemencie Design interfejsu API, dokumencie XML i czytniku tekstu dla kodu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Podczas projektowania interfejsu API pochodnego od XmlDocument i XMLTextReader należy mieć na uwadze <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> .  Używanie niezabezpieczonych wystąpień DTDProcessing w przypadku odwoływania się do lub rozpoznawania zewnętrznych źródeł jednostek lub ustawiania niezabezpieczonych wartości w kodzie XML może prowadzić do ujawnienia informacji.

## <a name="rule-description"></a>Opis reguły
 [Definicja typu dokumentu (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) to jeden z dwóch sposobów, przez który parser XML może ustalić ważność dokumentu, zgodnie z definicją [organizacja World Wide Web Consortium (W3C) XML (XML) 1,0](https://www.w3.org/TR/2008/REC-xml-20081126/). Ta reguła umożliwia wyszukiwanie właściwości i wystąpień, w przypadku których niezaufane dane są akceptowane, aby ostrzec deweloperów o potencjalnych zagrożeniach związanych z [ujawnianiem informacji](https://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) , co może prowadzić do ataków [typu "odmowa usługi" (DOS)](https://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) . Ta zasada wyzwala następujące wyzwalacze:

- <xref:System.Xml.XmlDocument>lub <xref:System.Xml.XmlTextReader> klasy używają domyślnych wartości programu rozpoznawania nazw do przetwarzania DTD.

- Nie zdefiniowano konstruktora dla klas pochodnych XmlDocument lub XmlTextReader lub nie jest używana bezpieczna wartość dla <xref:System.Xml.XmlResolver> .

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Należy prawidłowo przechwycić i przetworzyć wszystkie wyjątki XmlTextReader, aby uniknąć ujawnienia informacji o ścieżce.

- Użyj  <xref:System.Xml.XmlSecureResolver> zamiast XmlResolver, aby ograniczyć zasoby, do których XmlTextReader może uzyskać dostęp.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli nie masz pewności, że dane wejściowe są znane z zaufanego źródła, nie pomijaj reguły z tego ostrzeżenia.

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

### <a name="violation"></a>Krocz

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
