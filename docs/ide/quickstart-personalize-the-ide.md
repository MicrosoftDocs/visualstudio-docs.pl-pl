---
title: Ustawianie motywu kolorów i czcionek
ms.date: 03/23/2020
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c0b7b4e439f33e4e2eed8609d7e85e098068aea
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233153"
---
# <a name="personalize-the-visual-studio-ide-and-editor"></a>Personalizowanie ide i edytora programu Visual Studio

W tym samouczku 5-10 minut dostosujemy motyw kolorów programu Visual Studio, wybierając ciemny motyw. Dostosujemy również kolory dla dwóch różnych typów tekstu w edytorze tekstu.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="set-the-color-theme"></a>Ustawianie motywu kolorów

Domyślny motyw kolorów interfejsu użytkownika programu Visual Studio nosi nazwę **Niebieski**. Zmieńmy go na **Dark**.

1. Na pasku menu, który jest wierszem menu, takich jak **Plik** i **Edytuj,** wybierz opcję**Opcje** **narzędzi** > .

1. Na stronie Opcje**ogólne** **środowiska** > zmień wybór **motywu Kolor** na **Ciemny**, a następnie wybierz przycisk **OK**.

   Motyw kolorów dla całego środowiska programistycznego programu Visual Studio (IDE) zmienia się na **Ciemny**.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 w ciemnym motywie](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019 w ciemnym motywie](media/vs-2019/dark-theme.png)

   ::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> Dodatkowe wstępnie zdefiniowane motywy można zainstalować, instalując **Edytor motywów kolorów programu Visual Studio** w portalu Visual Studio [Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Po zainstalowaniu tego narzędzia na liście rozwijanej **Motyw kolorów** pojawią się dodatkowe motywy kolorystykowe.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Własne motywy można utworzyć, instalując **projektanta motywów kolorowych programu Visual Studio** w [portalu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner).

::: moniker-end

## <a name="change-text-color"></a>Zmienianie koloru tekstu

Teraz dostosujemy niektóre kolory tekstu dla edytora. Najpierw utwórzmy nowy plik XML, aby wyświetlić kolory domyślne.

1. Na pasku menu wybierz pozycję **Plik** > **nowy** > **plik**.

1. W oknie dialogowym **Nowy plik** w kategorii **Ogólne** wybierz pozycję **Plik XML**, a następnie wybierz pozycję **Otwórz**.

1. Wklej następujący kod XML poniżej wiersza, który zawiera `<?xml version="1.0" encoding="utf-8"?>`.

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

   Należy zauważyć, że numery linii są turkusowe-niebieski kolor, a `id="bk101"`atrybuty XML (takie jak ) są jasnoniebieski kolor. Zmienimy kolor tekstu tych elementów.

   ![Kolory czcionek pliku XML](media/quickstart-personalize-xml-file.png)

1. Aby otworzyć okno dialogowe **Opcje,** wybierz pozycję**Opcje** **narzędzi** > z paska menu.

1. W obszarze **Środowisko**wybierz kategorię **Czcionki i kolory.**

   Należy zauważyć, że tekst w obszarze **Pokaż ustawienia dla** mówi Edytor&mdash; **tekstu**jest to, co chcemy. Rozwiń listę rozwijaną, aby wyświetlić obszerną listę miejsc, w których można dostosować czcionki i kolor tekstu.

1. Aby zmienić kolor tekstu numerów wierszy, na liście **Elementy wyświetlane** wybierz pozycję **Numer wiersza**. W polu **Pierwszy plan pozycji** wybierz pozycję **Oliwka**.

   ![Okno dialogowe Opcje, Czcionki i kolory](media/quickstart-personalize-line-number-color.png)

   Niektóre języki mają własne ustawienia czcionek i kolorów. Jeśli jesteś deweloperem języka C++ i chcesz zmienić kolor używany dla funkcji, na przykład, możesz wyszukać **funkcje języka C++** na liście **Elementy wyświetlane.**

1. Zanim wyjdziemy z okna dialogowego, zmieńmy również kolor atrybutów XML. Na liście **Elementy wyświetlane** przewiń w dół do **atrybutu XML** i wybierz go. W polu **Pierwszy plan pozycji** wybierz pozycję **Lime**. Wybierz **przycisk OK,** aby zapisać nasze wybory i zamknąć okno dialogowe.

   Numery linii są teraz kolorem oliwkowym, a atrybuty XML są jasne, limonkowe. Jeśli otworzysz inny typ pliku, taki jak plik kodu C++ lub C#, zobaczysz, że numery wierszy są również wyświetlane w kolorze oliwkowym.

   ![Plik XML z nowymi kolorami czcionek](media/quickstart-personalize-xml-file-new-colors.png)

Zbadaliśmy tylko kilka sposobów dostosowywania kolorów w programie Visual Studio. Mamy nadzieję, że poznasz inne opcje dostosowywania w oknie dialogowym **Opcje,** aby naprawdę uczynić program Visual Studio swoim własnym.

## <a name="see-also"></a>Zobacz też

- [Dopasowywanie edytora](../ide/how-to-change-text-case-in-the-editor.md)
- [Środowisko IDE programu Visual Studio — przegląd](../get-started/visual-studio-ide.md)
