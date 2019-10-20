---
title: 'Instrukcje: edytowanie plików XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c099839cda87819ec0ec7932c2b2e6aa7698fa52
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670884"
---
# <a name="how-to-edit-xml-files"></a>Instrukcje: edytowanie plików XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor XML jest nowym edytorem plików XML. Może być używany w autonomicznym pliku XML lub w pliku skojarzonym z projektem programu Visual Studio. Edytor XML jest skojarzony z następującymi rozszerzeniami plików:. config,. DTD,. XML,. xsd,. XDR,. xsl,. XSLT i. vssettings. Edytor XML jest również skojarzony z innym typem pliku, który nie ma określonego edytora, i zawiera zawartość XML lub DTD.

> [!NOTE]
> Dokumenty XHTML są obsługiwane przez Edytor HTML.

### <a name="to-edit-an-xml-file"></a>Aby edytować plik XML

1. Kliknij dwukrotnie plik, który chcesz edytować.

### <a name="to-add-a-new-xml-file-to-a-project"></a>Aby dodać nowy plik XML do projektu

1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

2. Wybierz pozycję **plik XML** w okienku **Szablony** .

3. Wprowadź nazwę pliku w polu **Nazwa** i naciśnij przycisk **Dodaj**.

     Plik XML zostanie dodany do projektu i otwarty w edytorze XML. Plik zawiera domyślną deklarację XML, `<?xml version="1.0" encoding="utf-8" ?>`.

### <a name="to-add-an-existing-xml-file-to-a-project"></a>Aby dodać istniejący plik XML do projektu

1. W menu **projekt** wybierz pozycję **Dodaj istniejący element**.

     Pojawi się okno dialogowe **Dodaj istniejący element** .

2. Wybierz plik XML i naciśnij przycisk **Dodaj**.

### <a name="to-create-a-new-xml-or-xslt-file"></a>Aby utworzyć nowy plik XML lub XSLT

1. Z menu **plik** wybierz polecenie **Nowy**.

     Pojawi się okno dialogowe **nowy plik** .

2. Wybierz **plik XML** , aby utworzyć nowy plik XML; lub wybierz opcję **plik XSLT** , aby utworzyć nowy arkusz stylów XSLT.

3. Kliknij przycisk **Otwórz**.

### <a name="to-create-a-project-for-xml-files"></a>Aby utworzyć projekt dla plików XML

1. Z menu **plik** wybierz pozycję **Nowy**, a następnie wybierz pozycję **projekt**.

     Pojawi się okno dialogowe **Nowy projekt** .

2. Wybierz wybrany język kodu, wybierz pozycję **pusty projekt**, a następnie kliknij przycisk **OK**.

3. Dodaj pliki XML do projektu.

     Edytor XML znajduje schematy dodawane do tego projektu i używa ich do sprawdzania poprawności i IntelliSense w dowolnym pliku XML, schemacie lub XSLT, który można edytować, gdy ten projekt jest otwarty.

## <a name="see-also"></a>Zobacz też
 [](../xml-tools/xml-editor.md) [Właściwości dokumentu XML edytora XML, okno właściwości](../xml-tools/xml-document-properties-properties-window.md) [instrukcje: Tworzenie schematu XML na podstawie dokumentu XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
