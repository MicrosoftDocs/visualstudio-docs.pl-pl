---
title: Sposoby debugowania kodu XSLT
ms.date: 03/05/2019
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: f6f4a1ce60f04bcea6e21b52db9347a95292dab2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592857"
---
# <a name="debugging-xslt"></a>Debugowanie kodu XSLT

Można debugować kod XSLT w programie Visual Studio. Debuger XSLT obsługuje ustawianie punktów przerwania, wyświetlanie stanów wykonywania XSLT i tak dalej. Debuger XSLT może służyć do debugowania arkuszy stylów XSLT lub aplikacji XSLT.

Można wykonać kod jeden wiersz jednocześnie, przechodząc do kroku, przechodząc nad lub przechodzenie do kodu. Polecenia do korzystania z funkcji wykonywania kodu w debugerze XSLT są takie same jak w przypadku innych debugerów programu Visual Studio.

Po rozpoczęciu debugowania debuger XSLT otwiera system Windows, aby wyświetlić dokument wejściowy i dane wyjściowe XSLT.

> [!NOTE]
> Debuger XSLT jest dostępny tylko w wersjach Professional i Enterprise programu Visual Studio.

## <a name="debug-from-the-xml-editor"></a>Debuguj z edytora XML

Możesz uruchomić debuger, gdy masz arkusz stylów lub wejściowy plik XML otwarty w edytorze. Pozwala to debugować się podczas projektowania arkusza stylów.

1. Otwórz arkusz stylów lub plik XML w programie Visual Studio.

1. Wybierz pozycję **Rozpocznij debugowanie XSLT** z menu **XML** lub naciśnij klawisz **Alt**+**F5**.

## <a name="debug-from-an-app-that-uses-xslt"></a>Debugowanie z aplikacji używającej XSLT

Możesz przejść do języka XSLT podczas debugowania aplikacji. Po naciśnięciu klawisza **F11** w wywołaniu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> debuger może przejść do kodu XSLT.

> [!NOTE]
> Przechodzenie do XSLT z klasy <xref:System.Xml.Xsl.XslTransform> nie jest obsługiwane. Klasa <xref:System.Xml.Xsl.XslCompiledTransform> jest jedynym procesorem XSLT, który obsługuje krokowe przechodzenie do XSLT podczas debugowania.

### <a name="to-start-debugging-an-xslt-application"></a>Aby rozpocząć debugowanie aplikacji XSLT

1. Podczas tworzenia wystąpienia obiektu <xref:System.Xml.Xsl.XslCompiledTransform> należy ustawić parametr `enableDebug`, aby `true` w kodzie. Powoduje to nakazuje procesorowi XSLT tworzenie informacji debugowania podczas kompilowania kodu.

1. Naciśnij klawisz **F11** , aby przejść do kodu XSLT.

   Arkusz stylów XSLT zostanie załadowany w nowym oknie dokumentu, a debuger XSLT zostanie uruchomiony.

   Alternatywnie możesz dodać punkt przerwania do arkusza stylów i uruchomić aplikację.

### <a name="example"></a>Przykład

Poniżej znajduje się przykład programu C# XSLT. Pokazuje, jak włączyć debugowanie XSLT.

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
      xslt.Load(stylesheet);

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>Profiler XSLT

[Profiler XSLT](../xml-tools/xslt-profiler.md) to narzędzie, które umożliwia deweloperom mierzenie, ocenę i ukierunkowanie problemów związanych z wydajnością w kodzie XSLT przez tworzenie szczegółowych raportów o wydajności XSLT. Aby uzyskać więcej informacji, zobacz [XSLT Profiler](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: debugowanie arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Najpierw Spójrz na debuger programu Visual Studio](../debugger/debugger-feature-tour.md)
- [Podstawy debugowania: punkty przerwania](../debugger/using-breakpoints.md)
