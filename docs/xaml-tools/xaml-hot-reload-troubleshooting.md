---
title: Rozwiązywanie problemów z ponownym ładowaniem przy aktywnym kodzie XAML
description: Rozwiązywanie problemów, które mogą wystąpić w przypadku wczytywania gorącego kodu XAML.
ms.date: 09/04/2019
ms.topic: troubleshooting
helpviewer_keywords:
- xaml edit and continue, troubleshooting
- xaml hot reload, troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 40be42871bac0a138d15b11b86f34419f2a6c67d
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535294"
---
# <a name="troubleshooting-xaml-hot-reload"></a>Rozwiązywanie problemów z ponownym ładowaniem przy aktywnym kodzie XAML

Ten przewodnik rozwiązywania problemów zawiera szczegółowe instrukcje, które powinny rozwiązać większość problemów, które uniemożliwiają poprawne działanie ponownego ładowania języka XAML.

Hot reload języka XAML jest obsługiwany dla aplikacji WPF i platformy UWP. Aby uzyskać szczegółowe informacje o wymaganiach dotyczących systemu operacyjnego i narzędzi, zobacz [pisanie i debugowanie uruchomionego kodu XAML za pomocą usługi XAML](xaml-hot-reload.md).

## <a name="hot-reload-is-not-available"></a>Zapasowe ponowne ładowanie nie jest dostępne

Jeśli podczas debugowania aplikacji zobaczysz komunikat "gorąca ponowna próba nie jest dostępna" na pasku narzędzi w aplikacji, postępuj zgodnie z instrukcjami opisanymi w tym artykule, aby rozwiązać ten problem.

## <a name="verify-that-xaml-hot-reload-is-enabled"></a>Sprawdź, czy włączono funkcję dynamicznego ponownego ładowania XAML

Funkcja jest domyślnie włączona. Po rozpoczęciu debugowania aplikacji upewnij się, że widzisz pasek narzędzi w aplikacji, który potwierdza, że dostępny jest dostęp do gorącego ładowania XAML:

![Dostępny jest dostęp do gorącego ładowania XAML](../debugger/media/xaml-hot-reload-available.png)

Jeśli nie widzisz paska narzędzi w aplikacji, Otwórz**opcje**  >  **debugowania**  > **Ogólne**. Upewnij się, że są zaznaczone obie opcje, **Włącz narzędzia debugowania interfejsu użytkownika dla języka XAML** i wybierz **opcję Włącz funkcję dynamicznego ponownego ładowania XAML** .

![Włącz gorącą ponowną ładowanie XAML](../debugger/media/xaml-hot-reload-enable.png)

Jeśli są wybrane te opcje, przejdź do aktywnego drzewa wizualnego (**Debug** > **Windows** > **Live Visual Tree**) i upewnij się, że jest zaznaczona opcja **Pokaż narzędzia środowiska uruchomieniowego na** pasku narzędzi aplikacji (po lewej stronie).

![Włącz gorącą ponowną ładowanie XAML](../debugger/media/xaml-hot-reload-show-runtime-tools.png)

## <a name="verify-that-you-use-start-debugging-rather-than-attach-to-process"></a>Sprawdź, czy używasz debugowania początkowego zamiast dołączania do procesu

Funkcja ładowania gorącego XAML wymaga, aby zmienna środowiskowa `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` była ustawiona na 1 podczas uruchamiania aplikacji. Program Visual Studio automatycznie ustawia tę wartość jako część **debugowania** > **Rozpocznij debugowanie** (lub **F5**). Jeśli chcesz użyć języka XAML do ponownego załadowania przy użyciu  >  **debugowania** **Dołącz do procesu** , a następnie Ustaw zmienną środowiskową samodzielnie.

> [!NOTE]
> Aby ustawić zmienną środowiskową, wyszukaj ciąg "zmienna środowiskowa" i wybierz polecenie **Edytuj zmienne środowiskowe systemu**. W otwartym oknie dialogowym wybierz **zmienne środowiskowe**, a następnie dodaj je jako zmienną użytkownika i ustaw wartość na `1`. Aby wyczyścić, Usuń zmienną po zakończeniu debugowania.

## <a name="verify-that-your-msbuild-properties-are-correct"></a>Sprawdź, czy właściwości programu MSBuild są poprawne

Domyślnie informacje źródłowe są zawarte w konfiguracji debugowania. Jest on kontrolowany przez właściwości programu MSBuild w plikach projektu (na przykład *. csproj). Dla platformy WPF właściwość jest `XamlDebuggingInformation`, która musi być ustawiona na `True`. Dla platformy UWP właściwość jest `DisableXbfLineInfo`, która musi być ustawiona na `False`. Na przykład:

KODOW

`<XamlDebuggingInformation>True</XamlDebuggingInformation>`

PLATFORMY UWP

`<DisableXbfLineInfo>False</DisableXbfLineInfo>`

## <a name="verify-that-you-are-using-the-correct-build-configuration-name"></a>Sprawdź, czy używasz prawidłowej nazwy konfiguracji kompilacji

Musisz ręcznie ustawić poprawną Właściwość programu MSBuild, aby obsługiwała ładowanie gorące w języku XAML (zobacz poprzednią sekcję) lub użyć domyślnej nazwy konfiguracji kompilacji (Debug). Jeśli nie ustawisz prawidłowo właściwości programu MSBuild, niestandardowa nazwa konfiguracji kompilacji nie będzie działała ani kompilacja wydania zostanie utworzona.

## <a name="verify-that-your-xaml-file-has-no-errors"></a>Sprawdź, czy plik XAML nie zawiera błędów

Jeśli plik XAML zawiera błędy w **Lista błędów**, usługa XAML gorąca reload może nie zadziałała.

## <a name="see-also"></a>Zobacz także

[Pisanie i debugowanie uruchomionego kodu XAML z gorącą funkcją XAML](xaml-hot-reload.md)
