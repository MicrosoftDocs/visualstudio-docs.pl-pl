---
title: 'Instrukcje: Wybieranie schematów XML do użycia'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 553fbc9bc8a96377a31864e1250987713714e147
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920564"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Instrukcje: Wybieranie schematów XML do użycia

Edytor XML udostępnia znajduje się w pamięci podręcznej schematów *%InstallDir%\Xml\Schemas* katalogu. Pamięci podręcznej schematów obejmuje dobrze znanych schematów XML, które są używane do weryfikacji dokumentu IntelliSense i XML.

**Schematów** właściwości dokumentu jest używany do wybierania jednego lub więcej XML schematu definicji języka (XSD) schematy do użycia. Umożliwia wybieranie schematów z pamięci podręcznej schematu lub określ schemat, który nie znajduje się w pamięci podręcznej.

Schematy, należy określić są zapisywane w ukrytym plik opcji użytkownika rozwiązania (. *suo*), wraz z innych XML właściwości dokumentu. W rezultacie nie trzeba ponownie wprowadzić te wartości przy następnym otwarciu rozwiązania.

> [!NOTE]
> Edytora można sprawdzić poprawność przy użyciu wbudowanego schematu lub schemat przywoływany przez `xsd:schemaLocation` atrybutu. Aby uzyskać więcej informacji, zobacz [Walidacja dokumentów XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Aby wybrać schematu XML z pamięci podręcznej schematów

1. Otwórz plik w edytorze XML.

2. W oknie dialogowym właściwości dokumentu, kliknij przycisk **schematów** pola.

    **Schematów XML** zostanie wyświetlone okno dialogowe. Okno dialogowe wyświetla listę wszystkich schematów z. *xsd* rozszerzenie w pamięci podręcznej schematu (w tym schematy przywoływane w *catalog.xml* pliku), a także dowolnego schematu, który w bieżącym rozwiązaniu, Otwórz w programie Visual Studio, o której mowa w `xsd:schemaLocation` atrybut lub do których odwołuje się **schematów** właściwości.

3. Wybieranie schematów do użycia w celu weryfikacji, wykonując jedną z następujących czynności:

   - Wybierz schemat na liście **schematów XML** okno dialogowe, kliknij przycisk **użyj** kolumny, a następnie wybierz **używają tego schematu**.

     —lub—

   - Wybierz wiele schematów na liście **schematów XML** okno dialogowe, kliknij prawym przyciskiem myszy i wybierz **używają tego schematu**.

4. Kliknij przycisk **OK**.

    Lista wybranych schematów są kopiowane z powrotem do **schematów** właściwości dokumentu.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Aby dodać schematu XML do pamięci podręcznej schematów

1.  W oknie dialogowym właściwości dokumentu, kliknij przycisk **schematów** pola.

2.  Kliknij przycisk **Dodaj**.

     Spowoduje to otwarcie **otwieranie schematu XSD** okna dialogowego.

3.  Przeglądaj i wybierz schematy, aby dodać do pamięci podręcznej schematów.

4.  Kliknij przycisk **Otwórz**.

     Schematy dodane do schematu w pamięci podręcznej i jest **użyj** jest równa wartości w kolumnie **używają tego schematu**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Aby usunąć schematu XML z pamięci podręcznej schematów

1.  W oknie dialogowym właściwości dokumentu, kliknij przycisk **schematów** pola.

2.  Wybierz schemat, Usuń, a następnie kliknij przycisk **Usuń**.

     Schemat zostanie usunięty z pamięci podręcznej schematów w pamięci, ale nie jest on usuwany z systemu plików.

    > [!NOTE]
    > Jeśli nadal masz odwołanie do schematu za pomocą `schemaLocation` atrybutu lub pasujący obiekt typu `targetNamespace` następnie **Usuń** nie będzie działać w tej sytuacji ze względu na skojarzenie automatyczne. W takim przypadku zalecane jest, oznaczeniu schematu jako **nie używaj wybranych schematów** w **użyj** kolumny.

## <a name="see-also"></a>Zobacz także

- [Pamięci podręcznej schematów](../xml-tools/schema-cache.md)
- [Okno dialogowe schematy XML](../xml-tools/xml-schemas-dialog-box.md)
- [Edytor XML](../xml-tools/xml-editor.md)