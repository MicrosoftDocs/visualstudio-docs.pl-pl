---
title: 'Instrukcje: Edytowanie plików XML'
ms.date: 11/04/2016
description: Informacje dotyczące edytowania plików zawierających zawartość XML lub DTD przy użyciu edytora XML w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 933ce2912845b69ceb73584c0599566b0a037fef
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399985"
---
# <a name="how-to-edit-xml-files"></a>Instrukcje: edytowanie plików XML

Edytor XML jest nowym edytorem plików XML. Może być używany w autonomicznym pliku XML lub w pliku skojarzonym z projektem programu Visual Studio. Edytor XML jest skojarzony z następującymi rozszerzeniami plików: *. config* , *. DTD* , *. XML* , *. xsd* , *. XDR* , *. xsl* , *. XSLT* i *. vssettings*. Edytor XML jest również skojarzony z innym typem pliku, który nie ma określonego edytora, i zawiera zawartość XML lub DTD.

> [!NOTE]
> Dokumenty XHTML są obsługiwane przez Edytor HTML.

Aby edytować plik XML, Otwórz plik, który chcesz edytować.

## <a name="add-a-new-xml-file-to-a-project"></a>Dodawanie nowego pliku XML do projektu

1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

2. Wybierz pozycję **plik XML** w okienku **Szablony** .

3. Wprowadź nazwę pliku w polu **Nazwa** i naciśnij przycisk **Dodaj**.

   Plik XML zostanie dodany do projektu i otwarty w edytorze XML. Plik zawiera domyślną deklarację XML, `<?xml version="1.0" encoding="utf-8" ?>` .

## <a name="add-an-existing-xml-file-to-a-project"></a>Dodawanie istniejącego pliku XML do projektu

1. W menu **projekt** wybierz pozycję **Dodaj istniejący element**.

   Pojawi się okno dialogowe **Dodaj istniejący element** .

2. Wybierz plik XML i naciśnij przycisk **Dodaj**.

## <a name="create-a-new-xml-or-xslt-file"></a>Utwórz nowy plik XML lub XSLT

1. Z menu **plik** wybierz polecenie **Nowy**.

   Pojawi się okno dialogowe **nowy plik** .

2. Wybierz **plik XML** , aby utworzyć nowy plik XML; lub wybierz opcję **plik XSLT** , aby utworzyć nowy arkusz stylów XSLT.

3. Wybierz pozycję **Otwórz**.

## <a name="create-an-empty-project-for-xml-files"></a>Utwórz pusty projekt dla plików XML

::: moniker range="vs-2017"

1. Z menu **plik** wybierz pozycję **Nowy** > **projekt**.

   Zostanie wyświetlone okno dialogowe **Nowy projekt**.

2. Wybierz wybrany język kodu, a następnie wybierz szablon **pusty projekt (.NET Framework)** .

3. Wybierz przycisk **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Z menu **plik** wybierz pozycję **Nowy** > **projekt**.

2. W polu wyszukiwania szablonu wprowadź **pusty projekt** , wybierz szablon **pusty projekt (.NET Framework)** , a następnie wybierz przycisk **dalej**.

3. Wybierz przycisk **Utwórz**.

::: moniker-end

4. Dodaj pliki XML do projektu.

   Edytor XML znajduje schematy dodawane do tego projektu i używa ich do sprawdzania poprawności i IntelliSense w dowolnym pliku XML, schemacie lub XSLT, który można edytować, gdy ten projekt jest otwarty.

## <a name="see-also"></a>Zobacz też

- [Edytor XML](../xml-tools/xml-editor.md)
- [Właściwości dokumentu XML, okno właściwości](../xml-tools/xml-document-properties-properties-window.md)
- [Instrukcje: Tworzenie schematu XML na podstawie dokumentu XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
