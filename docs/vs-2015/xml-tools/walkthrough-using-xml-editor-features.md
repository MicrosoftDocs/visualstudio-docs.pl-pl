---
title: 'Przewodnik: Korzystanie z funkcji edytora XML | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 55e7cdc06b1876fe40310f5af44152a70e4a4375
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438878"
---
# <a name="walkthrough-using-xml-editor-features"></a>Przewodnik: Korzystanie z funkcji edytora XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kroki opisane w tym przewodniku opisano można utworzyć nowego dokumentu XML. Przewodnik używa także niektóre funkcje edytora XML, które ułatwiają cenny na potrzeby tworzenia XML.  
  
> [!NOTE]
> Przed rozpoczęciem instruktażu, należy zapisać plik hireDate.xsd (przedstawionym poniżej w tym temacie) na komputerze lokalnym.  
  
### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Aby utworzyć nowy plik XML i skojarzyć go z schematu XML  
  
1. Na **pliku** menu wskaż **New**i kliknij przycisk **pliku**.  
  
2. Wybierz **pliku XML** w **szablony** okienku i kliknij przycisk **Otwórz**.  
  
     Nowy plik jest otwarty w edytorze. Ten plik zawiera deklarację XML domyślne `<?xml version="1.0" encoding="utf-8">`.  
  
3. W oknie dialogowym właściwości dokumentu, kliknij przycisk przeglądania (**...** ) na **schematów** pola.  
  
     **Schematy XSD** zostanie wyświetlone okno dialogowe.  
  
4. Kliknij przycisk **Dodaj**.  
  
     **Otwieranie schematu XSD** zostanie wyświetlone okno dialogowe.  
  
5. Wybierz plik hireDate.xsd, a następnie kliknij przycisk **Otwórz**.  
  
6. Kliknij przycisk **OK**.  
  
     Schemat XML jest teraz skojarzone z dokumentem XML. Schemat XML jest używany do walidacji dokumentu. Również służy przez technologię IntelliSense do wypełniania listy członków prawidłowe elementy.  
  
### <a name="to-add-data"></a>Aby dodać dane  
  
1. Typ `<` w okienku edytora.  
  
     Lista elementów członkowskich Wyświetla możliwych elementów:  
  
    - **! —** Aby dodać komentarz.  
  
    - **! DOCTYPE** można dodać typu dokumentu.  
  
    - **?** Aby dodać instrukcji przetwarzania.  
  
    - **Pracownik** można dodać elementu głównego.  
  
2. Wybierz  **\<!--** Dodaj węzeł komentarzy, a następnie naciśnij klawisz ENTER.  
  
     Edytor wstawia tagu końcowego komentarz i umieszcza kursor między tagiem początkowym i końcowym w komentarz.  
  
3. Wpisz **pliku XML testu**.  
  
4. W nowym wierszu, wpisz `<`i wybierz **pracowników** z listy elementów członkowskich.  
  
     Edytor dodaje początek XML element `<employee`. W tym momencie można dodawać atrybutów do elementu, lub możesz ją zamknąć tagu początkowego, wpisując `>`.  
  
5. Typ `>` zamknięcie tagu.  
  
6. Edytor dodaje tag końcowy. Tag końcowy zostanie dodany z linią falistą wskazujący błąd sprawdzania poprawności. Etykietki narzędzia wyświetlany jest komunikat: Element "pracownik" ma niekompletną zawartość. Oczekiwano 'ID'.  
  
7. Typ `<` i wybierz **identyfikator** z listy elementów członkowskich. Następnie wpisz `>`.  
  
     Edytor dodaje XML element `<ID></ID>`i umieszcza kursor po identyfikatorze taga otwierającego.  
  
8. Typ **abc**.  
  
     **Abc** tekstu jest linią falistą. Etykietki narzędzia wyświetlany jest komunikat: Element "ID" ma nieprawidłową wartość przy uwzględnieniu jego typu danych.  
  
9. Kliknij prawym przyciskiem myszy ID element, a następnie wybierz pozycję **przejdź do definicji**.  
  
     Edytor otwiera plik hireDate.xsd w nowym oknie dokumentu i umieszcza kursor w definicji elementu schematu Identyfikatora.  
  
10. Wróć do pliku XML i Zastąp **abc** tekstem **123**.  
  
     Faliste podkreślenie i etykietek narzędzi są usuwane w ramach wartości elementu Identyfikatora. Etykietka narzędzia dla tagu końcowego pracowników teraz wyświetlany jest komunikat: Element "pracownik" ma niekompletną zawartość. Oczekiwano "-Data zatrudnienia".  
  
11. Umieść kursor po identyfikatorze tagu końcowego, wpisz w `<`, wybierz datę zatrudnienia z listy elementów członkowskich, a następnie wpisz w `>`.  
  
     Edytor dodaje XML element `<hire-date></hire-date>`i umieszcza kursor po Data zatrudnienia taga otwierającego.  
  
12. Wpisz **2003-01-10** wartości Data zatrudnienia.  
  
### <a name="to-format-the-xml-document"></a>Format dokumentu XML  
  
1. Wybierz **Formatuj dokument** przycisk na pasku narzędzi edytora XML.  
  
     Dokument XML jest sformatowany.  
  
### <a name="to-save-the-xml-document"></a>Można zapisać dokumentu XML  
  
1. Z **pliku** menu, wybierz opcję **Zapisz jako**.  
  
     **Zapisz plik jako** zostanie wyświetlone okno dialogowe. Domyślna nazwa pliku jest "XMLFile1".  
  
2. Wprowadź nazwę pliku i lokalizację dokumentu XML, a następnie kliknij przycisk **Zapisz**.  
  
## <a name="hiredatexsd-file"></a>hireDate.xsd File  
 Następujący plik schematu jest używany przez instruktażu.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Edytor XML](../xml-tools/xml-editor.md)
