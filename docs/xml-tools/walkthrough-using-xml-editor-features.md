---
title: 'Przewodnik: Korzystanie z funkcji edytora XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57f1f8274d121b5370f47dfdb62be3a8e5cdd017
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525873"
---
# <a name="walkthrough-use-xml-editor-features"></a>Przewodnik: Korzystanie z funkcji edytora XML

Kroki opisane w tym przewodniku opisano można utworzyć nowego dokumentu XML. Przewodnik używa także niektóre funkcje edytora XML, które ułatwiają cenny na potrzeby tworzenia XML.

> [!NOTE]
> Przed rozpoczęciem instruktażu, należy zapisać *hireDate.xsd* pliku (przedstawionym poniżej w tym temacie) na komputerze lokalnym.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Aby utworzyć nowy plik XML i skojarzyć go z schematu XML

1.  Na **pliku** menu wskaż **New**i kliknij przycisk **pliku**.

2.  Wybierz **pliku XML** w **szablony** okienku i kliknij przycisk **Otwórz**.

     Nowy plik jest otwarty w edytorze. Ten plik zawiera deklarację XML domyślne `<?xml version="1.0" encoding="utf-8">`.

3.  W oknie dialogowym właściwości dokumentu, kliknij przycisk przeglądania (**...** ) na **schematów** pola.

     **Schematy XSD** zostanie wyświetlone okno dialogowe.

4.  Kliknij przycisk **Dodaj**.

     **Otwieranie schematu XSD** zostanie wyświetlone okno dialogowe.

5.  Wybierz *hireDate.xsd* plik i kliknij przycisk **Otwórz**.

6.  Kliknij przycisk **OK**.

     Schemat XML jest teraz skojarzone z dokumentem XML. Schemat XML jest używany do walidacji dokumentu. Również służy przez technologię IntelliSense do wypełniania listy członków prawidłowe elementy.

## <a name="to-add-data"></a>Aby dodać dane

1.  Typ `<` w okienku edytora.

     Lista elementów członkowskich Wyświetla możliwych elementów:

    -   **! —** Aby dodać komentarz.

    -   **! DOCTYPE** można dodać typu dokumentu.

    -   **?** Aby dodać instrukcji przetwarzania.

    -   **Pracownik** można dodać elementu głównego.

2.  Wybierz **<!--** można dodać węzeł komentarzy i naciśnij klawisz **Enter**.

     Edytor wstawia tagu końcowego komentarz i umieszcza kursor między tagiem początkowym i końcowym w komentarz.

3.  Wpisz **pliku XML testu**.

4.  W nowym wierszu, wpisz `<`i wybierz **pracowników** z listy elementów członkowskich.

     Edytor dodaje początek XML element `<employee`. W tym momencie można dodawać atrybutów do elementu, lub możesz ją zamknąć tagu początkowego, wpisując `>`.

5.  Typ `>` zamknięcie tagu.

6.  Edytor dodaje tag końcowy. Tag końcowy zostanie dodany z linią falistą wskazujący błąd sprawdzania poprawności. **Etykietki narzędzia** wyświetlany jest komunikat: **Element "pracownik" ma niekompletną zawartość. Oczekiwano 'ID'**.

7.  Typ `<` i wybierz **identyfikator** z listy elementów członkowskich. Następnie wpisz `>`.

     Edytor dodaje XML element `<ID></ID>`i umieszcza kursor po identyfikatorze taga otwierającego.

8.  Typ **abc**.

     **Abc** tekstu jest linią falistą. **Etykietki narzędzia** wyświetlany jest komunikat: **Element "ID" ma nieprawidłową wartość przy uwzględnieniu jego typu danych**.

9. Kliknij prawym przyciskiem myszy na elemencie identyfikator, a następnie wybierz pozycję **przejdź do definicji**.

     Zostanie otwarty edytor *hireDate.xsd* plik w nowym oknie dokumentu i umieszczenie kursora w definicji elementu schematu Identyfikatora.

10. Wróć do pliku XML i Zastąp **abc** tekstem **123**.

     Faliste podkreślenie i **etykietki narzędzia** zostaną wyczyszczone w obszarze wartości elementu Identyfikatora. **Etykietki narzędzia** dla elementu end pracowników tag teraz wyświetlany jest komunikat: **Element "pracownik" ma niekompletną zawartość. Oczekiwano "Data zatrudnienia"**.

11. Umieść kursor po identyfikatorze tagu końcowego, wpisz w `<`, wybierz opcję **Data zatrudnienia** z listy członków, a następnie wpisz w `>`.

     Edytor dodaje XML element `<hire-date></hire-date>`i umieszcza kursor po Data zatrudnienia taga otwierającego.

12. Wpisz **2003-01-10** wartości Data zatrudnienia.

## <a name="to-format-the-xml-document"></a>Format dokumentu XML

- Wybierz **Formatuj dokument** przycisk na pasku narzędzi edytora XML, lub naciśnij **Ctrl**+**E**,**D**.

   ![Format XML dokumentu przycisku w programie Visual Studio](media/format-xml-document.png)

   Dokument XML jest sformatowany.

## <a name="to-save-the-xml-document"></a>Można zapisać dokumentu XML

1.  Z **pliku** menu, wybierz opcję **Zapisz jako**.

     **Zapisz plik jako** zostanie wyświetlone okno dialogowe. Domyślna nazwa pliku jest *"XMLFile1"*.

2.  Wprowadź nazwę pliku i lokalizację dokumentu XML, a następnie kliknij przycisk **Zapisz**.

## <a name="hiredatexsd-file"></a>Plik hireDate.xsd

Następujący plik schematu jest używany w tym przewodniku:

```xml
<?xml version="1.0"?>
<xs:schema attributeFormDefault="unqualified"
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"
     xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="employee">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="ID" type="xs:unsignedShort" />
        <xs:element name="hire-date" type="xs:date" />
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)