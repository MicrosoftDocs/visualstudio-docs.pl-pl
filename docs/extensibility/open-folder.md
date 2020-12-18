---
title: Omówienie rozszerzalności otwartych folderów programu Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: overview
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 964b360806f6f834aa57c475d2117c124f2cf8af
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668641"
---
# <a name="open-folder-extensibility"></a>Rozszerzalność folderu Open

Funkcja [Otwórz folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) umożliwia użytkownikom otwieranie dowolnej bazy kodu w programie Visual Studio bez konieczności stosowania plików projektu lub rozwiązania. Folder Otwórz zawiera funkcje, których użytkownicy oczekują od programu Visual Studio, na przykład:

* Eksplorator rozwiązań integrację i wyszukiwanie
* Kolorowanie edytora
* Przejdź do nawigacji
* Wyszukiwanie w poszukiwaniu plików

W przypadku użycia z obciążeniami, takimi jak dla programowania .NET i C++, użytkownicy otrzymują również następujące możliwości:

* Zaawansowana technologia IntelliSense
* Funkcje specyficzne dla języka

Za pomocą folderu Open folder autorzy rozszerzeń mogą tworzyć bogate funkcje w dowolnym języku. Istnieją interfejsy API do obsługi kompilowania, debugowania i wyszukiwania symboli dla dowolnego pliku w bazie kodu użytkownika. Obecnie rozszerzalne mogą zaktualizować swoje istniejące funkcje programu Visual Studio, aby zrozumieć kod bez tworzenia kopii zapasowej projektów lub rozwiązania.

## <a name="an-api-without-project-systems"></a>Interfejs API bez systemów projektów

W przeszłości program Visual Studio zrozumiał tylko pliki w rozwiązaniu i jego projektach korzystających z systemów projektów. System projektu jest odpowiedzialny za funkcje i interakcje użytkownika dla załadowanego projektu. Zrozumienie, jakie pliki zawiera projekt, wizualna reprezentacja zawartości projektu, zależności od innych projektów i modyfikacja bazowego pliku projektu. Są to hierarchie i możliwości, które inne składniki działają w imieniu użytkownika. Nie wszystkie bazy kodu są dobrze reprezentowane w strukturze projektu i rozwiązania. Przydatne przykłady języków skryptów i kodu open source pisanego w języku C++ dla systemu Linux. Za pomocą folderu Open folder Program Visual Studio zapewnia użytkownikom nowy sposób współpracy z kodem źródłowym.

Interfejsy API otwartego folderu znajdują się pod `Microsoft.VisualStudio.Workspace.*` przestrzenią nazw i są dostępne dla rozszerzeń, które umożliwiają tworzenie i używanie danych lub akcji związanych z plikami w otwartym folderze. Rozszerzenia mogą korzystać z tych interfejsów API w celu zapewnienia funkcjonalności wielu obszarów, w tym:

- [Obszary robocze](workspaces.md) — punkt początkowy rozszerzalności rozszerzeń otwartych folderów to obszar roboczy i jego interfejsy API.
- [Konteksty pliku i akcje](workspace-file-contexts.md) — Analiza kodu specyficzna dla pliku dostępna za poorednictwem kontekstów plików.
- [Indeksowanie](workspace-indexing.md) — zbieranie i utrwalanie danych dotyczących otwartych obszarów roboczych folderu.
- [Usługi językowe](workspace-language-services.md) — Integruj usługi językowe z obszarami roboczymi otwartych folderów.
- [Kompilacja](workspace-build.md) — obsługa kompilacji dla obszarów roboczych otwartych folderów.

Do obsługi otwartych folderów należy zastosować nowe interfejsy API, które używają następujących typów:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Opinie, komentarze, problemy

Otwarte foldery i `Microsoft.VisualStudio.Workspace.*` interfejsy API są w trakcie aktywnego programowania. Jeśli widzisz nieoczekiwane zachowanie, zobacz znane problemy związane z jego wersją. [Społeczność deweloperów](https://aka.ms/feedback/suggest?space=8) jest zalecanym miejscem do głosowania i tworzenia wszelkich problemów. Dla każdej opinii zdecydowanie zalecamy szczegółowy opis problemu. Uwzględnij wersję programu Visual Studio, z której korzystasz, używane interfejsy API (zarówno zaimplementowane elementy, jak i informacje, z którymi prowadzisz działania), oczekiwany wynik i rzeczywisty wynik. Jeśli to możliwe, Uwzględnij zrzut procesu devenv.exe. Skorzystaj ze śledzenia problemów usługi GitHub, aby przekazać opinię na temat tej i powiązanej dokumentacji.

## <a name="next-steps"></a>Następne kroki

* [Obszary robocze](workspaces.md) — informacje o interfejsie API obszaru roboczego otwartego folderu.