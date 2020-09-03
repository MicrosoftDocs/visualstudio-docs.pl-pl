---
title: Dostosowywanie Eksploratora modelu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
ms.assetid: d2926444-9408-41d8-a27e-3fd0c416f9ac
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce96f2a3df901c1fea0aa4caa97d29c07db5e681
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654951"
---
# <a name="customizing-the-model-explorer"></a>Dostosowywanie Eksploratora modelu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wygląd i zachowanie Eksploratora dla projektanta języka specyficznego dla domeny można zmienić w następujący sposób:

- Zmień tytuł okna.

- Zmień ikonę tabulacji.

- Zmień ikony dla węzłów.

- Ukryj węzły.

## <a name="changing-the-window-title"></a>Zmiana tytułu okna
 Aby zmienić tytuł okna wygenerowanego Eksploratora, wybierz pozycję **zachowanie Eksploratora** w **Eksploratorze DSL**, a następnie w oknie **Właściwości** ustaw właściwość **title** na tytuł, który ma zostać wybrany.

## <a name="changing-the-tab-icon"></a>Zmiana ikony karty
 Aby zmienić ikonę karty dla Eksploratora, użyj ikony 16x16 pikseli w pliku BMP. Umieść plik ikony w folderze \DslPackage\Resources\, a następnie zmień nazwę pliku na **ModelExplorerToolWindowBitmaps.bmp**. Na przykład można zmienić [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] plik ikony Setup. ico na format bmp i zmienić jego nazwę na **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. Wygenerowany Projektant wyświetli tę ikonę na karcie Eksploratora, gdy zostanie ona zadokowany przy użyciu **Eksplorator rozwiązań**.

## <a name="setting-custom-icons-on-explorer-nodes"></a>Ustawianie ikon niestandardowych w węzłach Eksploratora
 Węzły w Eksploratorze można dostosować za pomocą ustawień węzła Eksploratora. Poniższa procedura pokazuje, jak dodać ikonę do węzła.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>Aby dodać ikonę do węzła Eksploratora

1. Utwórz [!INCLUDE[dsl](../includes/dsl-md.md)] rozwiązanie przy użyciu szablonu rozwiązania przepływu zadań.

2. Umieść plik BMP, który zawiera ikonę 16x16 pikseli w folderze **Dsl\Resources** w rozwiązaniu.

3. W **Eksploratorze DSL**kliknij prawym przyciskiem myszy pozycję **zachowanie Eksploratora** , a następnie kliknij polecenie **Dodaj nowe ustawienia węzła Eksploratora**.

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

3. W **Eksploratorze DSL**kliknij prawym przyciskiem myszy pozycję **zachowanie Eksploratora** , a następnie kliknij polecenie **Dodaj nowe ustawienia węzła Eksploratora**.

     Węzeł **ExplorerNodeSettings** jest wyświetlany w węźle **niestandardowe ustawienia węzła** .

4. Wybierz pozycję **ExplorerNodeSettings**, a następnie w oknie **Właściwości** **Ustaw wartość** **komentarz**.

5. Kliknij prawym przyciskiem myszy węzeł **komentarz** , a następnie kliknij polecenie **Dodaj nową ścieżkę właściwości**.

     Zostanie wyświetlony nowy węzeł o nazwie **wyświetlana właściwość**.

6. Wybierz pozycję **Właściwość wyświetlana**, a następnie w oknie **Właściwości** kliknij pole wartość **ścieżka do właściwości**. Wybierz pozycję **komentarz**, a następnie **CommentReferencesSubject**, a następnie pozycję **FlowElement**. Ścieżka wyników powinna wyglądać podobnie do **CommentReferencesSubject. Subject/! Temat**.

7. W polu wartość **Właściwości**wybierz pozycję **Nazwa**.

8. Przekształć wszystkie szablony, a następnie Skompiluj i uruchom swoje rozwiązanie.

9. W wygenerowanym projektancie Otwórz przykładowy diagram.

10. Narysuj **Łącznik komentarzy** między elementem komentarza a elementem **Task1** na diagramie.

     W węźle Eksploratora powinien być wyświetlany komentarz jako **Task1**.

## <a name="hiding-nodes"></a>Ukrywanie węzłów
 Węzeł w Eksploratorze można ukryć, dodając jego ścieżkę do węzła **węzły ukryte** w **Eksploratorze DSL**. Poniższa procedura pokazuje, jak ukryć węzły **komentarzy** .

#### <a name="to-hide-an-explorer-node"></a>Aby ukryć węzeł Eksploratora

1. Otwórz rozwiązanie, które zostało utworzone we wcześniejszej procedurze.

2. W **Eksploratorze DSL**kliknij prawym przyciskiem myszy pozycję **zachowanie Eksploratora** , a następnie kliknij polecenie **Dodaj nową ścieżkę domeny**.

     Węzeł **ścieżki domeny** jest wyświetlany w obszarze **ukryte węzły**.

3. Wybierz pozycję **ścieżka domeny**, a następnie w oknie **Właściwości** kliknij pole wartość **definicji ścieżki**. Wybierz pozycję **FlowGraph**, a następnie **FlowGraphHasComments**. Ścieżka wyników powinna wyglądać podobnie do **FlowGraphHasComments. Comments**

4. Przekształć wszystkie szablony, a następnie Skompiluj i uruchom swoje rozwiązanie.

5. W wygenerowanym projektancie Otwórz przykładowy diagram.

     Eksplorator powinien wyświetlać tylko węzeł **aktorzy** i nie powinien wyświetlać węzła **Komentarze** .

## <a name="see-also"></a>Zobacz też
 [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
