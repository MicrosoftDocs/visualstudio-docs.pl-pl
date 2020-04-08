---
title: Pisanie i debugowanie xaml przy użyciu funkcji XAML Hot Reload
description: XAML Hot Reload lub XAML edit and continue umożliwia wprowadzanie zmian w kodzie XAML podczas uruchamiania aplikacji
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
ms.openlocfilehash: 120ae30b3a33a04f17bd2ec23b747ac41c9427cf
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880094"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Pisanie i debugowanie z uruchomionym kodem XAML z załaduj gorącą ładować xaml w programie Visual Studio

XAML Hot Reload pomaga tworzyć interfejs użytkownika aplikacji WPF lub platformy uniwersalnej systemu wytwórczym (UI), umożliwiając wprowadzanie zmian w kodzie XAML, gdy aplikacja jest uruchomiona. Hot Reload jest dostępny zarówno w programie Visual Studio, jak i w programie Blend for Visual Studio. Ta funkcja umożliwia przyrostowe tworzenie i testowanie kodu XAML z korzyścią dla kontekstu danych uruchomionej aplikacji, stanu uwierzytelniania i innych rzeczywistych złożoności, które są trudne do symulacji w czasie projektowania. Jeśli potrzebujesz pomocy w rozwiązywaniu problemów z ładowaniem gorąca XAML, zobacz [Rozwiązywanie problemów z ładowaniem gorąca XAML](xaml-hot-reload-troubleshooting.md) zamiast tego.

> [!NOTE]
> Jeśli używasz xamarin.Forms, zobacz [XAML Hot Reload for Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload).

XAML Hot Reload jest szczególnie przydatne w tych scenariuszach:

* Rozwiązywanie problemów z interfejsem użytkownika znalezionych w kodzie XAML po uruchomieniu aplikacji w trybie debugowania.

* Tworzenie nowego składnika interfejsu użytkownika dla aplikacji, która jest w fazie rozwoju, przy jednoczesnym wykorzystaniu kontekstu środowiska uruchomieniowego aplikacji.

|Obsługiwane typy aplikacji|System operacyjny i narzędzia|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+ i .NET Core</br>Windows 7 i powyżej |
|Uniwersalne aplikacje systemu Windows (UWP)|Windows 10 i powyżej, z [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393+ |

Na poniższej ilustracji przedstawiono użycie dynamicznego drzewa wizualnego do otwierania kodu źródłowego, a następnie załaduj ponownie na gorąco xaml, aby zmienić tekst przycisku i kolor przycisku.

![Ponowne ładowanie przy aktywnym kodzie XAML](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Visual Studio XAML Hot Reload jest obecnie obsługiwany tylko podczas uruchamiania aplikacji w programie Visual Studio lub Blend for Visual Studio z dołączonym debugerem **(F5** lub **Start debugowania).** Nie można włączyć tego środowiska za pomocą [Dołącz do przetwarzania,](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) chyba że [ręcznie ustawić zmienną środowiskową](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process).

## <a name="known-limitations"></a>Znane ograniczenia

Poniżej przedstawiono znane ograniczenia ładowania gorąca XAML. Aby obejść wszelkie ograniczenia, które można uruchomić, wystarczy zatrzymać debugera, a następnie zakończyć operację.

|Ograniczenia|WPF|Platforma UWP|Uwagi|
|-|-|-|-|
|Zdarzenia okablowania do sterowania, gdy aplikacja jest uruchomiona|Nieobsługiwane|Nieobsługiwane|Zobacz błąd: *Upewnij się, że zdarzenie nie powiodło się*. Należy zauważyć, że w WPF można odwołać się do istniejącego programu obsługi zdarzeń. W aplikacjach platformy uniwersalnej systemu Windows odwoływanie się do istniejącego programu obsługi zdarzeń nie jest obsługiwane.|
|Tworzenie obiektów zasobów w słowniku zasobów, takich jak obiekty w oknie/oknie aplikacji lub *app.xaml*|Obsługiwane począwszy od aktualizacji 2 programu Visual Studio 2019|Obsługiwane|Przykład: dodawanie `SolidColorBrush` do słownika zasobów do `StaticResource`użycia jako plik .</br>Uwaga: Zasoby statyczne, konwertery stylów i inne elementy zapisane w słowniku zasobów mogą być stosowane/używane podczas korzystania z funkcji XAML Hot Reload. Tylko tworzenie zasobu nie jest obsługiwane.</br> Zmiana `Source` właściwości słownika zasobów.|
|Dodawanie nowych formantów, klas, okien lub innych plików do projektu, gdy aplikacja jest uruchomiona|Nieobsługiwane|Nieobsługiwane|Brak|
|Zarządzanie pakietami NuGet (dodawanie/usuwanie/aktualizowanie pakietów)|Nieobsługiwane|Nieobsługiwane|Brak|
|Zmienianie powiązania danych, które używa rozszerzenia znaczników {x:Bind}|Nie dotyczy|Obsługiwane od programu Visual Studio 2019|Wymaga to systemu Windows 10 w wersji 1809 (kompilacja 10.0.17763). Nie jest obsługiwana w programie Visual Studio 2017 lub poprzednich wersjach.|
|Zmiana x:Uid dyrektyw nie jest obsługiwana|Nie dotyczy|Nieobsługiwane|Brak|
|Wiele procesów | Nieobsługiwane | Nieobsługiwane | Hot reload może być używany tylko przeciwko 1 proces naraz. |

## <a name="error-messages"></a>Komunikaty o błędach

Podczas korzystania z funkcji XAML Hot Reload można natknąć się na następujące błędy.

|Komunikat o błędzie|Opis|
|-|-|
|Upewnij się, że zdarzenie nie powiodło się|Błąd wskazuje, że próbujesz podłączyć zdarzenie do jednego z formantów, który nie jest obsługiwany, gdy aplikacja jest uruchomiona.|
|Ta zmiana nie jest obsługiwana przez XAML Hot Reload i nie zostaną zastosowane podczas sesji debugowania.|Błąd wskazuje, że zmiana, którą próbujesz, nie jest obsługiwana przez ponowne ładowanie gorąca XAML. Zatrzymaj sesję debugowania, wykonuj zmiany, a następnie uruchom ponownie sesję debugowania. Jeśli znajdziesz nieobsługicony scenariusz, który chcesz wyświetlić obsługiwane, użyj naszej nowej opcji "Zaproponuj funkcję" w [społeczności deweloperów programu Visual Studio.](https://developercommunity.visualstudio.com/spaces/8/index.html) |

## <a name="see-also"></a>Zobacz też

* [Rozwiązywanie problemów z ponownym ładowaniem przy aktywnym kodzie XAML](xaml-hot-reload-troubleshooting.md)
* [XAML Hot Reload dla platformy Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload)
* [Edytuj i kontynuuj (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
