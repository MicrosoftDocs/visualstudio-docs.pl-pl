---
title: Jak używać fragmentów kodu XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d892ba202a73560568bdb6c43427a8ee0f7c1aee
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913629"
---
# <a name="how-to-use-xml-snippets"></a>Instrukcje: Używanie fragmentów kodu XML

Możesz wywołać fragmentów kodu XML za pomocą dwóch poniższych poleceń w menu kontekstowym edytora XML. **Wstaw fragment kodu** polecenia wstawia fragment kodu XML w położeniu kursora. **Otocz** polecenia opakowuje fragment kodu XML wokół zaznaczonego tekstu. Każdy fragment kodu XML został wyznaczony typy fragmentu kodu. Typy fragment określają, czy ten fragment kodu jest dostępna z **Wstaw fragment kodu** polecenia **Otocz** polecenia i / lub.

Po dodaniu fragment kodu XML do edytora wszelkie edytowalnego pola we fragmencie są wyróżnione na żółto. Ponadto kursor znajduje się na pierwsze pole można edytować.

## <a name="insert-snippet"></a>Wstaw fragment kodu

W poniższych procedurach opisano sposób uzyskiwania dostępu do **Wstaw fragment kodu** polecenia.

> [!NOTE]
> **Wstaw fragment kodu** polecenia jest także dostępny za pomocą skrótu klawiaturowego (**Ctrl**+**K**, następnie **Ctrl** + **X**).

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Aby wstawić fragmentów kodu z menu skrótów

1. Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.

2. Kliknij prawym przyciskiem myszy i wybierz **Wstaw fragment kodu**.

   Zostanie wyświetlona lista dostępnych fragmentów kodu XML.

3. Wybierz fragment listy za pomocą myszy lub wpisując nazwę fragmentu kodu i naciskając klawisz **kartę** lub **Enter**.

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Aby wstawić fragmentów kodu za pomocą menu funkcji IntelliSense

1. Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.

2. Z **Edytuj** menu wskaż **IntelliSense**, a następnie wybierz pozycję **Wstaw fragment kodu**.

   Zostanie wyświetlona lista dostępnych fragmentów kodu XML.

3. Wybierz fragment listy za pomocą myszy lub wpisując nazwę fragmentu kodu i naciskając klawisz **kartę** lub **Enter**.

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Aby wstawić fragmentów kodu za pośrednictwem listy Dokończ wyraz IntelliSense

1. Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.

2. Rozpocznij wpisywanie fragment kodu XML, który chcesz dodać do pliku. Jeśli jest włączona funkcja automatycznego uzupełniania, zostanie wyświetlona lista Dokończ wyraz IntelliSense. Jeśli nie zostanie wyświetlony, naciśnij klawisz **Ctrl**+**miejsca** go uaktywnić.

3. Wybierz fragment kodu XML z listy Dokończ wyraz.

4. Naciśnij klawisz **kartę**, **kartę** do wywoływania fragmencie kodu XML.

> [!NOTE]
> Można wykluczyć sytuacji podczas wywoływania fragmencie kodu XML nie uzyskać. Na przykład, jeśli podczas próby wstawienia `xs:complexType` element wewnątrz `xs:element` węzła, edytor nie generuje fragmentu kodu XML. Gdy `xs:complexType` elementu jest używana wewnątrz `xs:element` węzła, brak wymaganych atrybutów i dozwolone podelementy, więc edytor nie ma żadnych danych, aby wstawić.

### <a name="to-insert-snippets-using-the-shortcut-name"></a>Aby wstawić fragmentów kodu przy użyciu nazwy skrótu

1. Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.

2. Typ `<` w okienku edytora.

3. Naciśnij klawisz **Esc** zamknąć lista Dokończ wyraz IntelliSense.

4. Wpisz nazwę skrótów fragmentu kodu, a następnie naciśnij klawisz **kartę** do wywoływania fragmencie kodu XML.

## <a name="surround-with"></a>Otocz przez

W poniższych procedurach opisano sposób uzyskiwania dostępu do **Otocz** polecenia.

> [!NOTE]
> **Otocz** polecenia jest także dostępny za pomocą skrótu klawiaturowego (**Ctrl**+**K**, następnie **Ctrl** + **S**).

### <a name="to-use-surround-with-from-the-context-menu"></a>Aby korzystać z funkcji Otocz przez z menu kontekstowego

1. Zaznacz tekst, aby ująć w edytorze XML.

2. Kliknij prawym przyciskiem myszy i wybierz **Otocz**.

   Zostanie wyświetlona lista dostępnych otacza przy użyciu fragmentów kodu XML.

3. Wybierz fragment listy za pomocą myszy lub wpisując nazwę fragmentu kodu i naciskając klawisz **kartę** lub **Enter**.

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Aby użyć Otocz menu funkcji IntelliSense

1. Zaznacz tekst, aby ująć w edytorze XML.

2. Z **Edytuj** menu wskaż **IntelliSense**, a następnie wybierz pozycję **Otocz**.

   Zostanie wyświetlona lista dostępnych otacza przy użyciu fragmentów kodu XML.

3. Wybierz fragment listy za pomocą myszy lub wpisując nazwę fragmentu kodu i naciskając klawisz **kartę** lub **Enter**.

## <a name="use-xml-snippets"></a>Używanie fragmentów kodu XML

Po wybraniu fragmentu kodu XML, tekst fragment kodu dodaje się automatycznie w położeniu kursora. Wszystkie pola edycji we fragmencie są wyróżnione, a pierwsze pole można edytować jest wybrana automatycznie. Aktualnie wybrane pole jest opakowany.

Gdy pole jest zaznaczone, możesz wpisać nową wartość dla pola. Naciśnięcie klawisza **kartę** przełączanie po kolei edytowalnego pola fragment kodu; naciśnięcie **Shift**+**kartę** przewijać je w odwrotnej kolejności. Kliknięcie pola umieszcza kursor w polu, a następnie dwukrotne kliknięcie pola zaznacza go. Wyróżnionego pola etykietki narzędzia może być wyświetlany, oferując opis pola.

Tylko pierwsze wystąpienie określonego pola jest edytowalny. To pole jest wyróżniony, opisano inne wystąpienia tego pola. Po zmianie wartości pola można edytować tego pola jest zmieniany, wszędzie tam, gdzie jest używany w tym fragmencie kodu.

Naciśnięcie klawisza **Enter** lub **Esc** anuluje edytowanie pola i powróci do typowej wartości edytora.

Domyślne kolory dla pól fragmentu kodu można edytować można zmienić, modyfikując **pole fragmentu kodu** w **czcionki i kolory** okienku **opcje** okno dialogowe. Aby uzyskać więcej informacji, zobacz [jak: Zmiana czcionek i kolorów w edytorze](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Zobacz także

- [Fragmentów kodu XML](../xml-tools/xml-snippets.md)
- [Instrukcje: Generowanie fragmentu kodu XML na podstawie schematu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [Instrukcje: Tworzenie fragmentów kodu XML](../xml-tools/how-to-create-xml-snippets.md)