---
title: Projektowanie XAML w programie Visual Studio i narzędziu Blend
titleSuffix: ''
ms.date: 08/05/2019
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ec10ea271fad4c49402e75ad7f8b5a84ad287cea
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188878"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Projektuj kod XAML w programie Visual Studio i Blend for Visual Studio

Programy Visual Studio i Blend for Visual Studio oferują narzędzia wizualne do tworzenia atrakcyjnych interfejsów użytkownika i bogate środowiska multimedialne przy użyciu języka XAML dla różnych typów aplikacji. Oba zintegrowane środowiska deweloperskie (IDE) udostępniają wspólny zestaw funkcji, w tym edytor języka Visual XAML (Projektant). Blend for Visual Studio, który obsługuje platformy WPF i platformy UWP, oferuje dodatkowe narzędzia do projektowania Stanów wizualnych i tworzenia animacji.

Można przełączać się między programem Visual Studio i Blend for Visual Studio, a nawet w tym samym czasie może być otwarty w obu środowisk ideach. Zmiany zapisane w plikach XAML w jednym środowisku IDE mogą być stosowane przez automatyczne ponowne ładowanie po przełączeniu do innego środowiska IDE. Możesz kontrolować zachowanie ponownego ładowania, przechodząc do **narzędzi**  > **opcje**  > **środowisku**  > **dokumenty** w obu IDE.

## <a name="installation"></a>Instalacja

- Aby utworzyć aplikacje WPF, zainstaluj obciążenie **Programowanie aplikacji klasycznych platformy .NET** w programie Visual Studio. Zostanie również zainstalowany Blend for Visual Studio.
- Aby tworzyć aplikacje platformy UWP, zainstaluj obciążenie **programowanie platforma uniwersalna systemu Windows** w programie Visual Studio. Zostanie również zainstalowany Blend for Visual Studio.
- Aby utworzyć aplikacje platformy Xamarin. Forms, zainstaluj **Programowanie aplikacji mobilnych przy użyciu obciążenia .NET** w programie Visual Studio. *Nie* zainstalowano Blend for Visual Studio. Program Blend nie obsługuje aplikacji Xamarin. Forms.

## <a name="shared-capabilities"></a>Udostępnione możliwości

W przypadku większości podstawowych zadań programistycznych program Visual Studio i Blend for Visual Studio współdzielą ten sam zestaw okien i możliwości z niewielkimi różnicami. Niektóre najważniejsze elementy to:

- Funkcja **IntelliSense:** Obie środowisk IDE obsługują funkcje IntelliSense, takie jak uzupełnianie instrukcji.

- **Debugowanie:** Można debugować w programie [Visual Studio](../debugger/inspect-xaml-properties-while-debugging.md) i [Blend for Visual Studio](../xaml-tools/debug-xaml-in-blend.md), w tym ustawienia punktów przerwania w kodzie, aby debugować działającą aplikację i za pomocą funkcji [ponownego ładowania](../xaml-tools/xaml-hot-reload.md) , można zmienić kod XAML, gdy aplikacja jest uruchomiona. Aby zachować spójne środowisko debugowania w programie Visual Studio, Blend for Visual Studio zawiera większość okien debugowania i pasków narzędzi programu Visual Studio.

- **Załaduj plik:** Pliki XAML można edytować w programie Visual Studio lub Blend for Visual Studio. Edytowane pliki, które zostały zapisane automatycznie Załaduj, podczas przełączania między środowisk IDE. Możesz kontrolować zachowanie ponownego ładowania, przechodząc do **narzędzi**  > **opcje**  > **środowisku**  > **dokumenty** w obu IDE.

- **Zsynchronizowane układy i ustawienia:** Niestandardowe preferencje okna narzędzi i ustawienia dla programu Visual Studio lub Blend for Visual Studio są synchronizowane przez urządzenia i wersje po zalogowaniu się przy użyciu tego samego konta personalizacji. Zobacz [Synchronizowanie ustawień na wielu komputerach](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Zaawansowane możliwości w Blend for Visual Studio

Aby zwiększyć produktywność, należy rozważyć użycie Blend for Visual Studio dla następujących zadań. Poniżej znajdują się obszary, w których Blend for Visual Studio oferuje więcej funkcji niż Projektant lub sam kod programu Visual Studio.

| Zadanie | Visual Studio | Blend for Visual Studio | Więcej informacji |
| - | - | - | - |
| **Projektowanie Stanów wizualnych** | Nie jest dostępne żadne narzędzie ułatwiające projektowanie Stanów wizualnych; należy je tworzyć programowo. | Narzędzia do projektowania umożliwiają zmianę wyglądu kontrolki na podstawie jej stanu. | [Stany wizualne](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Tworzenie animacji** |Nie istnieje narzędzie projektowania dla animacji; należy je tworzyć programowo. Wymaga to wiedzy na temat animacji i systemu chronometrażu w WPF i obszernej znajomości kodu.|Animacje można tworzyć wizualnie i wyświetlać je w Blend for Visual Studio. Jest to szybsze i bardziej dokładne niż Kompilowanie animacji w kodzie. Możesz dodać wyzwalacze do obsługi interakcji z użytkownikiem i można przełączyć się do kodu, aby dodać programy obsługi zdarzeń i inne funkcje.|[Animowanie obiektów](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Przekształcanie kształtów i tekstu w ścieżki w celu ułatwienia manipulowania**|Nieobsługiwane.|Można wprowadzać delikatne lub znaczące zmiany w kształtach (takich jak prostokąty i wielokropki), konwertując je na ścieżki, co zapewnia lepszą kontrolę edycji. Można przekształcać i łączyć ścieżki oraz tworzyć ścieżki złożone z wielu kształtów.<br /><br />Możesz również skonwertować bloki tekstu na ścieżki, aby manipulować nimi w postaci obrazów wektorowych.|[Rysowanie kształtów i ścieżek](../xaml-tools/draw-shapes-and-paths.md)|
|**Edytowanie kontrolek, szablonów i stylów**|Wymaga kodowania i znajomości stylów i szablonów WPF.|Przekształcenie dowolnego obrazu w kontrolkę.<br /><br />Za pomocą narzędzi do edycji szablonów można wprowadzać zmiany w kontrolkach, stylach i szablonach za pomocą zaledwie kilku kliknięć myszą.<br /><br />Na przykład możesz użyć zasobów stylów Blend for Visual Studio do implementowania wspólnych kontrolek WPF (takich jak przyciski, pola listy, paski przewijania, menu itp.), a także zmieniać kolory, style lub szablony bazowe bezpośrednio w Blend for Visual Studio. Następnie możesz przełączyć się do kodu, aby dokończył się w razie potrzeby.|[Modyfikowanie stylu obiektów](../designers/modify-the-style-of-objects-in-blend.md)|
|**Połącz interfejs użytkownika z danymi**|Można utworzyć źródło danych z zasobów, takich jak baza danych SQL Server, usług WCF lub sieci Web, obiektów lub listy programu SharePoint, a następnie powiązać źródło danych z kontrolkami interfejsu użytkownika.<br /><br />Dane czasu projektowania muszą być tworzone ręcznie dla interaktywnego środowiska projektowego.|W przypadku aplikacji .NET Framework można łatwo tworzyć przykładowe dane w celu tworzenia prototypów i testowania. Przejdź do danych na żywo, gdy wszystko będzie gotowe.<br /><br />Funkcje generacji danych Blend for Visual Studio są zaległe (można łatwo dodawać nazwy, cyfry, adresy URL i zdjęcia), a także zaoszczędzić dużo czasu.<br /><br />W przypadku danych na żywo można powiązać kontrolki interfejsu użytkownika z plikiem XML lub dowolnym źródłem danych CLR.|[Wyświetlanie danych](display-data-in-blend.md)|

Aby uzyskać więcej informacji na temat zaawansowanego projektowania XAML, zobacz [Tworzenie interfejsu użytkownika przy użyciu Blend for Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md).
