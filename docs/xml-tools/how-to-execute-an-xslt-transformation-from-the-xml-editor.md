---
title: Wykonywanie transformacji XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e84b1c6303da4c0db39da1b3585a7d4548560feb
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526376"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Instrukcje: Wykonywanie transformacji XSLT w edytorze XML

Edytor XML pozwala skojarzyć arkusz stylów XSLT z dokumentu XML na przekształcenie i wyświetlić dane wyjściowe. Dane wyjściowe z transformację XSLT jest wyświetlany w nowym oknie dokumentu.

**Dane wyjściowe** właściwość określa nazwę pliku dla danych wyjściowych. Jeśli **dane wyjściowe** właściwość jest pusta, nazwa_pliku jest generowany w katalogu tymczasowym. Rozszerzenie pliku zależy od `xsl:output` element swojego stylu arkusz i może być. *XML*,. *txt* lub. *htm*.

Jeśli **dane wyjściowe** właściwość określa nazwę pliku. *htm* lub. *HTML* rozszerzenie, dane wyjściowe XSLT jest traktuje, korzystając z przeglądarki internetowej. Inne rozszerzenia pliku są otwierane przy użyciu domyślnego edytora wybierany przez program Visual Studio. Na przykład, jeśli plik ma rozszerzenie. *xml*, Visual Studio korzysta z edytora XML.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>Wykonywanie transformacji XSLT z pliku XML

1. Otwórz dokument XML w edytorze XML.

2. Arkusz stylów XSLT należy skojarzyć z dokumentu XML.

    - Dodaj `xml-stylesheet` przetwarzania instrukcji w dokumencie XML. Na przykład dodaj następujący wiersz do prologu dokumentu: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       —lub—

    - Dodaj using arkusza stylów XSLT **właściwości** okna. W pliku XML jest otwarty w edytorze, kliknij prawym przyciskiem myszy w dowolnym miejscu w edytorze, a następnie wybierz **właściwości**. W **właściwości** kliknij w oknie **arkusza stylów** pola, a następnie kliknij przycisk przeglądania (...). Wybierz arkusz stylów XSLT, a następnie wybierz **Otwórz**.

3. Na pasku menu wybierz **XML** > **Rozpocznij debugowanie kodu XSLT bez**. Lub naciśnij **Ctrl**+**Alt**+**F5**.

   Dane wyjściowe z transformację XSLT jest wyświetlany w nowym oknie dokumentu.

   > [!NOTE]
   > W przypadku arkusza stylów, nie skojarzonych z dokumentu XML, okno dialogowe monit zapewniają arkusza stylów do użycia.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Wykonywanie transformacji XSLT z arkusza stylów XSLT

1. Otworzyć arkusz stylów XSLT w edytorze XML.

2. Określ dokumentu XML w **dane wejściowe** pola dokumentu **właściwości** okna.

   > [!NOTE]
   > Dokument XML jest dokument wejściowy używany do transformacji. Jeśli dokument nie jest określony, uruchamianiu przekształcenie XSLT **Otwieranie pliku** pojawi się okno dialogowe, a ponadto można określić dokument, w tym czasie.

3. Na pasku menu wybierz **XML** > **Rozpocznij debugowanie kodu XSLT bez**. Lub naciśnij **Ctrl**+**Alt**+**F5**.

   Dane wyjściowe z transformację XSLT jest wyświetlany w nowym oknie dokumentu.

## <a name="specify-an-output-file-name"></a>Określ nazwę pliku wyjściowego

Można określić nazwę pliku wyjściowego dla plików XML i XSL. Otwórz **właściwości** okna i określ nazwę pliku w **dane wyjściowe** pola.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)