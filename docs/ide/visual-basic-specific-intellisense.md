---
title: Visual Basic IntelliSense
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Basic.IntelliSense
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 118de9ec05bcd5c56376376619bea0c5148d36ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594191"
---
# <a name="intellisense-for-visual-basic-code-files"></a>Pliki kodu IntelliSense for Visual Basic

Edytor kodu źródłowego języka Visual Basic oferuje następujące funkcje intellisense:

## <a name="syntax-tips"></a>Wskazówki dotyczące składni

Wskazówki składniowe wyświetlają składnię wpisywanych instrukcji. Jest to przydatne w przypadku instrukcji, takich jak [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).

## <a name="automatic-completion"></a>Automatyczne uzupełnianie

- Uzupełnianie różnych słów kluczowych

     Na przykład w `goto` przypadku wpisywanie i spacja w menu rozwijanym program IntelliSense wyświetli listę zdefiniowanych etykiet. Inne obsługiwane słowa `Exit`kluczowe `Implements` `Option`to `Declare`, , i .

- Zakończenie `Enum` i`Boolean`

    Gdy instrukcja będzie odnosić się do członka wyliczenia, IntelliSense `Enum`wyświetla listę członków . Gdy instrukcja będzie `Boolean`odnosić się do , IntelliSense wyświetla menu rozwijane true-false.

Zakończenie można domyślnie wyłączyć, odznaczając **elementy członkowskie listy auto** ze strony Właściwości **Ogólne** w folderze **Visual Basic.**

Zakończenie można wywołać ręcznie, wywołując listę członków, ukończoną lub **altową**+**strzałkę w prawo**. Aby uzyskać więcej informacji, zobacz [Korzystanie z programu IntelliSense](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>IntelliSense w strefie

Technologia IntelliSense w strefie pomaga deweloperom [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] języka Visual Basic, którzy muszą wdrażać aplikacje i są ograniczeni do ustawień częściowego zaufania. Ta funkcja:

- Umożliwia wybranie uprawnień, z których aplikacja będzie działać.

- Wyświetlaj interfejsy API w wybranej strefie jako dostępne w członkom listy i wyświetlaj interfejsy API, które wymagają dodatkowych uprawnień jako niedostępne.

Aby uzyskać więcej informacji, zobacz [Zabezpieczenia dostępu do kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="filtered-completion-lists"></a>Filtrowane listy uzupełnień

W języku Visual Basic listy uzupełniania IntelliSense mają dwa kontrolki kart znajdujące się u dołu list. Na karcie **Wspólne,** która jest zaznaczona domyślnie, są wyświetlane elementy, które są najczęściej używane do ukończenia instrukcji, które piszesz. Na karcie **Wszystkie** są wyświetlane wszystkie elementy, które są dostępne do automatycznego uzupełniania, w tym elementy, które są również na karcie **Wspólne.**

## <a name="see-also"></a>Zobacz też

- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
