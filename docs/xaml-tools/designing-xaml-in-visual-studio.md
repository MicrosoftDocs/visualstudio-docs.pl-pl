---
title: Projektowanie kodu XAML w programie Visual Studio i w programie Blend for Visual Studio
titleSuffix: ''
ms.date: 02/28/2020
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: eb18a2face5d9f1831bec35379a423f272c3e6ce
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649824"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Projektowanie xaml w programie Visual Studio i blend dla programu Visual Studio

Visual Studio i Blend for Visual Studio zapewniają narzędzia wizualne do tworzenia atrakcyjnych interfejsów użytkownika i środowisk multimedialnych za pomocą języka XAML dla różnych typów aplikacji. Oba zintegrowane środowiska programistyczne (IDE) mają wspólny zestaw funkcji, w tym wizualny edytor XAML (projektant). Blend for Visual Studio, który obsługuje platformy WPF i platformy platformy platformy uniwersalnej systemu i platformy uniwersalnej systemu, zapewnia dodatkowe narzędzia do projektowania stanów wizualnych i tworzenia animacji.

Można przełączać się tam iz powrotem między programami Visual Studio i Blend dla programu Visual Studio, a nawet można mieć ten sam projekt otwarty w obu ice w tym samym czasie. Zmiany zapisane w plikach XAML w jednym IDE można zastosować za pomocą automatycznego ponownego ładowania po przełączeniu do innego IDE. Zachowanie ponownego ładowania można kontrolować, przechodząc do**dokumentów** **środowiska** > **opcje** >  **narzędzi** > w obu IDE.

## <a name="installation"></a>Instalacja

- Aby utworzyć aplikacje WPF, zainstaluj .NET obciążenia **deweloperskie pulpitu** w programie Visual Studio. Zostanie również zainstalowana aplikacja Blend for Visual Studio.

     ![Zrzut ekranu przedstawiający obciążenie programem .NET desktop development z instalatora programu Visual Studio](../xaml-tools/media/dotnet-desktop-dev-workload.png)

- Aby utworzyć aplikacje platformy uniwersalnej systemu Windows, należy zainstalować obciążenie **deweloperskie platformy uniwersalnej systemu Windows** w programie Visual Studio. Zostanie również zainstalowana aplikacja Blend for Visual Studio.

     ![Zrzut ekranu przedstawiający obciążenie deweloperskie platformy systemu Windows z Instalatora programu Visual Studio](../xaml-tools/media/uwp-workload.png)

- Aby utworzyć aplikacje platformy Xamarin.Forms, należy zainstalować program Mobile development z obciążeniem **platformy .NET** w programie Visual Studio. Program Blend for Visual Studio *nie* jest zainstalowany; Blend nie obsługuje aplikacji platformy Xamarin.Forms.

     ![Zrzut ekranu przedstawiający program Mobile Development z obciążeniem platformy .NET z instalatora programu Visual Studio](../xaml-tools/media/mobile-dev-dotnet-workload.png)

## <a name="shared-capabilities"></a>Współdzielone możliwości

W przypadku większości podstawowych zadań programistycznych program Visual Studio i Blend for Visual Studio współużytkują ten sam zestaw okien i możliwości z pewnymi subtelnymi różnicami. Jej najważniejsze funkcje obejmują:

- **Technologia IntelliSense:** Oba identyfikatory obsługują funkcje intellisense, takie jak uzupełnianie instrukcji.

- **Debugowanie:** Można debugować w [programie Visual Studio](inspect-xaml-properties-while-debugging.md) i Blend dla programu Visual [Studio](../xaml-tools/debug-xaml-in-blend.md), w tym ustawienie punktów przerwania w kodzie do debugowania uruchomionej aplikacji i za pomocą [hot reload,](../xaml-tools/xaml-hot-reload.md) aby zmienić kod XAML, gdy aplikacja jest uruchomiona. Aby zachować spójne środowisko debugowania z visual studio, Blend dla programu Visual Studio zawiera większość okien debugowania programu Visual Studio i pasków narzędzi.

- **Ponowne załadowanie pliku:** Pliki XAML można edytować w programie Visual Studio lub programie Blend for Visual Studio. Edytowane pliki, które zostały zapisane, ładują się ponownie automatycznie podczas przełączania się między tymi plikami. Zachowanie ponownego ładowania można kontrolować, przechodząc do**dokumentów** **środowiska** > **opcje** >  **narzędzi** > w obu IDE.

- **Zsynchronizowane układy i ustawienia:** Układy okien okien narzędzi dostosowywania projektowania i preferencje ustawień programu Visual Studio lub Blend dla programu Visual Studio są synchronizowane między urządzeniami i wersjami po zalogowaniu się przy tym samym koncie personalizacji. Zobacz [Synchronizowanie ustawień na wielu komputerach](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Zaawansowane możliwości w programie Blend dla programu Visual Studio

Aby zwiększyć produktywność, należy rozważyć użycie programu Blend for Visual Studio do następujących zadań. Są to obszary, w których Blend for Visual Studio oferuje więcej funkcji niż projektant programu Visual Studio lub sam kod.

| Zadanie | Visual Studio | Blend for Visual Studio | Więcej informacji |
| - | - | - | - |
| **Projektowanie stanów wizualnych** | Nie ma żadnego narzędzia, które pomaga w projektowaniu stanów wizualnych; należy je utworzyć programowo. | Użyj narzędzi do projektowania, aby zmienić wygląd formantu na podstawie jego stanu. | [Stany wizualne](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Tworzenie animacji** |Nie ma narzędzia do projektowania animacji; musisz je tworzyć programowo. Wymaga to zrozumienia systemu animacji i chronometrażu w WPF i rozległej wiedzy na temat kodowania.|Animacje są wyświetlane wizualnie i można wyświetlać ich podgląd w programie Blend for Visual Studio. Jest to szybsze i dokładniejsze niż tworzenie animacji w kodzie. Można dodać wyzwalacze do obsługi interakcji z użytkownikiem i można przełączyć się do kodu, aby dodać programy obsługi zdarzeń i inne funkcje.|[Animowanie obiektów](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Przekształcanie kształtów i tekstu w ścieżki w celu łatwiejszej manipulacji**|Bez pomocy technicznej.|Można wprowadzić subtelne lub dramatyczne zmiany kształtów (takie jak prostokąty i elipsy), konwertując je na ścieżki, które zapewniają lepszą kontrolę edycji. Można zmienić kształt lub połączyć ścieżki oraz utworzyć ścieżki złożone z wielu kształtów.<br /><br />Można również konwertować bloki tekstowe na ścieżki, aby manipulować nimi jako obrazami wektorowymi.|[Rysowanie kształtów i ścieżek](../xaml-tools/draw-shapes-and-paths.md)|
|**Edytowanie formantów, szablonów i stylów**|Wymaga kodowania i znajomości stylów I szablonów WPF.|Przeksztuj dowolny obraz w formant.<br /><br />Narzędzia do edycji szablonów umożliwia wprowadzanie zmian w formantach, stylach i szablonach za pomocą zaledwie kilku kliknięć myszą.<br /><br />Na przykład można użyć zasobów stylu Programu Blend for Visual Studio do zaimplementowania typowych formantów WPF (takich jak przyciski, pola listy, paski przewijania, menu itp.) i zmienić ich kolor, styl lub szablon podstawowy bezpośrednio w programie Blend for Visual Studio. Następnie można przełączyć się do kodu do wykończenia, jeśli chcesz.|[Modyfikowanie stylu obiektów](modify-the-style-of-objects-in-blend.md)|
|**Łączenie interfejsu użytkownika z danymi**|Źródło danych można utworzyć z zasobów, takich jak baza danych programu SQL Server, WCF lub usługa sieci web, obiekt lub lista programu SharePoint, a następnie powiązać źródło danych z formantami interfejsu użytkownika.<br /><br />Dane w czasie projektowania muszą być tworzone ręcznie, aby uzyskać interaktywne środowisko projektowania.|W przypadku aplikacji platformy .NET Framework łatwo utwórz przykładowe dane do tworzenia prototypów i testowania. Przełączaj się na dane na żywo, gdy będziesz gotowy.<br /><br />Możliwości generowania danych programu Blend For Visual Studio są wyjątkowe (można łatwo dodawać nazwy, numery, adresy URL i zdjęcia w locie) i zaoszczędzić dużo czasu.<br /><br />W przypadku danych na żywo można powiązać formanty interfejsu użytkownika z plikiem XML lub dowolnym źródłem danych CLR.|[Wyświetlanie danych](display-data-in-blend.md)|

Aby uzyskać więcej informacji na temat zaawansowanego projektu XAML, zobacz [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="see-also"></a>Zobacz też

- [Przegląd XAML](xaml-overview.md)
- [Omówienie programu Blend for Visual Studio](creating-a-ui-by-using-blend-for-visual-studio.md)
