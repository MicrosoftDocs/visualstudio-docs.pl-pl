---
title: 'Instrukcje: Edytowanie plików XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b25eebad9efc70e4fda45131e232983e81961625
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840372"
---
# <a name="how-to-edit-xml-files"></a>Instrukcje: Edytowanie plików XML

Edytor XML jest nowym edytorze plików XML. Może służyć autonomiczny plik XML lub plik skojarzony z projektu programu Visual Studio. Edytor XML jest skojarzony z następujących rozszerzeń pliku: *.config*, *.dtd*, *.xml*, *XSD*, *.xdr*, *XSL*, *.xslt*, i *.vssettings*. Edytor XML jest powiązany z pliku innego typu ma nie określonych Edytor zarejestrowany i zawiera zawartość DTD lub XML.

> [!NOTE]
> XHTML dokumentów są obsługiwane w edytorze HTML.

Aby edytować plik XML, kliknij dwukrotnie plik, który chcesz edytować.

## <a name="add-a-new-xml-file-to-a-project"></a>Dodaj nowy plik XML do projektu

1. Z **projektu** menu, wybierz opcję **Dodaj nowy element**.

2. Wybierz **pliku XML** z **szablony** okienka.

3. Wprowadź nazwę pliku w **nazwa** pole i naciśnij klawisz **Dodaj**.

   Plik XML jest dodawany do projektu i zostanie otwarty w edytorze XML. Ten plik zawiera domyślne deklaracji XML, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="add-an-existing-xml-file-to-a-project"></a>Dodawanie istniejącego pliku XML do projektu

1. Z **projektu** menu, wybierz opcję **Dodaj istniejący element**.

   **Dodaj istniejący element** pojawi się okno dialogowe.

2. Wybierz plik XML i naciśnij klawisz **Dodaj**.

## <a name="create-a-new-xml-or-xslt-file"></a>Utwórz nowy plik XML lub XSLT

1. Z **pliku** menu, wybierz opcję **New**.

   **Nowy plik** pojawi się okno dialogowe.

2. Wybierz **pliku XML** Aby utworzyć nowy plik XML; lub wybierz **pliku XSLT** do utworzenia nowego arkusza stylów XSLT.

3. Kliknij przycisk **Otwórz**.

## <a name="create-an-empty-project-for-xml-files"></a>Utwórz pusty projekt dla plików XML

::: moniker range="vs-2017"

1. Z **pliku** menu, wybierz opcję **New** > **projektu**.

   **Nowy projekt** pojawi się okno dialogowe.

2. Wybierz język kodu, co pozwala wybierz **pusty projekt**.

3. Kliknij przycisk **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Z **pliku** menu, wybierz opcję **New** > **projektu**.

2. Wprowadź **pusty projekt** w polu wyszukiwania szablonu wybierz **pusty projekt (.NET Framework)** szablonu, a następnie kliknij **dalej**.

3. Kliknij przycisk **Utwórz**.

::: moniker-end

4. Dodaj pliki XML do projektu.

   Edytor XML znajduje schematy dodanych do tego projektu i używa ich do walidacji i IntelliSense w dowolnym XML, schematu lub pliki XSLT, które możesz edytować, gdy ten projekt jest otwarty.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)
- [Właściwości dokumentu XML, okno właściwości](../xml-tools/xml-document-properties-properties-window.md)
- [Instrukcje: Tworzenie schematu XML z dokumentu XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)