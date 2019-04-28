---
title: 'Instrukcje: Rozpoczynanie debugowania kodu XSLT | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 8358335a-fcb0-45e0-a37e-45b43e49ec0a
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e3067b86c7474858379a26803e6809b1c21f8d21
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433089"
---
# <a name="how-to-start-debugging-xslt"></a>Instrukcje: Rozpoczynanie debugowania kodu XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger XSLT może służyć do debugowania, arkusz stylów XSLT lub aplikacji XSLT. Podczas debugowania, można wykonać jednego wiersza kodu naraz, przechodzenie do, pominięcie lub przechodzenie krok po kroku z kodu. Te polecenia, aby korzystać z funkcji przeglądania kodu są takie same jak w przypadku programu Visual Studio w debugerze XSLT debugery. Po rozpoczęciu debugowania, debuger XSLT otwiera systemu windows, aby pokazać, że dokument wejściowy i XSLT danych wyjściowych.  
  
## <a name="xml-editor"></a>Edytor XML  
 Można uruchomić debuger w edytorze XML. Dzięki temu można debugować w miarę projektowania arkusza stylów.  
  
#### <a name="to-start-debugging-from-a-style-sheet"></a>Aby rozpocząć debugowanie z arkusza stylów  
  
1. Otworzyć arkusz stylów w edytorze XML.  
  
2. Wybierz **debugowania XSL** z **XML** menu.  
  
#### <a name="to-start-debugging-from-an-xml-input-document"></a>Aby rozpocząć debugowanie z wejściowy dokument XML  
  
1. Otwórz dokument XML w edytorze XML.  
  
2. Wybierz **debugowania XSL** z **XML** menu.  
  
## <a name="xslt-from-other-languages"></a>XSLT przy użyciu innych języków  
 Możesz również wejść do XSLT podczas debugowania aplikacji. Po naciśnięciu klawisza F11 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> wywołanie, Debuger można wkroczyć do kodu XSLT.  
  
> [!NOTE]
> Przechodzenie do XSLT z <xref:System.Xml.Xsl.XslTransform> klasy nie jest obsługiwane. <xref:System.Xml.Xsl.XslCompiledTransform> Klasy jest tylko procesora XSLT, który obsługuje Przechodzenie do XSLT podczas debugowania.  
  
#### <a name="to-start-debugging-an-xslt-application"></a>Aby rozpocząć debugowanie aplikacji XSLT  
  
1. Podczas tworzenia wystąpienia <xref:System.Xml.Xsl.XslCompiledTransform> obiektu, należy ustawić `enableDebug` parametr `true` w kodzie.  
  
     Oznacza to, że procesora XSLT można utworzyć informacji debugowania, gdy kod jest kompilowany.  
  
2. Naciśnij klawisz F11, aby przejść do kodu XSLT.  
  
     Arkusz stylów XSLT jest ładowany w nowym oknie dokumentu, a debuger XSLT jest uruchomiony.  
  
     Można również dodać punkt przerwania do arkusza stylów i uruchom aplikację.  
  
### <a name="example"></a>Przykład  
 Oto przykład programu w języku C# XSLT. Widoczny jest sposób włączyć debugowanie kodu XSLT.  
  
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
 [Przewodnik: Debugowanie arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)   
 [Omówienie wykonywania kodu](http://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9)
