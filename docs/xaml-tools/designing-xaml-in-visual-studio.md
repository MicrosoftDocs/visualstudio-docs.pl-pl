---
title: Projektuj kod XAML w programie Visual Studio i w Blend for Visual Studio
titleSuffix: ''
ms.date: 02/28/2020
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: decba18e6b11b2c861edc20ff0a8e1e1c8f77b4a
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78235188"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Projektuj kod XAML w programie Visual Studio i Blend for Visual Studio

Program Visual Studio i Blend for Visual Studio zapewnia narzędzia graficzne do kompilowania interesujące interfejsy użytkownika, i rozbudowane treści multimedialne możliwości pracy z XAML dla różnych typów aplikacji. Oba zintegrowane środowiska deweloperskie (IDE) udostępniają wspólny zestaw funkcji, w tym edytor języka Visual XAML (Projektant). Blend for Visual Studio, który obsługuje platformy WPF i platformy UWP, oferuje dodatkowe narzędzia do projektowania Stanów wizualnych i tworzenia animacji.

Można przełączać się między programem Visual Studio i Blend for Visual Studio, a nawet w tym samym czasie może być otwarty w obu środowisk ideach. Zmiany zapisane w plikach XAML w jednym środowisku IDE mogą być stosowane przez automatyczne ponowne ładowanie po przełączeniu do innego środowiska IDE. Możesz kontrolować zachowanie ponownego ładowania, przechodząc do **narzędzi** > **opcje** > **środowisku** > **dokumenty** w obu IDE.

## <a name="installation"></a>Instalacja

- Aby utworzyć aplikacje WPF, zainstaluj obciążenie **Programowanie aplikacji klasycznych platformy .NET** w programie Visual Studio. Zostanie również zainstalowany Blend for Visual Studio.

     ![Zrzut ekranu przedstawiający obciążenie Programowanie aplikacji klasycznych platformy .NET z Instalator programu Visual Studio](../xaml-tools/media/dotnet-desktop-dev-workload.png)

- Aby tworzyć aplikacje platformy UWP, zainstaluj obciążenie **programowanie platforma uniwersalna systemu Windows** w programie Visual Studio. Zostanie również zainstalowany Blend for Visual Studio.

     ![Zrzut ekranu przedstawiający obciążenie związane z programowaniem platforma uniwersalna systemu Windows z Instalator programu Visual Studio](../xaml-tools/media/uwp-workload.png)

- Aby utworzyć aplikacje platformy Xamarin. Forms, zainstaluj **Programowanie aplikacji mobilnych przy użyciu obciążenia .NET** w programie Visual Studio. *Nie* zainstalowano Blend for Visual Studio. Program Blend nie obsługuje aplikacji Xamarin. Forms.

     ![Zrzut ekranu przedstawiający opracowywanie aplikacji mobilnych za pomocą obciążenia .NET z Instalator programu Visual Studio](../xaml-tools/media/mobile-dev-dotnet-workload.png)

## <a name="shared-capabilities"></a>Współdzielone możliwości

W przypadku większości podstawowych zadań programistycznych program Visual Studio i Blend for Visual Studio współdzielą ten sam zestaw okien i możliwości z niewielkimi różnicami. Jej najważniejsze funkcje obejmują:

- Funkcja **IntelliSense:** Obie środowisk IDE obsługują funkcje IntelliSense, takie jak uzupełnianie instrukcji.

- **Debugowanie:** Można debugować w programie [Visual Studio](../debugger/inspect-xaml-properties-while-debugging.md) i [Blend for Visual Studio](../xaml-tools/debug-xaml-in-blend.md), w tym ustawienia punktów przerwania w kodzie, aby debugować działającą aplikację i za pomocą funkcji [ponownego ładowania](../xaml-tools/xaml-hot-reload.md) , można zmienić kod XAML, gdy aplikacja jest uruchomiona. Aby zapewnić spójne środowisko debugowania w programie Visual Studio, program Blend for Visual Studio zawiera większość debugowania systemu windows i paski narzędzi programu Visual Studio.

- **Załaduj plik:** Pliki XAML można edytować w programie Visual Studio lub Blend for Visual Studio. Edytowane pliki, które zostały zapisane automatycznie Załaduj, podczas przełączania między środowisk IDE. Możesz kontrolować zachowanie ponownego ładowania, przechodząc do **narzędzi** > **opcje** > **środowisku** > **dokumenty** w obu IDE.

- **Zsynchronizowane układy i ustawienia:** Preferencje i ustawienia okna narzędzia dostosowywania projektu dla programu Visual Studio lub Blend for Visual Studio są synchronizowane przez urządzenia i wersje po zalogowaniu się przy użyciu tego samego konta personalizacji. Zobacz [Synchronizowanie ustawień na wielu komputerach](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Zaawansowane możliwości w Blend for Visual Studio

Aby zwiększyć wydajność, należy wziąć pod uwagę przy użyciu Blend dla programu Visual Studio w celu uwzględnienia poniższych zadań. Poniżej znajdują się obszary, w których Blend for Visual Studio oferuje więcej funkcji niż Projektant lub sam kod programu Visual Studio.

| Zadanie | Visual Studio | Blend for Visual Studio | Więcej informacji |
| - | - | - | - |
| **Projektowanie Stanów wizualnych** | Nie jest dostępne żadne narzędzie ułatwiające projektowanie Stanów wizualnych; należy je tworzyć programowo. | Narzędzia do projektowania umożliwiają zmianę wyglądu kontrolki na podstawie jej stanu. | [Stany wizualne](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Tworzenie animacji** |Brak narzędzia do projektowania nie animacje; należy utworzyć je programowo. Ta migracja wymaga zrozumienia Animacja i system chronometrażu w WPF i obszerną wiedzę kodowania.|Wizualne Tworzenie animacji i można przeglądać je w programie Blend for Visual Studio. Jest większa szybkość i dokładność niż Tworzenie animacji w kodzie. Możesz dodać wyzwalacze do obsługi interakcji z użytkownikiem i możesz przełączyć się do kodu w celu dodania obsługi zdarzeń i inne funkcje.|[Animowanie obiektów](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Przekształcanie kształtów i tekstu w ścieżki w celu ułatwienia manipulowania**|Nieobsługiwane.|Po przekonwertowaniu ich na ścieżki, które zapewniają kontrolę lepiej edycji ułatwia subtelne lub znaczne zmiany do kształtów zewnętrznych (takich jak prostokąty i elipsy). Możesz zmienić kształt lub łączenia ścieżek i utworzyć ścieżki złożone z wielu kształtów.<br /><br />Można również przeprowadzić konwersję bloki tekstu do ścieżki do manipulowania nimi jako obrazy wektorowe.|[Rysowanie kształtów i ścieżek](../xaml-tools/draw-shapes-and-paths.md)|
|**Edytowanie kontrolek, szablonów i stylów**|Wymaga kodowania i wiedzy na temat WPF — style i szablony.|Włącz obrazów w formancie.<br /><br />Szablon narzędzi edycji Aby wprowadzić zmiany do kontrolek, stylów i szablonów za pomocą zaledwie kilkoma kliknięciami.<br /><br />Na przykład można użyć programu Blend dla programu Visual Studio zasoby stylów, implementować wspólnych formantów WPF (takie jak przyciski, pola listy, paski przewijania, menu itd.) oraz zmieniać ich kolor, styl lub podstawowego szablonu bezpośrednio w programie Blend for Visual Studio. Można następnie przełączyć kod poprawek, jeśli chcesz.|[Modyfikowanie stylu obiektów](modify-the-style-of-objects-in-blend.md)|
|**Połącz interfejs użytkownika z danymi**|Można utworzyć źródło danych z zasobów, takich jak baza danych SQL Server, usług WCF lub sieci Web, obiektów lub listy programu SharePoint, a następnie powiązać źródło danych z kontrolkami interfejsu użytkownika.<br /><br />Dane w czasie projektowania musi zostać utworzony ręcznie dla środowisko interaktywne projektu.|W przypadku aplikacji .NET Framework można łatwo tworzyć przykładowe dane w celu tworzenia prototypów i testowania. Przełącz, aby dane na żywo, gdy wszystko będzie gotowe.<br /><br />Program Blend for możliwości istnieją zaległe Generowanie danych programu Visual Studio (można dodać nazwy, liczby, adresy URL i zdjęcia prosty sposób na bieżąco) i zaoszczędzić dużo czasu.<br /><br />W przypadku danych na żywo można powiązać formantów interfejsu użytkownika do pliku XML lub do dowolnego źródła danych środowiska CLR.|[Wyświetlanie danych](display-data-in-blend.md)|

Aby uzyskać więcej informacji na temat zaawansowanego projektowania XAML, zobacz [Tworzenie interfejsu użytkownika przy użyciu Blend for Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie XAML](xaml-overview.md)
- [Przegląd Blend for Visual Studio](creating-a-ui-by-using-blend-for-visual-studio.md)
