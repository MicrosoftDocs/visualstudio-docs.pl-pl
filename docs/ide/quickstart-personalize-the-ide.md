---
title: Zestaw motyw kolorów i czcionek
ms.date: 11/20/2017
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 504b33ee897ac59b7fe55625a67a01b8dca8ff32
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57869334"
---
# <a name="quickstart-personalize-the-visual-studio-ide-and-editor"></a>Szybki start: Personalizowanie programu Visual Studio IDE i edytorem

W tym przewodniku Szybki Start 5 – 10 minut firma Microsoft będzie dostosować motyw kolorów programu Visual Studio, wybierając ciemnego motywu. Firma Microsoft będzie również dostosować kolory dla dwóch różnych typów tekstu w edytorze tekstów.

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

## <a name="set-the-color-theme"></a>Ustaw motyw kolorów

Motyw domyślny dla interfejsu użytkownika programu Visual Studio jest nazywany **niebieski**. Zmieńmy go do **ciemny**.

1. Na pasku menu, czyli wiersz menu, takich jak **pliku** i **Edytuj**, wybierz **narzędzia** > **opcje**.

1. Na **środowiska** > **ogólne** Strona opcji, zmień **motyw kolorów** wyboru, aby **ciemny**, a następnie wybierz pozycję **OK**.

   Motyw kolorów dla całego programu Visual Studio środowiska programistycznego (IDE) jest zmieniana na **ciemny**.

   ![W PORÓWNANIU z motywu ciemny](media/quickstart-personalize-dark-theme.png)

> [!TIP]
> Można zainstalować dodatkowe predefiniowane motywy, instalując **Edytor motywów kolorystycznych programu Visual Studio** z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Po zainstalowaniu tego narzędzia, motywy kolorów dodatkowe są wyświetlane w **motyw kolorów** listy rozwijanej.

## <a name="change-text-color"></a>Zmienianie koloru tekstu

Firma Microsoft będzie teraz dostosować niektóre kolory tekstu edytora. Najpierw utwórz nowy plik XML, aby wyświetlić domyślne kolory.

1. Na pasku menu wybierz **pliku** > **New** > **pliku**.

1. W **nowy plik** okno dialogowe, w obszarze **ogólne** kategorii, wybierz **pliku XML**, a następnie wybierz **Otwórz**.

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

   Zauważ, że numery wierszy są kolor niebieski turkusowy i atrybutów XML (takie jak `id="bk101"`) są jasny kolor niebieski. Zamierzamy zmianę koloru tekstu dla tych elementów.

   ![Kolory czcionek w pliku XML](media/quickstart-personalize-xml-file.png)

1. Aby otworzyć **opcje** okna dialogowego wybierz **narzędzia** > **opcje** z paska menu.

1. W obszarze **środowiska**, wybierz **czcionki i kolory** kategorii.

   Należy zauważyć, że tekst w polu **Pokaż ustawienia dla** mówi **Edytor tekstu**&mdash;jest to, co chcemy zrobić. Rozwiń listy rozwijanej, po prostu, aby zobaczyć obszerną listę miejsca, w którym można dostosowywać czcionek i kolorów tekstu.

1. Aby zmienić kolor tekstu numery wiersza, w **wyświetlania elementów** wybierz **numer wiersza**. W **pierwszy plan elementu** wybierz **oliwek**.

   ![Okno dialogowe opcji, czcionki i kolory kategorii](media/quickstart-personalize-line-number-color.png)

   Niektóre języki mają swoje własne szczególne ustawienia czcionek i kolorów. Jeśli jesteś programistą języka C++ i chcesz zmienić kolor używany na potrzeby funkcji, na przykład, można wyszukać **funkcji języka C++** w **wyświetlania elementów** listy.

1. Zanim firma wyjście z okna dialogowego, również zmienimy kolor atrybutów XML. W **wyświetlania elementów** listy, przewiń w dół do **atrybutu XML** i wybierz ją. W **pierwszy plan elementu** wybierz **wapna**. Wybierz **OK** naszej opcji Zapisz i zamknij okno dialogowe.

   Numery wierszy są teraz oliwek kolorów i atrybutów XML jasny, Limonowozielony. Jeśli otworzysz plik innego typu, takich jak plik kodu C++ lub C#, zobaczysz, że numery wierszy są również wyświetlane w kolorze oliwek.

   ![Plik XML z nowych kolorów czcionki](media/quickstart-personalize-xml-file-new-colors.png)

Rozważyliśmy dostosowywanie kolorów w programie Visual Studio na kilka sposobów. Mamy nadzieję, że dowiesz się o innych opcji dostosowywania w **opcje** okno dialogowe, aby naprawdę dostosować Visual Studio do własnych potrzeb.

## <a name="see-also"></a>Zobacz także

- [Dopasowywanie edytora](../ide/customizing-the-editor.md)
- [Środowisko IDE programu Visual Studio — przegląd](../get-started/visual-studio-ide.md)