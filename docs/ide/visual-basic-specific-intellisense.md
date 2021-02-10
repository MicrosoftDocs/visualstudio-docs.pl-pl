---
title: Visual Basic IntelliSense
description: Dowiedz się, jak używać funkcji IntelliSense oferowanych przez Edytor kodu źródłowego Visual Basic.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Basic.IntelliSense
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1420165c8ca574c74efe6911bb9c5635e729a260
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955557"
---
# <a name="intellisense-for-visual-basic-code-files"></a>Funkcja IntelliSense dla plików kodu Visual Basic

Edytor kodu źródłowego Visual Basic oferuje następujące funkcje IntelliSense:

## <a name="syntax-tips"></a>Wskazówki dotyczące składni

Wskazówki dotyczące składni wyświetlają składnię wpisywanej instrukcji. Jest to przydatne w przypadku instrukcji, takich jak [DECLARE](/dotnet/visual-basic/language-reference/statements/declare-statement).

## <a name="automatic-completion"></a>Automatyczne uzupełnianie

- Uzupełnianie dla różnych słów kluczowych

     Na przykład po wpisaniu `goto` i spacji funkcja IntelliSense wyświetla listę zdefiniowanych etykiet w menu rozwijanym. Inne obsługiwane słowa kluczowe obejmują `Exit` , `Implements` , `Option` , i `Declare` .

- Ukończenie `Enum` i `Boolean`

    Gdy instrukcja odwołuje się do elementu członkowskiego wyliczenia, IntelliSense wyświetla listę elementów członkowskich `Enum` . Gdy instrukcja będzie odnosić się do `Boolean` , IntelliSense wyświetla menu rozwijane true-false.

Zakończenie można wyłączyć domyślnie, usuwając zaznaczenie pozycji **autolista członków** z **ogólnej** strony właściwości w folderze **Visual Basic** .

Można ręcznie wywołać uzupełnianie, wywołując członków listy, kompletny wyraz lub **Alt** + **Strzałka w prawo**. Aby uzyskać więcej informacji, zobacz [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>Technologia IntelliSense w strefie

Funkcja IntelliSense w strefie pomaga Visual Basic deweloperom, którzy muszą wdrażać aplikacje w systemie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i są ograniczone do ustawień częściowej relacji zaufania. Ta funkcja:

- Umożliwia wybranie uprawnień, z którymi będzie uruchamiana aplikacja.

- Wyświetlaj interfejsy API w wybranej strefie jako dostępne w liście członków i wyświetlaj interfejsy API, które wymagają dodatkowych uprawnień jako niedostępne.

Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="filtered-completion-lists"></a>Filtrowane listy uzupełniania

W Visual Basic, listy uzupełniania IntelliSense mają dwie kontrolki tabulacji znajdujące się w dolnej części listy. Karta **Typowa** , która jest zaznaczona domyślnie, wyświetla elementy, które są najczęściej używane do ukończenia wykonywanej instrukcji. Na karcie **wszystkie** są wyświetlane wszystkie elementy, które są dostępne do automatycznego uzupełniania, łącznie z tymi, które są również na karcie **wspólne** .

## <a name="see-also"></a>Zobacz też

- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
