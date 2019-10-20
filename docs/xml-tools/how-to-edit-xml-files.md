---
title: 'Instrukcje: edytowanie plików XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd8671bf45230ec24a37d5006a2d32e5aabe8f28
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645921"
---
# <a name="how-to-edit-xml-files"></a>Instrukcje: edytowanie plików XML

Edytor XML jest nowym edytorem plików XML. Może być używany w autonomicznym pliku XML lub w pliku skojarzonym z projektem programu Visual Studio. Edytor XML jest skojarzony z następującymi rozszerzeniami plików: *. config*, *. DTD*, *. XML*, *. xsd*, *. XDR*, *. xsl*, *. XSLT*i *. vssettings*. Edytor XML jest również skojarzony z innym typem pliku, który nie ma określonego edytora, i zawiera zawartość XML lub DTD.

> [!NOTE]
> Dokumenty XHTML są obsługiwane przez Edytor HTML.

Aby edytować plik XML, kliknij dwukrotnie plik, który chcesz edytować.

## <a name="add-a-new-xml-file-to-a-project"></a>Dodawanie nowego pliku XML do projektu

1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

2. Wybierz pozycję **plik XML** w okienku **Szablony** .

3. Wprowadź nazwę pliku w polu **Nazwa** i naciśnij przycisk **Dodaj**.

   Plik XML zostanie dodany do projektu i otwarty w edytorze XML. Plik zawiera domyślną deklarację XML, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="add-an-existing-xml-file-to-a-project"></a>Dodawanie istniejącego pliku XML do projektu

1. W menu **projekt** wybierz pozycję **Dodaj istniejący element**.

   Pojawi się okno dialogowe **Dodaj istniejący element** .

2. Wybierz plik XML i naciśnij przycisk **Dodaj**.

## <a name="create-a-new-xml-or-xslt-file"></a>Utwórz nowy plik XML lub XSLT

1. Z menu **plik** wybierz polecenie **Nowy**.

   Pojawi się okno dialogowe **nowy plik** .

2. Wybierz **plik XML** , aby utworzyć nowy plik XML; lub wybierz opcję **plik XSLT** , aby utworzyć nowy arkusz stylów XSLT.

3. Kliknij przycisk **Otwórz**.

## <a name="create-an-empty-project-for-xml-files"></a>Utwórz pusty projekt dla plików XML

::: moniker range="vs-2017"

1. Z menu **plik** wybierz pozycję **Nowy** **projekt**>.

   Pojawi się okno dialogowe **Nowy projekt** .

2. Wybierz wybrany język kodu, a następnie wybierz szablon **pusty projekt (.NET Framework)** .

3. Kliknij przycisk **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Z menu **plik** wybierz pozycję **Nowy** **projekt**>.

2. W polu wyszukiwania szablonu wprowadź **pusty projekt** , wybierz szablon **pusty projekt (.NET Framework)** , a następnie kliknij przycisk **dalej**.

3. Kliknij przycisk **Utwórz**.

::: moniker-end

4. Dodaj pliki XML do projektu.

   Edytor XML znajduje schematy dodawane do tego projektu i używa ich do sprawdzania poprawności i IntelliSense w dowolnym pliku XML, schemacie lub XSLT, który można edytować, gdy ten projekt jest otwarty.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)
- [Właściwości dokumentu XML, okno właściwości](../xml-tools/xml-document-properties-properties-window.md)
- [Instrukcje: Tworzenie schematu XML na podstawie dokumentu XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)