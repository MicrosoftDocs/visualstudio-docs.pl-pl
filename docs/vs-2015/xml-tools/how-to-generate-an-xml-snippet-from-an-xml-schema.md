---
title: 'Instrukcje: generowanie fragmentu kodu XML na podstawie schematu XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e3d90185180cac5f526594650bde0a8f380c7668
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666524"
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>Instrukcje: Generowanie fragmentu kodu XML na podstawie schematu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor XML ma możliwość generowania fragmentów kodu XML z schematu języka definicji schematu XML (XSD). Na przykład podczas tworzenia pliku XML, gdy jest umieszczony obok nazwy elementu, można nacisnąć klawisz TAB, aby wypełnić element danymi XML wygenerowanymi na podstawie informacji o schemacie dla tego elementu.

 Ta funkcja jest dostępna tylko dla elementów. Obowiązują również następujące reguły:

- Element musi mieć skojarzony typ schematu; oznacza to, że element musi być prawidłowy zgodnie z niezależnym schematem. Typ schematu nie może być abstrakcyjny, a typ musi zawierać wymagane atrybuty i/lub wymagane elementy podrzędne.

- Bieżący element w edytorze musi być pusty bez atrybutów. Na przykład wszystkie następujące są prawidłowe

  - `<Account`

  - `<Account>`

  - `<Account></Account>`

- Kursor musi znajdować się bezpośrednio z prawej strony nazwy elementu.

  Wygenerowany fragment kodu zawiera wszystkie wymagane atrybuty i elementy. Jeśli `minOccurs` jest większa niż jeden, wymagana minimalna liczba wystąpień tego elementu jest dołączana do fragmentu kodu, maksymalnie 100 wystąpień. Wszystkie ustalone wartości Znalezione w schemacie powodują stałe wartości w fragmencie kodu. `xsd:any``xsd:anyAttribute`elementy i są ignorowane i nie powodują żadnych dodatkowych konstrukcji fragmentów kodu.

  Wartości domyślne są generowane i zanotowane jako wartości edytowalne. Jeśli schemat określa wartość domyślną, używana jest ta wartość domyślna. Jeśli jednak wartość domyślna schematu jest pustym ciągiem, Edytor generuje wartości domyślne w następujący sposób:

- Jeśli typ schematu zawiera wszelkie zestawy reguł wyliczenia, bezpośrednio lub pośrednio za pomocą któregokolwiek z elementów członkowskich typu Union pierwsza wartość wyliczana w modelu obiektu schematu jest używana jako domyślna.

- Jeśli typ schematu jest typem niepodzielnym, Edytor pobiera typ niepodzielny i wstawia nazwę typu niepodzielnego. Dla pochodnego typu prostego używa podstawowego typu prostego. Dla typu listy typ niepodzielny to `itemType` . Dla Unii, typ niepodzielny jest typem niepodzielnym pierwszego `memberType` .

## <a name="example"></a>Przykład
 Kroki opisane w tej sekcji pokazują, jak używać funkcji fragmentu kodu XML wygenerowanego przez schemat w edytorze XML.

> [!NOTE]
> Przed rozpoczęciem tych procedur Zapisz plik schematu na komputerze lokalnym.

#### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Aby utworzyć nowy plik XML i skojarzyć go ze schematem XML

1. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij polecenie **plik**.

2. W okienku **Szablony** wybierz pozycję **plik XML** , a następnie kliknij pozycję **Otwórz**.

     Nowy plik zostanie otwarty w edytorze. Plik zawiera domyślną deklarację XML, `<?xml version="1.0" encoding="utf-8">` .

3. W oknie właściwości dokumentu kliknij przycisk przeglądania (**...**) w polu **schematy** .

     Zostanie wyświetlone okno dialogowe **schematy XSD** .

4. Kliknij pozycję **Dodaj**.

     Zostanie wyświetlone okno dialogowe **otwieranie schematu XSD** .

5. Wybierz plik schematu, a następnie kliknij przycisk **Otwórz**.

6. Kliknij przycisk **OK**.

     Schemat XML jest teraz skojarzony z dokumentem XML.

#### <a name="to-generate-an-xml-snippet"></a>Aby wygenerować fragment kodu XML

1. Wpisz `<` w okienku edytora.

2. Lista członków wyświetla możliwe elementy:

     **!--** dodać komentarz.

     **! DOCTYPE** , aby dodać typ dokumentu.

     **?** w celu dodania instrukcji przetwarzania.

     **Skontaktuj się** z nami, aby dodać element główny.

3. Wybierz pozycję **kontakt** z listy członków i naciśnij klawisz ENTER.

     Edytor dodaje tag początkowy `<Contact` i ustawia kursor po nazwie elementu.

4. Naciśnij klawisz TAB, aby wygenerować dane XML dla `Contact` elementu na podstawie jego informacji o schemacie.

### <a name="input"></a>Dane wejściowe
 Przewodnik zawiera następujący plik schematu.

```
<?xml version="1.0" encoding="utf-8" ?>
<xs:schema elementFormDefault="qualified"
           xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:simpleType name="phoneType">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Voice"/>
      <xs:enumeration value="Fax"/>
      <xs:enumeration value="Pager"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:element name="Contact">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="Name">
          <xs:simpleType>
            <xs:restriction base="xs:string"></xs:restriction>
          </xs:simpleType>
        </xs:element>
        <xs:element name="Title"
                    type="xs:string" />
        <xs:element name="Phone"
                    minOccurs="1"
                    maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="Number"
                          minOccurs="1">
                <xs:simpleType>
                  <xs:restriction base="xs:string"></xs:restriction>
                </xs:simpleType>
              </xs:element>
              <xs:element name="Type"
                          default="Voice"
                          minOccurs="1"
                          type="phoneType"/>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

### <a name="output"></a>Dane wyjściowe
 Poniżej przedstawiono dane XML, które są generowane na podstawie informacji o schemacie skojarzonych z `Contact` elementem. Elementy oznaczone jako `bold` Wyznacz pola edytowalne w fragmencie kodu XML.

```
<Contact>
  <Name>name</Name>
  <Title>title</Title>
  <Phone>
    <Number>number</Number>
    <Type>Voice</Type>
  </Phone>
</Contact>
```

## <a name="see-also"></a>Zobacz też
 [Fragmenty kodu XML](../xml-tools/xml-snippets.md) [: używanie fragmentów kodu XML](../xml-tools/how-to-use-xml-snippets.md)
