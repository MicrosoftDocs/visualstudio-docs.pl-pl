---
title: Xamarin
description: 'Korzystanie z programu Xamarin w Visual Studio dla komputerów Mac umożliwia tworzenie aplikacji międzyplatformowych przeznaczonych dla systemów iOS, Mac, Android, systemu tvOS i systemu watchOS '
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: 339F6051-5F90-48DC-8237-EBBC8A03A32B
ms.openlocfilehash: 31fb7fa4c2a87820285809d24b98fe8e59a6be01
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714479"
---
# <a name="xamarin-mobile-app-development"></a>Programowanie aplikacji mobilnych dla platformy Xamarin

Najwyższej jakości pomoc techniczna dla platformy [Xamarin](/xamarin) umożliwia tworzenie rozbudowanych natywnych środowisk dla systemów Android, macOS, iOS, tvOS i watchOS. Aplikacje dla wielu platform oparte na platformie Xamarin.Forms ułatwiają współużytkowanie kodu interfejsu użytkownika opartego na języku XAML między systemami Android, iOS i macOS bez ograniczania dostępu do funkcji natywnych.

## <a name="xamarinforms"></a>Xamarin.Forms

Hot reload języka XAML dla platformy Xamarin. Forms jest wbudowana w Visual Studio dla komputerów Mac w wersji 8,3 i nowszych. Po włączeniu tej funkcji zmiany zostaną natychmiast odzwierciedlone w uruchomionej aplikacji przy każdym zapisaniu pliku.

Można włączyć funkcję dynamicznego ponownego ładowania kodu XAML, zaznaczając pole wyboru **Włącz rozszerzenie Xamarin Hot reload** w **programie Visual Studio > Preferences > Projects > Xamarin Hot reload**.

Aby uzyskać więcej informacji na temat ponownego ładowania, zobacz [Przewodnik po załadowaniu kodu XAML dla platformy Xamarin. Forms](/xamarin/xamarin-forms/xaml/hot-reload) w ramach dokumentacji.

## <a name="android"></a>Android

Visual Studio dla komputerów Mac ma własny zintegrowany Menedżer Android SDK, dzięki czemu można uzyskać dostęp do zestawów SDK, dla których aplikacja ma być docelowa.

W przypadku aplikacji systemu Android Visual Studio dla komputerów Mac obejmuje własny Projektant, który współpracuje z plikami `.axml` systemu Android w celu wizualnego konstruowania interfejsów użytkownika. Visual Studio dla komputerów Mac otworzy te pliki w Android Designer, jak pokazano na poniższej ilustracji:

![Projektant interfejsu użytkownika systemu Android](media/intro-image31.png)

Aby uzyskać więcej informacji na Android Designer, zobacz [Omówienie platformy Xamarin. Android Designer](/xamarin/android/user-interface/android-designer/index) .

## <a name="ios"></a>iOS

Program iOS Designer jest w pełni zintegrowany z Visual Studio dla komputerów Mac i umożliwia edycję wizualizacji plików. XIB i scenorysów w celu utworzenia interfejsów użytkownika i przejść dla systemów iOS, systemu tvOS i systemu watchOS. Cały interfejs użytkownika można skompilować przy użyciu funkcji przeciągania i upuszczania między przybornikiem i Powierzchnia projektowa, przy użyciu intuicyjnego podejścia do obsługi zdarzeń. Program iOS Designer obsługuje również [niestandardowe kontrolki](/xamarin/ios/user-interface/designer/ios-designable-controls-overview) z dodatkową korzyścią renderowania w czasie projektowania.

![Projektant scenorysu systemu iOS](media/intro-image30.png)

Aby uzyskać więcej informacji na temat korzystania z projektanta systemu iOS, zobacz Przewodniki [projektanta](/xamarin/ios/user-interface/designer/?tabs=macos) .

### <a name="mac"></a>Mac

Platforma Xamarin udostępnia natywne powiązania interfejsów API dla komputerów Mac, które umożliwiają tworzenie atrakcyjnych aplikacji dla komputerów Mac.

Aby uzyskać więcej informacji na temat pisania aplikacji dla komputerów Mac za pomocą Visual Studio dla komputerów Mac, zapoznaj się z przewodnikami dla platformy [Xamarin. Mac](/xamarin/mac/get-started/index) .

## <a name="xamarin-enterprise-features"></a>Funkcje platformy Xamarin Enterprise

> [!Note]
> Te produkty mogą być używane tylko z subskrypcją Visual Studio Enterprise.

### <a name="profiler"></a>Profiler

Xamarin Profiler ma trzy instrumenty dostępne do profilowania. [Wprowadzenie do przewodnika Xamarin Profiler zawiera](/xamarin/tools/profiler/index?tabs=macos) informacje o tym, co mierzą te instrumenty i jak analizuje swoją aplikację, a także objaśnia znaczenie danych przedstawionych na każdym ekranie.

### <a name="inspector"></a>Inspector

Xamarin Inspector zapewnia interaktywną C# konsolę z narzędziami użytkownika. Może służyć jako pomoc dotycząca debugowania lub diagnostyki podczas przeprowadzania inspekcji aplikacji na żywo, jako narzędzie edukacyjne, jako narzędzie do dokumentacji lub narzędzie do eksperymentowania.

![Xamarin Inspector](media/intro-inspector.png)

Składa się z aplikacji autonomicznej, która udostępnia C# rozbudowaną konsolę, która może kierować się różnymi platformami programistycznymi (Android, iOS, Mac i Windows) i integrują się z przepływem pracy debugowania środowisk IDE.

Aby uzyskać więcej informacji, zobacz Przewodnik [Xamarin Inspector](/xamarin/tools/inspector/) .
