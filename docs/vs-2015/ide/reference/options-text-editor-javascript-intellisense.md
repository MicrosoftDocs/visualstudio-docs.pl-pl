---
title: Opcje, Edytor tekstu, JavaScript, IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b0d9dec8ec9b3eb8860bb8b3a4ed8f7347aa54d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662234"
---
# <a name="options-text-editor-javascript-intellisense"></a>Opcje, edytor tekstu, JavaScript, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Na stronie **IntelliSense** okna dialogowego **Opcje** można modyfikować ustawienia, które mają wpływ na zachowanie funkcji IntelliSense dla języka JavaScript. Dostęp do strony **IntelliSense** można uzyskać, wybierając pozycję **Narzędzia**, **Opcje** na pasku menu, a następnie rozszerzając **Edytor tekstu**, **JavaScript**, **IntelliSense.**

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 Strona **IntelliSense** zawiera następujące sekcje:

## <a name="validation"></a>Walidacja
 Te opcje służą do ustawiania preferencji, w jaki sposób edytor kodu JavaScript sprawdza poprawność składni w dokumencie.

## <a name="uielement-list"></a>Lista elementów UI
 **Pokaż błędy składni** Gdy to pole wyboru nie jest zaznaczone, Edytor kodu JavaScript nie pokazuje błędów składniowych. Jest to przydatne, jeśli pracujesz z nieswoim kodem, w którym nie zamierzasz naprawiać błędów składniowych.

 Gdy to pole wyboru jest zaznaczone, można zaznaczyć pole wyboru **Pokaż błędy jako ostrzeżenia** .

 **Pokaż błędy jako ostrzeżenia** Gdy to pole wyboru jest zaznaczone, błędy JavaScript są wyświetlane jako ostrzeżenia zamiast błędów na liście błędów.

 **Pobierz zdalne odwołania (np. http://) dla plików w projekcie różne pliki** Gdy to pole wyboru jest zaznaczone, a plik JavaScript jest otwarty poza kontekstem projektu, program Visual Studio pobierze zdalne pliki JavaScript, do których odwołuje się plik na potrzeby udostępniania informacji IntelliSense. Gdy ta opcja jest zaznaczona, pliki zostaną pobrane po włączeniu ich jako odwołania w pliku JavaScript.

> [!NOTE]
> Dla projektów sieci Web domyślnie pobierane są pliki zdalne, do których odwołuje się projekt.

## <a name="statement-completion"></a>Dokańczanie instrukcji
 Możesz użyć tych opcji do zmiany zachowania dokańczania instrukcji IntelliSense.

## <a name="uielement-list"></a>Lista elementów UI
 **Użyj klawisza TAB lub ENTER, aby zatwierdzić** Gdy to pole wyboru jest zaznaczone, Edytor kodu JavaScript dołącza instrukcje do elementów wybranych na liście uzupełniania tylko po wybraniu karty lub klawisza ENTER. Gdy to pole wyboru nie jest zaznaczone, inne znaki, takie jak kropka, przecinek, dwukropek, nawias otwierający i otwierający nawias klamrowy ({) również mogą dołączać instrukcje z wybranymi elementami.

## <a name="references"></a>Dokumentacja
 Można używać tych opcji, aby określać typy plików .js IntelliSense, które znajdują się w zakresie dla różnych typów projektów JavaScript. Odwołania IntelliSense są zazwyczaj używane do obsługi technologii IntelliSense dla obiektów globalnych. Można również użyć tej strony, aby ustawić kolejność ładowania skryptów, które muszą być ładowane w czasie wykonywania, oraz aby dodawać pliki rozszerzeń IntelliSense.

## <a name="uielement-list"></a>Lista elementów UI
 **Grupy odwołań** Ta opcja określa typ grupy odwołania. Obsługiwane są trzy grupy odwołań:

 Można używać wstępnie zdefiniowanych grup odwołań w celu określania, że konkretne pliki .js IntelliSense znajdują się w zakresie dla różnych projektów JavaScript. Dostępne są cztery grupy odniesień:

- Niejawne ( *wersja*systemu Windows) dla [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikacji korzystających z języka JavaScript. Pliki dołączone do tej grupy są w zakresie dla każdego pliku. js otwartego w edytorze kodu dla [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikacji korzystających z języka JavaScript.

- Niejawna (sieć Web) dla projektów HTML5. Pliki dołączone do tej grupy są w zakresie dla każdego pliku .js otwartego w Edytorze kodu dla tych typów projektu.

- Grupy odwołań wyspecjalizowanych funkcji roboczych, dla funkcji roboczych HTML5 sieci Web. Pliki określone w tej grupie są w zakresie plików .js, które mają wyraźne odniesienie do grupy odwołań wyspecjalizowanych funkcji roboczych.

- Ogólna dla innych typów projektów języka JavaScript.

  **Dołączone pliki** Ta opcja określa kolejność, w jakiej pliki są ładowane do kontekstu usługi językowej. Kolejność można skonfigurować przy użyciu przycisków **Usuń**, Przenieś w **górę**i **Przenieś w dół** . Aby technologia IntelliSense działała poprawnie, plik, który jest zależny od innego, musi być załadowany po pliku, od którego zależy.

> [!CAUTION]
> Jeśli obiekt jest zdefiniowany bezwarunkowo w dwóch lub więcej odwołań niejawnych, ostatnie odwołanie na tej liście będzie używane do określenia obiektu.

 **Dodawanie odwołania do grupy** Ta opcja umożliwia dodanie dodatkowych plików IntelliSense. js poprzez przechodzenie do odpowiednich plików.

## <a name="see-also"></a>Zobacz też
 [JavaScript IntelliSense](../../ide/javascript-intellisense.md)
