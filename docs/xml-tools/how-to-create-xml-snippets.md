---
title: 'Instrukcje: Tworzenie fragmentów kodu XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ad13fd3c8c1c2efeeec28794e10a91d9dd0db1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060842"
---
# <a name="how-to-create-xml-snippets"></a>Instrukcje: Tworzenie fragmentów kodu XML

Edytor XML może służyć do tworzenia nowych fragmentów kodu XML. Edytor zawiera fragment XML o nazwie "Fragment", oznacza to fragment standardowy do tworzenia nowych fragmentów kodu XML.

## <a name="to-create-a-new-xml-snippet"></a>Aby utworzyć nowy fragment kodu XML

 Aby utworzyć nowy kod XML fragment kodu tworzy nowy plik XML i użyj **Wstaw fragment kodu** funkcji.

1. Na **pliku** menu, kliknij przycisk **New** a następnie kliknij przycisk **pliku**.

2. Kliknij przycisk **pliku XML** a następnie kliknij przycisk **Otwórz**.

3. Kliknij prawym przyciskiem myszy w okienku edytora, a następnie wybierz pozycję **Wstaw fragment kodu**.

4. Wybierz **fragment** z listy i kliknij **Enter**.

5. Wprowadź wszelkie zmiany do nowego fragmentu kodu.

6. Z **pliku** menu wybierz opcję **Zapisz XMLFile.xml**.

     **Zapisz plik jako** zostanie wyświetlone okno dialogowe.

7. Wprowadź nazwę dla nowego fragmentu kodu, a następnie wybierz pozycję **pliki fragmentu kodu** z **Zapisz jako typ** okna listy rozwijanej.

8. Użyj **Zapisz w** listy rozwijanej, aby zmienić lokalizację pliku do *fragmenty XML Snippets\XML\My 2005\Code My Documents\Visual Studio* folder, a następnie naciśnij klawisz **Zapisz**.

## <a name="snippet-description"></a>Opis fragmentu kodu

 W tej sekcji opisano niektóre kluczowe elementy we fragmencie standardowy. Aby uzyskać więcej informacji na temat elementów schematu posługują się fragmentów kodu XML, zobacz [odwołanie do schematu fragmentów kodu](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>Snippettype — element

 Edytor obsługuje dwa typy fragmentu kodu:

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

 `Expansion` Typ Określa, czy ten fragment kodu jest wyświetlany, gdy wywołujesz **Wstaw fragment kodu** polecenia. `SurroundsWith` Typ Określa, czy ten fragment kodu jest wyświetlany, gdy wywołujesz **otacza przy użyciu** polecenia.

### <a name="code-element"></a>Element Code

 `Code` Element definiuje tekstu XML, który zostanie wstawiony podczas wywoływania fragmencie kodu.

> [!NOTE]
> Tekst fragment kodu XML muszą być ujęte w `<![CDATA[...]]>` sekcji.

 Poniżej przedstawiono `Code` element, który jest tworzony przez fragment kodu standardowy.

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

 `Code` Element zawiera trzy zmienne.

- $name$ jest zmienną zdefiniowaną przez użytkownika. Tworzy `name` element, który ma wartość można edytować wartość domyślna to "name". Zmienne zdefiniowane przez użytkownika są definiowane przy użyciu `Literal` elementu.

- $ $wybrane to uprzednio zdefiniowanej zmiennej. Reprezentuje tekst, który został wybrany w edytorze XML przed wywołaniem do fragmentu kodu. Położenie ta zmienna Określa, gdzie zaznaczony tekst pojawia się we fragmencie kodu, który otacza wybieranie.

- $end$ jest uprzednio zdefiniowanej zmiennej. Gdy użytkownik naciśnie **Enter** aby zakończyć edytowanie pola fragment kodu, ta zmienna Określa, gdzie daszek (^) jest przenoszony do.

  Powyższe `Code` wstawia element następujący tekst XML:

```xml
<test>
  <name>name</name>
</test>
```

 Wartość elementu name jest oznaczona jako regionem edytowalnym.

### <a name="literal-element"></a>Literal — element

 `Literal` Element jest używany do identyfikowania tekst zastępczy, który można dostosować po wstawieniu do pliku. Na przykład ciągi literałowe, wartości liczbowe i nazwy niektórych zmiennych może być zadeklarowana jako literały. Można zdefiniować dowolną liczbę literałów w fragmentu kodu XML i mogą odwoływać się do nich wiele razy w tym fragmencie kodu. Oto przykład `Literal` element, który definiuje zmienną $ $name, której domyślna wartość to "name".

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

 Literały znajdują się funkcje. Edytor XML zawiera funkcję o nazwie **LookupPrefix**. **LookupPrefix** funkcja wyszukuje dany identyfikator URI przestrzeni nazw z lokalizacji w dokumencie XML, w tym fragmencie kodu jest wywoływany z i zwraca prefiks przestrzeni nazw zdefiniowanej dla tego obszaru nazw, jeśli istnieje i zawiera dwukropek (:) w tej nazwie. Oto przykład `Literal` element, który używa **LookupPrefix** funkcji.

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

 Zmienna $ $prefix mogą używane gdzie indziej w fragmentu kodu XML.

## <a name="see-also"></a>Zobacz także

- [Fragmentów kodu XML](../xml-tools/xml-snippets.md)
- [Instrukcje: Używanie fragmentów kodu XML](../xml-tools/how-to-use-xml-snippets.md)
- [Instrukcje: Generowanie fragmentu kodu XML na podstawie schematu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)