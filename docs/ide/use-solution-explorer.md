---
title: Dowiedz się więcej o Eksplorator rozwiązań narzędzi
description: Dowiedz się, jak za pomocą Eksplorator rozwiązań narzędzi w programie Visual Studio tworzyć & zarządzać plikami, projektami i rozwiązaniami.
ms.date: 06/29/2021
ms.topic: conceptual
helpviewer_keywords:
- solution explorer [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 005e6fd3e49d3a3ab739740d2aaa1dd77df5e5df
ms.sourcegitcommit: 3d0f4930e0ccf49f89bbcfe12a949fbbf37aae07
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2021
ms.locfileid: "113131503"
---
# <a name="how-to-use-solution-explorer"></a>Jak używać Eksplorator rozwiązań

Za pomocą okna Eksplorator rozwiązań można tworzyć narzędzia & zarządzać rozwiązaniami i projektami oraz wyświetlać & interakcji z kodem. W tym artykule szczegółowo opisano opcje interfejsu użytkownika, które ci w tym pomogą.

> [!NOTE]
> Ten temat dotyczy tylko Visual Studio w systemie Windows.

## <a name="solution-explorer-tool-window"></a>Eksplorator rozwiązań narzędzia

Na początek przyjrzyjmy się oknie narzędzia Eksplorator rozwiązań w programie [Visual Studio IDE](../get-started/visual-studio-ide.md)z otwartym rozwiązaniem konsoli języka C#, które ma dwa projekty.

[![Okno Eksplorator rozwiązań narzędzi w Visual Studio.](media/solution-explorer-tool-window.png)](media/solution-explorer-tool-window.png#lightbox)

Okno narzędzi zawiera następujące elementy interfejsu użytkownika:

- **Pasek menu**, na którym można kontrolować sposób, w jaki pliki są wyświetlane
- **Pasek wyszukiwania**, na którym można wyszukiwać określone pliki i typy plików
- **Okno główne**, w którym można wyświetlać pliki, projekty i rozwiązania oraz & nimi
- **Węzeł rozwiązania**, w którym można zarządzać rozwiązaniami
- **Węzeł projektu**, w którym można zarządzać projektami
- **Węzeł zależności**, w którym można zarządzać rozwiązaniem & zależności projektu
- **Węzeł programu**, w którym można wyświetlać i edytować program lub aplikację (aplikację) oraz zarządzać nimi
- **[Karta zmian usługi Git,](../version-control/git-with-visual-studio.md?view=vs-2019&preserve-view=true#git-changes-window)** na której można używać usługi Git & GitHub Visual Studio celu współpracy nad projektami z zespołem

> [!TIP]
> Jeśli nie widzisz okna narzędzia Eksplorator rozwiązań, możesz otworzyć je na pasku menu programu Visual Studio, używając polecenia **View**  >  **Eksplorator rozwiązań** lub naciskając klawisze **Ctrl** + **Alt** + **L**.

## <a name="solution-explorer-menu-bar"></a>Eksplorator rozwiązań paska menu

Aby kontynuować, przyjrzyjmy się bliżej pasek Eksplorator rozwiązań menu.

![Pasek Eksplorator rozwiązań menu w Visual Studio.](media/solution-explorer-menu-bar.png)

Pasek menu zawiera następujące elementy interfejsu użytkownika od lewej do prawej:

- **Przycisk** Wstecz, aby przełączać się między wynikami wyszukiwania
- **Przycisk** Do przodu, aby przełączać się między wynikami wyszukiwania
- **Przycisk** Strona główna, aby powrócić do widoku domyślnego
- **Przycisk** Przełączania, aby przełączać się między rozwiązaniami i dostępnymi widokami
- **Przycisk Filtr oczekujących** zmian & menu rozwijanego, aby wyświetlić otwarte pliki lub pliki z oczekującymi zmianami
- **Przycisk Synchronizuj z** aktywnym dokumentem w celu zlokalizowania pliku w edytorze kodu
- **Przycisk** Odśwież, który jest wyświetlany tylko po wybraniu zależności, takiej jak funkcja lub pakiet
- **Przycisk Zwiń** wszystko, aby zwinąć widok pliku w oknie głównym
- **Przycisk Pokaż wszystkie** pliki, aby wyświetlić wszystkie pliki, w tym [niezaładowane projekty](filtered-solutions.md#toggle-unloaded-project-visibility)
- **Przycisk** Właściwości do wyświetlania i zmieniania ustawień określonych plików i składników
- **Podgląd przycisku Wybrane** elementy, aby wyświetlić wybrany plik lub składnik w edytorze kodu

### <a name="solution-explorer-right-click-context-menu"></a>Eksplorator rozwiązań menu kontekstowe dostępne po kliknięciu prawym przyciskiem myszy

W Eksplorator rozwiązań istnieje kilka właściwości pliku, z których można korzystać za pomocą menu kontekstowego dostępnego po kliknięciu prawym przyciskiem myszy. Aby uzyskać więcej informacji na temat opcji menu kontekstowego dostępnego po kliknięciu prawym przyciskiem myszy, zobacz stronę [Zarządzanie właściwościami projektu i](managing-project-and-solution-properties.md) rozwiązania.

## <a name="see-also"></a>Zobacz też

- [Co to są rozwiązania i projekty w Visual Studio?](solutions-and-projects-in-visual-studio.md)
- [Dostosowywanie układów okien w Visual Studio](customizing-window-layouts-in-visual-studio.md)
