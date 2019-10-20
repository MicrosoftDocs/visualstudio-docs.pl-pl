---
title: 'Instrukcje: Tworzenie fragmentów kodu XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb511ba6f2eea9c56be4e826c3b689856c22214a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645940"
---
# <a name="how-to-create-xml-snippets"></a>Instrukcje: Tworzenie fragmentów kodu XML

Edytor XML może służyć do tworzenia nowych fragmentów kodu XML. Edytor zawiera fragment kodu XML o nazwie "fragment", który jest przykładowym fragmentem do tworzenia nowych fragmentów kodu XML.

## <a name="to-create-a-new-xml-snippet"></a>Aby utworzyć nowy fragment kodu XML

Aby utworzyć nowy fragment kodu XML, Utwórz nowy plik XML i użyj funkcji **Wstaw wstawki** .

1. W menu **plik** kliknij pozycję **Nowy** , a następnie kliknij pozycję **plik**.

2. Kliknij pozycję **plik XML** , a następnie kliknij przycisk **Otwórz**.

3. Kliknij prawym przyciskiem myszy w okienku edytora i wybierz **Wstaw fragment kodu**.

4. Wybierz z listy **fragment** i naciśnij klawisz **Enter**.

5. Wprowadź zmiany w nowym fragmencie kodu.

6. Z menu **plik** wybierz polecenie **Zapisz plik xmlfile. XML**.

     Zostanie wyświetlone okno dialogowe **Zapisywanie pliku jako** .

7. Wprowadź nazwę nowego fragmentu kodu i wybierz pozycję **pliki fragmentów** z listy rozwijanej **Zapisz jako typ** .

8. Użyj listy rozwijanej **Zapisz w** , aby zmienić lokalizację pliku do folderu *My Documents\Visual Studio 2005 \ Code Snippets\XML\My XML wstaweks* , a następnie naciśnij przycisk **Save (Zapisz**).

## <a name="snippet-description"></a>Opis fragmentu kodu

W tej sekcji opisano niektóre kluczowe elementy w fragmencie kodu. Aby uzyskać więcej informacji na temat elementów schematu używanych przez fragmenty kodu XML, zobacz [odwołania do schematu fragmentów kodu](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>Fragment kodu elementu

Edytor obsługuje dwa typy fragmentów kodu:

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

Typ `Expansion` określa, czy fragment pojawia się po wywołaniu polecenia **Wstaw fragment kodu** . Typ `SurroundsWith` określa, czy fragment pojawia się po wywołaniu poleceń **Otocz za pomocą** polecenia.

### <a name="code-element"></a>Element Code

Element `Code` definiuje tekst XML, który zostanie wstawiony po wywołaniu fragmentu kodu.

> [!NOTE]
> Tekst fragmentu kodu XML musi znajdować się w sekcji `<![CDATA[...]]>`.

Poniżej znajduje się element `Code`, który jest tworzony przy użyciu standardowego fragmentu kodu.

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

Element `Code` zawiera trzy zmienne.

- $name $ to zmienna zdefiniowana przez użytkownika. Tworzy element `name`, który ma edytowalną wartość domyślną "name". Zmienne zdefiniowane przez użytkownika są definiowane przy użyciu elementu `Literal`.

- $selected $ jest wstępnie zdefiniowaną zmienną. Reprezentuje tekst wybrany w edytorze XML przed wywołaniem fragmentu kodu. Położenie tej zmiennej określa miejsce, w którym zaznaczony tekst jest wyświetlany w fragmencie kodu, który otacza ten wybór.

- $end $ jest wstępnie zdefiniowaną zmienną. Gdy użytkownik naciśnie klawisz **Enter** , aby zakończyć edytowanie pól fragmentu kodu, ta zmienna określa, gdzie jest przenoszony karetka (^).

  Powyższy element `Code` wstawia następujący tekst XML:

```xml
<test>
  <name>name</name>
</test>
```

Wartość elementu Name jest oznaczona jako edytowalny region.

### <a name="literal-element"></a>Literal — element

Element `Literal` służy do identyfikowania tekstu zastępczego, który można dostosować po jego wstawieniu do pliku. Na przykład ciągi literałów, wartości liczbowe i niektóre nazwy zmiennych mogą być deklarowane jako literały. Można zdefiniować dowolną liczbę literałów w fragmencie kodu XML i można odwoływać się do nich wiele razy z fragmentu kodu. Poniżej znajduje się przykład elementu `Literal`, który definiuje zmienną $name $, której wartością domyślną jest "name".

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

Literały mogą również odwoływać się do funkcji. Edytor XML zawiera funkcję o nazwie **LookupPrefix**. Funkcja **LookupPrefix** wyszukuje podany identyfikator URI przestrzeni nazw z lokalizacji w dokumencie XML, z której jest wywoływany ten fragment kodu, i zwraca prefiks przestrzeni nazw, który jest zdefiniowany dla tej przestrzeni nazw (jeśli istnieje) i zawiera dwukropek (:) w tej nazwie. Poniżej znajduje się przykład elementu `Literal`, który używa funkcji **LookupPrefix** .

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

Zmiennej $prefix $ można następnie użyć w innym miejscu w fragmencie kodu XML.

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu XML](../xml-tools/xml-snippets.md)
- [Instrukcje: używanie fragmentów kodu XML](../xml-tools/how-to-use-xml-snippets.md)
- [Instrukcje: generowanie fragmentu kodu XML na podstawie schematu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)