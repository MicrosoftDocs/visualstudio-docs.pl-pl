---
title: 'Instrukcje: Wykonywanie transformacji XSLT w edytorze XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 918ef14c075bfd09e4361e24bb3b95df53d2e45c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953269"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Instrukcje: Wykonywanie transformacji XSLT w edytorze XML

Edytor XML umożliwia kojarzenie arkusz stylów XSLT z dokumentu XML na przekształcenie i wyświetlić dane wyjściowe. Dane wyjściowe z transformację XSLT jest wyświetlany w nowym oknie dokumentu.

**Dane wyjściowe** właściwość określa nazwę pliku dla danych wyjściowych. Jeśli **dane wyjściowe** właściwość jest pusta, nazwa_pliku jest generowany w katalogu tymczasowym. Rozszerzenie pliku zależy od `xsl:output` element swojego stylu arkusz i może być. *XML*,. *txt* lub. *htm*.

Jeśli **dane wyjściowe** właściwość określa nazwę pliku. *htm* lub. *HTML* rozszerzenie, dane wyjściowe XSLT jest traktuje, za pomocą [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] programu Internet Explorer. Inne rozszerzenia pliku są otwierane przy użyciu domyślnego edytora wybranego przez [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] programu Visual Studio. Na przykład, jeśli plik ma rozszerzenie. *xml*, Visual Studio korzysta z edytora XML.

## <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>Wykonywanie transformacji XSLT z dokumentu XML

1.  Otwórz dokument XML w edytorze XML.

2.  Arkusz stylów XSLT należy skojarzyć z dokumentu XML.

    -   Dodaj `xml-stylesheet` przetwarzania instrukcji w dokumencie XML. Na przykład, Dodaj następujący wiersz `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` się w prologu dokumentu.

         —lub—

    -   Dodaj using arkusza stylów XSLT **właściwości** okna. W dokumencie **okno właściwości**, kliknij przycisk **Przeglądaj** przycisku **arkusza stylów** , wybierz arkusz stylów XSLT, a następnie kliknij przycisk **Otwórz**.

3.  Kliknij przycisk **dane wyjściowe ShowXSL** znajdujący się na **edytora XML** paska narzędzi.

    > [!NOTE]
    > W przypadku arkusza stylów, nie skojarzonych z dokumentu XML, okno dialogowe monit zapewniają arkusza stylów do użycia.
    >
    >  Dane wyjściowe z transformację XSLT jest wyświetlany w nowym oknie dokumentu.

## <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Wykonywanie transformacji XSLT z arkusza stylów XSLT

1.  Otworzyć arkusz stylów XSLT w edytorze XML.

2.  Określ dokumentu XML w **dane wejściowe** pola dokumentu **właściwości** okna.

    > [!NOTE]
    > Dokument XML jest dokument wejściowy używany do transformacji. Jeśli dokument nie jest określony, uruchamianiu przekształcenie XSLT **Otwieranie pliku** pojawi się okno dialogowe, a w tym czasie można określić dokument.

3.  Kliknij przycisk **dane wyjściowe ShowXSLT** znajdujący się na **edytora XML** paska narzędzi.

     Dane wyjściowe z transformację XSLT jest wyświetlany w nowym oknie dokumentu.

## <a name="to-provide-a-different-output-file-name"></a>Aby podać nazwę pliku danych wyjściowych inne niż

1.  Określ nazwę pliku w **dane wyjściowe** pola dokumentu **właściwości** okna.

2.  Kliknij przycisk **dane wyjściowe ShowXSLT** znajdujący się na **edytora XML** paska narzędzi.

     Dane wyjściowe z transformację XSLT jest wyświetlany w nowym oknie dokumentu i Edytor używane w oknie danych wyjściowych jest zależna od rozszerzenia pliku swoje **dane wyjściowe** właściwości dokumentu.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)