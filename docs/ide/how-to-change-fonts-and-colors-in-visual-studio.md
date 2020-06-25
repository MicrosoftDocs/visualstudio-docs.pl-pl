---
title: Zmiana czcionek i kolorów
ms.date: 06/01/2020
ms.topic: how-to
helpviewer_keywords:
- Visual Studio, color themes
- color themes, Visual Studio
ms.assetid: 60d91ba1-244b-4c43-847f-60b744f1352a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0eb2373117b382cb19f374581ada45a5732b9c4c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284693"
---
# <a name="how-to-change-fonts-and-colors-in-visual-studio"></a>Instrukcje: zmiana czcionek i kolorów w programie Visual Studio

Czcionki i kolory w programie Visual Studio można zmienić na wiele sposobów. Na przykład można zmienić domyślny motyw niebieskiego koloru na ciemny (nazywany także "trybem ciemnym"). I można zmienić domyślną czcionkę i rozmiar tekstu na inną czcionkę i rozmiar.

## <a name="change-the-color-theme"></a>Zmień motyw kolorów

Poniżej przedstawiono sposób zmiany motywu kolorów ramki IDE i okien narzędzi w programie Visual Studio.

1. Na pasku menu wybierz **Narzędzia**  >  **Opcje**.

1. Na liście opcji wybierz pozycję **środowisko**  >  **Ogólne**.

1. Na liście **motyw kolorów** wybierz domyślny motyw **niebieski** , motyw **jasny** , motyw **ciemny** lub **niebieski (dodatkowy kontrast)** .

   ![Zrzut ekranu przedstawiający okno dialogowe Opcje umożliwiające zmianę motywu koloru](media/fonts-colors-theme.png "Zrzut ekranu przedstawiający okno dialogowe Opcje, za pomocą którego można zmienić motyw koloru")

    > [!NOTE]
    > Po zmianie motywu kolorów tekst w środowisku IDE przywraca domyślne lub wcześniej dostosowane czcionki i rozmiary dla tego motywu.

    :::moniker range="vs-2017"

    > [!TIP]
    > Możesz tworzyć i edytować własne motywy programu Visual Studio, instalując [Edytor motywów kolorów dla programu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor).

    :::moniker-end

    :::moniker range="vs-2019"

    > [!TIP]
    > Możesz tworzyć i edytować własne motywy programu Visual Studio, instalując [projektanta motywów kolorów programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner).

    :::moniker-end

## <a name="change-fonts-and-text-size"></a>Zmień czcionki i rozmiar tekstu

Możesz zmienić czcionkę i rozmiar tekstu dla wszystkich okienek i narzędzi IDE, lub tylko dla niektórych elementów systemu Windows lub tekstu. Możesz również zmienić czcionkę i rozmiar tekstu w edytorze.

### <a name="to-change-the-font-and-text-size-in-the-ide"></a>Aby zmienić czcionkę i rozmiar tekstu w IDE

1. Na pasku menu wybierz **Narzędzia**  >  **Opcje**.

1. Na liście Opcje wybierz pozycję **Environment**  >  **czcionki i kolory**środowiska.

1. Na liście **Pokaż ustawienia dla** wybierz **środowisko**.

   ![Zrzut ekranu przedstawiający okno dialogowe Opcje umożliwiające zmianę czcionek i kolorów w środowisku IDE](media/fonts-colors-environment.png "Zrzut ekranu przedstawiający okno dialogowe Opcje umożliwiające zmianę czcionek i kolorów w środowisku IDE")

    > [!NOTE]
    > Jeśli chcesz zmienić czcionkę tylko dla okien narzędzi, na liście **Pokaż ustawienia dla** wybierz opcję **wszystkie okna narzędzi tekstowych**.

1. Zmodyfikuj opcje **czcionki** i **rozmiaru** , aby zmienić czcionkę i rozmiar tekstu dla środowiska IDE.

1. Wybierz odpowiedni element w **pozycji elementy wyświetlane**, a następnie zmodyfikuj **pozycję Opcje pierwszego planu** i **tła** elementu.

### <a name="to-change-the-font-and-text-size-in-the-editor"></a>Aby zmienić czcionkę i rozmiar tekstu w edytorze

1. Na pasku menu wybierz **Narzędzia**  >  **Opcje**.

1. Na liście Opcje wybierz pozycję **Environment**  >  **czcionki i kolory**środowiska.

1. Na liście **Pokaż ustawienia dla** wybierz opcję **Edytor tekstu**.

   ![Zrzut ekranu przedstawiający okno dialogowe Opcje umożliwiające zmianę czcionek i kolorów w edytorze](media/fonts-colors-text-editor.png "Zrzut ekranu przedstawiający okno dialogowe Opcje umożliwiające zmianę czcionek i kolorów w edytorze")

1. Zmodyfikuj opcje **czcionki** i **rozmiaru** , aby zmienić czcionkę i rozmiar tekstu dla edytora.

1. Wybierz odpowiedni element w **pozycji elementy wyświetlane**, a następnie zmodyfikuj **pozycję Opcje pierwszego planu** i **tła** elementu.

Aby uzyskać więcej informacji, zobacz stronę [Zmień czcionki i kolory dla edytora](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md) .

## <a name="accessibility-options"></a>Opcje ułatwień dostępu

Jeśli napotkasz słabą wizję, są dostępne opcje motywu kolorów. Można użyć opcji dużego kontrastu dla *wszystkich* aplikacji i interfejsu użytkownika na komputerze lub opcji bardzo kontrast tylko dla programu Visual Studio.

### <a name="use-windows-high-contrast"></a>Użyj dużego kontrastu systemu Windows

Użyj jednej z następujących procedur, aby przełączyć opcję dużego kontrastu systemu Windows:

- W systemie Windows lub w dowolnej aplikacji firmy Microsoft naciśnij **Left Alt**klawisz + **SHIFT**w lewym klawiszem Alt + **PrtScn** .

- W systemie Windows wybierz pozycję **Rozpocznij**  >  **Ustawienia**  >  **łatwość dostępu**  >  **wysoki kontrast**.

    > [!WARNING]
    > Ustawienie dużego kontrastu systemu Windows ma wpływ na wszystkie aplikacje i interfejs użytkownika na komputerze.

### <a name="use-visual-studio-extra-contrast"></a>Użyj dodatkowego kontrastu programu Visual Studio

Poniższe procedury służą do przełączania opcji dodatkowego kontrastu programu Visual Studio:

1. Na pasku menu programu Visual Studio wybierz pozycję **Narzędzia**  >  **Opcje**, a następnie na liście Opcje wybierz pozycję **środowisko**  >  **Ogólne**.

1. Z listy rozwijanej **motyw kolorów** wybierz motyw **niebieski (dodatkowy kontrast)** , a następnie wybierz **OK**.

Aby dowiedzieć się więcej o innych dostępnych opcjach ułatwień dostępu programu Visual Studio, zobacz [funkcje ułatwień dostępu programu Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md) .

> [!TIP]
> Jeśli istnieje opcja dostępności dla kolorów lub czcionek, które mogą być przydatne, ale nie są obecnie dostępne w programie Visual Studio, daj nam znać, wybierając pozycję **Sugeruj funkcję** w [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/). Aby uzyskać więcej informacji na temat tego forum i sposobu jego działania, zobacz stronę [Sugeruj funkcję](../ide/suggest-a-feature.md) .

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat wszystkich elementów interfejsu użytkownika, dla których można zmienić czcionkę i schematy kolorów, zobacz stronę [okna dialogowego czcionki i kolory, środowisko, opcje](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) .

## <a name="see-also"></a>Zobacz też

- [Zmień czcionki i kolory dla edytora kodu](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)
- [Funkcje edytora kodu programu Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md)