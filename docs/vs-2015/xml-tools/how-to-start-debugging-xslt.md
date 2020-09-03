---
title: 'Instrukcje: Rozpoczynanie debugowania XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 8358335a-fcb0-45e0-a37e-45b43e49ec0a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 09471b9e62b758e4e02e054494ed108532bbd301
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656332"
---
# <a name="how-to-start-debugging-xslt"></a>Instrukcje: Rozpoczynanie debugowania kodu XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger XSLT może służyć do debugowania arkusza stylów XSLT lub aplikacji XSLT. Podczas debugowania można wykonać kod jeden wiersz jednocześnie, przechodząc do kroku, przechodząc nad lub przechodzenie do kodu. Polecenia do korzystania z funkcji wykonywania kodu są takie same dla debugera XSLT, jak w przypadku innych debugerów programu Visual Studio. Po rozpoczęciu debugowania debuger XSLT otwiera system Windows, aby wyświetlić dokument wejściowy i dane wyjściowe XSLT.

## <a name="xml-editor"></a>Edytor XML
 Debuger można uruchomić z edytora XML. Umożliwia to debugowanie podczas projektowania arkusza stylów.

#### <a name="to-start-debugging-from-a-style-sheet"></a>Aby rozpocząć debugowanie z arkusza stylów

1. Otwórz arkusz stylów w edytorze XML.

2. Wybierz pozycję **DEBUGUJ XSL** z menu **XML** .

#### <a name="to-start-debugging-from-an-xml-input-document"></a>Aby rozpocząć debugowanie z dokumentu wejściowego XML

1. Otwórz dokument XML w edytorze XML.

2. Wybierz pozycję **DEBUGUJ XSL** z menu **XML** .

## <a name="xslt-from-other-languages"></a>XSLT z innych języków
 Możesz również przejść do języka XSLT podczas debugowania aplikacji. Po naciśnięciu klawisza F11 w <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> wywołaniu debuger może przejść do kodu XSLT.

> [!NOTE]
> Przechodzenie do języka XSLT z <xref:System.Xml.Xsl.XslTransform> klasy nie jest obsługiwane. <xref:System.Xml.Xsl.XslCompiledTransform>Klasa jest jedynym procesorem XSLT, który obsługuje krokowe przechodzenie do XSLT podczas debugowania.

#### <a name="to-start-debugging-an-xslt-application"></a>Aby rozpocząć debugowanie aplikacji XSLT

1. Podczas tworzenia wystąpienia <xref:System.Xml.Xsl.XslCompiledTransform> obiektu Ustaw `enableDebug` parametr na wartość `true` w kodzie.

     Powoduje to nakazuje procesorowi XSLT tworzenie informacji debugowania podczas kompilowania kodu.

2. Naciśnij klawisz F11, aby przejść do kodu XSLT.

     Arkusz stylów XSLT jest ładowany w nowym oknie dokumentu, a debuger XSLT jest uruchamiany.

     Alternatywnie możesz dodać punkt przerwania do arkusza stylów i uruchomić aplikację.

### <a name="example"></a>Przykład
 Poniżej znajduje się przykład programu XSLT języka C#. Pokazuje, jak włączyć debugowanie XSLT.

```
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

## <a name="see-also"></a>Zobacz też
 [Przewodnik: Debugowanie kodu arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) [— Omówienie](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9)
