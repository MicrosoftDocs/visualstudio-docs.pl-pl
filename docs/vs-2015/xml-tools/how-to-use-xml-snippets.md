---
title: 'Instrukcje: Używanie fragmentów kodu XML | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: be8d42a5a4557b39a02e724eb54b5434c1b454ea
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59659972"
---
# <a name="how-to-use-xml-snippets"></a>Instrukcje: Używanie fragmentów kodu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wywołać fragmentów kodu XML za pomocą dwóch poniższych poleceń w menu kontekstowym edytora XML. **Wstaw fragment kodu** polecenia wstawia fragment kodu XML w położeniu kursora. **Otocz** polecenia opakowuje fragment kodu XML wokół zaznaczonego tekstu. Każdy fragment kodu XML został wyznaczony typy fragmentu kodu. Typy fragment określają, czy ten fragment kodu jest dostępna z **Wstaw fragment kodu** polecenia **Otocz** polecenia i / lub.  
  
 Po dodaniu fragment kodu XML do edytora wszelkie edytowalnego pola we fragmencie są wyróżnione na żółto. Ponadto kursor znajduje się na pierwsze pole można edytować.  
  
## <a name="insert-snippet"></a>Wstaw fragment kodu  
 W poniższych procedurach opisano sposób uzyskiwania dostępu do **Wstaw fragment kodu** polecenia.  
  
> [!NOTE]
>  **Wstaw fragment kodu** polecenia jest także dostępny za pomocą skrótu klawiaturowego (CTRL + K, a następnie klawisze CTRL + X).  
  
#### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Aby wstawić fragmentów kodu z menu skrótów  
  
1.  Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.  
  
2.  Kliknij prawym przyciskiem myszy i wybierz **Wstaw fragment kodu**.  
  
     Zostanie wyświetlona lista dostępnych fragmentów kodu XML.  
  
3.  Wybierz fragment z listy przy użyciu myszy lub wpisując nazwę fragmentu i naciskając klawisz TAB lub ENTER.  
  
#### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Aby wstawić fragmentów kodu za pomocą menu funkcji IntelliSense  
  
1.  Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.  
  
2.  Z **Edytuj** menu wskaż **IntelliSense**, a następnie wybierz pozycję **Wstaw fragment kodu**.  
  
     Zostanie wyświetlona lista dostępnych fragmentów kodu XML.  
  
3.  Wybierz fragment z listy przy użyciu myszy lub wpisując nazwę fragmentu i naciskając klawisz TAB lub ENTER.  
  
#### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Aby wstawić fragmentów kodu za pośrednictwem listy IntelliSense Dokończ wyraz  
  
1.  Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.  
  
2.  Rozpocznij wpisywanie fragment kodu XML, który chcesz dodać do pliku. Jeśli jest włączona funkcja automatycznego uzupełniania, zostanie wyświetlona lista Dokończ wyraz IntelliSense. Jeśli nie zostanie wyświetlony, naciśnij klawisze CTRL + SPACJA, aby ją uaktywnić.  
  
3.  Wybierz fragment kodu XML z listy Dokończ wyraz.  
  
4.  Naciśnij klawisz TAB, TAB, aby wywołać fragment kodu XML.  
  
> [!NOTE]
>  Można wykluczyć sytuacji podczas wywoływania fragmencie kodu XML nie uzyskać. Na przykład, jeśli podczas próby wstawienia `xs:complexType` element wewnątrz `xs:element` węzła, edytor nie generuje fragmentu kodu XML. Gdy `xs:complexType` elementu jest używana wewnątrz `xs:element` węzła, brak wymaganych atrybutów i dozwolone podelementy, więc edytor nie ma żadnych danych, aby wstawić.  
  
#### <a name="to-insert-snippets-using-the-shortcut-name"></a>Aby wstawić fragmentów kodu przy użyciu nazwy skrótu  
  
1.  Umieść kursor w miejscu, w którym chcesz wstawić fragment kodu XML.  
  
2.  Typ `<` w okienku edytora.  
  
3.  Naciśnij klawisz ESC, aby zamknąć lista Dokończ wyraz IntelliSense.  
  
4.  Wpisz nazwę skrótów fragmentu, a następnie naciśnij klawisz TAB, aby wywołać fragment kodu XML.  
  
## <a name="surround-with"></a>Otocz przez  
 W poniższych procedurach opisano sposób uzyskiwania dostępu do **Otocz** polecenia.  
  
> [!NOTE]
>  **Otocz** polecenia jest także dostępny za pomocą skrótu klawiaturowego (CTRL + K, a następnie klawisze CTRL + S).  
  
#### <a name="to-use-surround-with-from-the-context-menu"></a>Aby użyć umieszczanie w menu kontekstowym  
  
1.  Zaznacz tekst, aby ująć w edytorze XML.  
  
2.  Kliknij prawym przyciskiem myszy i wybierz **Otocz**.  
  
     Zostanie wyświetlona lista dostępnych otacza przy użyciu fragmentów kodu XML.  
  
3.  Wybierz fragment z listy przy użyciu myszy lub wpisując nazwę fragmentu i naciskając klawisz TAB lub ENTER.  
  
#### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Aby użyć Otocz za pomocą menu funkcji Intellisense  
  
1.  Zaznacz tekst, aby ująć w edytorze XML.  
  
2.  Z **Edytuj** menu wskaż **IntelliSense**, a następnie wybierz pozycję **Otocz**.  
  
     Zostanie wyświetlona lista dostępnych otacza przy użyciu fragmentów kodu XML.  
  
3.  Wybierz fragment z listy przy użyciu myszy lub wpisując nazwę fragmentu i naciskając klawisz TAB lub ENTER.  
  
## <a name="using-xml-snippets"></a>Za pomocą fragmentów kodu XML  
 Po wybraniu fragmentu kodu XML, tekst fragment kodu dodaje się automatycznie w położeniu kursora. Wszystkie pola edycji we fragmencie są wyróżnione, a pierwsze pole można edytować jest wybrana automatycznie. Aktualnie wybrane pole jest opakowany.  
  
 Gdy pole jest zaznaczone, możesz wpisać nową wartość dla pola. Naciśnięcie klawisza cykle kartę za pomocą pola edytowalne fragmentu; Naciśnięcie klawisza SHIFT + TAB cykle przetwarza je w odwrotnej kolejności. Kliknięcie pola umieszcza kursor w polu, a następnie dwukrotne kliknięcie pola zaznacza go. Wyróżnionego pola etykietki narzędzia może być wyświetlany, oferując opis pola.  
  
 Tylko pierwsze wystąpienie określonego pola jest edytowalny. To pole jest wyróżniony, opisano inne wystąpienia tego pola. Po zmianie wartości pola można edytować tego pola jest zmieniany, wszędzie tam, gdzie jest używany w tym fragmencie kodu.  
  
 Naciśnięcie klawisza ENTER lub ESC spowoduje anulowanie edytowania pól i zwraca Edytor do normalnego.  
  
 Domyślne kolory dla pól fragmentu kodu można edytować można zmienić, modyfikując ustawienie pole fragmentu kodu w **czcionki i kolory** okienku **opcje** okno dialogowe. Aby uzyskać więcej informacji, zobacz [jak: Zmiana czcionek i kolorów w edytorze](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Fragmentów kodu XML](../xml-tools/xml-snippets.md)   
 [Instrukcje: Generowanie fragmentu kodu XML na podstawie schematu XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)   
 [Instrukcje: Tworzenie fragmentów kodu XML](../xml-tools/how-to-create-xml-snippets.md)
