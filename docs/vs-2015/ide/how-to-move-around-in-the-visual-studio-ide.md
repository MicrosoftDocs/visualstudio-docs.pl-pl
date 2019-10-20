---
title: 'Instrukcje: poruszanie się w środowisku IDE | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89c4447eb6bbc4b2ae9f7667672626d5119c61d6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651796"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Porady: poruszanie się w środowisku IDE programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zintegrowane środowisko programistyczne (IDE) zostało zaprojektowane z myślą o umożliwieniu przejścia z okna do okna i pliku do pliku na kilka różnych sposobów, w zależności od wymagań związanych z preferencjami lub projektem. Możesz wybrać przechodzenie między otwartymi plikami w edytorze lub przełączać się między wszystkimi aktywnymi oknami narzędzi w IDE. Możesz również przełączyć się bezpośrednio do dowolnego pliku otwartego w edytorze, niezależnie od kolejności, w której ostatnio uzyskano dostęp. Te funkcje mogą pomóc zwiększyć produktywność podczas pracy w środowisku IDE.

> [!NOTE]
> Opcje dostępne w oknach dialogowych oraz nazwy i lokalizacje poleceń menu, które są widoczne, mogą się różnić od tego, co opisano w pomocy, w zależności od ustawień aktywnych lub wydania. Ta strona pomocy została zaprojektowana z uwzględnieniem **ogólnych ustawień deweloperskich** . Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe
 Niemal każde polecenie menu w programie Visual Studio ma skrót klawiaturowy. Możesz również utworzyć własne skróty niestandardowe. Aby uzyskać więcej informacji, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigating-among-files-in-the-editor"></a>Nawigowanie między plikami w edytorze
 Do przechodzenia między plikami otwartymi w edytorze można używać kilku metod. Można przechodzić między plikami w zależności od kolejności, w której uzyskuje się do nich dostęp, za pomocą Nawigatora IDE można szybko znaleźć dowolny plik, który jest aktualnie otwarty, lub przypinać Ulubione pliki do karty, aby były zawsze widoczne.

 Przejdź wstecz i przejdź do następnego cyklu, korzystając z otwartych plików w edytorze, na podstawie kolejności, w której były dostępne, podobnie jak wstecz i w przód — dla historii wyświetlania w programie Microsoft Internet Explorer.

#### <a name="to-move-through-open-files-in-order-of-use"></a>Aby przejść przez otwarte pliki w kolejności użycia

- Aby uaktywnić otwarte dokumenty w kolejności, w jakiej były ostatnio dotknięciem, naciśnij klawisze CTRL + MINUS znak.

- Aby uaktywnić otwarte dokumenty w odwrotnej kolejności, naciśnij klawisze CTRL + SHIFT + ZNAK MINUS.

  > [!NOTE]
  > **Przejdź do tyłu** i **Przejdź do przodu** w menu **Widok** .

  Możesz również przełączyć się do określonego pliku otwartego w edytorze, niezależnie od tego, kiedy ostatnio uzyskano dostęp do pliku przy użyciu **Nawigatora IDE**, listy **aktywne pliki** w edytorze lub okna dialogowego **systemu Windows** .

  **Nawigator IDE** działa podobnie jak przełącznik aplikacji systemu Windows. Nie jest on dostępny w menu i można uzyskać do niego dostęp tylko przy użyciu klawiszy skrótów. Możesz użyć jednego z dwóch poleceń, aby uzyskać dostęp do **Nawigatora IDE** (pokazanego poniżej) w celu przechodzenia przez pliki w zależności od kolejności, w której chcesz przeprowadzić cykl.

  ![Nawigator środowiska IDE programu Visual Studio](../ide/media/vs2015-ide-navigator.png "VS2015_IDE_Navigator")

  `Window.PreviousDocumentWindowNav` umożliwia przechodzenie do ostatniego dostępu do pliku, a `Window.NextDocumentWindowNav` umożliwia przechodzenie w odwrotnej kolejności. Ogólne ustawienia projektowe przypisuje klawisze CTRL + SHIFT + TAB do `Window.PreviousDocumentWindowNav` i CTRL + TAB, aby `Window.NextDocumentWindowNav`.

> [!NOTE]
> Jeśli używana kombinacja ustawień nie ma już kombinacji klawiszy skrótu przypisanych do tego polecenia, możesz przypisać własne polecenie niestandardowe przy użyciu strony **Klawiatura** okna dialogowego **Opcje** . Aby uzyskać więcej informacji, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-specific-files-in-the-editor"></a>Aby przełączyć się do określonych plików w edytorze

- Naciśnij klawisze CTRL + TAB, aby wyświetlić **Nawigator IDE**. Przytrzymaj wciśnięty klawisz CTRL i naciskaj klawisz TAB do momentu wybrania pliku, do którego chcesz się przełączyć.

    > [!TIP]
    > Aby odwrócić kolejność, w której można przejść przez listę **aktywnych plików** , przytrzymaj wciśnięty klawisz Ctrl + Shift i naciśnij klawisz Tab.

     \- lub-

- W prawym górnym rogu edytora wybierz przycisk **aktywne pliki** , a następnie wybierz plik z listy, aby przełączyć się na.

     \- lub-

- Na pasku menu wybierz **okno**, **okna.**

- Z listy wybierz plik, który chcesz wyświetlić, a następnie wybierz pozycję **Aktywuj**.

## <a name="navigating-among-tool-windows-in-the-ide"></a>Nawigowanie między oknami narzędzi w środowisku IDE
 **Nawigator IDE** umożliwia również przechodzenie przez okna narzędzi, które zostały otwarte w środowisku IDE. Możesz użyć jednego z dwóch poleceń, aby uzyskać dostęp do **Nawigatora IDE** w celu przechodzenia przez okna narzędzi, w zależności od kolejności, w której chcesz przeprowadzić cykl. `Window.PreviousToolWindowNav` umożliwia przechodzenie do ostatniego dostępu do pliku, a `Window.NextToolWindowNav` umożliwia przechodzenie w odwrotnej kolejności. Ogólne ustawienia projektowe przypisuje SHIFT + ALT + F7 do `Window.PreviousDocumentWindowNav` i ALT + F7, aby `Window.NextDocumentWindowNav`.

> [!NOTE]
> Jeśli używana kombinacja ustawień nie ma już kombinacji klawiszy skrótu przypisanych do tego polecenia, możesz przypisać własne polecenie niestandardowe przy użyciu strony **Klawiatura** okna dialogowego **Opcje** . Aby uzyskać więcej informacji, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>Aby przełączyć się do określonego okna narzędzia w środowisku IDE

- Naciśnij klawisze ALT + F7, aby wyświetlić **Nawigator IDE**. Przytrzymaj klawisz ALT i naciśnij kilkakrotnie klawisz F7 do momentu wybrania okna, do którego chcesz się przełączyć.

    > [!TIP]
    > Aby odwrócić kolejność, w której można przejść przez **aktywną listę okien narzędzi** , przytrzymaj wciśnięty klawisz Shift + Alt i naciśnij klawisz F7.

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie](../ide/customizing-window-layouts-in-visual-studio.md) [domyślnych skrótów klawiaturowych](../ide/default-keyboard-shortcuts-in-visual-studio.md) układów okien
