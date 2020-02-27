---
title: Pisanie i debugowanie kodu XAML przy użyciu gorącego ponownego ładowania XAML
description: Usługa XAML — ładowanie gorące lub Edycja i kontynuowanie XAML umożliwia wprowadzanie zmian w kodzie XAML podczas uruchamiania aplikacji
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d977d79ce55bdd3abcb467d7bf7518b88bad7402
ms.sourcegitcommit: 9de7d25056da59df0941508c80c0b12766ba6580
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706365"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Pisanie i debugowanie uruchomionego kodu XAML przy użyciu gorącego ponownego ładowania XAML w programie Visual Studio

Usługa XAML Hot reload umożliwia tworzenie interfejsu użytkownika aplikacji WPF lub platformy UWP, dzięki czemu można wprowadzać zmiany w kodzie XAML, gdy aplikacja jest uruchomiona. Zapasowe ponowne ładowanie są dostępne zarówno w programie Visual Studio, jak i w Blend for Visual Studio. Ta funkcja umożliwia przyrostowe kompilowanie i testowanie kodu XAML z korzyścią dla kontekstu danych uruchomionej aplikacji, stanu uwierzytelniania i innej skomplikowanej złożoności, która trudno się symulować w czasie projektowania. Jeśli potrzebujesz pomocy przy rozwiązywaniu problemów z aktywnym załadowaniem XAML, zobacz sekcję [Rozwiązywanie problemów z gorącą usługą XAML](xaml-hot-reload-troubleshooting.md) .

> [!NOTE]
> Jeśli używasz platformy Xamarin. Forms, zobacz [gorąca Załaduj kod XAML dla platformy Xamarin. Forms](/xamarin/xamarin-forms/xaml/hot-reload).

Hot reload języka XAML jest szczególnie przydatny w następujących scenariuszach:

* Rozwiązywanie problemów z interfejsem użytkownika znalezionych w kodzie XAML po uruchomieniu aplikacji w trybie debugowania.

* Tworzenie nowego składnika interfejsu użytkownika dla aplikacji, która jest w fazie tworzenia, przy jednoczesnym wykorzystaniu kontekstu środowiska uruchomieniowego aplikacji.

|Obsługiwane typy aplikacji|System operacyjny i narzędzia|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 + i .NET Core</br>System Windows 7 lub nowszy |
|Aplikacje uniwersalne systemu Windows (platformy UWP)|Windows 10 i nowsze, z [zestawem SDK systemu Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

Na poniższej ilustracji przedstawiono użycie aktywnego drzewa wizualnego, aby otworzyć kod źródłowy, a następnie przycisk Wczytaj ponownie z kodowaniem XAML, aby zmienić tekst przycisku i kolor przycisku.

![Ponowne ładowanie przy aktywnym kodzie XAML](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Hot reload programu Visual Studio XAML jest obecnie obsługiwany tylko w przypadku uruchamiania aplikacji w programie Visual Studio lub Blend for Visual Studio z dołączonym debugerem (**F5** lub **Start Debug**). Nie można włączyć tego środowiska przy użyciu funkcji [dołączania do procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) , chyba że [ręcznie ustawisz zmienną środowiskową](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process).

## <a name="known-limitations"></a>Znane ograniczenia

Poniżej przedstawiono znane ograniczenia dotyczące gorącego ładowania kodu XAML. Aby obejść wszystkie ograniczenia, z których korzystasz, Zatrzymaj debuger, a następnie ukończ operację.

|Ograniczenia|WPF|Platforma UWP|Uwagi|
|-|-|-|-|
|Zdarzenia okablowania do kontrolek, gdy aplikacja jest uruchomiona|Nieobsługiwane|Nieobsługiwane|Zobacz błąd: *upewnij się, że zdarzenie nie powiodło się*. Należy pamiętać, że w WPF można odwołać się do istniejącej procedury obsługi zdarzeń. W aplikacjach platformy UWP odwoływanie się do istniejącej procedury obsługi zdarzeń nie jest obsługiwane.|
|Tworzenie obiektów zasobów w słowniku zasobów, takich jak te znajdujące się w pliku/oknie lub pliku *App. XAML* aplikacji|Obsługiwane począwszy od programu Visual Studio 2019 Update 2|Obsługiwane|Przykład: dodanie `SolidColorBrush` do słownika zasobów do użycia jako `StaticResource`.</br>Uwaga: zasoby statyczne, konwertery stylów i inne elementy, które są zapisywane w słowniku zasobów, można stosować/używać podczas korzystania z usługi XAML. Tylko tworzenie zasobu nie jest obsługiwane.</br> Zmiana właściwości `Source` słownika zasobów.|
|Dodawanie nowych kontrolek, klas, okien lub innych plików do projektu, gdy aplikacja jest uruchomiona|Nieobsługiwane|Nieobsługiwane|None|
|Zarządzanie pakietami NuGet (Dodawanie/usuwanie/aktualizowanie pakietów)|Nieobsługiwane|Nieobsługiwane|None|
|Zmiana powiązania danych korzystającego z rozszerzenia znacznika {x:Bind}|Nie dotyczy|Obsługiwane począwszy od programu Visual Studio 2019|Wymaga to systemu Windows 10 w wersji 1809 (Kompilacja 10.0.17763). Nieobsługiwane w programie Visual Studio 2017 lub starszych wersjach.|
|Zmiana dyrektyw X:UID — nie jest obsługiwana|Nie dotyczy|Nieobsługiwane|None|

## <a name="error-messages"></a>Komunikaty o błędach

Podczas korzystania ze gorącego ładowania kodu XAML mogą występować następujące błędy.

|Komunikat o błędzie|Opis|
|-|-|
|Sprawdź, czy zdarzenie nie powiodło się|Błąd oznacza, że próbujesz obsłużyć zdarzenie do jednej z kontrolek, co nie jest obsługiwane, gdy aplikacja jest uruchomiona.|
|Ta zmiana nie jest obsługiwana przez kod XAML gorącego ładowania i nie zostanie zastosowana podczas sesji debugowania.|Błąd oznacza, że próba zmiany nie jest obsługiwana przez kod XAML. Zatrzymaj sesję debugowania, wprowadź zmianę, a następnie ponownie uruchom sesję debugowania. Jeśli znajdziesz nieobsługiwany scenariusz, który chcesz zobaczyć, użyj nowej opcji "Sugeruj funkcję" w [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). |

## <a name="see-also"></a>Zobacz też

* [Rozwiązywanie problemów z aktywnym załadowaniem XAML](xaml-hot-reload-troubleshooting.md)
* [Przeładowywanie kodu XAML na gorąco dla zestawu narzędzi Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload)
* [Edytuj i kontynuuj (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
