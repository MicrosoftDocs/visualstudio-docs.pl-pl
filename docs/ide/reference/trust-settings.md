---
title: Ustawienia zaufania dla plików i folderów
description: Dowiedz się, jak zmienić ustawienia zaufania dla plików i folderów, aby zapewnić bezpieczeństwo programu Visual Studio.
author: abuchholtzau
ms.author: allisb
ms.date: 09/05/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.PathTrustOptions
helpviewer_keywords:
- file security
- folder security
- mark of the web
- trusted files
- trusted folders
ms.openlocfilehash: 011673bca7be569b5b350dc264148d5a7890d39c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62789645"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Konfigurowanie ustawień zaufania dla plików i folderów

Program Visual Studio monituje o zatwierdzenie przez użytkownika przed otwarciem projektów, które mają [znak sieci Web](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85)). Aby zwiększyć bezpieczeństwo, można również skonfigurować program Visual Studio tak, aby monitował o zatwierdzenie przez użytkownika przed otwarciem dowolnego pliku lub folderu, który ma znak atrybutu sieci Web lub który nie jest oznaczony jako *zaufany.* Sprawdzanie plików i folderów jest domyślnie wyłączone.

> [!WARNING]
> Przed zatwierdzeniem pliku, folderu lub rozwiązania należy upewnić się, że plik, folder lub rozwiązanie pochodzą od zaufanej osoby lub zaufanej lokalizacji.

## <a name="configure-trust-settings"></a>Konfigurowanie ustawień zaufania

Aby zmienić ustawienia zaufania, wykonaj następujące czynności:

1. Otwórz**pozycję Ustawienia zaufania** **opcji** >  **narzędzi** > i wybierz łącze **Konfigurowanie ustawień zaufania** w okienku po prawej stronie.

2. Wybierz poziom kontroli plików i folderów. Możesz mieć różne czeki dla każdego z nich. Dostępne opcje to:

   * **Brak weryfikacji:** program Visual Studio nie przeprowadza żadnych kontroli.

   * **Sprawdź znak atrybutu sieci Web**: Jeśli plik lub folder ma znak atrybutu sieci web, program Visual Studio blokuje i prosi o pozwolenie na otwarcie.

   * **Sprawdź, czy ścieżka jest zaufana:** Jeśli ścieżka pliku lub folderu nie jest częścią listy **Zaufane ścieżki,** program Visual Studio blokuje i prosi o pozwolenie na otwarcie.

   ![Opcje weryfikacji zaufania](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Dodawanie zaufanych ścieżek

Aby dodać zaufane ścieżki, wykonaj następujące czynności:

1. Otwórz**pozycję Ustawienia zaufania** **opcji** >  **narzędzi** > i wybierz łącze **Konfigurowanie ustawień zaufania** w okienku po prawej stronie.

2. Kliknij **pozycję Dodaj** w oknie dialogowym Ustawienia **zaufania,** a następnie wybierz pozycję **Plik** lub **folder**.

3. Przejdź do pliku lub folderu, który chcesz dodać do listy zaufanej, i wybierz go.

   Ścieżka pliku lub folderu pojawi się na liście **Zaufane ścieżki.**

   ![Dodano zaufane ścieżki](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Usuwanie zaufanych ścieżek

Aby usunąć zaufane ścieżki, wykonaj następujące czynności:

1. Otwórz**pozycję Ustawienia zaufania** **opcji** >  **narzędzi** > i wybierz łącze **Konfigurowanie ustawień zaufania** w okienku po prawej stronie.

2. Wybierz ścieżkę, którą chcesz usunąć na liście **Zaufane ścieżki,** a następnie kliknij przycisk **Usuń**.

   > [!TIP]
   > Aby zaznaczyć wiele wpisów, przytrzymaj naciśnięty **klawisz Shift** podczas zaznaczania ścieżek.

   Wybrane ścieżki zostaną usunięte z listy **Zaufane ścieżki.**
