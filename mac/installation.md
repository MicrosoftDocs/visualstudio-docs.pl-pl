---
title: Zainstaluj program Visual Studio 2019 dla komputerów Mac
description: Instrukcje dotyczące sposobu instalowania programu Visual Studio 2019 for Mac oraz dodatkowych składników wymaganych do tworzenia aplikacji na wiele platform.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 03/04/2021
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 653e653a0574da52c0030b06c7a8c13b436ed686
ms.sourcegitcommit: 4bf7d82eb3a837ad5d1ae5c110039cbf74258f18
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2021
ms.locfileid: "106273417"
---
# <a name="install-visual-studio-2019-for-mac"></a>Zainstaluj program Visual Studio 2019 dla komputerów Mac

Aby rozpocząć tworzenie natywnych aplikacji platformy .NET dla wielu platform w systemie macOS, zainstaluj program Visual Studio 2019 for Mac, wykonując poniższe kroki.

 > [!div class="button"]
 > [Pobierz program Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/)

## <a name="requirements"></a>Wymagania

- Komputer Mac z macOS wysoka firma Sierra 10,13 lub nowszą.

Do kompilowania aplikacji platformy Xamarin dla systemu iOS lub macOS potrzebne są również:

- Komputer Mac, który jest zgodny z najnowszą wersją programu Xcode. Zapoznaj się z dokumentacją dotyczącą [minimalnych wymagań](https://developer.apple.com/support/xcode/) firmy Apple
- Najnowsza wersja programu [Xcode](https://developer.apple.com/xcode). Jeśli komputer Mac nie jest zgodny z najnowszą wersją, może być możliwe [użycie starszej wersji programu Xcode](https://docs.microsoft.com/xamarin/ios/troubleshooting/questions/old-version-xcode) .
- Identyfikator Apple ID. Jeśli nie masz już identyfikatora Apple ID, możesz utworzyć nowy https://appleid.apple.com . Konieczne jest posiadanie identyfikatora Apple ID na potrzeby instalacji i logowania do usługi Xcode.

## <a name="installation-instructions"></a>Instrukcje instalacji

1. Pobierz instalatora ze [strony pobierania Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/).
2. Po zakończeniu pobierania kliknij plik **VisualStudioforMacInstaller. dmg** , aby zainstalować Instalatora, a następnie uruchom go, dwukrotnie klikając logo strzałki:

    [![Kliknij dużą strzałkę, aby rozpocząć instalację.](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. Może zostać wyświetlone ostrzeżenie o aplikacji pobieranej z Internetu. Kliknij przycisk **Otwórz**.
4. Zaczekaj, aż Instalator sprawdzi swój system:

    [![Instalator sprawdza system pod kątem zainstalowanych składników](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Zostanie wyświetlony alert z prośbą o potwierdzenie postanowień dotyczących prywatności i licencji. Postępuj zgodnie z linkami, aby je odczytać, a następnie naciśnij pozycję **Kontynuuj** , jeśli akceptujesz:

    [![Postępuj zgodnie z linkami do prywatności i postanowień, a następnie Kontynuuj, jeśli zgadzasz się](media/install-privacy.png)](media/install-privacy.png#lightbox)

6. Zostanie wyświetlona lista dostępnych obciążeń. Wybierz składniki, których chcesz użyć:

    [![Zrzut ekranu przedstawiający ekran "co chcesz zainstalować?" w Instalatorze programu Visual Studio Mac z listą składników dostępnych do instalacji.](media/install-selection.png)](media/install-selection.png#lightbox)

   Jeśli nie chcesz instalować wszystkich platform, Skorzystaj z poniższego przewodnika, aby ułatwić podjęcie decyzji o tym, które platformy instalować:

   |Typ aplikacji  |Cel  |Wybór  |Uwagi  |
   |---------|---------|---------|---------|
   |**Aplikacje korzystające z platformy Xamarin**| Xamarin.Forms|Wybierz platformy **Android** i **iOS** |Konieczne będzie zainstalowanie [ **Xcode**](https://developer.apple.com/xcode/) |
   ||Tylko system iOS|Wybierz platformę **iOS**|Konieczne będzie zainstalowanie [ **Xcode**](https://developer.apple.com/xcode/)|
   ||Tylko system Android|Wybierz platformę **Android**|Pamiętaj, że należy również wybrać odpowiednie zależności|
   ||Tylko Mac|Wybierz platformę **macOS (kakao)**|Konieczne będzie zainstalowanie [ **Xcode**](https://developer.apple.com/xcode/)|
   |**Aplikacje platformy .NET Core**|         |Wybierz platformę **.NET Core** .|         |
   |**Aplikacje internetowe ASP.NET Core**|         |Wybierz platformę **.NET Core** .|         |
   |**Azure Functions**|         |Wybierz platformę **.NET Core** .|         |
   |**Programowanie gier dla wielu platform w środowisku Unity**|         |Nie trzeba instalować dodatkowych platform poza Visual Studio dla komputerów Mac.| Aby uzyskać więcej informacji na temat instalowania rozszerzenia aparatu Unity, zapoznaj się z [przewodnikiem Instalatora aparatu Unity](./setup-vsmac-tools-unity.md) .|

7. Po dokonaniu wyboru Naciśnij przycisk **Zainstaluj** .
8. Instalator wyświetli postęp, gdy pobiera i instaluje Visual Studio dla komputerów Mac i wybrane obciążenia. Zostanie wyświetlony monit o wprowadzenie hasła w celu udzielenia uprawnień niezbędnych do instalacji.

    [![Zrzut ekranu z Instalatora programu Visual Studio dla komputerów Mac z ekranem postępu instalacji dla programu .NET Developer Toolkit dla komputerów Mac.](media/installation-progress.png)](media/installation-progress.png#lightbox)

9. Po zainstalowaniu programu Visual Studio dla komputerów Mac wyświetli monit o spersonalizowanie instalacji, logując się i wybierając kluczowe powiązania, których chcesz użyć:

    [![Zaloguj się do środowiska IDE](media/ide-tour-2019-start-signin.png)](media/ide-tour-2019-start-signin.png#lightbox)

    [![Wybierz Skróty klawiaturowe, których chcesz użyć](media/ide-tour-2019-keyboard-shortcut.png)](media/ide-tour-2019-keyboard-shortcut.png#lightbox)

Jeśli podczas instalowania programu w środowisku firmowym występuje problem z siecią, zapoznaj się z instrukcjami dotyczącymi [instalacji za zaporą lub serwerem proxy](#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server) .

Dowiedz się więcej o zmianach wprowadzonych w [informacjach o wersji](/visualstudio/releasenotes/vs2019-mac-relnotes).

> [!NOTE]
> W przypadku wybrania opcji nieinstalowania platformy lub narzędzia podczas instalacji początkowej (bez zaznaczania w kroku #6), należy ponownie uruchomić Instalatora, jeśli chcesz dodać składniki później.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalowanie Visual Studio dla komputerów Mac za zaporą lub serwerem proxy

Aby zainstalować Visual Studio dla komputerów Mac za zaporą, należy udostępnić pewne punkty końcowe, aby umożliwić pobieranie wymaganych narzędzi i aktualizacji oprogramowania.

Skonfiguruj sieć w taki sposób, aby zezwalała na dostęp do następujących lokalizacji:

- [Punkty końcowe programu Visual Studio](./install-behind-a-firewall-or-proxy-server.md)

## <a name="next-steps"></a>Następne kroki

Zainstalowanie Visual Studio dla komputerów Mac pozwala rozpocząć pisanie kodu dla aplikacji. Podano następujące przewodniki, które przeprowadzą Cię przez kolejne kroki pisania i wdrażania projektów.

### <a name="ios"></a>iOS

1. [Witaj, iOS](https://docs.microsoft.com//xamarin/ios/get-started/hello-ios/)
2. [Inicjowanie obsługi administracyjnej urządzeń](https://docs.microsoft.com/xamarin/ios/get-started/installation/device-provisioning/)(do uruchamiania aplikacji na urządzeniu).

### <a name="android"></a>Android

1. [Hello, Android](https://docs.microsoft.com/xamarin/android/get-started/hello-android/)
2. [Korzystanie z programu Xamarin Android SDK Manager](https://docs.microsoft.com/xamarin/android/get-started/installation/android-sdk?tabs=macos)
3. [Emulator zestawu SDK systemu Android](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/)
4. [Konfigurowanie urządzenia na potrzeby programowania](https://docs.microsoft.com/xamarin/android/get-started/installation/set-up-device-for-development)

### <a name="xamarinforms"></a>Xamarin.Forms

Twórz natywne aplikacje Międzyplatformowe za pomocą interfejsu Xamarin. Forms:

1. [Przewodniki Szybki start zestawu narzędzi Xamarin.Forms](https://docs.microsoft.com/xamarin/get-started/quickstarts/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>Aplikacje platformy .NET Core, ASP.NET Core aplikacje sieci Web, Programowanie gier w środowisku Unity

W przypadku innych obciążeń zapoznaj się ze stroną [obciążenia](workloads.md) .

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Zobacz też

- [Zainstaluj program Visual Studio (w systemie Windows)](/visualstudio/install/install-visual-studio)
