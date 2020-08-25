---
title: Ustawianie ciemnego motywu programu Visual Studio i Zmienianie kolorów tekstu
description: Dowiedz się, jak zmienić domyślny motyw kolorów programu Visual Studio do trybu ciemnego i zmienić kolory czcionki w edytorze kodu.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperfq1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d58bf3a00d3db208abfad23a67bd115914f14a15
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801402"
---
# <a name="how-to-personalize-the-visual-studio-ide-and-the-editor"></a>Instrukcje: personalizowanie środowiska IDE programu Visual Studio i edytora

W tym artykule z tego artykułu opisano dostosowywanie motywu kolorów programu Visual Studio z domyślnego motywu niebieskiego do ciemnego motywu. Następnie dostosujemy kolory dla dwóch różnych typów tekstu w edytorze kodu.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="set-the-color-theme-for-the-ide"></a>Ustawianie motywu kolorów dla środowiska IDE

Domyślny motyw kolorów dla interfejsu użytkownika programu Visual Studio jest nazywany **niebieską**. Zmieńmy ją na **ciemny**.

1. Na pasku menu, który jest wierszem menu, takim jak **plik** i **Edycja**, wybierz pozycję **Narzędzia**  >  **Opcje**.

1. Na stronie **Environment**  >  **Ogólne** opcje środowiska Zmień wybór **motywu koloru** na **ciemny**, a następnie wybierz przycisk **OK**.

   Motyw kolorów dla całego środowiska projektowego programu Visual Studio (IDE) zmienia się na **ciemny**.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 w motywie ciemnym](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019 w motywie ciemnym](media/vs-2019/dark-theme.png)

   ::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> Możesz zainstalować dodatkowe wstępnie zdefiniowane motywy, instalując **Edytor motywów kolorów programu Visual Studio** z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Po zainstalowaniu tego narzędzia dodatkowe Motywy kolorów są wyświetlane na liście rozwijanej **motywu kolorów** .

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Możesz tworzyć własne motywy, instalując **projektanta motywów kolorów programu Visual Studio** z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner).

::: moniker-end

## <a name="change-text-colors-in-the-editor"></a>Zmień kolory tekstu w edytorze

Teraz dostosowujemy niektóre kolory tekstu dla edytora. Najpierw utwórz nowy plik XML, aby wyświetlić domyślne kolory.

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **plik**.

1. W oknie dialogowym **nowy plik** w obszarze Kategoria **Ogólne** wybierz pozycję **plik XML**, a następnie wybierz polecenie **Otwórz**.

1. Wklej poniższy kod XML poniżej wiersza, który zawiera `<?xml version="1.0" encoding="utf-8"?>` .

   ```xml
   <Catalog>
     <Book id="bk101">
     <Author>Garghentini, Davide</Author>
     <Title>XML Developer's Guide</Title>
     <Genre>Computer</Genre>
     <Price>44.95</Price>
     <PublishDate>2000-10-01</PublishDate>
     <Description>
       An in-depth look at creating applications with XML.
     </Description>
   </Book>
   <Book id="bk102">
     <Author>Garcia, Debra</Author>
     <Title>Midnight Rain</Title>
     <Genre>Fantasy</Genre>
     <Price>5.95</Price>
     <PublishDate>2000-12-16</PublishDate>
     <Description>
       A former architect battles corporate zombies, an evil
       sorceress, and her own childhood to become queen of the world.
     </Description>
   </Book>
   </Catalog>
   ```

   Zwróć uwagę, że numery wierszy są kolorem turkusowym, a atrybuty XML (takie jak `id="bk101"` ) są jasnoniebieskim kolorem. Zmienimy kolor tekstu dla tych elementów.

   ![Kolory czcionki pliku XML](media/quickstart-personalize-xml-file.png)

1. Aby otworzyć okno dialogowe **Opcje** , wybierz opcje **Narzędzia**  >  **Options** z paska menu.

1. W obszarze **środowisko**wybierz kategorię **czcionki i kolory** .

   Zwróć uwagę, że tekst w obszarze **Pokaż ustawienia dla** mówi **Edytor tekstu** &mdash; to wszystko, czego szukamy. Rozwiń listę rozwijaną, aby wyświetlić obszerną listę miejsc, w których można dostosować czcionki i kolor tekstu.

1. Aby zmienić kolor tekstu numerów wierszy, na liście **Wyświetl elementy** wybierz pozycję **numer wiersza**. W polu **Plan elementu** wybierz pozycję **oliwa**.

   ![Okno dialogowe Opcje, czcionki i kolory — Kategoria](media/quickstart-personalize-line-number-color.png)

   Niektóre języki mają własne ustawienia czcionek i kolorów. Jeśli jesteś deweloperem języka C++ i chcesz zmienić kolor używany do korzystania z funkcji, na przykład możesz wyszukać **funkcje języka c++** na liście **elementy wyświetlania** .

1. Przed wyjściem z okna dialogowego Zmień także kolor atrybutów XML. Na liście **Wyświetl elementy** przewiń w dół do **atrybutu XML** i wybierz go. W polu **Plan elementu** wybierz pozycję **wapno**. Wybierz **przycisk OK** , aby zapisać wybrane opcje i zamknąć okno dialogowe.

   Numery wierszy są teraz kolorem oliwy, a atrybuty XML to jasne, ciemnozielone. Jeśli otworzysz inny typ pliku, na przykład plik kodu C++ lub C#, zobaczysz, że numery wierszy są również wyświetlane w kolorze oliwki.

   ![Plik XML z nowymi kolorami czcionki](media/quickstart-personalize-xml-file-new-colors.png)

Eksplorujemy kilka sposobów dostosowywania kolorów w programie Visual Studio. Mamy nadzieję, że zapoznajesz się z innymi opcjami dostosowywania w oknie dialogowym [**Opcje**](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) , aby naprawdę wprowadzić własne Visual Studio.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: zmienianie czcionek, kolorów i motywów w programie Visual Studio](../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
- [Instrukcje: zmiana wielkości liter w edytorze](../ide/how-to-change-text-case-in-the-editor.md)
- [Środowisko IDE programu Visual Studio — omówienie](../get-started/visual-studio-ide.md)
