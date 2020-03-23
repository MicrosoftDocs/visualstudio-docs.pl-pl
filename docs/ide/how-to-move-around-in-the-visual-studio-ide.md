---
title: Jak poruszać się w IDE
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2febdedf5cf472132de936c37cad787df3d77518
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590998"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Jak: Poruszanie się w środowiskach IDE programu Visual Studio

Zintegrowane środowisko programistyczne (IDE) zostało zaprojektowane w taki sposób, aby umożliwić przechodzenie z okna do okna i plik do pliku na kilka różnych sposobów, w zależności od preferencji lub wymagań projektu. Można wybrać, aby przełączać się między otwartymi plikami w edytorze lub przełączać się między wszystkimi aktywnymi oknami narzędzi w IDE. Można również przełączyć się bezpośrednio do dowolnego pliku otwartego w edytorze, niezależnie od kolejności, w jakiej był ostatnio dostępny. Te funkcje mogą pomóc zwiększyć produktywność podczas pracy w IDE.

> [!NOTE]
> Opcje dostępne w oknach dialogowych oraz nazwy i lokalizacje wyświetlonych poleceń menu mogą różnić się od opisanych w tym artykule, w zależności od aktywnych ustawień lub wersji. Ten artykuł został napisany z myślą o ustawieniach **ogólnych.** Aby zmienić ustawienia, na przykład na **Ustawienia ogólne** lub **Visual C++,** wybierz pozycję Ustawienia**importu i eksportu** **narzędzi,** > a następnie wybierz pozycję **Resetuj wszystkie ustawienia**.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

Prawie każde polecenie menu w programie Visual Studio ma skrót klawiaturowy. Można również tworzyć własne niestandardowe skróty. Aby uzyskać więcej informacji, zobacz [Identyfikowanie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigate-among-files-in-the-editor"></a>Poruszanie się między plikami w edytorze

Można użyć kilku metod, aby przejść przez pliki otwarte w edytorze. Możesz przenosić między plikami na podstawie kolejności, w jakiej do nich uzyskujesz dostęp, użyć nawigatora IDE, aby szybko znaleźć dowolny plik aktualnie otwarty, lub dobrze przypiąć ulubione pliki do karty, aby były zawsze widoczne.

Nawiguj wstecz i nawiguj do przodu, przechodząc do przodu, przechodząc przez otwarte pliki w edytorze na podstawie kolejności, w jakiej były dostępne, podobnie jak wstecz i do przodu, aby wykonać historię przeglądania w programie Microsoft Internet Explorer.

### <a name="to-move-through-open-files-in-order-of-use"></a>Aby poruszać się po otwartych plikach w kolejności użytkowania

- Aby aktywować otwarte dokumenty w kolejności, w jakiej zostały ostatnio dotknięte, naciśnij klawisz **Ctrl** + **-** (łącznik).

- Aby aktywować otwarte dokumenty w odwrotnej kolejności, naciśnij **klawisze Ctrl**+**Shift** + **-** (łącznik).

    > [!NOTE]
    > **Nawigacja do tyłu** i **Nawigacja do przodu** również można znaleźć w menu **Widok.**

Można również przełączyć się do określonego pliku otwartego w edytorze, niezależnie od tego, kiedy ostatnio dostęp do pliku, za pomocą **IDE Navigator**, **active files** list w edytorze lub okna dialogowego **systemu Windows.**

**Ide Navigator** działa podobnie jak przełącznik aplikacji systemu Windows. Nie jest on dostępny w menu i można uzyskać do niego dostęp tylko za pomocą klawiszy skrótów. Za pomocą jednego z dwóch poleceń można uzyskać dostęp do **nawigatora IDE** (pokazanego poniżej), aby przełączać pliki, w zależności od kolejności, w jakiej chcesz przechodzić między nimi.

![Nawigator IDE programu Visual Studio](../ide/media/vs2015_ide_navigator.png)

`Window.PreviousDocumentWindowNav`pozwala przejść do pliku, do którego `Window.NextDocumentWindowNav` ostatnio dostęp uzyskał dostęp, i pozwala na poruszanie się w odwrotnej kolejności. **Ogólne ustawienia rozwoju** przypisuje **Shift**+ `Window.PreviousDocumentWindowNav` **Alt**+**F7** `Window.NextDocumentWindowNav`do i **Alt**+**F7** do .

> [!NOTE]
> Jeśli do tego polecenia przypisana jest już kombinacja ustawień, do której nie przypisano kombinacji klawiszy skrótu, można przypisać własne polecenie niestandardowe za pomocą strony **Klawiatura** okna dialogowego **Opcje.** Aby uzyskać więcej informacji, zobacz [Identyfikowanie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-specific-files-in-the-editor"></a>Aby przełączyć się do określonych plików w edytorze

- Naciśnij **klawisz Ctrl**+**Tab,** aby wyświetlić **nawigator IDE**. Przytrzymaj klawisz **Ctrl** i naciskaj klawisz **Tab,** aż wybierzesz plik, na który chcesz się przełączyć.

    > [!TIP]
    > Aby odwrócić kolejność przechodzenia przez listę **Aktywne pliki,** przytrzymaj klawisze **Ctrl**+**Shift** i naciśnij klawisz **Tab**.

    \-lub -

- W prawym górnym rogu edytora wybierz przycisk **Aktywne pliki,** a następnie wybierz plik z listy, do na który chcesz się przełączyć.

    \-lub -

- Na pasku menu wybierz polecenie **Okno** > **Windows**.

- Na liście zaznacz plik, który chcesz wyświetlić, a następnie wybierz pozycję **Aktywuj**.

## <a name="navigate-among-tool-windows-in-the-ide"></a>Nawigowanie między oknami narzędzi w idei

**Nawigator IDE** umożliwia również przechodzenie między oknami narzędzi, które zostały otwarte w IDE. Za pomocą jednego z dwóch poleceń można uzyskać dostęp do **nawigatora IDE,** aby przełączać się między oknami narzędzi, w zależności od kolejności, w jakiej chcesz przechodzić między nimi. `Window.PreviousToolWindowNav`pozwala przejść do pliku, do którego `Window.NextToolWindowNav` ostatnio dostęp uzyskał dostęp, i pozwala na poruszanie się w odwrotnej kolejności. **Ogólne ustawienia rozwoju** przypisuje **Shift**+ `Window.PreviousDocumentWindowNav` **Alt**+**F7** `Window.NextDocumentWindowNav`do i **Alt**+**F7** do .

> [!NOTE]
> Jeśli do tego polecenia przypisana jest już kombinacja ustawień, do której nie przypisano kombinacji klawiszy skrótu, można przypisać własne polecenie niestandardowe za pomocą strony **Klawiatura** okna dialogowego **Opcje.** Aby uzyskać więcej informacji, zobacz [Identyfikowanie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>Aby przełączyć się do określonego okna narzędzia w

- Naciśnij **klawisz Alt**+**F7,** aby wyświetlić **nawigator IDE**. Przytrzymaj klawisz **Alt** i naciskaj klawisz **F7** wielokrotnie, aż wybierzesz okno, do którego chcesz się przełączyć.

    > [!TIP]
    > Aby odwrócić kolejność przechodzenia przez listę **Aktywnych narzędzi systemu Windows,** przytrzymaj klawisze **Shift**+**Alt** i naciśnij klawisz **F7**.

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie układów okien](../ide/customizing-window-layouts-in-visual-studio.md)
- [Domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md)
