---
title: 'Instrukcje: Wybieranie schematów XML do użycia'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 275def786a93d42e6b8e110d3b3d785a24e948b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601910"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Instrukcje: Wybieranie schematów XML do użycia

Edytor XML udostępnia pamięć podręczną schematu znajdującą się w katalogu *%VSInstallDir%\xml\Schemas* . Pamięć podręczna schematu zawiera dobrze znane schematy XML, które są używane do sprawdzania poprawności dokumentów IntelliSense i XML.

Użyj właściwości dokumentu **schematów** , aby wybrać co najmniej jeden schemat języka definicji schematu XML (XSD). Można wybrać schematy z pamięci podręcznej schematów lub w innym miejscu.

Określone schematy są zapisywane w postaci (ukrytego) pliku opcji użytkownika rozwiązania (. *SUO*), wraz ze wszystkimi innymi właściwościami dokumentu XML. W związku z tym nie trzeba ponownie wprowadzać tych wartości przy następnym otwarciu rozwiązania.

> [!NOTE]
> Edytor może sprawdzić poprawność przy użyciu schematu wbudowanego lub schematu, do którego odwołuje się atrybut `xsd:schemaLocation`. Aby uzyskać więcej informacji, zobacz [Walidacja dokumentu XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Aby wybrać schemat XML z pamięci podręcznej schematów

1. Otwórz plik w edytorze XML.

2. W oknie właściwości dokumentu kliknij w polu **schematy** . Gdy zostanie wyświetlony przycisk przeglądania (...), kliknij go.

   ![Właściwość schematów dla pliku XML](media/properties-schemas.png)

   Zostanie otwarte okno [dialogowe schematy XML](xml-schemas-dialog-box.md) . W oknie dialogowym są wyświetlane wszystkie schematy z. rozszerzenie *XSD* w pamięci podręcznej schematów (w tym schematy, do których odwołuje się plik *Catalog. XML* ), a także wszystkie schematy, które znajdują się w bieżącym rozwiązaniu, otwierają się w programie Visual Studio, do których odwołuje się atrybut `xsd:schemaLocation` lub przywoływane w **schematach** wartość.

3. Wybierz schematy do użycia na potrzeby walidacji, wykonując jedną z następujących czynności:

   - Wybierz schemat z listy w oknie dialogowym **schematy XML** , kliknij kolumnę **Użyj** , a następnie wybierz pozycję **Użyj tego schematu**.

     —lub—

   - Zaznacz wiele schematów w oknie dialogowym **schematy XML** , a następnie kliknij prawym przyciskiem myszy i wybierz pozycję **Użyj tego schematu**.

4. Wybierz **przycisk OK**.

   Lista wybranych schematów jest kopiowana z powrotem do właściwości dokumentu **schematu** .

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Aby dodać schemat XML do pamięci podręcznej schematu

1. W oknie właściwości dokumentu kliknij przycisk w polu **schematy** .

2. Kliknij przycisk **Dodaj**.

   Otworzy się okno dialogowe **Otwórz schemat XSD** .

3. Przeglądaj i wybierz schematy, które mają zostać dodane do pamięci podręcznej schematów.

4. Kliknij przycisk **Otwórz**.

   Schematy są dodawane do pamięci podręcznej schematu, a wartość **Użyj** wartości kolumna jest ustawiona na **Użyj tego schematu**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Aby usunąć schemat XML z pamięci podręcznej schematów

1. W oknie właściwości dokumentu kliknij przycisk w polu **schematy** .

2. Wybierz schemat do usunięcia, a następnie kliknij przycisk **Usuń**.

   Schemat zostanie usunięty z pamięci podręcznej schematu w pamięci, ale nie jest usuwany z systemu plików.

   > [!NOTE]
   > Jeśli nadal masz odwołanie do schematu za pośrednictwem atrybutu `schemaLocation` lub pasujące `targetNamespace` następnie **Remove** nie będą działały w tej sytuacji z powodu autoskojarzenia. W takim przypadku zaleca się oznaczyć schemat jako **nieużywający wybranych schematów** w kolumnie **Użyj** .

## <a name="see-also"></a>Zobacz także

- [Pamięć podręczna schematu](../xml-tools/schema-cache.md)
- [Okno dialogowe schematy XML](../xml-tools/xml-schemas-dialog-box.md)
- [Edytor XML](../xml-tools/xml-editor.md)