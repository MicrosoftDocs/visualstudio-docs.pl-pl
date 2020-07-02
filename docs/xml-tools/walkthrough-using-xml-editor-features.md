---
title: 'Wskazówki: korzystanie z funkcji edytora XML'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1cebf6f7621fb5fada37b8e4592efd429bdc85e6
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817401"
---
# <a name="walkthrough-use-xml-editor-features"></a>Przewodnik: korzystanie z funkcji edytora XML

Kroki opisane w tym instruktażu pokazują, jak utworzyć nowy dokument XML. Przewodnik używa również niektórych funkcji edytora XML, które są przydatne do tworzenia kodu XML.

> [!NOTE]
> Przed rozpoczęciem przewodnika Zapisz plik *HireDate. xsd* (zawarty poniżej w tym temacie) na komputerze lokalnym.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Aby utworzyć nowy plik XML i skojarzyć go ze schematem XML

1. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij polecenie **plik**.

2. W okienku **Szablony** wybierz pozycję **plik XML** , a następnie kliknij pozycję **Otwórz**.

     Nowy plik zostanie otwarty w edytorze. Plik zawiera domyślną deklarację XML, `<?xml version="1.0" encoding="utf-8">` .

3. W oknie właściwości dokumentu kliknij przycisk przeglądania (**...**) w polu **schematy** .

     Zostanie wyświetlone okno dialogowe **schematy XSD** .

4. Kliknij pozycję **Dodaj**.

     Zostanie wyświetlone okno dialogowe **otwieranie schematu XSD** .

5. Wybierz plik *HireDate. xsd* , a następnie kliknij przycisk **Otwórz**.

6. Kliknij przycisk **OK**.

     Schemat XML jest teraz skojarzony z dokumentem XML. Schemat XML jest używany do walidacji dokumentu. Jest on także używany przez funkcję IntelliSense do wypełniania listy elementów członkowskich prawidłowych elementów.

## <a name="to-add-data"></a>Aby dodać dane

1. Wpisz `<` w okienku edytora.

     Lista członków wyświetla możliwe elementy:

    - **!--** dodać komentarz.

    - **! DOCTYPE** , aby dodać typ dokumentu.

    - **?** w celu dodania instrukcji przetwarzania.

    - **Pracownik** , aby dodać element główny.

2. Wybierz pozycję ** &lt; !--** , aby dodać węzeł komentarza, a następnie naciśnij klawisz **Enter**.

     Edytor wstawia tag końcowy komentarza i umieszcza kursor między tagami początkowymi i końcowymi komentarzami.

3. Wpisz w **testowym pliku XML**.

4. W nowym wierszu wpisz `<` i wybierz pozycję **Employee** z listy członków.

     Edytor dodaje początek elementu XML, `<employee` . W tym momencie można dodać atrybuty do elementu lub zamknąć tag początkowy, wpisując ciąg `>` .

5. Wpisz, `>` Aby zamknąć tag.

6. Edytor dodaje tag końcowy. Tag końcowy jest dodawany ze falistą podkreśleniem wskazującym błąd walidacji. **Etykietka narzędzia** wyświetla komunikat: **element "Employee" ma niekompletną zawartość. Oczekiwano elementu "ID"**.

7. Wpisz `<` i wybierz **Identyfikator** z listy elementów członkowskich. Następnie wpisz polecenie `>` .

     Edytor dodaje element XML, `<ID></ID>` i położenie kursora po tagu początkowym ID.

8. Wpisz **ABC**.

     Tekst **ABC** jest podkreślony linią falistą. **Etykietka narzędzia** wyświetla komunikat: **element "ID" ma nieprawidłową wartość przy uwzględnieniu jego typu danych**.

9. Kliknij prawym przyciskiem myszy element ID i wybierz polecenie **Przejdź do definicji**.

     Edytor otwiera plik *HireDate. xsd* w nowym oknie dokumentu i umieszcza kursor w definicji elementu schematu identyfikatora.

10. Wróć do pliku XML i Zastąp tekst **ABC** tekstem **123**.

     Podkreślenie faliste i **etykietka narzędzia** są czyszczone pod wartością elementu ID. **Etykietka narzędzia** dla tagu końcowego pracownika wyświetla teraz komunikat: **element "pracownik" ma niekompletną zawartość. Oczekiwano daty "zatrudnienie"**.

11. Umieść kursor po tagu End ID, wpisz tekst `<` , wybierz pozycję **Zatrudnij** z listy członków, a następnie wpisz tekst `>` .

     Edytor dodaje element XML, i umieszcza `<hire-date></hire-date>` kursor po tagu początkowym data zatrudnienia.

12. Wpisz wartość **2003-01-10** dla wartości daty zatrudnienia.

## <a name="to-format-the-xml-document"></a>Aby sformatować dokument XML

- Wybierz przycisk **Formatuj dokument** na pasku narzędzi edytora XML lub naciśnij **klawisze CTRL** + **E**,**D**.

   ![Przycisk formatowania dokumentu XML w programie Visual Studio](media/format-xml-document.png)

   Dokument XML zostanie przekształcony ponownie.

## <a name="to-save-the-xml-document"></a>Aby zapisać dokument XML

1. Z menu **Plik** wybierz pozycję **Zapisz jako**.

     Zostanie wyświetlone okno dialogowe **Zapisywanie pliku jako** . Domyślną nazwą pliku jest *"xmlplik1"*.

2. Wprowadź nazwę pliku i lokalizację dokumentu XML, a następnie kliknij przycisk **Zapisz**.

## <a name="hiredatexsd-file"></a>hireDate. xsd — plik

W tym instruktażu jest używany następujący plik schematu:

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
