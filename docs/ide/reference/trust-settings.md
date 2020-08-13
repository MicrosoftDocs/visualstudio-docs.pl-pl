---
title: Ustawienia zaufania dla plików i folderów
description: Dowiedz się, jak zmienić ustawienia zaufania dla plików i folderów, aby zapewnić bezpieczeństwo programu Visual Studio.
author: 2percentsilk
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
ms.openlocfilehash: 492a94962d255a9d18dcabdababf7fa6a540ada1
ms.sourcegitcommit: 935e1388281df0f04147802606b5cb7f513d45ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2020
ms.locfileid: "88197394"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Konfigurowanie ustawień zaufania dla plików i folderów

Program Visual Studio wyświetli komunikat z prośbą o zatwierdzenie użytkownika przed otwarciem projektów, które mają [znacznik sieci Web](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85)). Aby zwiększyć bezpieczeństwo, można również skonfigurować program Visual Studio, aby monitował o zatwierdzenie przez użytkownika przed otwarciem pliku lub folderu, który ma znacznik atrybutu sieci Web lub który nie został wyznaczono jako *zaufany*. Sprawdzanie plików i folderów jest domyślnie wyłączone.

> [!WARNING]
> Nadal należy upewnić się, że plik, folder lub rozwiązanie pochodzi od zaufanej osoby lub zaufanej lokalizacji przed jej zatwierdzeniem.

## <a name="configure-trust-settings"></a>Konfigurowanie ustawień zaufania

Aby zmienić ustawienia zaufania, wykonaj następujące czynności:

1. Otwórz pozycję **Narzędzia**  >  **Opcje**  >  **zaufania ustawienia** , a następnie wybierz link **Konfiguruj ustawienia zaufania** w okienku po prawej stronie.

2. Wybierz poziom kontroli dla plików i folderów. Możesz mieć różne sprawdzenia dla każdej z nich. Dostępne są następujące opcje:

   * **Brak weryfikacji**: program Visual Studio nie wykonuje żadnych testów.

   * **Sprawdź poprawność znacznika atrybutu sieci Web**: Jeśli plik lub folder ma oznaczenie atrybutu sieci Web, program Visual Studio blokuje i prosi o uprawnienia do otwarcia.

   * **Sprawdź, czy ścieżka jest zaufana**: Jeśli ścieżka pliku lub folderu nie jest częścią listy **zaufanych ścieżek** , program Visual Studio blokuje i prosi o zezwolenie na otwarcie.

   ![Opcje weryfikacji zaufania](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Dodaj zaufane ścieżki

Aby dodać zaufane ścieżki, wykonaj następujące kroki:

1. Otwórz pozycję **Narzędzia**  >  **Opcje**  >  **zaufania ustawienia** , a następnie wybierz link **Konfiguruj ustawienia zaufania** w okienku po prawej stronie.

2. W oknie dialogowym **ustawienia zaufania** kliknij pozycję **Dodaj** , a następnie wybierz pozycję **plik** lub **folder**.

3. Przejdź do i wybierz plik lub folder, który chcesz dodać do listy zaufanych.

   Ścieżka pliku lub folderu zostanie wyświetlona na liście **zaufanych ścieżek** .

   ![Dodano zaufane ścieżki](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Usuń zaufane ścieżki

Aby usunąć zaufane ścieżki, wykonaj następujące kroki:

1. Otwórz pozycję **Narzędzia**  >  **Opcje**  >  **zaufania ustawienia** , a następnie wybierz link **Konfiguruj ustawienia zaufania** w okienku po prawej stronie.

2. Wybierz ścieżkę, którą chcesz usunąć, na liście **zaufanych ścieżek** , a następnie kliknij przycisk **Usuń**.

   > [!TIP]
   > Aby zaznaczyć wiele wpisów, przytrzymaj wciśnięty klawisz **SHIFT** podczas wybierania ścieżek.

   Wybrane ścieżki zostaną usunięte z listy **zaufanych ścieżek** .
