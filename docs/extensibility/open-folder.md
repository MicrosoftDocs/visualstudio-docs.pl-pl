---
title: Przegląd rozszerzalności usługi Visual Studio, otwórz Folder | Dokumentacja firmy Microsoft
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2bb74703f639848d643f536edf620e30b1836310
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986014"
---
# <a name="open-folder-extensibility"></a>Otwórz Folder rozszerzalności

[Otwórz Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) funkcja umożliwia użytkownikom otworzyć dowolny bazy kodu w programie Visual Studio bez konieczności plików projektu ani rozwiązania. Otwórz Folder zapewnia, że użytkownicy funkcji oczekiwać od programu Visual Studio, takich jak:

* Integracja z Eksploratorem rozwiązań i wyszukiwanie
* Kolorowanie edytora
* Przejdź do nawigacji
* Znajdź w plikach wyszukiwania

W przypadku użycia z obciążeniami takie samo jak w przypadku programowania .NET i C++, użytkownicy również otrzymać:

* Rozbudowana funkcja Intellisense
* Funkcje językowe

Otwórz Folder twórcy rozszerzenia umożliwia tworzenie zaawansowanych funkcji w dowolnym języku. Brak interfejsów API do obsługi tworzenia, debugowania i wyszukiwania symboli dla każdego pliku w użytkownika ścieżce bazowej kodu zespołu. Bieżący rozszerzeń można zaktualizować ich istniejących funkcji programu Visual Studio, aby zrozumieć kod bez zapasowego projektów lub rozwiązań.

## <a name="an-api-without-project-systems"></a>Interfejs API bez systemy projektu

W przeszłości Visual Studio rozumieć pliki w rozwiązaniu i jego projekty, korzystając z systemów projektu. System projektu jest odpowiedzialny za interakcje funkcji i użytkownika załadowanego projektu. Sam co pliki projekt zawiera wizualnej reprezentacji treści projektu zależności w innych projektach i modyfikacji elementu bazowego pliku projektu. Jest za pośrednictwem tych hierarchie i możliwości, które inne składniki działają w imieniu użytkownika. Nie wszystkie ścieżek bazowych kodów również są reprezentowane w strukturze projektu i rozwiązania. Języki skryptów i kodu typu open source napisana w języku C++ dla systemu Linux są dobre przykłady. Z otwartego folderu programu Visual Studio zapewnia użytkownikom nowy sposób interakcji z kodu źródłowego.

Otwarte interfejsy API w folderze znajdują się pod `Microsoft.VisualStudio.Workspace.*` przestrzeni nazw są dostępne dla urządzenia Extender do tworzenia i wykorzystywania danych lub akcje wokół pliki znajdujące się w otwartym folderze. Rozszerzenia można użyć tych interfejsów API umożliwiają korzystanie z funkcji do wielu obszarów, takich jak:

- [Obszary robocze](workspaces.md) — od punktu funkcja otwierania folderu rozszerzeń jest obszar roboczy i jej interfejsów API.
- [Plik kontekstów i akcje](workspace-file-contexts.md) — plik określonego kodu analizy dostępne za pośrednictwem konteksty plików.
- [Indeksowanie](workspace-indexing.md) — zbierania, i utrwalić dane dotyczące obszarów roboczych Otwórz Folder.
- [Usługi języka](workspace-language-services.md) -Integrowanie usług językowych Otwórz Folder w obszarach roboczych.
- [Tworzenie](workspace-build.md) — Obsługa otwierania folderu obszarów roboczych kompilacji.

Funkcje, które korzystają z następujących typów należy przyjąć nowe interfejsy API do obsługi Otwórz Folder:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Opinie, komentarze, problemy

Otwórz Folder i `Microsoft.VisualStudio.Workspace.*` interfejsy API są opracowywane active. Jeśli widzisz nieoczekiwane zachowanie, zobacz znane problemy dotyczące wersji zainteresowania. [Społeczność deweloperów](https://developercommunity.visualstudio.com) jest to zalecane miejsce do głosowania i utworzyć wszelkie problemy. Dla każdej informacji zwrotnych zdecydowanie zalecamy szczegółowy opis problemu. Obejmują wersji programu Visual Studio, którą tworzysz oprogramowanie, interfejsów API, używasz (zastało zaimplementowane i jakie są interakcje z), oczekiwany wynik i rzeczywistym wynikiem. Jeśli to możliwe obejmują zrzut procesu devenv.exe. Użyj śledzenie wyrażanie opinii na ten problem z serwisu GitHub i związane z dokumentacją.

## <a name="next-steps"></a>Następne kroki

* [Obszary robocze](workspaces.md) — informacje o obszarze roboczym otwórz Folder interfejsu API.