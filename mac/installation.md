---
title: Instalowanie programu Visual Studio 2019 dla komputerów Mac
description: Instrukcje dotyczące instalowania programu Visual Studio 2019 dla komputerów Mac i dodatkowych składników wymaganych do tworzenia między platformami.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: 45f9756607cbb638d1f69f77bdf8cd2ee30953c5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75851950"
---
# <a name="install-visual-studio-2019-for-mac"></a>Instalowanie programu Visual Studio 2019 dla komputerów Mac

Aby rozpocząć tworzenie natywnych, wieloplatformowych aplikacji platformy .NET w systemie macOS, zainstaluj program Visual Studio 2019 dla komputerów Mac, wykonując poniższe kroki.

 > [!div class="button"]
 > [Pobieranie programu Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/)

## <a name="requirements"></a>Wymagania

- Komputer Mac z systemem macOS High Sierra 10.12 lub wyższym.

Aby tworzyć aplikacje platformy Xamarin dla systemu iOS lub macOS, potrzebujesz również:

- Xcode 10.0 lub wyższy. Najnowsza stabilna wersja jest zwykle zalecana.
- Identyfikator Apple ID. Jeśli nie masz już konta Apple ID, możesz https://appleid.apple.comutworzyć nowy w pliku . Do zainstalowania i zalogowania się do xcode konieczne jest utworzenie konta Apple ID.

## <a name="installation-instructions"></a>Instrukcje instalacji

1. Pobierz instalator ze [strony pobierania programu Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/).
2. Po zakończeniu pobierania kliknij **visualstudioforMacInstaller.dmg,** aby zamontować instalator, a następnie uruchom go, klikając dwukrotnie logo strzałki:

    [![Kliknij dużą strzałkę, aby rozpocząć instalację](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. Może zostać wyświetlone ostrzeżenie o aplikacji pobieranej z Internetu. Kliknij przycisk **Open** (Otwórz).
4. Poczekaj, aż instalator sprawdzi system:

    [![Instalator sprawdza system pod kątem zainstalowanych komponentów](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Pojawi się alert z prośbą o potwierdzenie prywatności i postanowień licencyjnych. Skorzystaj z linków, aby je przeczytać, a następnie naciśnij **przycisk Kontynuuj,** jeśli się zgadzasz:

    [![Postępuj zgodnie z linkami do prywatności i warunków, a następnie kontynuuj, jeśli zgadzasz się](media/install-privacy.png)](media/install-privacy.png#lightbox)

6. Zostanie wyświetlona lista dostępnych obciążeń. Wybierz komponenty, których chcesz użyć:

    [![Wybierz, które opcjonalne funkcje obciążenia chcesz zainstalować](media/install-selection.png)](media/install-selection.png#lightbox)

   Jeśli nie chcesz instalować wszystkich platform, skorzystaj z poniższego przewodnika, aby pomóc Ci zdecydować, które platformy zainstalować:


|Typ aplikacji  |Środowisko docelowe  |Wybór  |Uwagi  |
|---------|---------|---------|---------|
|**Aplikacje korzystające z platformy Xamarin**| Xamarin.Forms|Wybierz platformy **Android** i **iOS** |Należy zainstalować [ **xcode**](https://developer.apple.com/xcode/) |
||Tylko system iOS|Wybierz platformę **systemu iOS**|Należy zainstalować [ **xcode**](https://developer.apple.com/xcode/)|
||Tylko Android|Wybierz platformę **Android**|Należy również pamiętać, że należy również wybrać odpowiednie zależności|
||Tylko mac|Wybierz platformę **macOS (Cocoa)**|Należy zainstalować [ **xcode**](https://developer.apple.com/xcode/)|
|**Aplikacje .NET Core**|         |Wybierz **platformę .NET Core.**|         |
|**Aplikacje internetowe ASP.NET Core**|         |Wybierz **platformę .NET Core.**|         |
|**Azure Functions**|         |Wybierz **platformę .NET Core.**|         |
|**Międzyplatformowy unity game development**|         |Nie trzeba instalować żadnych dodatkowych platform poza programem Visual Studio dla komputerów Mac.| Więcej informacji na temat instalowania rozszerzenia Unity można znaleźć w [podręczniku konfiguracji unity.](/visualstudio/mac/setup-vsmac-tools-unity)|


7. Po dokonaniu wyboru naciśnij przycisk **Zainstaluj.**
8. Instalator wyświetli postęp podczas pobierania i instalowania programu Visual Studio dla komputerów Mac i wybranych obciążeń. Zostanie wyświetlony monit o wprowadzenie hasła w celu przyznania uprawnień niezbędnych do instalacji.:

    [![Wybierz, które opcjonalne funkcje obciążenia chcesz zainstalować](media/installation-progress.png)](media/installation-progress.png#lightbox)

9. Po zainstalowaniu programu Visual Studio dla komputerów Mac wyświetli monit o spersonalizowanie instalacji przez zalogowanie się i wybranie powiązań kluczy, których chcesz użyć:

    [![Zaloguj się do ide](media/ide-tour-2019-start-signin.png)](media/ide-tour-2019-start-signin.png#lightbox)

    [![Wybieranie skrótów klawiaturowych, których chcesz używać](media/ide-tour-2019-keyboard-shortcut.png)](media/ide-tour-2019-keyboard-shortcut.png#lightbox)

Jeśli masz problemy z siecią podczas instalacji w środowisku firmowym, zapoznaj się z [instrukcjami instalacji za zaporą lub serwerem proxy.](/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server)

Dowiedz się więcej o zmianach w [informacjach o wersji](/visualstudio/releasenotes/vs2019-mac-relnotes).

> [!NOTE]
> Jeśli podczas oryginalnej instalacji nie zainstalowano platformy lub narzędzia (odznaczając je krok po #6), należy ponownie uruchomić instalator, jeśli chcesz dodać składniki później.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalowanie programu Visual Studio dla komputerów Mac za zaporą lub serwerem proxy

Aby zainstalować program Visual Studio dla komputerów Mac za zaporą, niektóre punkty końcowe muszą być dostępne, aby umożliwić pobieranie wymaganych narzędzi i aktualizacji oprogramowania.

Skonfiguruj sieć, aby zezwoliła na dostęp do następujących lokalizacji:

- [Punkty końcowe programu Visual Studio](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Następne kroki

Instalowanie programu Visual Studio dla komputerów Mac umożliwia rozpoczęcie pisania kodu dla aplikacji. Poniższe przewodniki są dostarczane, aby poprowadzić Cię przez kolejne kroki pisania i wdrażania projektów.

### <a name="ios"></a>iOS

1. [Witaj, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Inicjowanie obsługi administracyjnej urządzenia](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning)(aby uruchomić aplikację na urządzeniu).

### <a name="android"></a>Android

1. [Korzystanie z menedżera SDK systemu Android platformy Xamarin](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Emulator zestawu SDK systemu Android](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Konfigurowanie urządzenia na potrzeby programowania](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>Aplikacje .NET Core, ASP.NET podstawowe aplikacje internetowe, tworzenie gier Unity

W przypadku innych obciążeń zobacz strony [Obciążenia.](workloads.md)

## <a name="related-video"></a>Podobne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Zobacz też

- [Instalowanie programu Visual Studio (w systemie Windows)](/visualstudio/install/install-visual-studio)
