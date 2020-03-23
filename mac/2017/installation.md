---
title: Instalowanie programu Visual Studio 2017 dla komputerów Mac
description: Instrukcje dotyczące instalowania programu Visual Studio dla komputerów Mac i dodatkowe składniki wymagane do tworzenia między platformami.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: dfc9f7469f5954aaac56b5d45bb5ae722110dfcc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984914"
---
# <a name="install-visual-studio-2017-for-mac"></a>Instalowanie programu Visual Studio 2017 dla komputerów Mac

> [!NOTE]
> Visual Studio 2019 dla [komputerów](installation.md?view=vsmac-2019)Mac jest już dostępny . W przypadku starszych wersji programu Visual Studio dla [komputerów](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac)Mac zobacz stronę pobierania programu Visual Studio .

## <a name="downgrading-from-visual-studio-2019-for-mac"></a>Obniżenie wersji programu Visual Studio 2019 dla komputerów Mac?

Aby uzyskać najlepsze środowisko, przed przejściem na starszą wersję produktu należy upewnić się, że [odinstalujesz program](uninstall.md) Visual Studio 2019 dla komputerów Mac. Jeśli masz problemy, które powodują pobranie, poinformuj nas o tym, [zgłaszając problem.](report-a-problem.md)
 
## <a name="requirements"></a>Wymagania

Aby rozpocząć tworzenie natywnych, wieloplatformowych aplikacji podczas pobierania programu Visual Studio dla komputerów Mac, istnieje kilka rzeczy, które należy zainstalować i skonfigurować w ramach przygotowań.

Do pracy z systemem iOS w programie Visual Studio potrzebne są następujące elementy:

- komputer Mac z systemem macOS Sierra 10.12 lub wyższym
- Xcode 9.3 lub wyższy. Najnowsza stabilna wersja jest zwykle zalecana.
- Identyfikator Apple ID. Jeśli nie masz już konta Apple ID, możesz https://appleid.apple.comutworzyć nowy w pliku . Do zainstalowania i zalogowania się do xcode konieczne jest utworzenie konta Apple ID.

## <a name="install"></a>Instalowanie

1. Pobierz program Visual Studio dla komputerów Mac z [my.visualstudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac)

2. Po pobraniu pakietu instalacyjnego kliknij plik **VisualStudioForMacInstaller.dmg,** aby zainstalować instalator, a następnie uruchom go, klikając dwukrotnie logo, co ilustruje poniższy obraz:

   ![Okno dialogowe Instalatora](media/installer-image1.png)

3. Może zostać wyświetlony monit z komunikatem dialogowym alertu podobnym do poniższego obrazu. W takim przypadku kliknij przycisk **Otwórz:**

   ![okno dialogowe alertów](media/installer-image2.png)

4. Instalator sprawdza system, aby sprawdzić, które składniki muszą zostać zainstalowane lub zaktualizowane:

   ![Ocena systemu](media/installer-image3.png)

5. Następnie zostanie wyświetlone okno dialogowe z prośbą o potwierdzenie postanowień dotyczących prywatności i licencji. Naciśnij przycisk **Kontynuuj,** aby potwierdzić warunki:

   ![Okno dialogowe Licencjonowanie](media/installer-image4.png)

6. Instalator przedstawia listę wymaganych składników, których brakuje i które należy pobrać i zainstalować. Wybierz produkty, które chcesz pobrać tutaj:

   ![Wybierz elementy](media/installer-image5.png)

   Jeśli nie chcesz instalować wszystkich platform, skorzystaj z poniższego przewodnika, aby pomóc Ci zdecydować, które platformy zainstalować:

   * **Aplikacje korzystające z platformy Xamarin**:
      - Xamarin.Forms — wybierz platformy **Android** i **iOS.**
      - tylko iOS — wybierz platformę **iOS** (Należy pamiętać, że trzeba będzie zainstalować [**Xcode**](https://developer.apple.com/xcode/)).
      - Tylko Android — wybierz platformę **Android** (Należy pamiętać, że należy również wybrać odpowiednie zależności).
      - Tylko Mac - Wybierz platformę **macOS** (Należy pamiętać, że trzeba będzie zainstalować [**Xcode**](https://developer.apple.com/xcode/)).
      - W pełni wieloplatformowe aplikacje Xamarin — wybierz platformy **Android,** **iOS**i **macOS.**
   * **Aplikacje .NET Core** — wybierz platformę **.NET Core.**
   * **ASP.NET podstawowych aplikacji sieci Web** — wybierz platformę **.NET Core.**
   * **Wieloplatformowe unity game development** — nie trzeba instalować żadnych dodatkowych platform poza programem Visual Studio dla komputerów Mac. Więcej informacji na temat instalowania rozszerzenia Unity można znaleźć w [podręczniku konfiguracji unity.](/visualstudio/mac/setup-vsmac-tools-unity)

   Na tym ekranie instalacji wyświetlana jest wersja i rozmiar poszczególnych składników. Możesz kliknąć każdy składnik, aby wyświetlić listę zależności dla tego składnika (dla systemu Android), zobacz dodatkowe pakiety, które pobiera (dla .NET Core) lub wyświetlić wszystkie dodatkowe aplikacje wymagane (dla systemów iOS i macOS):

   ![Dodatkowe zależności systemu Android](media/installer-image6.png)

7. Po zaznaczeniu wyboru wybierz przycisk **Zainstaluj i Aktualizuj,** aby rozpocząć proces instalacji.

8. Instalator rozpoczyna proces pobierania i instalowania wybranych elementów:

   ![Rozpoczęcie instalacji](media/installer-image7.png)

   ![Pobieranie xamarin.Mac](media/installer-image8.png)

   ![Instalacja wykańczająca](media/installer-image9.png)

9. Może zostać wyświetlony monit o podniesienie uprawnień niezbędnych dla poszczególnych składników, które są potrzebne do ukończenia instalacji. Wprowadź poświadczenia administratora w tym miejscu, aby kontynuować proces instalacji:

   ![Wprowadź uprawnienia do kontynuowania instalacji](media/installer-image10.png)

10. Po pomyślnym zakończeniu instalacji można rozpocząć tworzenie aplikacji w programie Visual Studio, naciskając przycisk **Start:**

    ![Otwórz program Visual Studio.](media/installer-image11.png)

> [!NOTE]
> Jeśli podczas oryginalnej instalacji wybrano opcję nieinstalowania platformy lub narzędzia (odznaczając je krok po #6), należy ponownie uruchomić [instalator,](https://visualstudio.microsoft.com/vs/) jeśli chcesz dodać składniki później.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalowanie programu Visual Studio dla komputerów Mac za zaporą lub serwerem proxy

Aby zainstalować program Visual Studio dla komputerów Mac za zaporą, niektóre punkty końcowe muszą być dostępne, aby umożliwić pobieranie wymaganych narzędzi i aktualizacji oprogramowania.

Skonfiguruj sieć, aby zezwoliła na dostęp do następujących lokalizacji:

- [Punkty końcowe programu Visual Studio](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

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

W przypadku innych obciążeń zobacz strony [Obciążenia.](/visualstudio/mac/workloads)

## <a name="related-video"></a>Podobne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Zobacz też

- [Instalowanie programu Visual Studio 2017 (w systemie Windows)](/visualstudio/install/install-visual-studio)
