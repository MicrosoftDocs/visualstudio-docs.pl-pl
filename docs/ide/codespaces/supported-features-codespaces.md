---
title: Obsługiwane funkcje programu Visual Studio (wersja zapoznawcza)
description: Dowiedz się więcej o funkcjach środowiska IDE programu Visual Studio dostępnych podczas pracy z usługą GitHub Codespaces.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 68fbdef0e86b125971480ae1bd6a7ba6d3108cd8
ms.sourcegitcommit: 74b67f102d243e3b74a93563e834f49df298e4b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2020
ms.locfileid: "97696535"
---
# <a name="supported-visual-studio-features-preview"></a>Obsługiwane funkcje programu Visual Studio (wersja zapoznawcza)

Program Visual Studio zapewnia rozbudowane środowisko programistyczne podczas nawiązywania połączenia z usługą codespace. Uzyskasz narzędzia wewnętrznej pętli programu Visual Studio, które znasz, aby edytować, debugować, testować i korzystać z kodu źródłowego, a także funkcje produktywności, takie jak szablony projektów, rozbudowana Nawigacja w kodzie i technologia IntelliSense.

W bieżącej [publicznej wersji beta](https://github.com/features/codespaces)usługi GitHub Codespaces niektóre funkcje programu Visual Studio mogą nie mieć pełnej obsługi lub mogą być początkowo niedostępne. W poniższych sekcjach znajdują się informacje o tym, czego można oczekiwać od programu Visual Studio i wersji beta usługi GitHub Codespaces. 

Nie jest to **pełna lista**, ale w celu wyjaśnienia ogólnych możliwości programu Visual Studio w przypadku połączenia z usługą codespace.

> [!NOTE]
> Jeśli w programie Visual Studio nie ma żadnej funkcji, powiadom nas, otwierając problem w [społeczności deweloperów programu Visual Studio](https://aka.ms/feedback/suggest?space=8). Pomaga nam określić priorytety najbardziej pożądanych funkcji.

> [!NOTE]
> Funkcje opisane poniżej dotyczą programu Visual Studio, a nie dwóch innych klientów Codespaces usługi GitHub. Visual Studio Code i Edytor w przeglądarce.

## <a name="edit-and-navigation"></a>Edytuj i nawigacyjny

Podczas pobierania funkcji języka inteligentnego, takich jak IntelliSense, nawigowanie po kodzie, Diagnostyka i sugestie, należy zauważyć, że nie trzeba edytować kodu źródłowego w codespace.

* Technologia
* Nawigacja po kodzie *
* Formatowanie kodu z dokumentem formatu
* Podświetlanie składni
* Szybkie informacje *
* HTML, CSS, edytory Razor *-częściowa pomoc techniczna.
* Obsługa języka JavaScript i edytora TypeScript * — częściowa pomoc techniczna.

Jeszcze niedostępne:

* IntelliSense * — niektóre filtry autouzupełniania/listy składowych są niedostępne. Uzupełnianie dla nieimportowanych typów i IntelliSense w oknie czujki nie jest jeszcze dostępne.
* Nawigacja po kodzie * — większość poleceń jest obsługiwanych. Przejdź do bazy i Znajdź w plikach ze specyfikacją ścieżki nie są jeszcze obsługiwane.
* Szybkie informacje * — kolorowanie w szybkich informacjach nie jest obsługiwane.
* HTML, CSS, edytory Razor * — Diagnostyka, uzupełnianie IntelliSense, szybkie informacje, inteligentne wcięcie. Obecnie nie jest obsługiwane kolorowanie semantyczne, polecenia nawigacji itp.
* Skrypty JavaScript i TypeScript Editor *-bloki skryptów (na przykład zawartość JavaScript w plikach HTML i CSHTML) i wyróżnianie semantyczne nie są jeszcze obsługiwane. Znane problemy związane z funkcjami żarówki i zaznaczanie błędów.
* Widok elementów docelowych CMake
* Edytor ustawień projektu CMake
* Ctrl + F7 (Kompilowanie pliku)
* CodeLens
* Fragmenty kodu
* IntelliCode

## <a name="application-types-and-configuration"></a>Typy i konfiguracja aplikacji

Obsługiwane są większość typów aplikacji i konfiguracji projektu, ale konieczna będzie Edycja kodu projektu bezpośrednio bez pomocy dla projektantów wizualizacji. Aby uzyskać więcej wskazówek dotyczących konfiguracji, zobacz [How to Dostosowywanie codespace](customize-codespaces.md).

* Szablony projektów i elementów
* Projekty .NET Core i ASP.NET Core
* Aplikacje konsolowe języka C++ — obsługiwane są CMake i vcxproj
* Aplikacje języka C++ przeznaczone dla systemu Linux — przede wszystkim obsługują dla innych niż graficznego interfejsu użytkownika. Możliwość instalacji i aprowizacji WSL, technologii IntelliSense i kompilacji dla platformy.
* Edytowanie plików projektu — głównie obsługiwane. Brak niektórych funkcji uzupełniania, wyróżniania składni i zaawansowanej edycji.
* Konta usługi GitHub — mogą służyć do tworzenia i łączenia się z usługą Codespaces oraz uzyskiwania dostępu do zasobów dostępnych dla konta w usłudze GitHub.
* Interfejs wiersza polecenia platformy Azure — nie udostępnia tożsamości zalogowanego programu Visual Studio ani kont łańcucha kluczy. Logowanie oparte na przeglądarce nie jest obsługiwane, ale można przeprowadzić uwierzytelnianie wewnątrz zintegrowanego terminalu przy użyciu: `az login --use-device-code` .

Jeszcze niedostępne:

* Projektanci interfejsu użytkownika — WinForms, WPF i projektantów zasobów
* Projekty Visual Basic i F #
* .NET Framework projekty skierowane
* Projekty Docker Compose
* Strony właściwości projektu
* Opcje uwierzytelniania w szablonach ASP.NET Core
* Aplikacje wymagające graficznego interfejsu użytkownika do zainstalowania — wszystkie elementy, które mogą być instalowane z terminalem, są obsługiwane (w tym Instalatora czekolady), ale rzeczywisty interfejs GUI nie będzie natychmiast dostępny. Aby można było uzyskać dostęp do GUI, należy włączyć pełny Live Share ekran. Konsole administracyjne nie są dostępne. Aplikacje, które wymagają ponownego uruchomienia w celu instalacji, nie są obsługiwane.
* Zarządzane tożsamości dla zasobów platformy Azure w programie Visual Studio
* Zasoby intranetowe (sieć prywatna) — obecnie codespaces nie będzie w stanie połączyć się z żadnym zasobem, który wymaga sieci VPN.
* Rozszerzenia — żadne rozszerzenia nie są obsługiwane w przypadku używania Codespaces z programem Visual Studio.

## <a name="debugging"></a>Debugowanie

Obsługiwane jest podstawowe debugowanie pętli wewnętrznej, w tym ustawianie punktów przerwania, podstawowe przechodzenie do kodu, sprawdzanie zmiennych i okien lokalnych, Autostart i Czujka. Niektóre dodatkowe okna, dostosowania i Wizualizatory nie są obsługiwane.

* Punkty przerwania
* Podstawowe przechodzenie
* Elementy lokalne, autostarty, Watch Windows * — obsługa częściowa.
* Wszystkie częściowo obsługiwane są wszystkie porady dotyczące serwera symboli, serwera źródłowego i importowania/eksportowania danych.

Jeszcze niedostępne:

* Punkty przerwania * — etykiety punktów przerwania, punkty przerwania danych i ustaw punkt przerwania w oknie demontażu są w toku. Importowanie i eksportowanie punktów przerwania jest obsługiwane częściowo.
* Locale, autostarts, Watch Windows * — niektóre funkcje, takie jak uzupełnianie instrukcji w polu wyszukiwania i nawigowanie w polu wyszukiwania.
* Dostosowania interfejsu użytkownika — właściwości Pinnable i Ukryj parametry szablonu nie są obsługiwane.
* Wizualizatory — obsługiwana częściowo obsługa języka C++. Okno demontaż, Diagnostyka wizualna XAML, niestandardowe Wizualizatory platformy .NET i Wizualizatory zestawu danych nie są obsługiwane.
* Dodatkowe okna debugera — procesy obsługiwane częściowo przez system Windows. Okno stosów równoległych — widok zadań, centrum diagnostyki oraz okno dialogowe Znajdowanie źródła/symboli nie są obsługiwane.
* Niektóre przepływy pracy debugera — Dołącz do procesu, debuger just in Time (JIT), debugowanie zrzutów, profilowanie i IntelliTrace nie są obsługiwane. Przechodzenie w języku C++ Tylko mój kod jest częściowo obsługiwane.
* Edytuj i Kontynuuj — nieobsługiwane dla kodu zarządzanego i natywnego.
* Funkcje wątkowe — blokowanie/odblokowywanie wątków, zmiana nazwy wątku i wyświetlanie wątków w źródle nie są obsługiwane.
* Dodatkowe funkcje krok po kroku — automatyczne przechodzenie nad właściwościami i operatorami (.NET Core) i wkroczenie do określonych nie jest obsługiwane. 

## <a name="features"></a>Funkcje

Podczas pracy z programem Visual Studio połączonym z codespace uzyskasz te same funkcje ułatwień dostępu jak podczas pracy lokalnie.

* Kontrola źródła — pełna obsługa Git za pomocą nowego [zintegrowanego środowiska git](../git-with-visual-studio.md).
* Ułatwienia dostępu — istnieje jeden znany problem z technologią pomocniczą, która nie może uzyskać dostępu do appcasting debugowanej aplikacji. Oprócz tego ograniczenia nie uważamy, że istnieją inne problemy ze zgodnością, które jeszcze nie istnieją w lokalnym środowisku programu Visual Studio. Skontaktuj się z nami, jeśli wykryjesz usterki przez zgłoszenie problemu w [społeczności deweloperów](https://aka.ms/feedback/report?space=8).
* Publikowanie-publikowanie na platformie Azure za pomocą akcji GitHub jest obsługiwane.
* Połączone usługi — Usługa App Insights, Magazyn kluczy, magazyn, SQL, Redis, Cosmos, openAPI i gRPC są częściowo obsługiwane.
* Eksplorator testów * — głównie obsługiwane.

Jeszcze niedostępne:

* Eksplorator testów * — niektóre funkcje, takie jak domyślna architektura wyboru, uruchamianie testów równolegle, list odtwarzania itp. Znane problemy związane z debugowaniem testów jednostkowych, uruchamianiem ustawień i niektórymi dodatkowymi funkcjami przedsiębiorstwa. Profilowanie testów jednostkowych nie jest obsługiwane.
* Interfejs użytkownika Menedżera pakietów NuGet — wiersz polecenia NuGet jest obsługiwany.
* Funkcje testowania dla przedsiębiorstw — Live Unit Testing, fałszywe firmy Microsoft, pokrycie kodu i IntelliTest nie są obsługiwane.
* Zaawansowane scenariusze publikowania — publikowanie selektywne, publikowanie FTP, Podgląd zmian, pasek narzędzi szybkiej publikacji itp.

## <a name="see-also"></a>Zobacz też

* [Co to jest GitHub Codespaces?](codespaces-overview.md)
* [Jak używać programu Visual Studio z codespace](use-visual-studio-with-codespaces.md)
* [Jak dostosować codespace](customize-codespaces.md)
