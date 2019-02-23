---
title: Odśwież aplikację platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.workload:
- uwp
ms.openlocfilehash: 4bd14f0d0a8fa0697ed8fead43bac69b0b002ed3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690568"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Odświeżanie aplikacji platformy UWP w programie Visual Studio

 Można wprowadzić zmiany do kodu podczas debugowania, a następnie Odśwież aplikację platformy UWP przy użyciu języka JavaScript, wybierając **aplikacji Windows Odśwież** znajdujący się na **debugowania** paska narzędzi. Wybranie tego przycisku ponownie ładuje aplikację bez zatrzymywania i ponownego uruchamiania debugera. Funkcja odświeżania umożliwia modyfikowanie kodu HTML, CSS i JavaScript i szybko wyświetlić wyniki. Ta funkcja jest obsługiwana dla aplikacji platformy uniwersalnej systemu Windows.

 Odświeżanie nie zarządzania stanem swojej aplikacji lub uwzględnić następujące zmiany w aplikacji:

-   Zmiany pliku manifestu pakietu, w tym zmiany w manifeście pakietu obrazów.

-   Odwołanie zmiany, takie jak dodawanie lub usuwanie odwołania zestawu SDK lub zmiana składników środowiska wykonawczego Windows (winmd).

-   Zmiany zasobów, takich jak zmiany na ciągi w plikach .resjson.

-   Zmiany pliku projektu, które powodują zmiany nazwy ścieżki, nowe pliki projektu lub usunięte pliki.

-   Zmiany właściwości projektów i elementów, takich jak zmiany na wybranym urządzeniu debugowania lub zmiany Akcja pakietu dla pliku (w oknie dialogowym Właściwości).

> [!IMPORTANT]
>  Podczas zmiany odwołania, zmień manifest pakietu lub wprowadzić inne zmiany, określone w powyższej liście musisz zatrzymać i ponownie uruchomić debugera, aby zaktualizować pliki źródłowe HTML, CSS i JavaScript.

### <a name="to-refresh-an-app"></a>Aby odświeżyć aplikację

1.  Otwórz w programie Visual Studio projekt platformy uniwersalnej systemu Windows wybierz **komputera lokalnego** jako cel debugowania.

     ![Wybierz opcję debugowania listy docelowej](../debugger/media/js_select_target.png "JS_Select_Target")

3.  Naciśnij klawisz F5, aby uruchomić aplikację w trybie debugowania.

4.  Przełącz się do programu Visual Studio.

5.  Na stronie głównej aplikacji platformy uniwersalnej systemu Windows należy edytować część HTML.

7.  Kliknij przycisk **aplikacji Windows Odśwież** przycisku, który wygląda następująco: ![Odśwież aplikację Windows](../debugger/media/js_refresh.png "JS_Refresh"). (Lub naciśnij klawisz F4).

8.  Przełącz się do aplikacji. Aplikacja zostanie ponownie załadowana i zaktualizowane HTML jest używany do renderowania aplikacji.

## <a name="see-also"></a>Zobacz też
- [Szybki start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)