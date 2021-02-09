---
title: Co to jest debugowanie?
description: Informacje o tym, co oznacza debugowanie aplikacji
ms.custom: debug-experiment
ms.date: 10/17/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3435b7a270d89dc38f5ff10a1350418a24f91c0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883938"
---
# <a name="what-is-debugging"></a>Co to jest debugowanie?

Debuger programu Visual Studio jest zaawansowanym narzędziem. Zanim poinformujemy, jak z niej korzystać, chcemy porozmawiać na temat pewnych warunków, takich jak *debuger*, *debugowanie* i *tryb debugowania*. W ten sposób podczas kolejnej rozmowy o Znajdowanie i naprawianie usterek będziemy mówić o tym samym zakresie.

## <a name="debugger-vs-debugging"></a>Debuger a debugowanie

Termin *debugowania* może oznaczać wiele różnych rzeczy, ale najbardziej dosłownie oznacza usunięcie usterek z kodu. Teraz istnieje wiele sposobów, aby to zrobić. Na przykład możesz debugować, skanując kod szukający literówki lub używając analizatora kodu. Kod można debugować za pomocą profilera wydajności. Lub można debugować za pomocą *debugera*.

Debuger to bardzo wyspecjalizowane narzędzie programistyczne, które dołącza do uruchomionej aplikacji i umożliwia sprawdzenie kodu. W dokumentacji debugowania dla programu Visual Studio jest to zazwyczaj znaczenie, gdy będziemy mówić "Debugowanie".

## <a name="debug-mode-vs-running-your-app"></a>Tryb debugowania a uruchamianie aplikacji

Po uruchomieniu aplikacji w programie Visual Studio po raz pierwszy możesz ją uruchomić, naciskając przycisk Zielona strzałka ![Rozpocznij debugowanie](../debugger/media/dbg-tour-start-debugging.png "Rozpocznij debugowanie") na pasku narzędzi (lub **F5**). Domyślnie wartość **debugowania** pojawia się na liście rozwijanej po lewej stronie. Jeśli dopiero zaczynasz używać programu Visual Studio, może to pozostawać wrażenie, że debugowanie aplikacji ma coś do działania w celu uruchomienia aplikacji — co robi, ale są one zasadniczo dwa bardzo różne zadania.

![Wybierz kompilację debugowania](../debugger/media/what-is-debugging-debug-build.png)

Wartość **debugowania** wskazuje konfigurację debugowania. Po uruchomieniu aplikacji (Naciśnij zieloną strzałkę lub **F5**) w konfiguracji debugowania uruchamiasz aplikację w *trybie debugowania*, co oznacza, że aplikacja jest uruchamiana z dołączonym debugerem. Pozwala to na pełny zestaw funkcji debugowania, których można użyć, aby pomóc w znalezieniu usterek w aplikacji.

Jeśli masz otwarty projekt, wybierz selektor listy rozwijanej, gdzie mówi **debugowania** , a następnie wybierz pozycję **Zwolnij** .

![Wybierz kompilację wydania](../debugger/media/what-is-debugging-release-build.png)

Po przełączeniu tego ustawienia projekt zostanie zmieniony z konfiguracji debugowania na konfigurację wydania. Projekty programu Visual Studio mają osobne konfiguracje wersji i debugowania dla Twojego programu. Można skompilować wersję do debugowania dla debugowania i wersję wydania dla ostatecznej dystrybucji wersji. Kompilacja wydania jest zoptymalizowana pod kątem wydajności, ale Kompilacja debugowania jest lepsza dla debugowania.

## <a name="when-to-use-a-debugger"></a>Kiedy używać debugera

Debuger to podstawowe narzędzie do znajdowania i naprawiania usterek w aplikacjach. Jednak kontekst to król i ważne jest, aby korzystać z wszystkich narzędzi w miejscu, aby pomóc szybko wyeliminować błędy lub błędy. Czasami odpowiednie "Narzędzie" może być lepszym rozwiązaniem do tworzenia kodu. Pouczenie się, kiedy należy używać debugera a innego narzędzia, dowiesz się również, jak wydajniej korzystać z debugera.

## <a name="next-steps"></a>Następne kroki

W tym artykule przedstawiono kilka ogólnych pojęć dotyczących debugowania. Następnie możesz zacząć uczenie się, jak debugować program Visual Studio i jak pisać kod z mniejszą ilością błędów. W poniższych artykułach przedstawiono przykłady kodu w języku C#, ale pojęcia dotyczą wszystkich języków obsługiwanych przez program Visual Studio.

> [!div class="nextstepaction"]
> [Debugowanie dla całkowicie początkujących](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [Narzędzia i techniki debugowania](../debugger/write-better-code-with-visual-studio.md)
