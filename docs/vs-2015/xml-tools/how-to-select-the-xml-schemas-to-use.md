---
title: 'Instrukcje: Wybieranie schematów XML do użycia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f607d500bfcb8a745bfb129490d2c2b09c6b105c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666505"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Instrukcje: Wybieranie schematów XML do użycia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor XML udostępnia pamięć podręczną schematu znajdującą się w katalogu%InstallDir%\Xml\Schemas. Pamięć podręczna schematu zawiera dobrze znane schematy XML, które są używane do sprawdzania poprawności dokumentów IntelliSense i XML.

 Właściwość dokumentu **schematów** służy do wybierania co najmniej jednego schematu języka definicji schematu XML (XSD) do użycia. Pozwala wybrać schematy z pamięci podręcznej schematów lub określić schemat, który nie znajduje się w pamięci podręcznej.

 Określone schematy są zapisywane w ukrytym pliku opcji użytkownika rozwiązania (. suo), wraz ze wszystkimi innymi właściwościami dokumentu XML. W związku z tym nie trzeba ponownie wprowadzać tych wartości przy następnym otwarciu rozwiązania.

> [!NOTE]
> Edytor może sprawdzić poprawność przy użyciu wbudowanego schematu lub schematu, do którego odwołuje się atrybut `xsd:schemaLocation`. Aby uzyskać więcej informacji, zobacz [Walidacja dokumentu XML](../xml-tools/xml-document-validation.md).

### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Aby wybrać schemat XML z pamięci podręcznej schematów

1. Otwórz plik w edytorze XML.

2. W oknie właściwości dokumentu kliknij przycisk w polu **schematy** .

    Zostanie wyświetlone okno dialogowe **schematy XML** . W oknie dialogowym są wyświetlane wszystkie schematy o rozszerzeniu XSD w pamięci podręcznej schematu (w tym schematy, do których odwołuje się plik Catalog. xml), a także wszelkie schematy, które znajdują się w bieżącym rozwiązaniu, otwierane w programie Visual Studio, do których odwołuje się atrybut `xsd:schemaLocation` lub przywoływane w Właściwości **schematów** .

3. Wybierz schematy do użycia na potrzeby walidacji, wykonując jedną z następujących czynności:

   - Wybierz schemat z listy w oknie dialogowym **schematy XML** , kliknij kolumnę **Użyj** , a następnie wybierz pozycję **Użyj tego schematu**.

     —lub—

   - Zaznacz wiele schematów w oknie dialogowym **schematy XML** , kliknij prawym przyciskiem myszy i wybierz opcję **Użyj tego schematu**.

4. Kliknij przycisk **OK**.

    Lista wybranych schematów jest kopiowana z powrotem do właściwości dokumentu **schematu** .

### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Aby dodać schemat XML do pamięci podręcznej schematu

1. W oknie właściwości dokumentu kliknij przycisk w polu **schematy** .

2. Kliknij przycisk **Dodaj**.

     Spowoduje to otwarcie okna dialogowego **otwieranie schematu XSD** .

3. Przeglądaj i wybierz schematy, które mają zostać dodane do pamięci podręcznej schematów.

4. Kliknij przycisk **Otwórz**.

     Schemat (-y) dodany do pamięci podręcznej schematu i jest ustawiony na **użycie tego schematu**przez wartość kolumna **Użyj** .

### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Aby usunąć schemat XML z pamięci podręcznej schematów

1. W oknie właściwości dokumentu kliknij przycisk w polu **schematy** .

2. Wybierz schemat do usunięcia, a następnie kliknij przycisk **Usuń**.

     Schemat zostanie usunięty z pamięci podręcznej schematu w pamięci, ale nie jest usuwany z systemu plików.

    > [!NOTE]
    > Jeśli nadal masz odwołanie do schematu za pośrednictwem atrybutu `schemaLocation` lub pasujące `targetNamespace` następnie **Remove** nie będą działały w tej sytuacji z powodu autoskojarzenia. W takim przypadku zaleca się oznaczyć schemat jako **nieużywający wybranych schematów** w kolumnie **Użyj** .

## <a name="see-also"></a>Zobacz też
 [Edytor XML](../xml-tools/xml-editor.md) [schematów XML schematy](../xml-tools/xml-schemas-dialog-box.md) [pamięci podręcznej schematu](../xml-tools/schema-cache.md)
