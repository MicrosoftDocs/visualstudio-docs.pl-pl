---
title: Instalowanie programu Visual Studio 2019 r dla komputerów Mac (wersja zapoznawcza)
description: Instrukcje dotyczące sposobu instalowania programu Visual Studio 2019 dla komputerów Mac (wersja zapoznawcza) i dodatkowe składniki wymagane dla wieloplatformowego opracowywania aplikacji.
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: acd8f3bc4f5fefa0a0c8b273856579067fb33c6a
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2019
ms.locfileid: "54316194"
---
# <a name="install-visual-studio-2019-for-mac-preview"></a>Instalowanie programu Visual Studio 2019 r dla komputerów Mac (wersja zapoznawcza)

> [!NOTE]
> Visual Studio 2019 r dla komputerów Mac w wersji zapoznawczej jest dostępna do zainstalowania side-by-side przy użyciu najnowszej stabilnej wersji programu Visual Studio dla komputerów Mac. Podczas instalowania wyświetli monit o aktualizacji istniejącego programu Visual Studio, jeśli nie jest najnowsza stabilna wersja.

## <a name="requirements-for-the-visual-studio-2019-for-mac-preview"></a>Wymagania dotyczące Visual 2019 r Studio dla komputerów Mac w wersji zapoznawczej

- Komputer Mac z systemem macOS wysokiej 10.13 Sierra lub nowszym.

Aby kompilować aplikacje Xamarin dla systemu iOS lub macOS, należy także:

- Środowisko Xcode 10.0 lub nowszy. Najnowsza stabilna wersja zazwyczaj jest zalecane.
- Tego identyfikatora firmy Apple. Jeśli nie masz jeszcze identyfikatora Apple ID można utworzyć nowe konto na https://appleid.apple.com. Należy mieć identyfikator Apple ID do instalowania i rejestrowania się w środowisku Xcode.

## <a name="installing-the-preview"></a>Instalowanie wersji zapoznawczej

1. Pobierz Instalatora w wersji zapoznawczej z [programu Visual Studio dla komputerów Mac w wersji zapoznawczej strony](https://aka.ms/vs4mac-preview).
2. Po ukończeniu pobierania kliknij **VisualStudioforMacPreviewInstaller.dmg** Zainstaluj Instalator, następnie uruchom go, klikając dwukrotnie plik logo strzałkę:

    [![Kliknij strzałkę w dużych, aby rozpocząć instalację](media/install-preview-installer-sml.png)](media/install-preview-installer.png#lightbox)

3. Może być przedstawiany z ostrzeżeniem o aplikacji są pobierane z Internetu. Kliknij przycisk **Otwórz**.
4. Zaczekaj, aż Instalator sprawdza, czy system:

    [![Instalator sprawdza, czy zainstalowanych składników w systemie](media/install-preview-checking-sml.png)](media/install-preview-checking.png#lightbox)

5. Alert zostanie wyświetlony prośbą o potwierdzenie warunki ochrony prywatności i licencji. Skorzystaj z linków, aby je odczytać, a następnie naciśnij klawisz **Kontynuuj** Jeśli zgadzasz się:

    [![Skorzystaj z linków do prywatności i warunki, a następnie kontynuuj, wyrażasz zgodę](media/install-preview-privacy-sml.png)](media/install-preview-privacy.png#lightbox)

6. Zostanie wyświetlona lista dostępnych obciążeń. Wybierz te, których chcesz użyć:

    [![Wybierz funkcji opcjonalnych obciążenia, które chcesz zainstalować](media/install-preview-selection-sml.png)](media/install-preview-selection.png#lightbox)

    Jeśli Twoja bieżąca programu Visual Studio 2017 dla komputerów Mac jest starsza niż wersja 7.7, poprosimy Cię o zatwierdzenie uaktualnienie do najnowszej stabilnej wersji (który jest wymagany do obsługi instalacji side-by-side). Naciśnij klawisz **Kontynuuj** zatwierdzić uaktualnienia:

    ![Uaktualnianie stabilną wersję do 7.7 jest wymagana](media/install-preview-older-upgrade.png)

7. Po dokonaniu wyborów, naciśnij klawisz **zainstalować** przycisku.
8. Instalator wyświetli postęp pobierania i instalacji programu Visual Studio dla komputerów Mac i wybranego obciążenia. Może zostać wyświetlony o wprowadzenie hasła do przyznawania uprawnień niezbędnych do instalacji.
9. Użyj **programu Visual Studio (wersja zapoznawcza)** w dowolnym momencie chcesz przetestować w wersji zapoznawczej lub przejdź z powrotem do najnowszej czasu trwania stanu stabilnego programu Visual Studio do pracy w środowisku produkcyjnym. Tutaj są wyświetlane dwie ikony:

    ![Różnice ikonę działające stabilnie i ze (wersja zapoznawcza)](media/install-preview-icons-sml.png)

Jeśli masz problemy z siecią podczas instalowania w środowisku firmowym, zapoznaj się z [instalacji za zaporą lub serwer proxy](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server) instrukcje.

Dowiedz się więcej o zmianach w [informacje o wersji](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-preview-relnotes).

> [!NOTE]
> Wybranego nie zainstalują platformy lub narzędzia podczas oryginalnej instalacji (cofając go w kroku #6), należy uruchomić Instalatora ponownie w razie potrzeby można później dodać składniki.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Zainstaluj program Visual Studio dla komputerów Mac za serwerem zapory lub serwera proxy

Aby zainstalować program Visual Studio dla komputerów Mac za zaporą, niektóre punkty końcowe muszą być udostępnione w celu pobrania wymagane narzędzia i aktualizacje oprogramowania.

Skonfiguruj sieci, aby zezwolić na dostęp do następujących lokalizacji:

- [Visual Studio punktów końcowych.](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

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

W przypadku innych obciążeń zobacz [obciążeń](/visualstudio/mac/workloads) strony.

## <a name="see-also"></a>Zobacz także

- [Instalowanie programu Visual Studio 2017 (na Windows)](/visualstudio/install/install-visual-studio)
