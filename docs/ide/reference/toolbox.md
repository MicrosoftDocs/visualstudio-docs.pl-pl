---
title: Okno przybornika
ms.date: 01/18/2018
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
ms.openlocfilehash: c7decdb80cd06b1af3230b2926c4ebd37b48e422
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596453"
---
# <a name="toolbox"></a>Przybornik

Okno **Przybornik** wyświetla formanty, które można dodać do projektów programu Visual Studio. Aby otworzyć przybornik, wybierz **polecenie Przybornik** w menu **Widok.**

![Okno przybornika](media/toolbox.png)

Można przeciągać i upuszczać różne kontrolki na powierzchnię używanego projektanta oraz zmienić rozmiar i położenie formantów.

Przybornik jest wyświetlany w połączeniu z widokami projektanta, takimi jak widok projektanta pliku XAML. **Przybornik** wyświetla tylko te formanty, które mogą być używane w bieżącym projektancie. Można wyszukiwać w **przyborniku,** aby dodatkowo filtrować elementy, które się pojawią.

> [!NOTE]
> W przypadku niektórych typów projektów **przybornik** może nie wyświetlać żadnych elementów.

Wersja .NET, która jest przeznaczona dla projektu, wpływa również na zestaw formantów widocznych w przyborniku. W razie potrzeby można zmienić docelową wersję frameworka ze stron właściwości projektu. Wybierz węzeł projektu w **Eksploratorze rozwiązań,** a następnie na pasku menu **wybierz** > polecenie**Właściwości projektu**. Na **karcie Aplikacja** użyj listy rozwijanej **Struktura docelowa.**

## <a name="manage-the-toolbox-window-and-its-controls"></a>Zarządzanie oknem przybornika i jego formantami

Domyślnie **Przybornik** jest zwinięty wzdłuż lewej strony środowiska IDE programu Visual Studio i pojawia się, gdy kursor jest przenoszony nad nim. **Przybornik** można przypiąć (klikając ikonę **Przypnij** na pasku narzędzi), aby pozostał otwarty po przesunięciu kursora. Okno **przybornika** można również oddokować i przeciągnąć je w dowolne miejsce na ekranie. **Przybornik** można dokować, oddokować i ukryć, klikając prawym przyciskiem myszy jego pasek narzędzi i wybierając jedną z opcji.

Elementy można zmienić na karcie **Przybornik** lub dodać niestandardowe karty i elementy za pomocą następujących poleceń w menu prawym przyciskiem myszy:

- **Zmień nazwę elementu** — zmienia nazwę zaznaczonego elementu.

- **Pokaż wszystko** — pokazuje wszystkie możliwe formanty (nie tylko te, które mają zastosowanie do bieżącego projektanta).

- **Widok listy** — pokazuje formanty na liście pionowej. Jeśli ta zaznaczona jest niezaznaczona, formanty są wyświetlane poziomo.

- **Wybierz elementy** — otwiera okno dialogowe **Wybieranie elementów przybornika,** aby można było określić elementy wyświetlane w **przyborniku**. Element można wyświetlić lub ukryć, zaznaczając lub czyszcząc jego pole wyboru.

- **Sortuj elementy alfabetycznie** — sortuje elementy według nazwy.

- **Resetuj pasek narzędzi** — przywraca domyślne ustawienia i elementy **przybornika.**

- **Karta Dodawanie** — dodaje nową kartę **Przybornik.**

- **Przenieś w górę** - Przesuwa zaznaczony element w górę.

- **Przenieś w dół** - Przesuwa zaznaczony element w dół.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Tworzenie i rozpowszechnianie niestandardowych kontrolek przybornika

Niestandardowe kontrolki **przybornika** można utworzyć, zaczynając od szablonu projektu opartego na [Fundacji prezentacji systemu Windows](../../extensibility/creating-a-wpf-toolbox-control.md) lub w [formularzach systemu Windows](../../extensibility/creating-a-windows-forms-toolbox-control.md). Następnie można rozpowszechniać formant niestandardowy do członków zespołu lub publikować go w internecie za pomocą [Instalatora kontrolek przyborów](https://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx)narzędzi.

## <a name="help-on-toolbox-tabs"></a>Pomoc dotycząca kart Przybornika

Następujące tematy zawierają więcej informacji na temat niektórych dostępnych kart **przybornika:**

- [Przybornik, karta Dane](../../ide/reference/toolbox-data-tab.md)
- [Przybornik, karta Składniki](../../ide/reference/toolbox-components-tab.md)
- [Przybornik, karta HTML](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Zobacz też

- [Wybieranie elementów przybornika, składników WPF](choose-toolbox-items-wpf-components.md)
