---
title: Okno przybornika
description: Dowiedz się więcej na temat okna przybornika i sposobu, w jaki są wyświetlane kontrolki, które można dodać do Visual Studio projektach.
ms.custom: SEO-VS-2020
ms.date: 06/01/2020
ms.topic: reference
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1a926084ccd8b1aafabb50f5a93f3f46d77bc6d4
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308470"
---
# <a name="toolbox"></a>Przybornik

W **oknie przybornika** są wyświetlane kontrolki, które można dodać do Visual Studio projektów. Aby otworzyć **przybornik,** wybierz **pozycję View**  >  **Toolbox** (Wyświetl przybornik) na pasku menu lub naciśnij **klawisze Ctrl** + **Alt** + **X**.

![Zrzut ekranu przedstawiający okno przybornika z opcjami w sekcji Kontenery.](media/vs-2019/toolbox.png "Zrzut ekranu przedstawiający okno przybornika")

Możesz przeciągać i upuszczać różne kontrolki na powierzchnię projektanta, z których korzystasz, oraz zmieniać rozmiar i położenie kontrolek.

Przybornik jest wyświetlany w połączeniu z widokami projektanta, takimi jak widok projektanta pliku XAML lub Windows Forms aplikacji. **Przybornik** wyświetla tylko te kontrolki, które mogą być używane w bieżącym projektancie. Możesz wyszukiwać w **przyborniku,** aby dalej filtrować wyświetlane elementy.

> [!NOTE]
> W przypadku niektórych typów projektów **przybornik** może nie pokazywać żadnych elementów.

Wersja .NET, dla których jest przeznaczony projekt, ma również wpływ na zestaw kontrolek widocznych w przyborniku. W razie potrzeby można zmienić wersję struktury docelowej na stronach właściwości projektu. Wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie na pasku menu wybierz pozycję   >  **Project projectname Properties (Właściwości nazwy projektu).** Na karcie **Aplikacja** użyj listy **rozwijanej Docelowa** framework.

::: moniker range=">=vs-2019"

![Zrzut ekranu przedstawiający okno dialogowe Aplikacja z opcjami na liście rozwijanej Docelowa framework.](media/vs-2019/toolbox-change-dotnet-version.png "Zrzut ekranu przedstawiający okno dialogowe, w którym można zmienić wersję programu .NET")

::: moniker-end

## <a name="manage-the-toolbox-window-and-its-controls"></a>Zarządzanie oknem przybornika i jego kontrolkami

Domyślnie **przybornik jest** zwinięty wzdłuż lewej Visual Studio IDE i pojawia się po przesunięciu kursora na niego. Przybornik **można przypiąć** (klikając ikonę Przypnij na jego pasku narzędzi), aby pozostał on otwarty podczas przesuwania kursora.  Możesz również oddokować okno **przybornika** i przeciągnąć je w dowolne miejsce na ekranie. Przybornik można zadokować, oddokować i ukryć **przybornik,** klikając prawym przyciskiem myszy jego pasek narzędzi i wybierając jedną z opcji.

> [!TIP]
> Jeśli przybornik nie jest już wyświetlany jako zwinięty wzdłuż lewej strony środowiska IDE Visual Studio, możesz dodać go ponownie, wybierając pozycję Układ okna resetowania okna na  >   pasku menu.

Elementy na karcie Przybornik  można zmienić lub dodać niestandardowe karty i elementy przy użyciu następujących poleceń w menu kontekstowym dostępnym po kliknięciu prawym przyciskiem myszy:

- **Zmień nazwę elementu** — zmienia nazwę wybranego elementu.

- **Widok listy** — pokazuje kontrolki na pionowej liście. Jeśli pole wyboru nie jest zaznaczone, kontrolki są wyświetlane w poziomie.

- **Pokaż wszystko** — pokazuje wszystkie możliwe kontrolki (nie tylko te, które mają zastosowanie do bieżącego projektanta).

- **Wybierz elementy** — otwiera **okno dialogowe Wybieranie** elementów przybornika, aby można było określić elementy wyświetlane w przyborniku .  Możesz pokazać lub ukryć element, zaznaczając lub usuwając jego pole wyboru.

- **Sortuj elementy alfabetycznie** — sortuje elementy według nazwy.

- **Resetuj** pasek narzędzi — przywraca domyślne ustawienia **i** elementy przybornika.

- **Dodaj kartę** — dodaje nową **kartę Przybornik.**

- **Przenieś w** górę — przenosi wybrany element w górę.

- **Przenieś w dół** — przenosi zaznaczony element w dół.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Tworzenie i dystrybuowanie niestandardowych kontrolek przybornika

Możesz tworzyć niestandardowe **kontrolki** przybornika, zaczynając od szablonu projektu opartego [na](../../extensibility/creating-a-wpf-toolbox-control.md) Windows Presentation Foundation lub na [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md). Następnie możesz rozpowszechnić kontrolkę niestandardową do swoich członków zespołu lub opublikować ją w Internecie za pomocą Instalatora [kontrolek przybornika](https://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o niektórych dostępnych kartach przybornika, zapoznaj się z następującymi **linkami:**

- [Przybornik, karta Dane](../../ide/reference/toolbox-data-tab.md)
- [Przybornik, karta Składniki](../../ide/reference/toolbox-components-tab.md)
- [Przybornik, karta HTML](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Zobacz też

- [Wybieranie elementów przybornika, składniki WPF](choose-toolbox-items-wpf-components.md)
