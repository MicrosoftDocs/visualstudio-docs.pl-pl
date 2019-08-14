---
title: Projektuj Windows Forms aplikacje
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8280a60f1d265336d427079bdef6612b42ed4330
ms.sourcegitcommit: 6b0503ed8d25454d6e39a8e606910b3fa58cf1d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68984194"
---
# <a name="windows-forms-designer-overview"></a>Przegląd Projektant formularzy systemu Windows

Projektant formularzy systemu Windows w programie Visual Studio oferuje szybkie rozwiązanie programistyczne do tworzenia aplikacji opartych na Windows Forms. Projektant formularzy systemu Windows pozwala łatwo dodawać kontrolki do formularza, rozmieścić je i pisać kod dla swoich zdarzeń. Aby uzyskać więcej informacji na temat Windows Forms, zobacz [Windows Forms Omówienie](/dotnet/framework/winforms/windows-forms-overview).

## <a name="functionality"></a>Funkcja

Za pomocą projektanta można:

- Dodawanie składników, kontrolek danych lub formantów opartych na systemie Windows do formularza.

- Kliknij dwukrotnie formularz w Projektancie i napisz kod w `Load` zdarzeniu dla tego formularza lub kliknij dwukrotnie formant w formularzu i napisz kod dla zdarzenia domyślnego formantu.

- Edytuj właściwość Text kontrolki, zaznaczając kontrolkę i wpisując nazwę.

- Dostosuj położenie zaznaczonego formantu, przenosząc je za pomocą myszy lub klawiszy strzałek. Podobnie Dostosuj umieszczanie przy użyciu klawiszy CTRL i strzałki. Na koniec Dostosuj rozmiar formantu przy użyciu klawiszy Shift i strzałka.

- Zaznacz opcję wiele kontrolek, wybierając **klawisz Shift** lub **Ctrl** po kliknięciu przycisku. W przypadku używania pojedynczo **SHIFT**+ kliknięcie pierwszy wybrany formant jest formantem dominującym podczas wyrównywania lub manipulowania rozmiarem. W przypadku korzystania z **kombinacji klawiszy CTRL**i kliknięcia Ostatnia wybrana kontrolka ma wartość dominującą, więc formant dominujący zmienia się z każdą dodaną nową kontrolką. Alternatywnie można wybrać wiele kontrolek, przeciągając prostokąt zaznaczenia wokół kontrolek, które chcesz wybrać.

> [!NOTE]
> Użyj Projektant formularzy systemu Windows, a nie edytora zasobów, aby wprowadzić zmiany w pliku zasobów formularza ( *. resx*). Jeśli edytujesz plik resx oparty na formularzu, zobaczysz ostrzeżenie, że zmiany wprowadzone w edytorze zasobów mogą zostać utracone. Dzieje się tak, ponieważ Projektant formularzy systemu Windows generuje plik resx.

## <a name="see-also"></a>Zobacz także

- [Przegląd Windows Forms](/dotnet/framework/winforms/windows-forms-overview)
- [Kontrolki Windows Forms](/dotnet/framework/winforms/controls/)
- [Ułatwienia dostępu dla formantów Windows Forms](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [Dane wejściowe użytkownika w Windows Forms](/dotnet/framework/winforms/user-input-in-windows-forms)
- [Powiązanie danych w Windows Forms](/dotnet/framework/winforms/windows-forms-data-binding)
- [Ulepszanie aplikacji Windows Forms](/dotnet/framework/winforms/advanced/)