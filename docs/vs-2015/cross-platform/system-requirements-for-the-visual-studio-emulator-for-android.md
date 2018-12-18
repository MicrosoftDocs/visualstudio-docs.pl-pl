---
title: Wymagania systemowe dotyczące emulatora programu dla systemu Android | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35e766ad-269f-41e4-ba23-74a556c315f3
caps.latest.revision: 7
ms.author: crdun
manager: crdun
ms.openlocfilehash: f96451551cc15df4ae9357c721276383d1060a47
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058941"
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>Wymagania systemowe dotyczące emulatora programu Visual Studio dla systemu Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Visual Studio Emulator for Android działa jako maszyna wirtualna funkcji Hyper-v, technologia wirtualizacji systemu Windows 8 i nowszych. Aby uruchomić emulator, komputer musi spełniać wymagania do uruchomienia funkcji Hyper-V, zgodnie z opisem w tym temacie.

 Program instalacyjny próbuje dyskretnie konfigurowanie wymagań wstępnych dla Ciebie, po zainstalowaniu emulatora. Gdy Instalator pomyślnie skonfiguruje wymagania wstępne, emulator po prostu działa zgodnie z oczekiwaniami. W przeciwnym razie może być konieczne ręcznie włączyć te wymagania wstępne. Jeśli trzeba ręcznie skonfigurować wymagania wstępne narzędzia i kroki są te same kroki opisane [tutaj](https://msdn.microsoft.com/library/windows/apps/jj863509\(v=vs.105\).aspx) emulatora Windows Phone.

> [!IMPORTANT]
>  Program instalacyjny dla emulatora sprawdza wymagania wstępne dotyczące uruchamiania programu Visual Studio Emulator dla systemu Android. Wyświetla ostrzeżenia, jeśli wymagania wstępne nie są obecne, ale go nie wymaga.

 Ten temat zawiera następujące sekcje.

-   [Szybka lista kontrolna](#Checklist)

-   [Wymagania systemowe](#System)

-   [Wymagania dotyczące sieci](#Network)

-   [Wymagania funkcji Hyper-V](#HyperV)

-   [Uruchamianie emulatora z rozruchowego dysku VHD nie jest obsługiwana.](#BootableVHD)

-   [Funkcji Hyper-V wymaga bez kompresji i szyfrowania plików](#Files)

##  <a name="Checklist"></a> Szybka lista kontrolna
 Poniżej przedstawiono listę kontrolną szybkiego wymagań dotyczących uruchamiania emulatora programu Visual Studio dla systemu Android. Aby uzyskać więcej szczegółowych informacji zobacz kolejnych sekcjach tego tematu.

 Wymagania systemowe

- Obsługa funkcji Hyper-V (zobacz poniższe wymagania funkcji Hyper-V)

- 6 GB lub więcej pamięci RAM.

- 64-bitowej wersji Pro w wersji Windows10 systemu Windows 8, Windows 8.1 lub nowszy

- Procesor obsługujący instrukcji SSSE3 lub nowszej.

  Wymagania dotyczące sieci

- DHCP

- Automatycznie skonfigurowana DNS i ustawień bramy

  Wymagania funkcji Hyper-V

- W systemie BIOS muszą być obsługiwane następujące funkcje:

  -   Wirtualizacja sprzętowa

  -   Drugi adres poziomu Translation (SLAT)

  -   Zapobieganie wykonywaniu danych oparte na sprzęcie (DEP)

- W Windows funkcji Hyper-V musi być włączona i uruchomiona.

- Musisz być członkiem lokalnej grupy Administratorzy funkcji Hyper-V.

##  <a name="System"></a> Wymagania systemowe
 Komputer musi spełniać następujące wymagania:

- Obsługa funkcji Hyper-V (zobacz [wymagania funkcji Hyper-V](#HyperV))

- 6 GB lub więcej pamięci RAM.

- wersja 64-bitowej wersji Pro Windows10 systemu Windows 8, Windows 8.1 lub nowszy.

  Aby sprawdzić wymagania dotyczące pamięci RAM i Windows, w Panelu sterowania wybierz pozycję System i zabezpieczenia, a następnie wybierz systemu.

  ![Sprawdź wymagania systemowe](../cross-platform/media/android-emu-system-requirements.png "Android_Emu_System_Requirements")

##  <a name="Network"></a> Wymagania dotyczące sieci
 Sieć musi spełniać następujące wymagania:

- DHCP

   Emulator wymaga protokołu DHCP, ponieważ konfiguruje się jako osobne urządzenia do sieci za pomocą adresu IP.

- Automatycznie skonfigurowana DNS i ustawień bramy

   Nie jest możliwe do skonfigurowania ustawień DNS i bramę ręcznie dla emulatora.

  Aby rozwiązać problemy z siecią w emulatorze, zobacz następujące tematy:

- [Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

##  <a name="HyperV"></a> Wymagania funkcji Hyper-V
 Wymagania funkcji Hyper-V w systemie BIOS

 System BIOS komputera musi obsługiwać następujące wymagania i należy je włączyć:

- Wirtualizacja sprzętowa

- Drugi adres poziomu Translation (SLAT)

- Zapobieganie wykonywaniu danych oparte na sprzęcie (DEP)

  Wymagania funkcji Hyper-V w Windows

  Jeśli ustawienia systemu BIOS i komputer, na których są już skonfigurowane do obsługi funkcji Hyper-V, program instalacyjny włącza się i uruchamia funkcji Hyper-V. W przeciwnym razie może być konieczne ręcznie włączyć te wymagania.

|Wymaganie|Jak sprawdzić i włączyć to wymaganie|
|-----------------|----------------------------------------------|
|Musi być zainstalowana funkcja Hyper-V|Postępuj zgodnie z instrukcjami w tym samym umożliwia [Włączanie funkcji Hyper-V na emulator Windows Phone](https://msdn.microsoft.com/library/windows/apps/jj863509\(v=vs.105\).aspx).<br /><br /> Sprawdź stan **zarządzania maszynami wirtualnymi funkcji Hyper-V** usługi w przystawce usługi.|
|Musi być uruchomiona funkcja Hyper-V.|Aby uzyskać więcej informacji na temat zarządzania usługami zobacz następujące tematy:<br /><br /> -   [Uruchom, Zatrzymaj, Wstrzymaj, Wznów lub ponownego uruchomienia usługi](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [Konfigurowanie sposobu uruchamiania usługi](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|

 Musisz być członkiem lokalnej grupy Administratorzy funkcji Hyper-V.

 Aby uruchomić program Visual Studio Emulator for Android bez cyklicznego monit o podniesienie uprawnień użytkownika, musisz być członkiem lokalnej grupy Administratorzy funkcji Hyper-V. Jeśli jesteś już administratorem lokalnym na komputerze podczas instalowania zestawu SDK, program instalacyjny dla zestawu SDK dodaje do grupy Administratorzy funkcji Hyper-V. W przeciwnym razie może być konieczne ręcznie włączyć to wymaganie.

 Po uruchomieniu emulatora, jeśli nie jesteś już członkiem grupy Administratorzy funkcji Hyper-V, wyświetlany jest monit o dołączenie do grupy (okno dialogowe odwołuje się do emulatora Windows Phone). Dołączenia do grupy wymaga uprawnień administratora.

> [!IMPORTANT]
> Po dołączeniu do grupy, wyloguj się lub ponowne uruchomienie, aby zmiany zaczęły obowiązywać.

 ![Łączenie Hyper&#45;grupy zabezpieczeń Administratorzy V](../cross-platform/media/android-emu-hyperv-admin.png "Android_Emu_HyperV_Admin")

 Aby samodzielnie ręcznie dodać do grupy, otwórz lokalni użytkownicy i grupy w przystawce.

##  <a name="BootableVHD"></a> Uruchamianie emulatora z rozruchowego dysku VHD nie jest obsługiwana.
 W przypadku uruchamiania aplikacji w Visual Studio Emulator dla systemu Android, gdy używasz Windows rozruchowego dysku VHD emulator zazwyczaj trwa kilka minut, aby uruchomić lub nie została uruchomiona. Jeśli emulator nie powiedzie się, zostanie wyświetlony następujący komunikat: Wdrażanie aplikacji nie powiodło się. Spróbuj ponownie później.

 Ta konfiguracja nie jest obsługiwana. Aby uzyskać informacji na temat problemów, zobacz [Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).

##  <a name="Files"></a> Funkcji Hyper-V wymaga bez kompresji i szyfrowania plików
 Na dysku twardym skonfigurowane przy użyciu systemu plików NTFS pliki wirtualnych dysków twardych, używany przez funkcję Hyper-V muszą nieskompresowany i bez szyfrowania. Upewnij się, że nie skompresowane lub zaszyfrowane następujących katalogów:

- %localappdata%\Microsoft\XDE

- C:\Program Files (x86)\Microsoft Emulator Manager

- C:\Program pliki (x86) \Microsoft Visual Studio Emulator for Android

- %localappdata%\Microsoft\VisualStudioEmulator

  W systemie plików ReFS pliki wirtualnego dysku twardego nie może mieć zestaw integralności bit.

## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>Wymagania dotyczące sprzętu grafiki przekazywania (Obsługa OpenGL ES)
 Emulatora do emulowania wywołania do procesora GPU, takich jak używane przez OpenGL ES komputer musi mieć zgodną jednostkę GPU DirectX przy użyciu odpowiednich sterowników DirectX zainstalowane.

## <a name="see-also"></a>Zobacz też
 [Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
