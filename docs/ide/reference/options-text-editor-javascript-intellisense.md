---
title: Opcje, edytor tekstu, JavaScript, IntelliSense
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.IntelliSense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff36bf74249ec5266218060eedb879e4d796625c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938699"
---
# <a name="options-text-editor-javascript-intellisense"></a>Opcje, edytor tekstu, JavaScript, IntelliSense
Użyj **IntelliSense** strony **opcje** okno dialogowe, aby zmodyfikować ustawienia, które wpływają na działanie technologii IntelliSense dla języka JavaScript. Możesz uzyskać dostęp **IntelliSense** strony, wybierając **narzędzia** > **opcje** na pasku menu, a następnie rozwijając **edytora tekstów**  >  **JavaScript** > **IntelliSense.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

**IntelliSense** strona zawiera następujące sekcje:

## <a name="statement-completion"></a>Dokańczanie instrukcji
 Możesz użyć tych opcji do zmiany zachowania dokańczania instrukcji IntelliSense.

### <a name="uielement-list"></a>Lista elementów UI
 **Składać Tab lub Enter, aby zatwierdzić**

 Gdy to pole wyboru jest zaznaczone, Edytor kodu JavaScript dołącza instrukcje z elementami zaznaczonymi na liście dokańczania dopiero po wybraniu **kartę** lub **Enter** klucza. Usuń zaznaczenie tego pola wyboru, inne znaki — na przykład okres, przecinek, dwukropek, nawiasem otwierającym i otwierający nawias klamrowy ({}) — można także dołączyć instrukcje z wybranymi elementami.

## <a name="references"></a>Odwołania
 Można używać tych opcji, aby określać typy plików .js IntelliSense, które znajdują się w zakresie dla różnych typów projektów JavaScript. Odwołania IntelliSense są zazwyczaj używane do obsługi technologii IntelliSense dla obiektów globalnych. Można również użyć tej strony, aby ustawić kolejność ładowania skryptów, które muszą być ładowane w czasie wykonywania, oraz aby dodawać pliki rozszerzeń IntelliSense.

### <a name="uielement-list"></a>Lista elementów UI
 **Grupy odwołań**

 Ta opcja określa typ grupy odwołania. Obsługiwane są trzy grupy odwołań:

 Można używać wstępnie zdefiniowanych grup odwołań w celu określania, że konkretne pliki .js IntelliSense znajdują się w zakresie dla różnych projektów JavaScript. Dostępne są cztery grupy odniesień:

- Niejawna (Windows *wersji*), dla [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] aplikacji przy użyciu języka JavaScript. Pliki zawarte w tej grupie znajdują się w zakresie dla każdego pliku .js otwartego w edytorze kodu dla [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] aplikacji przy użyciu języka JavaScript.

- Niejawna (sieć Web) dla projektów HTML5. Pliki dołączone do tej grupy są w zakresie dla każdego pliku .js otwartego w Edytorze kodu dla tych typów projektu.

- Grupy odniesienia dedykowanych procesów roboczych dla roboczych HTML5 sieci web. Pliki określone w tej grupie są w zakresie plików .js, które mają wyraźne odniesienie do grupy odwołań wyspecjalizowanych funkcji roboczych.

- Ogólna dla innych typów projektów języka JavaScript.

**Dołączone pliki**

Ta opcja określa kolejność, w której pliki są ładowane do kontekstu usługi języka. Kolejność można skonfigurować za pomocą **Usuń**, **Przenieś w górę**, i **Przenieś w dół** przycisków. Aby technologia IntelliSense działała poprawnie, plik, który jest zależny od innego, musi być załadowany po pliku, od którego zależy.

> [!CAUTION]
> Jeśli obiekt jest zdefiniowany bezwarunkowo w dwóch lub więcej odwołań niejawnych, ostatnie odwołanie na tej liście będzie używane do określenia obiektu.


**Dodaj odwołanie do grupy**

Ta opcja umożliwia dodawanie dodatkowych plików .js IntelliSense przez przechodzenie do odpowiednich plików.

**Pobierz zdalne odwołania (np. http://) dla plików w projekcie plików pozostałych**

Gdy to pole wyboru jest zaznaczone, a jeśli masz plik JavaScript otwarty poza kontekstem projektu, Visual Studio pobierze zdalne pliki JavaScript, do których odwołuje się plik w celu przekazywania informacji IntelliSense. Jeśli ta opcja jest zaznaczona, pliki zostaną pobrane po włączeniu ich jako odwołania w pliku JavaScript.

> [!NOTE]
> Dla projektów sieci web domyślnie pobierane są pliki zdalne, do którego odwołuje się projekt.



## <a name="see-also"></a>Zobacz też

- [Funkcja IntelliSense dla języka JavaScript](../../ide/javascript-intellisense.md)