---
title: Rozwiązywanie problemów z rozszerzeniami dla diagramów zależności
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 01b8486c9ca0ffc62d338b9d9a46e50248182581
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028598"
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Rozwiązywanie problemów z rozszerzeniami dla diagramów zależności

W tym temacie omawia niektóre problemy, które można napotkać podczas tworzenia warstwy modelu rozszerzeń.

## <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-visual-studio"></a>Po naciśnięciu klawisza klawisz F5, aby debugować Moje rozszerzenia, polecenia, programy obsługi gestu, rozszerzenia sprawdzania poprawności lub właściwości niestandardowe nie są wyświetlane na wykresach zależności w doświadczalnym wystąpieniu programu Visual Studio

1. Otwórz swoje rozwiązanie rozszerzenia w doświadczalnym wystąpieniu programu Visual Studio, a także na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

2. Naciśnij klawisz **F5** lub **kombinację klawiszy CTRL + F5** do uruchom wystąpienie eksperymentalne programu Visual Studio. Otwórz diagram zależności i przetestuj swoje rozszerzenia.

   Przejdź do następnej procedury, jeśli to konieczne.

## <a name="an-old-version-of-my-extension-runs"></a>Uruchamia starą wersję mojego rozszerzenia.

1. Upewnij się, że żadne wystąpienie doświadczalne programu Visual Studio jest uruchomiony.

2. Usuń następujący folder: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [wersja]

   > [!NOTE]
   > % LocalAppData % zazwyczaj znajduje *DriveName*: \Users\\*UserName*\AppData\Local.

   Przejdź do następnej procedury, jeśli to konieczne.

## <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Pojawi się stara wersja mojego wyniku weryfikacji lub Moja metoda sprawdzania poprawności nie jest wywoływana.

1.  W doświadczalnym wystąpieniu programu Visual Studio na **kompilacji** menu, kliknij przycisk **czyste rozwiązanie**. Czyści buforowane wyników poprzedniej analizy sprawdzania poprawności.

2.  Upewnij się, że warstwy w modelu są skojarzone z elementami kodu i że istnieje co najmniej jedno łącze zależności w modelu. Sprawdzanie poprawności nie jest wywoływana, jeśli nie ma nic do sprawdzania poprawności.

3.  Regularne punkty przerwania mogą nie działać w metodzie sprawdzania poprawności, ponieważ jest uruchamiana w oddzielnym procesie. Należy wstawić wywołanie `System.Diagnostics.Debugger.Launch()` Jeśli chcesz przejść przez metodę.

4.  W **source.extension.vsixmanifest** upewnij się, że dodano zarówno w projekcie sprawdzania poprawności warstwy **składnik MEF** elementu i **niestandardowy typ rozszerzenia** w obszarze **Zawartości**.

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie diagramów zależności](../modeling/extend-layer-diagrams.md)
