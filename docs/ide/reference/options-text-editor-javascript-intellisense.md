---
title: Opcje, edytor tekstu, JavaScript, IntelliSense
ms.date: 10/29/2018
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.IntelliSense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3d030e028332bd57afe66eee31c888713721212
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68605982"
---
# <a name="options-dialog-box-text-editor--javascript--intellisense"></a>Opcje — okno dialogowe: Edytor tekstu \> JavaScript \> IntelliSense

Na stronie **IntelliSense** okna dialogowego **Opcje** można modyfikować ustawienia, które mają wpływ na zachowanie funkcji IntelliSense dla języka JavaScript. Dostęp do strony **IntelliSense** można uzyskać, wybierając pozycję **Narzędzia**  >  **Options** na pasku menu, a następnie rozszerzając **Edytor tekstu**  >  **JavaScript/TypeScript**  >  **IntelliSense.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

Strona **IntelliSense** zawiera następujące sekcje:

## <a name="statement-completion"></a>Dokańczanie instrukcji

Możesz użyć tych opcji do zmiany zachowania dokańczania instrukcji IntelliSense.

### <a name="uielement-list"></a>Lista elementów UIElement

**Użyj klawisza TAB lub ENTER, aby zatwierdzić**

Po zaznaczeniu tego pola wyboru Edytor kodu JavaScript dołącza instrukcje do elementów wybranych na liście uzupełniania tylko po wybraniu **karty** lub klawisza **Enter** . Po usunięciu zaznaczenia tego pola wyboru inne znaki — takie jak kropka, przecinek, dwukropek, nawias otwierający i otwierające nawiasy klamrowe ({) — mogą również dołączać instrukcje do wybranych elementów.

## <a name="references"></a>Dokumentacja

Można używać tych opcji, aby określać typy plików .js IntelliSense, które znajdują się w zakresie dla różnych typów projektów JavaScript. Odwołania IntelliSense są zazwyczaj używane do obsługi technologii IntelliSense dla obiektów globalnych. Można również użyć tej strony, aby ustawić kolejność ładowania skryptów, które muszą być ładowane w czasie wykonywania, oraz aby dodawać pliki rozszerzeń IntelliSense.

### <a name="uielement-list"></a>Lista elementów UIElement

**Grupy odwołań**

Ta opcja określa typ grupy odwołania. Obsługiwane są trzy grupy odwołań:

Można używać wstępnie zdefiniowanych grup odwołań w celu określania, że konkretne pliki .js IntelliSense znajdują się w zakresie dla różnych projektów JavaScript. Dostępne są cztery grupy odniesień:

- Niejawne ( *wersja*systemu Windows) dla [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] aplikacji korzystających z języka JavaScript. Pliki dołączone do tej grupy są w zakresie dla każdego pliku. js otwartego w edytorze kodu dla [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] aplikacji korzystających z języka JavaScript.

- Niejawna (sieć Web) dla projektów HTML5. Pliki dołączone do tej grupy są w zakresie dla każdego pliku .js otwartego w Edytorze kodu dla tych typów projektu.

- Grupy odwołań dedykowanego procesu roboczego, dla procesów roboczych sieci Web HTML5. Pliki określone w tej grupie są w zakresie plików .js, które mają wyraźne odniesienie do grupy odwołań wyspecjalizowanych funkcji roboczych.

- Ogólna dla innych typów projektów języka JavaScript.

**Dołączone pliki**

Ta opcja określa kolejność, w której pliki są ładowane do kontekstu usługi języka. Kolejność można skonfigurować przy użyciu przycisków **Usuń**, Przenieś w **górę**i **Przenieś w dół** . Aby technologia IntelliSense działała poprawnie, plik, który jest zależny od innego, musi być załadowany po pliku, od którego zależy.

> [!CAUTION]
> Jeśli obiekt jest zdefiniowany bezwarunkowo w dwóch lub więcej odwołań niejawnych, ostatnie odwołanie na tej liście będzie używane do określenia obiektu.

**Dodawanie odwołania do grupy**

Ta opcja umożliwia dodawanie dodatkowych plików .js IntelliSense przez przechodzenie do odpowiednich plików.

**Pobierz zdalne odwołania (np. http://) dla plików w projekcie różne pliki**

Gdy to pole wyboru jest zaznaczone, a plik JavaScript jest otwarty poza kontekstem projektu, program Visual Studio pobierze zdalne pliki JavaScript, do których odwołuje się plik na potrzeby udostępniania informacji IntelliSense. Jeśli ta opcja jest zaznaczona, pliki zostaną pobrane po dodaniu ich jako odwołania w pliku JavaScript.

> [!NOTE]
> W przypadku projektów sieci Web pliki zdalne, do których odwołuje się projekt, są domyślnie pobierane.

## <a name="see-also"></a>Zobacz też

- [JavaScript IntelliSense](../../ide/javascript-intellisense.md)