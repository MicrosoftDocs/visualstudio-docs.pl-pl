---
title: 'Instrukcje: Generowanie fragmentu kodu XML na podstawie schematu XML | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ec2d14a03649b63a068d2e0a95877ccd03ddf97a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753754"
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>Instrukcje: Generowanie fragmentu kodu XML na podstawie schematu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Edytor XML ma możliwość generowania fragmentów kodu XML na podstawie schematu języka (XSD) definicji schematu XML. Na przykład zgodnie z tworzenia pakietów w pliku XML, podczas gdy umieszczony obok nazwy elementu, naciśnięciu klawisza TAB, aby wypełnić element z danymi XML wygenerowany na podstawie informacji o schemacie dla tego elementu.  
  
 Ta funkcja jest dostępna tylko w przypadku elementów. Ponadto obowiązują następujące reguły:  
  
- Element musi mieć powiązany typ schematu; oznacza to, że element musi być prawidłowa dla niektórych skojarzonego schematu. Typ schematu nie może być abstrakcyjny i typ musi zawierać wymaganych atrybutów i/lub wymaganych elementów podrzędnych.  
  
- Bieżący element w edytorze może być pusty, bez atrybutów. Na przykład poniżej przedstawiono wszystkie ważne  
  
  -   `<Account`  
  
  -   `<Account>`  
  
  -   `<Account></Account>`  
  
- Kursor musi znajdować się natychmiast na prawo od nazwy elementu.  
  
  Wygenerowany fragment kodu zawiera wszystkie wymagane atrybuty i elementy. Jeśli `minOccurs` jest większa niż jeden, minimalna wymagana liczba wystąpień tego elementu znajduje się we fragmencie, maksymalnie 100 wystąpień. Naprawiono dowolnej wartości znajdujące się w wyniku schematu w stałych wartości w tym fragmencie kodu. `xsd:any` i `xsd:anyAttribute` elementy są ignorowane i spowodować konstrukcje nie dodatkowe fragmentu kodu.  
  
  Wartości domyślne są generowane i oznaczane jako wartości można edytować. Jeśli schemat określa wartość domyślną, ta wartość domyślna jest używana. Jednak jeśli wartości domyślne schematu jest pustym ciągiem, Edytor generuje wartości domyślne w następujący sposób:  
  
- Jeśli typ schematu zawiera wszystkie aspekty wyliczenia bezpośrednio lub pośrednio za pomocą dowolnego z elementów członkowskich typu złożenia, pierwsza wartość wyliczenia w modelu obiektów schematu jest używany jako domyślny.  
  
- Jeśli typ schematu, który jest typem niepodzielnym, Edytor pobiera typ niepodzielny i wstawia nazwę typu atomic. Dla typu prostego pochodnej używa podstawowego typu prostego. Typ listy Typ niepodzielny to `itemType`. Dla Unii, typ niepodzielny to typ niepodzielny pierwszego `memberType`.  
  
## <a name="example"></a>Przykład  
 Kroki opisane w tej sekcji pokazują, jak używać wygenerować schematu XML fragmentu kodu funkcji edytora XML.  
  
> [!NOTE]
>  Przed rozpoczęciem tych procedur, należy zapisać plik schematu na komputerze lokalnym.  
  
#### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Aby utworzyć nowy plik XML i skojarzyć go z schematu XML  
  
1.  Na **pliku** menu wskaż **New**i kliknij przycisk **pliku**.  
  
2.  Wybierz **pliku XML** w **szablony** okienku i kliknij przycisk **Otwórz**.  
  
     Nowy plik jest otwarty w edytorze. Ten plik zawiera deklarację XML domyślne `<?xml version="1.0" encoding="utf-8">`.  
  
3.  W oknie dialogowym właściwości dokumentu, kliknij przycisk przeglądania (**...** ) na **schematów** pola.  
  
     **Schematy XSD** zostanie wyświetlone okno dialogowe.  
  
4.  Kliknij przycisk **Dodaj**.  
  
     **Otwieranie schematu XSD** zostanie wyświetlone okno dialogowe.  
  
5.  Wybierz plik schematu, a następnie kliknij przycisk **Otwórz**.  
  
6.  Kliknij przycisk **OK**.  
  
     Schemat XML jest teraz skojarzone z dokumentem XML.  
  
#### <a name="to-generate-an-xml-snippet"></a>Aby wygenerować fragmentu kodu XML  
  
1.  Typ `<` w okienku edytora.  
  
2.  Lista elementów członkowskich Wyświetla możliwych elementów:  
  
     **! —** Aby dodać komentarz.  
  
     **! DOCTYPE** można dodać typu dokumentu.  
  
     **?** Aby dodać instrukcji przetwarzania.  
  
     **Skontaktuj się z pomocą** można dodać elementu głównego.  
  
3.  Wybierz **skontaktuj się z pomocą** listę elementów członkowskich i naciśnij klawisz ENTER.  
  
     Edytor dodaje tag początkowy `<Contact` i umieszcza kursor po nazwie elementu.  
  
4.  Naciśnij klawisz TAB, aby wygenerować dane XML `Contact` elementu na podstawie jego schematu informacji.  
  
### <a name="input"></a>Dane wejściowe  
 Następujący plik schematu jest używany przez instruktażu.  
  
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
 Poniżej przedstawiono dane XML, który jest generowany na podstawie informacji schematu skojarzone z `Contact` elementu. Elementy są oznaczone jako `bold` wyznaczyć edytowalnego pola we fragmencie kodu XML.  
  
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
 [Fragmentów kodu XML](../xml-tools/xml-snippets.md)   
 [Instrukcje: Używanie fragmentów kodu XML](../xml-tools/how-to-use-xml-snippets.md)
