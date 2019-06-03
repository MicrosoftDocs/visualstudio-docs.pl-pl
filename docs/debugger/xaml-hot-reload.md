---
title: Twórz i Debuguj XAML przy użyciu XAML gorąca Załaduj ponownie
description: Załaduj ponownie XAML gorąca lub XAML, Edytuj i Kontynuuj, pozwala wprowadzić zmiany w kodzie XAML podczas uruchamiania aplikacji
ms.custom: ''
ms.date: 02/28/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f526cc8d5ff7835b3d0b942325f5755898fad147
ms.sourcegitcommit: c6249a8f3054db881ba62f4e80bf006d440f5a2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2019
ms.locfileid: "66462145"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Pisanie i debugowanie kodu XAML z gorącej ponownego ładowania XAML w programie Visual Studio

Visual Studio XAML gorąca Załaduj ponownie ułatwia tworzenie aplikacji WPF lub platforma UWP interfejsu użytkownika, dzięki czemu można było wprowadzać zmiany do kodu XAML, gdy aplikacja jest uruchomiona. Ta funkcja umożliwia przyrostowe kompilowanie i testowanie kodu XAML i czerpać korzyści z kontekstu danych w uruchomionej aplikacji, stan uwierzytelniania i innych złożoności świata rzeczywistego, który jest trudny do symulacji w czasie projektowania.

Załaduj ponownie gorąca XAML jest szczególnie przydatne w następujących scenariuszach:

* Rozwiązywanie problemów z interfejsu użytkownika można odnaleźć w kodzie XAML po uruchomieniu aplikacji była w trybie debugowania.

* Kompilowanie nowy składnik interfejsu użytkownika dla aplikacji, która jest w fazie projektowania, przy wykorzystaniu możliwości kontekst czasu wykonywania aplikacji.

|Typy aplikacji obsługiwane|System operacyjny i narzędzia|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+</br>Windows 7 i nowsze wersje |
|Windows Universal apps (UWP)|System Windows 10 i nowsze wersje z [systemu Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

> [!NOTE]
> Visual Studio XAML, gorąca reload jest obecnie obsługiwany tylko w przypadku uruchamiania aplikacji w programie Visual Studio w debugerze (**F5** lub **Rozpocznij debugowanie**). Nie można włączyć to środowisko za pomocą *dołączyć do procesu*.

## <a name="known-limitations"></a>Znane ograniczenia

Poniżej przedstawiono znane że ograniczenia XAML hot Załaduj ponownie. Aby uniknąć wszelkich ograniczenie, które wystąpiły, po prostu Zatrzymaj debuger, a następnie ukończ operację.

|Ograniczenie|WPF|Platforma UWP|Uwagi|
|-|-|-|-|
|Dołączenie zdarzenia do formantów, gdy aplikacja jest uruchomiona|Nieobsługiwane|Nieobsługiwane|Wyświetlony błąd: *Upewnij się, zdarzeń nie powiodło się*|
|Tworzenie obiektów zasobu w słowniku zasobów, takich jak te w okno strona Twojej aplikacji lub *App.xaml*|Nieobsługiwane|Obsługiwane|Przykład: dodawanie ```SolidColorBrush``` do słownika zasobów do użycia jako ```StaticResource```.</br>Uwaga: Zasoby statyczne, styl konwerterów i inne elementy zapisywane do słownika zasobów może być stosowane używane podczas korzystania z gorącej ponownego ładowania XAML. Tworzenie zasobu nie jest obsługiwane.</br> Zmiana słownika zasobów ```Source``` właściwości.| 
|Dodawanie nowych kontrolek, klasy, systemu windows lub inne pliki do projektu, gdy aplikacja jest uruchomiona|Nieobsługiwane|Nieobsługiwane|Brak|
|Zarządzanie pakietami NuGet (Dodawanie/usuwanie/aktualizowania pakietów)|Nieobsługiwane|Nieobsługiwane|Brak|
|Zmieniającymi się danymi powiązania, który używa rozszerzenia znaczników {rozszerzenia x: Bind}|Brak|Obsługiwane w programie Visual Studio 2019 r i nowszych wersjach|Nie są obsługiwane w programie Visual Studio 2017 lub starszych wersji|

## <a name="error-messages"></a>Komunikaty o błędach

Podczas korzystania z gorącej ponownego ładowania XAML mogą pochodzić między następujące błędy.

|Komunikat o błędzie|Opis|
|-|-|-|
|Upewnij się, zdarzeń nie powiodło się|Błąd wskazuje, że próbujesz powiązać zdarzenia do jednego z kontrolkom, które nie jest obsługiwana, gdy aplikacja jest uruchomiona.|
|Edytuj XAML i Kontynuuj nie znalazła elementów do zaktualizowania.|Błąd występuje, gdy edytujesz XAML, który gorąca Załaduj ponownie nie można zaktualizować w swojej aplikacji.</br> Czasami można naprawić ten błąd za pomocą uruchomionej aplikacji można przejść do widoku XAML jest używane w sytuacji.</br> Czasami ten błąd oznacza, że nie można zastosować określonej zmiany dopiero po ponownym uruchomieniu sesji debugowania. |
|Ta zmiana nie jest obsługiwana podczas sesji debugowania.|Błąd wskazuje, czy zmiana, którą próbujesz nie jest obsługiwana przez gorąca ponownego ładowania XAML. Zatrzymaj sesję debugowania, wprowadzić zmiany, a następnie uruchom ponownie sesję debugowania.|
