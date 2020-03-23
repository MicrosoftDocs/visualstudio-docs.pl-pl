---
title: Projektowanie aplikacji formularzy systemu Windows
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 171cdffa569b342bdbc7dd0da1c8da218e1d622c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589893"
---
# <a name="windows-forms-designer-overview"></a>Projektant formularzy systemu Windows — omówienie

Projektant formularzy systemu Windows w programie Visual Studio zapewnia szybkie rozwiązanie programistyczne do tworzenia aplikacji opartych na formularzach systemu Windows. Program Windows Forms Designer umożliwia łatwe dodawanie formantów do formularza, rozmieszczanie ich i pisanie kodu dla ich zdarzeń. Aby uzyskać więcej informacji o formularzach systemu Windows, zobacz [Omówienie formularzy systemu Windows](/dotnet/framework/winforms/windows-forms-overview).

## <a name="functionality"></a>Funkcjonalność

Za pomocą projektanta można:

- Dodawanie składników, formantów danych lub formantów opartych na systemie Windows do formularza.

- Kliknij dwukrotnie formularz w projektancie i `Load` napisz kod w zdarzeniu dla tego formularza lub kliknij dwukrotnie formant w formularzu i napisz kod dla domyślnego zdarzenia formantu.

- Edytuj właściwość Text formantu, zaznaczając formant i wpisując nazwę.

- Dostosuj położenie wybranego formantu, przesuwając go za pomocą myszy lub klawiszy strzałek. Podobnie dostosuj położenie za pomocą klawiszy Ctrl i klawiszy strzałek. Na koniec dostosuj rozmiar formantu za pomocą klawiszy Shift i klawiszy strzałek.

- Zaznacz wiele kontrolek, zaznaczając klawisz **Shift** lub **Ctrl** podczas klikania. Podczas korzystania z funkcji **Shift**+click, pierwszy wybrany formant jest dominującą formantem podczas wyrównywania lub manipulowania rozmiarem. Podczas korzystania z **ctrl**+click, ostatni wybrany formant jest dominujący, więc dominujący formant zmienia się z każdym dodanym nowym formantu. Alternatywnie można zaznaczyć wiele formantów, przeciągając prostokąt zaznaczenia wokół formantów, które chcesz zaznaczyć.

> [!NOTE]
> Użyj projektanta formularzy systemu Windows, a nie Edytora zasobów, aby wprowadzić zmiany w pliku zasobu formularza (*.resx*). Jeśli edytujesz plik .resx oparty na formularzu, zobaczysz ostrzeżenie, że zmiany wprowadzone w Edytorze zasobów mogą zostać utracone. Dzieje się tak, ponieważ projektant formularzy systemu Windows generuje plik .resx.

## <a name="see-also"></a>Zobacz też

- [Omówienie formularzy systemu Windows](/dotnet/framework/winforms/windows-forms-overview)
- [formanty Formularzy systemu Windows](/dotnet/framework/winforms/controls/)
- [Dane wejściowe użytkownika w formularzach systemu Windows](/dotnet/framework/winforms/user-input-in-windows-forms)
- [Powiązanie danych w formularzach systemu Windows](/dotnet/framework/winforms/windows-forms-data-binding)
- [Ulepszanie aplikacji formularzy systemu Windows](/dotnet/framework/winforms/advanced/)
- <xref:System.Windows.Forms?displayProperty=fullName>Odwołanie do interfejsu API
