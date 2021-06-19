---
title: Dostosowywanie Eksploratora modelu
description: Dowiedz się, jak zmienić wygląd i zachowanie eksploratora dla projektanta języka specyficznego dla domeny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c842988f3e5c9f1bbed5a859e73680cb109ecd43
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385906"
---
# <a name="customizing-the-model-explorer"></a>Dostosowywanie Eksploratora modelu
Wygląd i zachowanie eksploratora dla projektanta języka specyficznego dla domeny można zmienić w następujący sposób:

- Zmień tytuł okna.

- Zmień ikonę karty.

- Zmień ikony dla węzłów.

- Ukryj węzły.

## <a name="changing-the-window-title"></a>Zmienianie tytułu okna
 Aby zmienić tytuł okna wygenerowanego eksploratora, wybierz pozycję Zachowanie eksploratora  w eksploratorze **DSL,** a następnie w oknie Właściwości ustaw właściwość **Title** na tytuł, który chcesz. 

## <a name="changing-the-tab-icon"></a>Zmienianie ikony karty
 Aby zmienić ikonę karty eksploratora, użyj ikony 16 x 16 pikseli w .bmp pliku. Umieść plik ikony w folderze \DslPackage\Resources\, a następnie zmień nazwę pliku **naModelExplorerToolWindowBitmaps.bmp**. Na przykład możesz zmienić format pliku Visual Studio ikony setup.ico na .bmp i zmienić jego nazwę na **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. Wygenerowany projektant wyświetli tę ikonę na karcie eksploratora, gdy zostanie zadokowany razem z Eksplorator rozwiązań **.**

## <a name="setting-custom-icons-on-explorer-nodes"></a>Ustawianie ikon niestandardowych w węzłach eksploratora
 Węzły w eksploratorze można dostosować przy użyciu ustawień węzła eksploratora. W poniższej procedurze przedstawiono sposób dodawania ikony do węzła.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>Aby dodać ikonę do węzła eksploratora

1. Utwórz rozwiązanie [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] przy użyciu szablonu rozwiązania Przepływ zadań.

2. Umieść plik .bmp zawierający ikonę 16 x 16 pikseli w folderze **Dsl\Resources** w rozwiązaniu.

3. W **Eksploratorze DSL** kliknij prawym przyciskiem myszy pozycję **Zachowanie eksploratora,** a następnie kliknij polecenie **Dodaj nowe ustawienia węzła Eksploratora.**

    Węzeł **ExplorerNodeSettings** jest wyświetlany w **węźle Niestandardowe ustawienia węzła.**

4. Wybierz **pozycję ExplorerNodeSettings,** a następnie w **oknie Właściwości** ustaw opcję **Klasa** na wartość **Aktor.**

5. Ustaw **pozycję Ikona, aby** wyświetlić ścieżkę do pliku ikony.

6. Przekształć wszystkie szablony, a następnie skompilować i uruchomić rozwiązanie.

7. W wygenerowanym projektancie otwórz przykładowy diagram.

    W Eksploratorze powinny być wyświetlane trzy **węzły** aktora, które mają Twoją ikonę.

> [!NOTE]
> Jeśli ustawiono ikonę węzła dla dowolnego elementu wyświetlanego w wygenerowanym eksploratorze, ikona zostanie wyświetlona we wszystkich węzłach eksploratora. Jeśli ikona nie została ustawiona, w węzłach będzie wyświetlana ikona domyślna.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Zmienianie nazwy wyświetlanej w węźle Eksploratora
 Możesz zmienić sposób wyświetlania nazw elementów modelu w eksploratorze. W poniższej procedurze przedstawiono sposób wyświetlania nazwy **zadania,** do których odwołuje się komentarz **w** węźle komentarza.

#### <a name="to-display-a-property"></a>Aby wyświetlić właściwość

1. Otwórz rozwiązanie utworzone we wcześniejszej procedurze.

2. Upewnij się, że **komentarz** odwołuje się tylko do pojedynczej klasy domeny, ustawiając liczebność roli o nazwie właściwości **Podmioty** na 0..1. Nazwa właściwości powinna mieć wartość **Temat,** a nazwa relacji powinna mieć wartość **CommentReferencesSubject.**

3. W **Eksploratorze DSL** kliknij prawym przyciskiem myszy pozycję **Zachowanie eksploratora,** a następnie kliknij polecenie **Dodaj nowe ustawienia węzła Eksploratora.**

     Węzeł **ExplorerNodeSettings** jest wyświetlany w **węźle Niestandardowe ustawienia węzła.**

4. Wybierz **pozycję ExplorerNodeSettings,** a następnie w **oknie Właściwości** ustaw opcję **Klasa** na **wartość Komentarz.**

5. Kliknij prawym przyciskiem myszy węzeł **Komentarz,** a następnie kliknij polecenie **Dodaj nową ścieżkę właściwości**.

     Zostanie wyświetlony nowy węzeł o nazwie **Właściwość Wyświetlana.**

6. Wybierz **pozycję Właściwość wyświetlana,** a następnie w **oknie** Właściwości kliknij pole wartości właściwości **Ścieżka do**. Wybierz **pozycję Comment**(Komentarz), a następnie pozycję **CommentReferencesSubject (Komentarz),** a następnie pozycję **FlowElement (Element przepływu).** Wynikowa ścieżka powinna **przypominać CommentReferencesSubject.Subject/! Temat**.

7. W polu wartości właściwości **wybierz** pozycję **Nazwa**.

8. Przekształć wszystkie szablony, a następnie skompilować i uruchomić rozwiązanie.

9. W wygenerowanym projektancie otwórz przykładowy diagram.

10. Rysowanie **łącznika komentarza** między elementem komentarza i **elementem Task1** na diagramie.

     W węźle Eksplorator komentarz powinien być wyświetlany jako **Zadanie1.**

## <a name="hiding-nodes"></a>Ukrywanie węzłów
 Możesz ukryć węzeł w eksploratorze, dodając jego ścieżkę do węzła **Ukryte węzły** **w Eksploratorze DSL.** W poniższej procedurze przedstawiono sposób ukrywania **węzłów komentarza.**

#### <a name="to-hide-an-explorer-node"></a>Aby ukryć węzeł eksploratora

1. Otwórz rozwiązanie utworzone we wcześniejszej procedurze.

2. W **Eksploratorze DSL** kliknij prawym przyciskiem myszy pozycję **Zachowanie eksploratora,** a następnie kliknij polecenie **Dodaj nową ścieżkę domeny.**

     Węzeł **Ścieżka domeny jest** wyświetlany w obszarze Ukryte **węzły**.

3. Wybierz **pozycję Ścieżka domeny,** a następnie w **oknie Właściwości** kliknij pole wartości w polu Definicja **ścieżki.** Wybierz **pozycję FlowGraph,** a następnie **pozycję FlowGraphHasComments .** Wynikowa ścieżka powinna wyglądać **następująco: FlowGraphHasComments.Comments**

4. Przekształć wszystkie szablony, a następnie skompilować i uruchomić rozwiązanie.

5. W wygenerowanym projektancie otwórz przykładowy diagram.

     W eksploratorze powinien być pokazywany tylko węzeł **Actors,** a nie węzeł **Komentarze.**

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownika](/previous-versions/bb126564(v=vs.100))