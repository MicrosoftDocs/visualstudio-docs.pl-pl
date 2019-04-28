---
title: Zaufania ustawienia dla plików i folderów
description: Dowiedz się, jak zmienić ustawień zaufania dla plików i folderów, aby zabezpieczyć program Visual Studio.
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789645"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Konfigurowanie ustawień zaufania dla plików i folderów

Program Visual Studio wyświetla monit o zatwierdzenie użytkownika przed otwarciem projektów, które mają [MOTW](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85)). Aby zwiększyć bezpieczeństwo, można również skonfigurować program Visual Studio, monit o zatwierdzenie użytkownika przed otwarciem dowolnego pliku lub folderu, że zaznaczone jest pole atrybutu sieci web lub który nie jest wyznaczony jako *zaufanych*. Sprawdzanie plików i folderów są domyślnie wyłączone.

> [!WARNING]
> Nadal należy upewnić się czy plik, folder lub rozwiązania pochodzą od zaufanej osoby lub z zaufanej lokalizacji przed zatwierdzeniem.

## <a name="configure-trust-settings"></a>Konfigurowanie ustawień zaufania

Aby zmienić ustawienia zaufania, wykonaj następujące kroki:

1. Otwórz **narzędzia** > **opcje** > **ustawienia zaufania** i wybierz **Konfigurowanie ustawień zaufania** link okienko po prawej stronie.

2. Wybierz poziom kontroli, które Twoim zdaniem dla plików i folderów. Może mieć różnych kontroli dla każdego z nich. Dostępne są następujące opcje:

   * **Nie weryfikacji**: Program Visual Studio nie wykonuje żadnych testów.

   * **Sprawdź znacznik atrybutu web**: Jeśli plik lub folder zaznaczone jest pole atrybutu sieci web, programu Visual Studio blokuje i poprosi o podanie uprawnień do otwarcia.

   * **Sprawdź ścieżkę jest zaufany**: Jeśli ścieżka pliku lub folderu nie jest częścią **zaufanych ścieżek** listy blokuje programu Visual Studio i poprosi o podanie uprawnień do otwarcia.

   ![Opcje weryfikacji zaufania](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Dodawanie zaufanych ścieżek

Aby dodać zaufanych ścieżek, wykonaj następujące kroki:

1. Otwórz **narzędzia** > **opcje** > **ustawienia zaufania** i wybierz **Konfigurowanie ustawień zaufania** link okienko po prawej stronie.

2. Kliknij przycisk **Dodaj** w **ustawienia zaufania** okna dialogowego, a następnie wybierz **pliku** lub **folderu**.

3. Przejdź do, a następnie wybierz żądany plik lub folder, który chcesz dodać do listy zaufanych.

   Ścieżka pliku lub folderu pojawia się w **zaufanych ścieżek** listy.

   ![Dodano zaufanych ścieżek](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Usuwanie zaufanych ścieżek

Aby usunąć zaufanych ścieżek, wykonaj następujące kroki:

1. Otwórz **narzędzia** > **opcje** > **ustawienia zaufania** i wybierz **Konfigurowanie ustawień zaufania** link okienko po prawej stronie.

2. Wybierz ścieżkę, czy chcesz usunąć **zaufanych ścieżek** listy, a następnie kliknij przycisk **Usuń**.

   > [!TIP]
   > Aby wybrać wiele wpisów, przytrzymaj wciśnięty **Shift** podczas wybierania ścieżki.

   Wybrane ścieżki zostaną usunięte z **zaufanych ścieżek** listy.
