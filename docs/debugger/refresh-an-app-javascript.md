---
title: Odświeżanie aplikacji platformy UWP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: dd38a758a69b2e19079a2bc2511e7edf5cbfb0ab
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348161"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Odświeżanie aplikacji platformy UWP w programie Visual Studio

 Podczas debugowania można wprowadzać zmiany w kodzie, a następnie odświeżyć aplikację platformy UWP przy użyciu języka JavaScript, wybierając przycisk **Odśwież aplikację systemu Windows** na pasku narzędzi **debugowania** . Wybranie tego przycisku spowoduje ponowne załadowanie aplikacji bez zatrzymywania i ponownego uruchamiania debugera. Funkcja odświeżania umożliwia modyfikowanie kodu HTML, CSS i JavaScript oraz szybkie wyświetlanie wyników. Ta funkcja jest obsługiwana w przypadku aplikacji platformy UWP.

 Odświeżanie nie utrzymuje stanu aplikacji ani nie odzwierciedla następujących zmian w aplikacji:

- Zmiany pliku manifestu pakietu, w tym zmiany obrazów określone w manifeście pakietu.

- Zmiany odniesienia, takie jak dodawanie lub usuwanie odwołania do zestawu SDK lub zmiany składników środowisko wykonawcze systemu Windows (plików winmd).

- Zmiany zasobów, takie jak zmiany w ciągach w plikach. resjson.

- Plik projektu zmienia się w wyniku zmiany nazwy ścieżki, nowych plików projektu lub usuniętych plików.

- Zmiany właściwości projektu i elementu, takie jak zmiany w wybranym urządzeniu debugowania, lub zmiany akcji pakietu dla pliku (w okno Właściwości).

> [!IMPORTANT]
> Po zmianie odwołań, zmianie manifestu pakietu lub wprowadzeniu innych zmian określonych na poprzedniej liście należy zatrzymać i ponownie uruchomić debuger, aby zaktualizować pliki źródłowe HTML, CSS i JavaScript.

### <a name="to-refresh-an-app"></a>Aby odświeżyć aplikację

1. Gdy projekt platformy UWP jest otwarty w programie Visual Studio, wybierz opcję **komputer lokalny** jako element docelowy debugowania.

     ![Wybierz listę obiektów docelowych debugowania](../debugger/media/js_select_target.png "JS_Select_Target")

3. Naciśnij klawisz F5, aby uruchomić aplikację w trybie debugowania.

4. Przejdź do programu Visual Studio.

5. Na stronie głównej aplikacji platformy UWP Edytuj część kodu HTML.

7. Kliknij przycisk **Odśwież aplikację systemu Windows** , który wygląda podobnie do tego: ![Odśwież przycisk aplikacji systemu Windows](../debugger/media/js_refresh.png "JS_Refresh"). (Lub naciśnij klawisz F4).

8. Przejdź do aplikacji. Aplikacja zostanie ponownie załadowana, a zaktualizowany kod HTML jest używany do renderowania aplikacji.

## <a name="see-also"></a>Zobacz też
- [Szybki start: debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)