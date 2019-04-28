---
title: Sposoby debugowania kodu XSLT
ms.date: 03/05/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 23e108e476bfa9cb3ce699a16c77eb3520ed4785
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838483"
---
# <a name="debugging-xslt"></a>Debugowanie kodu XSLT

Możesz debugować kod XSLT w programie Visual Studio. XSLT jest debugera obsługuje ustawianie punktów przerwania, wyświetlanie stanów wykonania XSLT i tak dalej. Debuger XSLT może służyć do debugowania arkuszy stylów XSLT lub aplikacje XSLT.

Przechodzenie do, pominięcie lub przechodzenie krok po kroku z kodu, można wykonać jednego wiersza kodu naraz. Polecenia do używania funkcji Przechodzenie do kodu debuger XSLT są takie same jak dla programu Visual Studio debugery.

Po rozpoczęciu debugowania, debuger XSLT otwiera systemu windows, aby pokazać, że dokument wejściowy i XSLT danych wyjściowych.

> [!NOTE]
> Debuger XSLT jest dostępna tylko w wersji Enterprise programu Visual Studio.

## <a name="debug-from-the-xml-editor"></a>Debuguj z poziomu edytora XML

Można uruchomić debugera, gdy arkusz stylów lub wejściowy plik XML, Otwórz w edytorze. Dzięki temu można debugować w miarę projektowaniu arkusza stylów.

1. Otworzyć arkusz stylów lub plik XML w programie Visual Studio.

1. Wybierz **Rozpocznij debugowanie kodu XSLT** z **XML** menu lub naciśnij klawisz **Alt**+**F5**.

## <a name="debug-from-an-app-that-uses-xslt"></a>Debuguj z poziomu aplikacji, która używa XSLT

Możesz wejść do XSLT podczas debugowania aplikacji. Po naciśnięciu klawisza **F11** na <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> wywołanie, Debuger można wkroczyć do kodu XSLT.

> [!NOTE]
> Przechodzenie do XSLT z <xref:System.Xml.Xsl.XslTransform> klasy nie jest obsługiwane. <xref:System.Xml.Xsl.XslCompiledTransform> Klasy jest tylko procesora XSLT, który obsługuje Przechodzenie do XSLT podczas debugowania.

### <a name="to-start-debugging-an-xslt-application"></a>Aby rozpocząć debugowanie aplikacji XSLT

1. Podczas tworzenia wystąpienia <xref:System.Xml.Xsl.XslCompiledTransform> obiektu, należy ustawić `enableDebug` parametr `true` w kodzie. Oznacza to, że procesora XSLT można utworzyć informacji debugowania, gdy kod jest kompilowany.

1. Naciśnij klawisz **F11** wejść kod XSLT.

   Arkusz stylów XSLT jest ładowany w nowym oknie dokumentu, a następnie uruchamia debuger XSLT.

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
    private const string stylesheet = @"c:\data\xsl_files\below-average.xsl";
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

## <a name="xslt-profiler"></a>Profiler XSLT

[XSLT profiler](../xml-tools/xslt-profiler.md) to narzędzie, które umożliwia deweloperom mierzyć, oceny i określania elementów docelowych problemy związane z wydajnością w kodzie XSLT, tworząc szczegółowe raporty dotyczące wydajności XSLT. Aby uzyskać więcej informacji, zobacz [XSLT profiler](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Debugowanie arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Pierwsze spojrzenie na debugera programu Visual Studio](../debugger/debugger-feature-tour.md)
- [Podstawy debugowania: Punkty przerwania](../debugger/using-breakpoints.md)