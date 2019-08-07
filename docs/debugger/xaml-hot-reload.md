---
title: Pisanie i debugowanie kodu XAML przy użyciu gorącego ponownego ładowania XAML
description: Usługa XAML — ładowanie gorące lub Edycja i kontynuowanie XAML umożliwia wprowadzanie zmian w kodzie XAML podczas uruchamiania aplikacji
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2728f26319b3d395381d60f136fba7d0c20da977
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68822141"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Pisanie i debugowanie uruchomionego kodu XAML przy użyciu gorącego ponownego ładowania XAML w programie Visual Studio

Usługa XAML Hot reload umożliwia tworzenie interfejsu użytkownika aplikacji WPF lub platformy UWP, dzięki czemu można wprowadzać zmiany w kodzie XAML, gdy aplikacja jest uruchomiona. Zapasowe ponowne ładowanie są dostępne zarówno w programie Visual Studio, jak i w Blend for Visual Studio. Ta funkcja umożliwia przyrostowe kompilowanie i testowanie kodu XAML z korzyścią dla kontekstu danych uruchomionej aplikacji, stanu uwierzytelniania i innej skomplikowanej złożoności, która trudno się symulować w czasie projektowania.

Hot reload języka XAML jest szczególnie przydatny w następujących scenariuszach:

* Rozwiązywanie problemów z interfejsem użytkownika znalezionych w kodzie XAML po uruchomieniu aplikacji w trybie debugowania.

* Tworzenie nowego składnika interfejsu użytkownika dla aplikacji, która jest w fazie tworzenia, przy jednoczesnym wykorzystaniu kontekstu środowiska uruchomieniowego aplikacji.

|Obsługiwane typy aplikacji|System operacyjny i narzędzia|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 +</br>System Windows 7 lub nowszy |
|Aplikacje uniwersalne systemu Windows (platformy UWP)|Windows 10 i nowsze, z [zestawem SDK systemu Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

> [!NOTE]
> Hot reload programu Visual Studio XAML jest obecnie obsługiwany tylko w przypadku uruchamiania aplikacji w programie Visual Studio lub Blend for Visual Studio z dołączonym debugerem (**F5** lub **Start Debug**). Nie można włączyć tego środowiska przy użyciu funkcji [Dołącz do procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="known-limitations"></a>Znane ograniczenia

Poniżej przedstawiono znane ograniczenia dotyczące gorącego ładowania kodu XAML. Aby obejść wszystkie ograniczenia, z których korzystasz, Zatrzymaj debuger, a następnie ukończ operację.

|Bieg|WPF|Platforma UWP|Uwagi|
|-|-|-|-|
|Zdarzenia okablowania do kontrolek, gdy aplikacja jest uruchomiona|Nieobsługiwane|Nieobsługiwane|Zobacz błąd: *Sprawdź, czy zdarzenie nie powiodło się*|
|Tworzenie obiektów zasobów w słowniku zasobów, takich jak te znajdujące się w pliku/oknie lub pliku *App. XAML* aplikacji|Nieobsługiwane|Obsługiwane|Przykład: Dodawanie `SolidColorBrush` do słownika zasobów do użycia `StaticResource`jako.</br>Uwaga: Zasoby statyczne, konwertery stylów i inne elementy zapisywane w słowniku zasobów mogą być stosowane/używane podczas korzystania z usługi XAML. Tylko tworzenie zasobu nie jest obsługiwane.</br> Zmiana właściwości słownik `Source` zasobów.|
|Dodawanie nowych kontrolek, klas, okien lub innych plików do projektu, gdy aplikacja jest uruchomiona|Nieobsługiwane|Nieobsługiwane|Brak|
|Zarządzanie pakietami NuGet (Dodawanie/usuwanie/aktualizowanie pakietów)|Nieobsługiwane|Nieobsługiwane|Brak|
|Zmiana powiązania danych korzystającego z rozszerzenia znacznika {x:Bind}|Brak|Obsługiwane w programie Visual Studio 2019 i jego nowszych wersjach|Nieobsługiwane w programie Visual Studio 2017 lub w poprzednich wersjach|

## <a name="error-messages"></a>Komunikaty o błędach

Podczas korzystania ze gorącego ładowania kodu XAML mogą występować następujące błędy.

|Komunikat o błędzie|Opis|
|-|-|-|
|Sprawdź, czy zdarzenie nie powiodło się|Błąd oznacza, że próbujesz obsłużyć zdarzenie do jednej z kontrolek, co nie jest obsługiwane, gdy aplikacja jest uruchomiona.|
|Edycja XAML i Kontynuuj nie znalazła żadnych elementów do zaktualizowania.|Wystąpił błąd podczas edytowania kodu XAML, który nie może zostać zaktualizowany w aplikacji.</br> Ten błąd może być czasami naprawiony za pomocą działającej aplikacji, aby przejść do widoku, w którym jest używany kod XAML.</br> Czasami ten błąd oznacza, że nie można zastosować określonej zmiany, dopóki sesja debugowania nie zostanie ponownie uruchomiona. |
|Ta zmiana nie jest obsługiwana podczas sesji debugowania.|Błąd oznacza, że próba zmiany nie jest obsługiwana przez kod XAML. Zatrzymaj sesję debugowania, wprowadź zmianę, a następnie ponownie uruchom sesję debugowania.|
