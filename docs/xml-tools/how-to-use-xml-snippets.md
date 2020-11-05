---
title: Jak używać fragmentów kodu XML
description: Dowiedz się, jak używać poleceń w edytorze XML do wstawiania fragmentów kodu XML lub zawijania fragmentu kodu XML wokół zaznaczonego tekstu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bebca3a27d11015388e45ff6839f446506e716c
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400118"
---
# <a name="how-to-use-xml-snippets"></a>Instrukcje: używanie fragmentów kodu XML

Można wywołać fragmenty kodu XML przy użyciu dwóch poniższych poleceń w menu skrótów edytora XML. Polecenie **Wstaw fragment** kodu wstawia fragment kodu XML w pozycji kursora. Element **przestrzenny z** poleceniem otacza fragment kodu XML wokół zaznaczonego tekstu. Każdy fragment kodu XML wyznaczył typy fragmentów kodu. Typy fragmentów określają, czy fragment kodu jest dostępny za pomocą polecenia **Wstaw fragment kodu** , polecenia **przestrzenny** lub obu.

Po dodaniu fragmentu kodu XML do edytora wszystkie pola edytowalne w fragmencie kodu zostaną wyróżnione kolorem żółtym, a kursor zostanie umieszczony w pierwszym edytowalnym polu.

## <a name="insert-snippet"></a>Wstaw fragment kodu

W poniższych procedurach opisano sposób uzyskiwania dostępu do polecenia **Wstaw fragment kodu** .

> [!NOTE]
> Polecenie **Wstaw fragment kodu** jest również dostępne za pomocą skrótu klawiaturowego ( **Ctrl** + **K** , a następnie **Ctrl** + **X** ).

### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Aby wstawić fragmenty kodu z menu skrótów

1. Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.

2. Kliknij prawym przyciskiem myszy i wybierz **Wstaw fragment kodu**.

   Zostanie wyświetlona lista dostępnych fragmentów kodu XML.

3. Wybierz fragment z listy za pomocą myszy lub wpisz nazwę tego fragmentu, a następnie naciśnij klawisz **Tab** lub **Enter**.

### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Aby wstawić fragmenty kodu przy użyciu menu IntelliSense

1. Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.

2. W menu **Edycja** wskaż polecenie **IntelliSense** , a następnie wybierz polecenie **Wstaw fragment kodu**.

   Zostanie wyświetlona lista dostępnych fragmentów kodu XML.

3. Wybierz fragment z listy za pomocą myszy lub wpisując nazwę tego fragmentu, a następnie naciśnij klawisz **Tab** lub **Enter**.

### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Aby wstawić fragmenty kodu za pomocą listy uzupełniania wyrazów IntelliSense

1. Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.

2. Rozpocznij wpisywanie fragmentu kodu XML, który chcesz dodać do pliku. Jeśli automatyczne uzupełnianie jest włączone, zostanie wyświetlona lista wyrazów uzupełniających IntelliSense. Jeśli nie jest wyświetlany, naciśnij klawisz **Ctrl** , + **Space** aby go uaktywnić.

3. Wybierz fragment kodu XML z listy kompletny wyraz.

4. Naciśnij **Tab** klawisz Tab **, aby** wywołać fragment kodu XML.

> [!NOTE]
> W przypadku braku wywołania fragmentu kodu XML mogą wystąpić przypadki. Na przykład, jeśli spróbujesz wstawić `xs:complexType` element wewnątrz `xs:element` węzła, Edytor nie generuje FRAGMENTU kodu XML. Gdy `xs:complexType` element jest używany wewnątrz `xs:element` węzła, nie ma wymaganych atrybutów ani podelementów, więc Edytor nie ma żadnych danych do wstawienia.

### <a name="to-insert-snippets-using-the-shortcut-name"></a>Aby wstawić fragmenty kodu przy użyciu nazwy skrótu

1. Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.

2. Wpisz `<` w okienku edytora.

3. Naciśnij klawisz **ESC** , aby zamknąć listę wyrazów uzupełniających IntelliSense.

4. Wpisz nazwę skrótu wstawki, a następnie naciśnij klawisz **Tab** , aby wywołać fragment kodu XML.

## <a name="surround-with"></a>Otocz za pomocą

W poniższych procedurach opisano, jak uzyskać dostęp do polecenia **przestrzenny z** poleceniem.

> [!NOTE]
> Polecenie **Otocz za pomocą** polecenia jest również dostępne za pomocą skrótu klawiaturowego ( **Ctrl** + **K** , a następnie **Ctrl** + **S** ).

### <a name="to-use-surround-with-from-the-context-menu"></a>Aby użyć funkcji Otocz z z menu kontekstowego

1. Zaznacz tekst, który ma być otoczony w edytorze XML.

2. Kliknij prawym przyciskiem myszy i wybierz opcję **Otocz za pomocą**.

   Zostanie wyświetlona lista dostępnych elementów otaczających ze fragmentami kodu XML.

3. Wybierz fragment z listy za pomocą myszy lub wpisz nazwę tego fragmentu, a następnie naciśnij klawisz **Tab** lub **Enter**.

### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Aby użyć funkcji Otocz z z poziomu menu IntelliSense

1. Zaznacz tekst, który ma być otoczony w edytorze XML.

2. W menu **Edycja** wskaż polecenie **IntelliSense** , a następnie wybierz opcję **Otocz za pomocą**.

   Zostanie wyświetlona lista dostępnych elementów otaczających ze fragmentami kodu XML.

3. Wybierz fragment z listy za pomocą myszy lub wpisz nazwę tego fragmentu, a następnie naciśnij klawisz **Tab** lub **Enter**.

## <a name="use-xml-snippets"></a>Używanie fragmentów kodu XML

Po wybraniu fragmentu kodu XML tekst wstawki zostanie automatycznie wstawiony w pozycji kursora. Wszystkie pola edytowalne w fragmencie kodu są wyróżnione i pierwsze pole można edytować automatycznie. Aktualnie wybrane pole jest opakowane.

Gdy pole jest zaznaczone, można wpisać nową wartość pola. Naciskanie **tabulatorów** za pomocą pól edytowalnych fragmentu kodu; naciśnięcie klawisza **SHIFT** powoduje + **Tab** przechodzenie między nimi w odwrotnej kolejności. Kliknięcie pola powoduje umieszczenie kursora w polu, a następnie dwukrotne kliknięcie pola. Gdy pole zostanie wyróżnione, może zostać wyświetlona etykietka narzędzia zawierająca opis pola.

Tylko pierwsze wystąpienie danego pola jest edytowalne. W przypadku zaznaczenia tego pola są podane inne wystąpienia tego pola. Gdy zmienisz wartość pola edytowalnego, to pole jest zmieniane wszędzie tam, gdzie jest używane w fragmencie kodu.

Naciśnięcie klawisza **Enter** lub **ESC** anuluje edycję pola i przywraca Edytor normalny.

Domyślne kolory dla edytowalnych pól fragmentu kodu można zmienić, modyfikując ustawienie **pola fragmentu kodu** w okienku **czcionki i kolory** okna dialogowego **Opcje** . Aby uzyskać więcej informacji, zobacz [How to: zmiana czcionek i kolorów w edytorze](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu XML](../xml-tools/xml-snippets.md)
- [Instrukcje: generowanie fragmentu kodu XML na podstawie schematu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)
- [Instrukcje: Tworzenie fragmentów kodu XML](../xml-tools/how-to-create-xml-snippets.md)
