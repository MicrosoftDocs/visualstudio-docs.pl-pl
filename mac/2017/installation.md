---
title: Zainstaluj program Visual Studio 2017 dla komputerów Mac
description: Instrukcje dotyczące sposobu instalowania Visual Studio dla komputerów Mac i dodatkowych składników wymaganych do tworzenia aplikacji na wiele platform.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: c494f8d8543e0aa51b0c2be0ee52c0cb80aba982
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862440"
---
# <a name="install-visual-studio-2017-for-mac"></a>Zainstaluj program Visual Studio 2017 dla komputerów Mac

> [!NOTE]
> Program Visual Studio 2019 for Mac jest [teraz dostępny](installation.md?view=vsmac-2019). Starsze wersje Visual Studio dla komputerów Mac można znaleźć na [stronie pliki do pobrania](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac)programu Visual Studio.

## <a name="downgrading-from-visual-studio-2019-for-mac"></a>Czy przechodzenie na starszą wersję z programu Visual Studio 2019 for Mac?

Aby uzyskać najlepsze doświadczenia, przed obniżeniem poziomu należy upewnić się, że program Visual Studio 2019 dla komputerów Mac został [odinstalowany](uninstall.md) . Jeśli masz problemy, które powodują pobranie, pamiętaj o tym, aby poinformować nas o [problemie](report-a-problem.md).
 
## <a name="requirements"></a>Wymagania

Aby rozpocząć tworzenie aplikacji natywnych dla wielu platform podczas pobierania Visual Studio dla komputerów Mac istnieje kilka rzeczy, które należy zainstalować i skonfigurować w przygotowaniu.

Do pracy z systemem iOS w programie Visual Studio potrzebne są następujące elementy:

- Komputer Mac z macOS wysoka firma Sierra 10,13 lub nowszą.
- Xcode 9,3 lub nowszy. Zwykle zalecana jest najnowsza stabilna wersja.
- Identyfikator Apple ID. Jeśli nie masz już identyfikatora Apple ID, możesz utworzyć nowy https://appleid.apple.com . Konieczne jest posiadanie identyfikatora Apple ID na potrzeby instalacji i logowania do usługi Xcode.

## <a name="install"></a>Instalowanie

1. Pobierz Visual Studio dla komputerów Mac z [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac)

2. Po pobraniu pakietu Instalatora kliknij plik **VisualStudioForMacInstaller. dmg** , aby zainstalować Instalatora, a następnie uruchom go przez dwukrotne kliknięcie logo, jak pokazano na poniższej ilustracji:

   ![Okno dialogowe Instalatora](media/installer-image1.png)

3. Może zostać wyświetlony monit o podanie okna dialogowego alertu podobnego do poniższego obrazu. W takim przypadku kliknij przycisk **Otwórz**:

   ![okno dialogowe alertu](media/installer-image2.png)

4. Instalator sprawdzi system w celu sprawdzenia, które składniki muszą być zainstalowane lub zaktualizowane:

   ![Ocenianie systemu](media/installer-image3.png)

5. Zostanie wyświetlone okno dialogowe alertu z prośbą o potwierdzenie postanowień dotyczących prywatności i licencji. Naciśnij przycisk **Kontynuuj** , aby potwierdzić warunki:

   ![Okno dialogowe licencji](media/installer-image4.png)

6. Instalator przedstawia listę wymaganych składników, których brakuje i które muszą zostać pobrane i zainstalowane. Wybierz produkty, które chcesz pobrać tutaj:

   ![Wybierz elementy](media/installer-image5.png)

   Jeśli nie chcesz instalować wszystkich platform, Skorzystaj z poniższego przewodnika, aby ułatwić podjęcie decyzji o tym, które platformy instalować:

   * **Aplikacje korzystające z platformy Xamarin**:
      - Xamarin. Forms — wybierz platformy **Android** i **iOS** .
      - tylko system iOS — wybierz platformę **iOS** (należy pamiętać, że konieczne będzie zainstalowanie [**Xcode**](https://developer.apple.com/xcode/)).
      - Tylko system Android — Wybierz platformę **Android** (należy pamiętać, że należy również wybrać odpowiednie zależności).
      - Tylko Mac — wybierz platformę **macOS** (należy pamiętać, że konieczne będzie zainstalowanie [**Xcode**](https://developer.apple.com/xcode/)).
      - W pełni Międzyplatformowe aplikacje Xamarin — wybierz platformy **Android**, **iOS**i **macOS** .
   * **Aplikacje .NET Core** — Wybierz platformę **.NET Core** .
   * **ASP.NET Core aplikacji sieci Web** — Wybierz platformę **.NET Core** .
   * **Programowanie gier dla wielu platform** w środowisku Unity — nie trzeba instalować dodatkowych platform poza Visual Studio dla komputerów Mac. Aby uzyskać więcej informacji na temat instalowania rozszerzenia aparatu Unity, zapoznaj się z [przewodnikiem Instalatora aparatu Unity](./setup-vsmac-tools-unity.md) .

   Na tym ekranie instalacji zostanie wyświetlona wersja i rozmiar każdego pojedynczego składnika. Możesz kliknąć każdy składnik, aby wyświetlić listę zależności dla tego składnika (dla systemu Android), zapoznać się z dodatkowymi pakietami, które są pobierane (dla platformy .NET Core), lub wyświetlić dodatkowe wymagane aplikacje (dla systemów iOS i macOS):

   ![Dodatkowe zależności systemu Android](media/installer-image6.png)

7. Gdy będziesz zadowolony z wyboru, wybierz przycisk **Zainstaluj i Aktualizuj** , aby rozpocząć proces instalacji.

8. Instalator uruchamia proces pobierania i instalacji wybranych elementów:

   ![Rozpoczynanie instalacji](media/installer-image7.png)

   ![Pobieranie platformy Xamarin. Mac](media/installer-image8.png)

   ![Kończenie instalacji](media/installer-image9.png)

9. Może zostać wyświetlony monit o podniesienie uprawnień niezbędnych do przeprowadzenia instalacji przez poszczególne składniki. Wprowadź tutaj poświadczenia administratora, aby kontynuować proces instalacji:

   ![Wprowadź uprawnienia do kontynuowania instalacji](media/installer-image10.png)

10. Po pomyślnym zakończeniu instalacji możesz rozpocząć tworzenie aplikacji w programie Visual Studio, naciskając pozycję **Start**:

    ![Otwórz program Visual Studio.](media/installer-image11.png)

> [!NOTE]
> W przypadku wybrania opcji nie instaluj platformy lub narzędzia podczas instalacji oryginalnej (w tym celu należy usunąć zaznaczenie w kroku #6), należy ponownie uruchomić [Instalatora](https://visualstudio.microsoft.com/vs/) , jeśli chcesz dodać składniki później.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalowanie Visual Studio dla komputerów Mac za zaporą lub serwerem proxy

Aby zainstalować Visual Studio dla komputerów Mac za zaporą, należy udostępnić pewne punkty końcowe, aby umożliwić pobieranie wymaganych narzędzi i aktualizacji oprogramowania.

Skonfiguruj sieć w taki sposób, aby zezwalała na dostęp do następujących lokalizacji:

- [Punkty końcowe programu Visual Studio](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Następne kroki

Zainstalowanie Visual Studio dla komputerów Mac pozwala rozpocząć pisanie kodu dla aplikacji. Podano następujące przewodniki, które przeprowadzą Cię przez kolejne kroki pisania i wdrażania projektów.

### <a name="ios"></a>iOS

1. [Witaj, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Inicjowanie obsługi administracyjnej urządzeń](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning)(do uruchamiania aplikacji na urządzeniu).

### <a name="android"></a>Android

1. [Korzystanie z programu Xamarin Android SDK Manager](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Emulator zestawu SDK systemu Android](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Konfigurowanie urządzenia na potrzeby programowania](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>Aplikacje platformy .NET Core, ASP.NET Core aplikacje sieci Web, Programowanie gier w środowisku Unity

W przypadku innych obciążeń zapoznaj się ze stroną [obciążenia](./workloads.md) .

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Zobacz też

- [Zainstaluj program Visual Studio 2017 (w systemie Windows)](/visualstudio/install/install-visual-studio)