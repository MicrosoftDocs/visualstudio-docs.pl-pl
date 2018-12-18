---
title: Zainstaluj program Visual Studio dla komputerów Mac
description: Instrukcje dotyczące sposobu instalowania programu Visual Studio dla komputerów Mac i dodatkowe składniki wymagane dla wieloplatformowego opracowywania aplikacji.
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: e725234cadc301d5e0e369131efd53c1c69d6337
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53158960"
---
# <a name="set-up-and-install-visual-studio-for-mac"></a>Ustaw w pionie i zainstaluj program Visual Studio dla komputerów Mac

## <a name="requirements"></a>Wymagania

Do rozpoczęcia tworzenia natywnych, aplikacje dla wielu platform, po pobraniu programu Visual Studio dla komputerów Mac istnieje kilka rzeczy, które należy zainstalować i skonfigurować w ramach przygotowań.

Do pracy z systemem iOS w programie Visual Studio potrzebne są następujące elementy:

* komputer Mac z systemem macOS Sierra 10.12 lub nowszej
* Xcode 8.3 lub nowszej. Najnowsza stabilna wersja zazwyczaj jest zalecane.
* Tego identyfikatora firmy Apple. Jeśli nie masz jeszcze identyfikatora Apple ID można utworzyć nowe konto na https://appleid.apple.com. Należy mieć identyfikator Apple ID do instalowania i rejestrowania się w środowisku Xcode.

> [!TIP]
> Visual Studio 2019 r dla komputerów Mac (wersja zapoznawcza) jest [udostępniono](install-preview.md) do testowania.

## <a name="install"></a>Zainstaluj

1. Pobierz program Visual Studio dla komputerów Mac z [https://visualstudio.microsoft.com/](https://visualstudio.microsoft.com/)

2. Po pobraniu pakietu Instalatora kliknij przycisk **VisualStudioForMacInstaller.dmg** pliku, aby zainstalować Instalatora i uruchom go, klikając dwukrotnie plik logo, jak pokazano na poniższej ilustracji:

   ![Okno dialogowe Instalator](media/installer-image1.png)

3. Może zostać wyświetlony monit z okna dialogowego alertu podobny do poniższej ilustracji. W tym przypadku kliknij **Otwórz**:

   ![okna dialogowego alertu](media/installer-image2.png)

4. Instalator sprawdza systemu, aby sprawdzić składniki, które muszą być zainstalowane lub zaktualizowane:

   ![Ocena systemu](media/installer-image3.png)

5. Następnie zostaną wyświetlone z prośbą o potwierdzenie warunki ochrony prywatności i licencji okna dialogowego alertu. Naciśnij klawisz **Kontynuuj** przycisk, aby potwierdzić warunki:

   ![Okno dialogowe licencji](media/installer-image4.png)

6. Instalator wyświetla listę wymaganych składników, które nie istnieją, które muszą zostać pobrana i zainstalowana. Wybierz produkty, które chcesz pobrać tutaj:

   ![Wybierz elementy](media/installer-image5.png)

   Jeśli nie chcesz zainstalować na wszystkich platformach, należy pomóc zdecydować, które platformy, aby zainstalować za pomocą przewodnika poniżej:

   * **Aplikacje korzystające z platformy Xamarin**:
      - Zestaw narzędzi Xamarin.Forms — wybierz **Android** i **dla systemu iOS** platformy.
      - iOS — do wybrania **iOS** platformy (należy pamiętać, że będą musieli zainstalować [ **Xcode**](https://developer.apple.com/xcode/)).
      - Android — do wybrania **Android** platformy (należy zauważyć, że powinni wybrać też odpowiednie zależności).
      - Wybierz tylko — Mac **macOS** platformy (należy pamiętać, że będą musieli zainstalować [ **Xcode**](https://developer.apple.com/xcode/)).
      - Wybierz pełni Międzyplatformowe aplikacje Xamarin — **Android**, **dla systemu iOS**, i **macOS** platformy.
   * **Aplikacje .NET core** — wybierz **platformy .NET Core** platformy.
   * **Aplikacje sieci Web programu ASP.NET Core** — wybierz **platformy .NET Core** platformy.
   * **Opracowywanie gier Unity dla wielu platform** — żadnych dodatkowych platform muszą być zainstalowane poza Visual Studio dla komputerów Mac. Zapoznaj się [przewodnik konfiguracji środowiska Unity](setup-vsmac-tools-unity.md) Aby uzyskać więcej informacji na temat instalowania rozszerzenia aparatu Unity.

   Na tym ekranie instalacji Wyświetla wersję i rozmiar każdego składnika. Kliknij każdy składnik, aby wyświetlić listę zależności dla tego składnika (dla systemu Android), zobacz dodatkowe pakiety, które pobiera (dla platformy .NET Core) lub wyświetlić dodatkowe aplikacje wymagane (dla systemów iOS i macOS):

   ![Zależności dodatkowe systemu android](media/installer-image6.png)

7. Po przejściu wszystkiego najlepszego wyboru wybierz **Instalowanie i aktualizowanie** przycisk, aby rozpocząć proces instalacji.

8. Instalator uruchamia pliki do pobrania i zainstaluj proces wybrane elementy:

   ![Rozpoczynanie instalacji](media/installer-image7.png)

   ![Pobieranie rozszerzenia Xamarin.Mac](media/installer-image8.png)

   ![Kończenie instalacji](media/installer-image9.png)

9. Może zostać wyświetlony monit o podnoszenia poziomu uprawnień niezbędnych dla poszczególnych składników, które są niezbędne do ukończenia instalacji. Wprowadź swoje poświadczenia administratora, aby kontynuować proces instalacji:

   ![Podaj uprawnienia, aby kontynuować z Instalatorem](media/installer-image10.png)

10. Gdy instalacja się powiodła, możesz rozpocząć tworzenie aplikacji w programie Visual Studio, naciskając klawisz **Start**:

    ![Otwórz program Visual Studio](media/installer-image11.png)

> [!NOTE]
> Jeśli została wybrana opcja Instaluj platformy lub narzędzia podczas oryginalnej instalacji (cofając go w kroku #6), należy uruchomić [Instalatora](https://visualstudio.microsoft.com/vs/) ponownie w razie potrzeby można później dodać składniki.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Zainstaluj program Visual Studio dla komputerów Mac za serwerem zapory lub serwera proxy

Aby zainstalować program Visual Studio dla komputerów Mac za zaporą, niektóre punkty końcowe muszą być udostępnione w celu pobrania wymagane narzędzia i aktualizacje oprogramowania.

Skonfiguruj sieci, aby zezwolić na dostęp do następujących lokalizacji:

* [Visual Studio punktów końcowych.](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Następne kroki

Instalowanie programu Visual Studio dla komputerów Mac pozwala rozpocząć pisanie kodu dla aplikacji. Następujące przewodniki znajdują się przeprowadzenie Cię przez proces w następnych krokach pisania i wdrażania projektów.

### <a name="ios"></a>iOS

1. [Witaj, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Aprowizowanie urządzenia](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning)(w celu uruchomienia aplikacji na urządzeniu).

### <a name="android"></a>Android

1. [Przy użyciu Menedżera zestawów SDK platformy Xamarin Android](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Emulator zestawu SDK systemu Android](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Konfigurowanie urządzenia na potrzeby programowania](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>Aplikacje platformy .NET core, aplikacje sieci web platformy ASP.NET Core, tworzenia gier Unity

W przypadku innych obciążeń zobacz [obciążeń](workloads.md) strony.

## <a name="see-also"></a>Zobacz także

- [Instalowanie programu Visual Studio 2017 (na Windows)](/visualstudio/install/install-visual-studio)
