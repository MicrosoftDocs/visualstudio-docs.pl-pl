---
title: 'Instrukcje: wykonywanie transformacji XSLT z edytora XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b305d88779603b374e5f95842d7a5271a657268
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666536"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Instrukcje: wykonywanie transformacji XSLT z edytora XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor XML umożliwia kojarzenie arkusza stylów XSLT z dokumentem XML, wykonywanie transformacji i wyświetlanie danych wyjściowych. Wynikowe wyniki transformacji XSLT są wyświetlane w nowym oknie dokumentu.

 Właściwość **Output** określa nazwę pliku dla danych wyjściowych. Jeśli właściwość **Output** jest pusta, nazwa pliku jest generowana w katalogu tymczasowym. Rozszerzenie pliku jest oparte na `xsl:output` elemencie w arkuszu stylów i może być. XML,. txt lub. htm.

 Jeśli właściwość **Output** określa nazwę pliku z rozszerzeniem. htm lub. html, dane wyjściowe XSLT są wyświetlane przy użyciu [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer. Wszystkie inne rozszerzenia plików są otwierane przy użyciu domyślnego edytora wybranego przez [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio. Na przykład, jeśli rozszerzenie pliku to. XML, program Visual Studio używa edytora XML.

### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>Aby wykonać transformację XSLT z dokumentu XML

1. Otwórz dokument XML w edytorze XML.

2. Skojarz arkusz stylów XSLT z dokumentem XML.

    - Dodaj instrukcję przetwarzania `xml-stylesheet` do dokumentu XML. Na przykład Dodaj następujący wiersz `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` do prologu dokumentu.

         —lub—

    - Dodaj arkusz stylów XSLT przy użyciu okna **Właściwości** . W **oknie właściwości**dokumentu kliknij przycisk **Przeglądaj** dla pola **arkusz stylów** , wybierz arkusz stylów XSLT, a następnie kliknij przycisk **Otwórz**.

3. Kliknij przycisk **ShowXSL Output (dane wyjściowe** ) na pasku narzędzi **edytora XML** .

    > [!NOTE]
    > Jeśli z dokumentem XML nie jest skojarzony żaden arkusz stylów, okno dialogowe wyświetli komunikat z prośbą o podanie arkusza stylów, który ma być używany.
    >
    >  Wynikowe wyniki transformacji XSLT są wyświetlane w nowym oknie dokumentu.

### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Aby wykonać transformację XSLT z arkusza stylów XSLT

1. Otwórz arkusz stylów XSLT w edytorze XML.

2. Określ dokument XML w polu **wejściowym** okna **Właściwości** dokumentu.

    > [!NOTE]
    > Dokument XML jest dokumentem wejściowym używanym do przekształcania. Jeśli dokument nie zostanie określony po rozpoczęciu transformacji XSLT, pojawi się okno dialogowe **otwieranie pliku** , w którym można określić dokument w tym czasie.

3. Kliknij przycisk **ShowXSLT Output (dane wyjściowe** ) na pasku narzędzi **edytora XML** .

     Wynikowe wyniki transformacji XSLT są wyświetlane w nowym oknie dokumentu.

### <a name="to-provide-a-different-output-file-name"></a>Aby podać inną nazwę pliku wyjściowego

1. Określ nazwę pliku w polu **dane wyjściowe** okna **Właściwości** dokumentu.

2. Kliknij przycisk **ShowXSLT Output (dane wyjściowe** ) na pasku narzędzi **edytora XML** .

     Wynikowe wyniki transformacji XSLT są wyświetlane w nowym oknie dokumentu, a Edytor używany w oknie danych wyjściowych zależy od rozszerzenia pliku właściwości dokumentu **wyjściowego** .

## <a name="see-also"></a>Zobacz też
 [Edytor XML](../xml-tools/xml-editor.md)
