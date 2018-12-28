---
title: 'Instrukcje: Rozpoczynanie debugowania kodu XSLT'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 9e3251d83361623aea0c0a54a2752c97b06a66f8
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561869"
---
# <a name="how-to-start-debugging-xslt"></a>Instrukcje: Rozpoczynanie debugowania kodu XSLT

Debuger XSLT może służyć do debugowania, arkusz stylów XSLT lub aplikacji XSLT. Podczas debugowania, można wykonać jednego wiersza kodu naraz, przechodzenie do, pominięcie lub przechodzenie krok po kroku z kodu. Te polecenia, aby korzystać z funkcji przeglądania kodu są takie same jak w przypadku programu Visual Studio w debugerze XSLT debugery. Po rozpoczęciu debugowania, debuger XSLT otwiera systemu windows, aby pokazać, że dokument wejściowy i XSLT danych wyjściowych.

## <a name="xml-editor"></a>Edytor XML

Można uruchomić debuger w edytorze XML. Dzięki temu można debugować w miarę projektowania arkusza stylów.

### <a name="to-start-debugging-from-a-style-sheet"></a>Aby rozpocząć debugowanie z arkusza stylów

1. Otworzyć arkusz stylów w edytorze XML.

1. Wybierz **debugowania XSL** z **XML** menu.

### <a name="to-start-debugging-from-an-xml-input-document"></a>Aby rozpocząć debugowanie z wejściowy dokument XML

1. Otwórz dokument XML w edytorze XML.

1. Wybierz **debugowania XSL** z **XML** menu.

## <a name="xslt-from-other-languages"></a>XSLT przy użyciu innych języków

Możesz również wejść do XSLT podczas debugowania aplikacji. Po naciśnięciu klawisza F11 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> wywołanie, Debuger można wkroczyć do kodu XSLT.

> [!NOTE]
> Przechodzenie do XSLT z <xref:System.Xml.Xsl.XslTransform> klasy nie jest obsługiwane. <xref:System.Xml.Xsl.XslCompiledTransform> Klasy jest tylko procesora XSLT, który obsługuje Przechodzenie do XSLT podczas debugowania.

### <a name="to-start-debugging-an-xslt-application"></a>Aby rozpocząć debugowanie aplikacji XSLT

1. Podczas tworzenia wystąpienia <xref:System.Xml.Xsl.XslCompiledTransform> obiektu, należy ustawić `enableDebug` parametr `true` w kodzie.

     Oznacza to, że procesora XSLT można utworzyć informacji debugowania, gdy kod jest kompilowany.

1. Naciśnij klawisz F11, aby przejść do kodu XSLT.

     Arkusz stylów XSLT jest ładowany w nowym oknie dokumentu, a debuger XSLT jest uruchomiony.

     Można również dodać punkt przerwania do arkusza stylów i uruchom aplikację.

### <a name="example"></a>Przykład

Oto przykład programu w języku C# XSLT. Widoczny jest sposób włączyć debugowanie kodu XSLT.

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\belowAvg.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet)

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Debugowanie arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)   