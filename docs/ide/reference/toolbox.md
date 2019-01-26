---
title: Okno przybornika
ms.date: 01/18/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: feddaf034394e7f27411562d85631b66de3b66e3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012615"
---
# <a name="toolbox"></a>Przybornik

**Przybornika** formantów, które można dodawać do projektów programu Visual Studio jest wyświetlana w oknie. Aby otworzyć przybornik, wybierz **przybornika** na **widoku** menu.

![Okno przybornika](media/toolbox.png)

Możesz przeciągać i upuszczać inne kontrolki na powierzchnię projektanta jest używany i zmień rozmiar i położenie kontrolki.

Przybornik pojawi się w połączeniu z projektanta widoków, takich jak Widok projektanta w pliku XAML. **Przybornik** wyświetla tylko te formanty, które mogą być używane w bieżącym projektancie. Możesz przeszukiwać **przybornika** Aby dodatkowo filtrować widoczne elementy.

> [!NOTE]
> W przypadku niektórych typów projektu **przybornika** mogą nie być wyświetlane wszystkie elementy.

Wersja programu .NET Framework, że projekt jest ukierunkowany również wpływa na zbiór kontrolek widocznych w przyborniku. Można ustawić projekt, aby docelowa była inna wersja programu .NET Framework ze stron właściwości projektu. Wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na pasku menu wybierz **projektu** > **projectname właściwości**. Na **aplikacji** kartę, należy użyć **platformę docelową** listy rozwijanej.

## <a name="manage-the-toolbox-window-and-its-controls"></a>Zarządzanie okno przybornika i jego formantów

Domyślnie **przybornika** jest zwinięta z lewej strony środowiska IDE programu Visual Studio i jest wyświetlany, gdy kursor zostanie przeniesiony nad nim. Możesz przypiąć **przybornika** (klikając **numeru Pin** ikonę na jego pasku narzędzi) tak, aby zostanie zamknięte po przeniesieniu kursora. Można również oddokować **przybornika** okna i przeciągnij w dowolne miejsce na ekranie. Można zadokować, oddokować i ukrywać **przybornika** kliknij prawym przyciskiem myszy jego narzędzi i wybierając jedną z opcji.

Możesz zmienić kolejność elementów w **przybornika** tab lub dodać niestandardowe karty i elementów za pomocą następujących poleceń w menu kliknij prawym przyciskiem myszy:

- **Zmień nazwę elementu** — zmienia nazwę wybranego elementu.

- **Pokaż wszystkie** — pokazuje wszystkie możliwe kontrole (nie tylko tych, które są stosowane do bieżącego projektanta).

- **Widok listy** — zawiera kontrolki w pionie listy. Jeśli nie jest zaznaczone, formanty są wyświetlane w poziomie.

- **Wybierz elementy** -otwiera **wybierz elementy przybornika** okno dialogowe, aby określić elementy, które pojawiają się w **przybornika**. Możesz pokazać lub ukryć element, zaznaczając lub usuwając zaznaczenie pola wyboru.

- **Sortowanie elementów alfabetycznie** — Sortuje elementy według nazwy.

- **Resetuj narzędzi** — przywraca domyślne **przybornika** ustawień i elementów.

- **Dodaj kartę** — dodaje nowy **przybornika** kartę.

- **Przenieś w górę** -Przesuwa wybrany element w górę.

- **Przenieś w dół** -Przenosi zaznaczony element w dół.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Tworzenie i rozprowadzanie formantów przybornika niestandardowego

Możesz utworzyć niestandardowe **przybornika** formantów, za pomocą szablonu projektu, który jest oparty na uruchamianie [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) lub na [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md). Można następnie dystrybuować niestandardową kontrolkę do członków zespołu lub opublikować go w sieci web za pomocą [Instalatora kontrolki przybornika](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="help-on-toolbox-tabs"></a>Pomoc na temat kart przybornika

Poniższe tematy zawierają więcej informacji na temat niektórych dostępnych **przybornika** karty:

- [Przybornik, karta Dane](../../ide/reference/toolbox-data-tab.md)
- [Przybornik, karta Składniki](../../ide/reference/toolbox-components-tab.md)
- [Przybornik, karta HTML](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Zobacz także

- [Wybierz elementy paska narzędzi, składniki WPF](choose-toolbox-items-wpf-components.md)