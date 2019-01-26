---
title: 'Instrukcje: Edytowanie plików XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ee170d42390ed04292be28740dde4d597b7f7d9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005445"
---
# <a name="how-to-edit-xml-files"></a>Instrukcje: Edytowanie plików XML

Edytor XML jest nowym edytorze plików XML. Może służyć autonomiczny plik XML lub plik skojarzony z projektu programu Visual Studio. Edytor XML jest skojarzony z następujących rozszerzeń pliku: *.config*, *.dtd*, *.xml*, *XSD*, *.xdr*, *XSL*, *.xslt*, i *.vssettings*. Edytor XML jest powiązany z pliku innego typu ma nie określonych Edytor zarejestrowany i zawiera zawartość DTD lub XML.

> [!NOTE]
> XHTML dokumentów są obsługiwane w edytorze HTML.

## <a name="to-edit-an-xml-file"></a>Aby edytować plik XML

1.  Kliknij dwukrotnie plik, który chcesz edytować.

### <a name="to-add-a-new-xml-file-to-a-project"></a>Aby dodać nowy plik XML do projektu

1.  Z **projektu** menu, wybierz opcję **Dodaj nowy element**.

2.  Wybierz **pliku XML** z **szablony** okienka.

3.  Wprowadź nazwę pliku w **nazwa** pole i naciśnij klawisz **Dodaj**.

     Plik XML jest dodawany do projektu i otworzyć w edytorze XML. Ten plik zawiera domyślne deklaracji XML, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="to-add-an-existing-xml-file-to-a-project"></a>Aby dodać istniejący plik XML do projektu

1.  Z **projektu** menu, wybierz opcję **Dodaj istniejący element**.

     **Dodaj istniejący element** pojawi się okno dialogowe.

2.  Wybierz plik XML i naciśnij klawisz **Dodaj**.

## <a name="to-create-a-new-xml-or-xslt-file"></a>Aby utworzyć nowy plik XML lub XSLT

1.  Z **pliku** menu, wybierz opcję **New**.

     **Nowy plik** pojawi się okno dialogowe.

2.  Wybierz **pliku XML** Aby utworzyć nowy plik XML; lub wybierz **pliku XSLT** do utworzenia nowego arkusza stylów XSLT.

3.  Kliknij przycisk **Otwórz**.

## <a name="to-create-a-project-for-xml-files"></a>Aby utworzyć projekt dla plików XML

1.  Z **pliku** menu, wybierz opcję **New**, a następnie wybierz pozycję **projektu**.

     **Nowy projekt** pojawi się okno dialogowe.

2.  Wybierz język kodu, co pozwala wybierz **pusty projekt**i kliknij przycisk **OK**.

3.  Dodaj pliki XML do projektu.

     Edytor XML znajduje schematy dodanych do tego projektu i używa ich do walidacji i IntelliSense w dowolnym XML, schematu lub pliki XSLT, które możesz edytować, gdy ten projekt jest otwarty.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)
- [Właściwości dokumentu XML, okno właściwości](../xml-tools/xml-document-properties-properties-window.md)
- [Instrukcje: Tworzenie schematu XML z dokumentu XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)