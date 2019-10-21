---
title: Jak poruszać się w środowisku IDE
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3aa39c1c9748eb3a9270a66a3a6bbcb43fdcea2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645831"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Instrukcje: poruszanie się w środowisku IDE programu Visual Studio

Zintegrowane środowisko programistyczne (IDE) zostało zaprojektowane z myślą o umożliwieniu przejścia z okna do okna i pliku do pliku na kilka różnych sposobów, w zależności od wymagań związanych z preferencjami lub projektem. Możesz wybrać przechodzenie między otwartymi plikami w edytorze lub przełączać się między wszystkimi aktywnymi oknami narzędzi w IDE. Możesz również przełączyć się bezpośrednio do dowolnego pliku otwartego w edytorze, niezależnie od kolejności, w której ostatnio uzyskano dostęp. Te funkcje mogą pomóc zwiększyć produktywność podczas pracy w środowisku IDE.

> [!NOTE]
> Opcje dostępne w oknach dialogowych oraz nazwy i lokalizacje poleceń menu, które są widoczne, mogą się różnić od tego, co zostało opisane w tym artykule, w zależności od ustawień aktywnych lub wydania. Ten artykuł został zapisany z uwzględnieniem ustawień **ogólnych** . Aby zmienić ustawienia, na przykład **Ogólne** lub ustawienia **wizualizacji C++**  , wybierz pozycję **Narzędzia** > **Ustawienia importu i eksportu**, a następnie wybierz pozycję **Zresetuj wszystkie ustawienia**.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

Niemal każde polecenie menu w programie Visual Studio ma skrót klawiaturowy. Możesz również utworzyć własne skróty niestandardowe. Aby uzyskać więcej informacji, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigate-among-files-in-the-editor"></a>Nawigowanie między plikami w edytorze

Do przechodzenia między plikami otwartymi w edytorze można używać kilku metod. Można przechodzić między plikami w zależności od kolejności, w której uzyskuje się do nich dostęp, za pomocą Nawigatora IDE można szybko znaleźć dowolny plik, który jest aktualnie otwarty, lub przypinać Ulubione pliki do karty, aby były zawsze widoczne.

Przejdź wstecz i przejdź do następnego cyklu, korzystając z otwartych plików w edytorze, na podstawie kolejności, w której były dostępne, podobnie jak wstecz i w przód — dla historii wyświetlania w programie Microsoft Internet Explorer.

### <a name="to-move-through-open-files-in-order-of-use"></a>Aby przejść przez otwarte pliki w kolejności użycia

- Aby uaktywnić otwarte dokumenty w kolejności, w której zostały ostatnio zmienione, naciśnij **klawisze Ctrl**+ **-** (łącznik).

- Aby uaktywnić otwarte dokumenty w kolejności odwrotnej, naciśnij **klawisze Ctrl**+**SHIFT**+ **-** (łącznik).

    > [!NOTE]
    > **Przejdź do tyłu** i **Przejdź do przodu** w menu **Widok** .

Możesz również przełączyć się do określonego pliku otwartego w edytorze, niezależnie od tego, kiedy ostatnio uzyskano dostęp do pliku przy użyciu **Nawigatora IDE**, listy **aktywne pliki** w edytorze lub okna dialogowego **systemu Windows** .

**Nawigator IDE** działa podobnie jak przełącznik aplikacji systemu Windows. Nie jest on dostępny w menu i można uzyskać do niego dostęp tylko przy użyciu klawiszy skrótów. Możesz użyć jednego z dwóch poleceń, aby uzyskać dostęp do **Nawigatora IDE** (pokazanego poniżej) w celu przechodzenia przez pliki w zależności od kolejności, w której chcesz przeprowadzić cykl.

![Nawigator środowiska IDE programu Visual Studio](../ide/media/vs2015_ide_navigator.png)

`Window.PreviousDocumentWindowNav` umożliwia przechodzenie do ostatniego dostępu do pliku, a `Window.NextDocumentWindowNav` umożliwia przechodzenie w odwrotnej kolejności. **Ogólne ustawienia programowania** przypisuje **SHIFT**+**Alt**+**f7** do `Window.PreviousDocumentWindowNav` i **Alt**+**F7** do 0.

> [!NOTE]
> Jeśli używana kombinacja ustawień nie ma już kombinacji klawiszy skrótu przypisanych do tego polecenia, możesz przypisać własne polecenie niestandardowe przy użyciu strony **Klawiatura** okna dialogowego **Opcje** . Aby uzyskać więcej informacji, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-specific-files-in-the-editor"></a>Aby przełączyć się do określonych plików w edytorze

- Naciśnij klawisz **Ctrl** +**kartę** , aby wyświetlić **Nawigator IDE**. Przytrzymaj wciśnięty klawisz **Ctrl** i naciskaj klawisz **Tab** do momentu wybrania pliku, do którego chcesz się przełączyć.

    > [!TIP]
    > Aby odwrócić kolejność, w której można przejść przez listę **aktywnych plików** , przytrzymaj wciśnięty klawisz **Ctrl**+**SHIFT** i naciśnij klawisz **Tab**.

    \- lub-

- W prawym górnym rogu edytora wybierz przycisk **aktywne pliki** , a następnie wybierz plik z listy, aby przełączyć się na.

    \- lub-

- Na pasku menu wybierz **okno** > **Windows**.

- Z listy wybierz plik, który chcesz wyświetlić, a następnie wybierz pozycję **Aktywuj**.

## <a name="navigate-among-tool-windows-in-the-ide"></a>Nawigowanie między oknami narzędzi w środowisku IDE

**Nawigator IDE** umożliwia również przechodzenie przez okna narzędzi, które zostały otwarte w środowisku IDE. Możesz użyć jednego z dwóch poleceń, aby uzyskać dostęp do **Nawigatora IDE** w celu przechodzenia przez okna narzędzi, w zależności od kolejności, w której chcesz przeprowadzić cykl. `Window.PreviousToolWindowNav` umożliwia przechodzenie do ostatniego dostępu do pliku, a `Window.NextToolWindowNav` umożliwia przechodzenie w odwrotnej kolejności. **Ogólne ustawienia programowania** przypisuje **SHIFT**+**Alt**+**f7** do `Window.PreviousDocumentWindowNav` i **Alt**+**F7** do 0.

> [!NOTE]
> Jeśli używana kombinacja ustawień nie ma już kombinacji klawiszy skrótu przypisanych do tego polecenia, możesz przypisać własne polecenie niestandardowe przy użyciu strony **Klawiatura** okna dialogowego **Opcje** . Aby uzyskać więcej informacji, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>Aby przełączyć się do określonego okna narzędzia w środowisku IDE

- Naciśnij klawisz **Alt**+**F7** , aby wyświetlić **Nawigatora IDE**. Przytrzymaj klawisz **Alt** i naciśnij kilkakrotnie klawisz **F7** do momentu wybrania okna, do którego chcesz się przełączyć.

    > [!TIP]
    > Aby odwrócić kolejność, w której można przejść przez **aktywną listę okien narzędzi** , przytrzymaj wciśnięty klawisz **SHIFT**+**Alt** i naciśnij klawisz **F7**.

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie układów okien](../ide/customizing-window-layouts-in-visual-studio.md)
- [Domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md)