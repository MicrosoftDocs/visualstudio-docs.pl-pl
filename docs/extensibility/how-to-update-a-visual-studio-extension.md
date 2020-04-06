---
title: 'Jak: Aktualizowanie rozszerzenia programu Visual Studio | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 266c0a49db1bca03cec0eb68301445102173df3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710653"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Jak: Aktualizowanie rozszerzenia programu Visual Studio
Rozszerzenie programu Visual Studio można zaktualizować w systemie za pomocą **rozszerzeń i aktualizacji,** aby zainstalować zaktualizowaną wersję. Jeśli utworzysz zaktualizowaną wersję rozszerzenia, można oznaczyć go jako zaktualizowane przez zwiększenie numeru wersji w manifeście VSIX.

 Aktualizacje są instalowane, gdy manifest VSIX rozszerzenia przychodzącego ma taką samą, `ID` jak zainstalowaną i wyższą `Version` liczbę. Jeśli `Version` numer jest taki sam lub niższy, nie można zainstalować pakietu. Jeśli `ID` wartości nie są zgodne, pakiet, który nie jest jeszcze zainstalowany, jest rozpoznawany jako oddzielne rozszerzenie.

 Aby zapobiec konfliktom podczas tworzenia, zaleca się odinstalowanie wcześniejszych wersji rozszerzeń w toku, a także odinstalowanie lub wyłączenie innych potencjalnie sprzecznych rozszerzeń.

## <a name="to-update-an-extension-on-your-system"></a>Aby zaktualizować rozszerzenie w systemie

1. W menu **Narzędzia** kliknij pozycję **Rozszerzenia i aktualizacje**.

2. W lewym okienku kliknij pozycję **Aktualizacje**.

3. W środkowym okienku kliknij aktualizację, którą chcesz zainstalować.

     Numer wersji zaktualizowanego rozszerzenia jest wyświetlany w prawym okienku wraz z innymi informacjami.

4. U dołu prawego okienka kliknij pozycję **Aktualizuj**.

## <a name="to-publish-an-update-of-an-extension"></a>Aby opublikować aktualizację rozszerzenia

1. W programie Visual Studio otwórz rozwiązanie dla rozszerzenia, które chcesz zaktualizować. Wprowadzać zmiany.

    > [!IMPORTANT]
    > Niepodpisane wszystkie rozszerzenia użytkownika nie są aktualizowane automatycznie. Należy zawsze podpisać rozszerzenia.

2. W **Eksploratorze rozwiązań**, open *source.extension.manifest*.

3. W projektancie manifestu zwiększ wartość liczby w polu **Wersja.**

4. Zapisz rozwiązanie i zbuduj go.

5. Przekaż nowy plik *vsix* (w folderze *\bin\Debug\* projektu) do witryny sieci Web programu Visual Studio [Marketplace.](https://marketplace.visualstudio.com/vs)

     Gdy użytkownik, który ma wcześniejszą wersję rozszerzenia, otworzy **rozszerzenia i aktualizacje,** nowa wersja pojawi się na liście **Aktualizacje,** pod warunkiem, że narzędzie jest ustawione na automatyczne wyszukanie aktualizacji.

     Automatyczne sprawdzanie aktualizacji u dołu**Options** > okienka **Aktualizacje** można włączyć lub wyłączyć automatyczne sprawdzanie dostępności (**Włącz/wyłącz automatyczne wykrywanie dostępnych aktualizacji),** które zmienia ustawienie **Sprawdź aktualizacje** w **ustawieniach Opcje** > **środowiska** > narzędzia**i aktualizacje**.

    > [!NOTE]
    > Począwszy od programu Visual Studio 2015 Update 2, można określić (w **narzędzia** > **opcje** > rozszerzenia**środowiska** > **i aktualizacje),** czy chcesz automatyczne aktualizacje dla rozszerzeń dla użytkownika, wszystkie rozszerzenia użytkownika lub obu (ustawienie domyślne).

## <a name="see-also"></a>Zobacz też
- [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Znajdowanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
