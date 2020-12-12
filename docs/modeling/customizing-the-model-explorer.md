---
title: Dostosowywanie Eksploratora modelu
description: Dowiedz się, jak można zmienić wygląd i zachowanie Eksploratora dla projektanta języka specyficznego dla domeny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d4bdfcea6cbc54fd620e9aacbdc6250493ca426
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362893"
---
# <a name="customizing-the-model-explorer"></a>Dostosowywanie Eksploratora modelu
Wygląd i zachowanie Eksploratora dla projektanta języka specyficznego dla domeny można zmienić w następujący sposób:

- Zmień tytuł okna.

- Zmień ikonę tabulacji.

- Zmień ikony dla węzłów.

- Ukryj węzły.

## <a name="changing-the-window-title"></a>Zmiana tytułu okna
 Aby zmienić tytuł okna wygenerowanego Eksploratora, wybierz pozycję **zachowanie Eksploratora** w **Eksploratorze DSL**, a następnie w oknie **Właściwości** ustaw właściwość **title** na tytuł, który ma zostać wybrany.

## <a name="changing-the-tab-icon"></a>Zmiana ikony karty
 Aby zmienić ikonę karty dla Eksploratora, użyj ikony 16x16 pikseli w pliku BMP. Umieść plik ikony w folderze \DslPackage\Resources\, a następnie zmień nazwę pliku na **ModelExplorerToolWindowBitmaps.bmp**. Na przykład można zmienić plik ikony Setup. ico programu Visual Studio na format bmp i zmienić jego nazwę na **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. Wygenerowany Projektant wyświetli tę ikonę na karcie Eksploratora, gdy zostanie ona zadokowany przy użyciu **Eksplorator rozwiązań**.

## <a name="setting-custom-icons-on-explorer-nodes"></a>Ustawianie ikon niestandardowych w węzłach Eksploratora
 Węzły w Eksploratorze można dostosować za pomocą ustawień węzła Eksploratora. Poniższa procedura pokazuje, jak dodać ikonę do węzła.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>Aby dodać ikonę do węzła Eksploratora

1. Utwórz [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] rozwiązanie przy użyciu szablonu rozwiązania przepływu zadań.

2. Umieść plik BMP, który zawiera ikonę 16x16 pikseli w folderze **Dsl\Resources** w rozwiązaniu.

3. W **Eksploratorze DSL** kliknij prawym przyciskiem myszy pozycję **zachowanie Eksploratora** , a następnie kliknij polecenie **Dodaj nowe ustawienia węzła Eksploratora**.

    Węzeł **ExplorerNodeSettings** jest wyświetlany w węźle **niestandardowe ustawienia węzła** .

4. Wybierz pozycję **ExplorerNodeSettings**, a następnie w oknie **Właściwości** ustaw pozycję **Klasa** na **aktor**.

5. Ustaw **ikonę, aby wyświetlić** ścieżkę pliku ikony.

6. Przekształć wszystkie szablony, a następnie Skompiluj i uruchom rozwiązanie.

7. W wygenerowanym projektancie Otwórz przykładowy diagram.

    Eksplorator powinien pokazać trzy węzły **aktora** , które mają swoją ikonę.

> [!NOTE]
> Jeśli ustawiono ikonę węzła dla każdego elementu, który jest wyświetlany w wygenerowanym Eksploratorze, wszystkie węzły Eksploratora będą wyświetlały tę ikonę. Jeśli ikona nie została ustawiona, w węzłach zostanie wyświetlona ikona domyślna.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Zmiana nazwy wyświetlanej w węźle Eksploratora
 Można zmienić sposób wyświetlania nazw elementów modelu w Eksploratorze. Poniższa procedura pokazuje, jak wyświetlić nazwę **zadania** , do którego odwołuje się **komentarz** w węźle komentarz.

#### <a name="to-display-a-property"></a>Aby wyświetlić właściwość

1. Otwórz rozwiązanie, które zostało utworzone we wcześniejszej procedurze.

2. Upewnij się, że **komentarz** odwołuje się tylko do pojedynczej klasy domeny, ustawiając liczebność roli z **tematami** nazw właściwości na 0.. 1. Nazwa właściwości powinna być **podmiotem**, a nazwa relacji powinna być **CommentReferencesSubject**.

3. W **Eksploratorze DSL** kliknij prawym przyciskiem myszy pozycję **zachowanie Eksploratora** , a następnie kliknij polecenie **Dodaj nowe ustawienia węzła Eksploratora**.

     Węzeł **ExplorerNodeSettings** jest wyświetlany w węźle **niestandardowe ustawienia węzła** .

4. Wybierz pozycję **ExplorerNodeSettings**, a następnie w oknie **Właściwości** **Ustaw wartość** **komentarz**.

5. Kliknij prawym przyciskiem myszy węzeł **komentarz** , a następnie kliknij polecenie **Dodaj nową ścieżkę właściwości**.

     Zostanie wyświetlony nowy węzeł o nazwie **wyświetlana właściwość**.

6. Wybierz pozycję **Właściwość wyświetlana**, a następnie w oknie **Właściwości** kliknij pole wartość **ścieżka do właściwości**. Wybierz pozycję **komentarz**, a następnie **CommentReferencesSubject**, a następnie pozycję **FlowElement**. Ścieżka wyników powinna wyglądać podobnie do **CommentReferencesSubject. Subject/! Temat**.

7. W polu wartość **Właściwości** wybierz pozycję **Nazwa**.

8. Przekształć wszystkie szablony, a następnie Skompiluj i uruchom swoje rozwiązanie.

9. W wygenerowanym projektancie Otwórz przykładowy diagram.

10. Narysuj **Łącznik komentarzy** między elementem komentarza a elementem **Task1** na diagramie.

     W węźle Eksploratora powinien być wyświetlany komentarz jako **Task1**.

## <a name="hiding-nodes"></a>Ukrywanie węzłów
 Węzeł w Eksploratorze można ukryć, dodając jego ścieżkę do węzła **węzły ukryte** w **Eksploratorze DSL**. Poniższa procedura pokazuje, jak ukryć węzły **komentarzy** .

#### <a name="to-hide-an-explorer-node"></a>Aby ukryć węzeł Eksploratora

1. Otwórz rozwiązanie, które zostało utworzone we wcześniejszej procedurze.

2. W **Eksploratorze DSL** kliknij prawym przyciskiem myszy pozycję **zachowanie Eksploratora** , a następnie kliknij polecenie **Dodaj nową ścieżkę domeny**.

     Węzeł **ścieżki domeny** jest wyświetlany w obszarze **ukryte węzły**.

3. Wybierz pozycję **ścieżka domeny**, a następnie w oknie **Właściwości** kliknij pole wartość **definicji ścieżki**. Wybierz pozycję **FlowGraph**, a następnie **FlowGraphHasComments**. Ścieżka wyników powinna wyglądać podobnie do **FlowGraphHasComments. Comments**

4. Przekształć wszystkie szablony, a następnie Skompiluj i uruchom swoje rozwiązanie.

5. W wygenerowanym projektancie Otwórz przykładowy diagram.

     Eksplorator powinien wyświetlać tylko węzeł **aktorzy** i nie powinien wyświetlać węzła **Komentarze** .

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownik](/previous-versions/bb126564(v=vs.100))