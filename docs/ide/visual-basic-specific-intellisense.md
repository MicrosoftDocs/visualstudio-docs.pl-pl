---
title: Visual Basic IntelliSense
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Basic.IntelliSense
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e01c255a7e89298a2a4bd7548bab0b548520ceed
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877893"
---
# <a name="intellisense-for-visual-basic-code-files"></a>Funkcja IntelliSense w plikach kodu języka Visual Basic

Edytor kodu źródłowego języka Visual Basic oferuje następujące funkcje IntelliSense:

## <a name="syntax-tips"></a>Porady dotyczące składni

Porady dotyczące składni Wyświetlanie składni instrukcji w miarę wpisywania. To jest przydatne w przypadku instrukcji takich jak [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).

## <a name="automatic-completion"></a>Automatyczne uzupełnianie

- Uzupełnianie na różnych słów kluczowych

     Na przykład, jeśli wpiszesz `goto` i spację, IntelliSense wyświetla listę etykiet zdefiniowanych w menu rozwijanym. Obejmują innych obsługiwanych słów kluczowych `Exit`, `Implements`, `Option`, i `Declare`.

- Uzupełnianie na `Enum` i `Boolean`

    Oświadczenie będzie odnosił się do elementu członkowskiego wyliczenia, IntelliSense wyświetla listę elementów członkowskich `Enum`. Kiedy oświadczenie będzie odnosił się do `Boolean`, IntelliSense wyświetla menu rozwijane PRAWDA / FAŁSZ.

Uzupełnianie można wyłączyć domyślnie, anulując **automatyczna lista członków** z **ogólne** — strona właściwości w **języka Visual Basic** folderu.

Można ręcznie wywołać uzupełnianie za pomocą listy członków, Dokończ wyraz lub **Alt**+**Strzałka w prawo**. Aby uzyskać więcej informacji, zobacz [IntelliSense użyj](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>Funkcja IntelliSense w strefie

Funkcja IntelliSense w strefie pomaga deweloperom języka Visual Basic, którzy muszą wdrażać aplikacje za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i są ograniczone do ustawienia częściowej relacji zaufania. Tej funkcji:

- Umożliwia wybranie uprawnień, których aplikacja będzie uruchamiana za pomocą.

- API wyświetlaną w wybranej strefie jako dostępne w listę elementów członkowskich, a następnie Wyświetl interfejsów API, które wymagają dodatkowych uprawnień jako niedostępny.

Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="filtered-completion-lists"></a>Filtrowane listy uzupełniania

W języku Visual Basic listy uzupełniania IntelliSense mają dwie kontrolki karty znajduje się w dolnej części listy. **Wspólnej** kartę, która jest domyślnie zaznaczone, wyświetla elementy, które są najczęściej używane do wykonania instrukcji, która jest pisana. **Wszystkich** karcie są wyświetlane wszystkie elementy, które są dostępne do automatycznego uzupełniania, łącznie z tymi, które są również na **wspólnej** kartę.

## <a name="see-also"></a>Zobacz także

- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)