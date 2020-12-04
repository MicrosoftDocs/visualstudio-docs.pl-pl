---
title: Okno przybornika
description: Dowiedz się więcej na temat okna przybornika i sposobu wyświetlania formantów, które można dodać do projektów programu Visual Studio.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 905288d4a580f5633196273666fbea3954d1767c
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560281"
---
# <a name="toolbox"></a>Przybornik

Okno **przybornika** wyświetla kontrolki, które można dodać do projektów programu Visual Studio. Aby otworzyć **Przybornik**, wybierz pozycję **Wyświetl**  >  **Przybornik** z paska menu lub naciśnij **klawisze CTRL** + **Alt** + **X**.

![Zrzut ekranu przedstawiający okno przybornika z opcjami w sekcji kontenery.](media/vs-2019/toolbox.png "Zrzut ekranu przedstawiający okno przybornika")

Możesz przeciągać i upuszczać różne kontrolki na powierzchnię projektanta, którego używasz, i zmieniać rozmiar i położenie formantów.

Przybornik pojawia się w połączeniu z widokami projektanta, takimi jak widok projektanta pliku XAML lub projekt aplikacji Windows Forms. W **przyborniku** są wyświetlane tylko te formanty, które mogą być używane w bieżącym projektancie. Możesz przeszukiwać w **przyborniku** , aby bardziej odfiltrować elementy, które są wyświetlane.

> [!NOTE]
> W przypadku niektórych typów projektów **Przybornik** nie może pokazywać żadnych elementów.

Wersja platformy .NET przeznaczona dla projektu ma także wpływ na zestaw kontrolek widocznych w przyborniku. W razie potrzeby można zmienić wersję platformy docelowej ze stron właściwości projektu. Wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie na pasku menu wybierz polecenie **Project**  >  **ProjectName Properties**. Na karcie **aplikacja** Użyj listy rozwijanej **platforma docelowa** .

::: moniker range="vs-2019"

![Zrzut ekranu przedstawiający okno dialogowe aplikacji z opcjami na liście rozwijanej platforma docelowa.](media/vs-2019/toolbox-change-dotnet-version.png "Zrzut ekranu przedstawiający okno dialogowe, w którym można zmienić wersję platformy .NET")

::: moniker-end

## <a name="manage-the-toolbox-window-and-its-controls"></a>Zarządzanie oknem przybornika i jego kontrolkami

Domyślnie **Przybornik** jest zwinięty wzdłuż lewej strony środowiska IDE programu Visual Studio i pojawia się po przesunięciu kursora nad nim. Możesz przypiąć **Przybornik** (klikając ikonę **pinezki** na jego pasku narzędzi), tak aby pozostała otwarta po przesunięciu kursora. Możesz również oddokować okno **przybornika** i przeciągnąć je w dowolne miejsce na ekranie. **Przybornik** można zadokować, oddokować i ukryć, klikając go prawym przyciskiem myszy i wybierając jedną z opcji.

> [!TIP]
> Jeśli Przybornik nie jest już wyświetlany jako zwinięty wzdłuż lewej strony środowiska IDE programu Visual Studio, możesz dodać go ponownie, wybierając pozycję **okno**  >  **Ustawienia układ okna** z paska menu.

Można zmienić rozmieszczenie elementów na karcie **przybornika** lub dodać niestandardowe karty i elementy przy użyciu następujących poleceń w menu kontekstowym po kliknięciu prawym przyciskiem myszy:

- **Zmień nazwę elementu** — zmienia nazwę wybranego elementu.

- **Widok listy** — pokazuje kontrolki na liście pionowej. W przypadku usunięcia zaznaczenia kontrolki są wyświetlane w poziomie.

- **Pokaż wszystko** — pokazuje wszystkie możliwe kontrolki (nie tylko te, które mają zastosowanie do bieżącego projektanta).

- **Wybierz elementy** — otwiera okno dialogowe **Wybierz elementy przybornika** , aby można było określić elementy, które są wyświetlane w **przyborniku**. Możesz pokazać lub ukryć element, zaznaczając lub usuwając zaznaczenie pola wyboru.

- **Sortuj elementy alfabetycznie** — sortuje elementy według nazwy.

- **Resetuj pasek narzędzi** — przywraca domyślne ustawienia i elementy **przybornika** .

- **Dodaj kartę** — dodaje nową kartę **przybornika** .

- **Przenieś w górę** — przenosi zaznaczony element w górę.

- **Przenieś w dół** — przenosi zaznaczony element w dół.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Tworzenie i dystrybuowanie niestandardowych kontrolek przybornika

Można utworzyć niestandardowe kontrolki **przybornika** , rozpoczynając od szablonu projektu opartego na [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) lub [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md). Następnie można dystrybuować kontrolkę niestandardową do członków zespołu lub publikować ją w sieci Web za pomocą [Instalatora formantów przybornika](https://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="next-steps"></a>Następne kroki

Zapoznania następujące linki, aby dowiedzieć się więcej na temat niektórych dostępnych kart **przybornika** :

- [Przybornik, karta Dane](../../ide/reference/toolbox-data-tab.md)
- [Przybornik, karta Składniki](../../ide/reference/toolbox-components-tab.md)
- [Przybornik, karta HTML](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Zobacz także

- [Wybieranie elementów przybornika, składniki WPF](choose-toolbox-items-wpf-components.md)
