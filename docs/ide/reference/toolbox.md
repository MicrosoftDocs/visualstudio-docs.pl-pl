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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5311c9a910c3140d5a5053a42befe7ed7f5b1278
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651122"
---
# <a name="toolbox"></a>Przybornik

Okno **przybornika** wyświetla kontrolki, które można dodać do projektów programu Visual Studio. Aby otworzyć przybornik, wybierz **Przybornik** w menu **Widok** .

![Okno przybornika](media/toolbox.png)

Możesz przeciągać i upuszczać różne kontrolki na powierzchnię projektanta, którego używasz, i zmieniać rozmiar i położenie formantów.

Przybornik pojawia się w połączeniu z widokami projektanta, takimi jak widok projektanta pliku XAML. W **przyborniku** są wyświetlane tylko te formanty, które mogą być używane w bieżącym projektancie. Możesz przeszukiwać w **przyborniku** , aby bardziej odfiltrować elementy, które są wyświetlane.

> [!NOTE]
> W przypadku niektórych typów projektów **Przybornik** nie może pokazywać żadnych elementów.

Wersja platformy .NET przeznaczona dla projektu ma także wpływ na zestaw kontrolek widocznych w przyborniku. W razie potrzeby można zmienić wersję platformy docelowej ze stron właściwości projektu. Wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie na pasku menu wybierz **projekt**  > **Właściwości ProjectName**. Na karcie **aplikacja** Użyj listy rozwijanej **platforma docelowa** .

## <a name="manage-the-toolbox-window-and-its-controls"></a>Zarządzanie oknem przybornika i jego kontrolkami

Domyślnie **Przybornik** jest zwinięty wzdłuż lewej krawędzi środowiska IDE programu Visual Studio i pojawia się po przesunięciu kursora nad nim. Możesz przypiąć **Przybornik** (klikając ikonę **pinezki** na jego pasku narzędzi), tak aby pozostała otwarta po przesunięciu kursora. Możesz również oddokować okno **przybornika** i przeciągnąć je w dowolne miejsce na ekranie. **Przybornik** można zadokować, oddokować i ukryć, klikając go prawym przyciskiem myszy i wybierając jedną z opcji.

Można zmienić rozmieszczenie elementów na karcie **przybornika** lub dodać niestandardowe karty i elementy przy użyciu następujących poleceń w menu po kliknięciu prawym przyciskiem myszy:

- **Zmień nazwę elementu** — zmienia nazwę wybranego elementu.

- **Pokaż wszystko** — pokazuje wszystkie możliwe kontrolki (nie tylko te, które mają zastosowanie do bieżącego projektanta).

- **Widok listy** — pokazuje kontrolki na liście pionowej. W przypadku usunięcia zaznaczenia kontrolki są wyświetlane w poziomie.

- **Wybierz elementy** — otwiera okno dialogowe **Wybierz elementy przybornika** , aby można było określić elementy, które są wyświetlane w **przyborniku**. Możesz pokazać lub ukryć element, zaznaczając lub usuwając zaznaczenie pola wyboru.

- **Sortuj elementy alfabetycznie** — sortuje elementy według nazwy.

- **Resetuj pasek narzędzi** — przywraca domyślne ustawienia i elementy **przybornika** .

- **Dodaj kartę** — dodaje nową kartę **przybornika** .

- **Przenieś w górę** — przenosi zaznaczony element w górę.

- **Przenieś w dół** — przenosi zaznaczony element w dół.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Tworzenie i dystrybuowanie niestandardowych kontrolek przybornika

Można utworzyć niestandardowe kontrolki **przybornika** , rozpoczynając od szablonu projektu opartego na [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) lub [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md). Następnie można dystrybuować kontrolkę niestandardową do członków zespołu lub publikować ją w sieci Web za pomocą [Instalatora formantów przybornika](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="help-on-toolbox-tabs"></a>Pomoc na temat kart przybornika

Poniższe tematy zawierają więcej informacji na temat niektórych dostępnych kart **przybornika** :

- [Przybornik, karta Dane](../../ide/reference/toolbox-data-tab.md)
- [Przybornik, karta Składniki](../../ide/reference/toolbox-components-tab.md)
- [Przybornik, karta HTML](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Zobacz także

- [Wybierz elementy przybornika, składniki WPF](choose-toolbox-items-wpf-components.md)