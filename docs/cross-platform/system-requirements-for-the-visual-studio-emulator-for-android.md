---
title: Wymagania systemowe emulatora programu Visual Studio dla systemu Android | Dokumenty firmy Microsoft
ms.custom: ''
ms.prod: visual-studio-dev15
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 35e766ad-269f-41e4-ba23-74a556c315f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f1462769a4ba9929a000bca998c1fe3708908798
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272052"
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>Wymagania systemowe dla emulatora programu Visual Studio dla systemu Android

Visual Studio Emulator dla systemu Android działa jako maszyna wirtualna w funkcji Hyper-V, technologii wirtualizacji dla systemu Windows 8 i nowszych wersji. Aby uruchomić emulator, komputer musi spełniać wymagania dotyczące uruchamiania funkcji Hyper-V zgodnie z opisem w tym temacie.

Program instalacyjny próbuje skonfigurować te wymagania wstępne w trybie dyskretnym podczas instalowania emulatora. Po pomyślnym skonfigurowaniu konfiguracji wymagań wstępnych emulator po prostu działa zgodnie z oczekiwaniami. W przeciwnym razie może być konieczna ręczne włączenie tych wymagań wstępnych. Jeśli musisz ręcznie skonfigurować wymagania wstępne, kroki i narzędzia są tymi samymi krokami opisanymi [w tym miejscu](/previous-versions/windows/apps/jj863509\(v=vs.105\)) dla emulatora systemu Windows Phone.

> [!IMPORTANT]
> Program instalacyjny emulatora sprawdza wymagania wstępne dotyczące uruchamiania emulatora programu Visual Studio dla systemu Android. Wyświetla ostrzeżenia, jeśli wymagania wstępne nie są obecne, ale nie wymaga ich.

## <a name="quick-checklist"></a><a name="Checklist"></a>Szybka lista kontrolna

Oto krótka lista kontrolna wymagań dotyczących uruchamiania emulatora programu Visual Studio dla systemu Android. Aby uzyskać bardziej szczegółowe informacje, zobacz kolejne sekcje w tym temacie.

Wymagania systemowe

- Obsługa funkcji Hyper-V (patrz wymagania funkcji Hyper-V poniżej)

- 6 GB lub więcej pamięci RAM.

- 64-bitowa wersja wersji Pro systemu Windows 8, Windows 8.1, Windows10 lub nowszej

- Procesor obsługujący SSSE3 lub nowsze.

Wymagania dotyczące sieci

- DHCP

- Automatycznie skonfigurowane ustawienia dns i bramy

Wymagania funkcji Hyper-V

- W systemie BIOS muszą być obsługiwane następujące funkcje:

  - Wirtualizacja sprzętowa

  - Tłumaczenie adresów drugiego poziomu (SLAT)

  - Ochrona danych oparta na sprzęcie (DEP)

- W systemie Windows funkcja Hyper-V musi być włączona i uruchomiona.

- Musisz być członkiem lokalnej grupy Administratorzy funkcji Hyper-V.

## <a name="system-requirements"></a>Wymagania systemowe
 Komputer musi spełniać następujące wymagania:

- Obsługa funkcji Hyper-V (patrz [wymagania funkcji Hyper-V)](#hyper-v-requirements)

- 6 GB lub więcej pamięci RAM.

- 64-bitowa wersja wersji Pro systemu Windows 8, Windows 8.1, Windows10 lub nowszej.

Aby sprawdzić wymagania dotyczące pamięci RAM i systemu Windows, w Panelu sterowania wybierz pozycję System i zabezpieczenia, a następnie wybierz pozycję System.

![Weryfikowanie wymagań systemowych](../cross-platform/media/android_emu_system_requirements.png "Android_Emu_System_Requirements")

## <a name="network-requirements"></a>Wymagania dotyczące sieci

Sieć musi spełniać następujące wymagania:

- DHCP

   Emulator wymaga usługi DHCP, ponieważ konfiguruje się jako oddzielne urządzenie w sieci z własnym adresem IP.

- Automatycznie skonfigurowane ustawienia dns i bramy

   Nie można ręcznie skonfigurować ustawień DNS i bramy dla emulatora.

  Aby rozwiązać problemy z siecią w emulatorze, zobacz następujące tematy:

- [Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

## <a name="hyper-v-requirements"></a>Wymagania funkcji Hyper-V

Wymagania funkcji Hyper-V w systemie BIOS

System BIOS komputera musi spełniać następujące wymagania i muszą być włączone:

- Wirtualizacja sprzętowa

- Tłumaczenie adresów drugiego poziomu (SLAT)

- Ochrona danych oparta na sprzęcie (DEP)

Wymagania funkcji Hyper-V w systemie Windows

Gdy komputer i system BIOS są już skonfigurowane do obsługi funkcji Hyper-V, program instalacyjny włącza i uruchamia funkcja Hyper-V. W przeciwnym razie może być wymagane włączenie tych wymagań ręcznie.

|Wymaganie|Jak sprawdzić i włączyć ten wymóg|
|-----------------|----------------------------------------------|
|Funkcja Hyper-V musi być zainstalowana|Postępuj zgodnie z tymi samymi instrukcjami, które są używane do [włączania funkcji Hyper-V dla emulatora systemu Windows Phone](/previous-versions/windows/apps/jj863509(v=vs.105)).<br /><br /> Sprawdź stan usługi **zarządzania maszynami wirtualnymi funkcji Hyper-V** w przystawce Usługi.|
|Funkcja Hyper-V musi być uruchomiona.|Aby uzyskać więcej informacji na temat zarządzania usługami, zobacz następujące tematy:<br /><br /> -   [Uruchamianie, zatrzymywanie, wstrzymywanie, wznawianie lub ponowne uruchamianie usługi](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [Konfigurowanie sposobu rozpoczęcia usługi](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|

 Musisz być członkiem lokalnej grupy Administratorzy funkcji Hyper-V.

 Aby uruchomić emulator programu Visual Studio dla systemu Android bez cyklicznego monitu o podniesienie poziomu praw, musisz być członkiem lokalnej grupy Administratorzy funkcji Hyper-V. Jeśli użytkownik jest już administratorem lokalnym na komputerze podczas instalowania pakietu SDK, program instalacyjny pakietu SDK zostanie dodany do grupy Administratorzy funkcji Hyper-V. W przeciwnym razie może być wymagane ręczne włączenie tego wymagania.

 Po uruchomieniu emulatora, jeśli nie jesteś jeszcze członkiem grupy Administratorzy funkcji Hyper-V, zostanie wyświetlony monit o dołączenie do grupy (okno dialogowe odnosi się do emulatora systemu Windows Phone). Dołączenie do grupy wymaga uprawnień administratora.

> [!IMPORTANT]
> Po dołączeniu do grupy wyloguj się lub uruchom ponownie, aby zmiana została uwzględniona.

 ![Dołączanie do grupy zabezpieczeń Administratorzy funkcji Hyper&#45;V](../cross-platform/media/android_emu_hyperv_admin.png "Android_Emu_HyperV_Admin")

 Aby dodać się do grupy ręcznie, otwórz przystawkę Użytkownicy i grupy lokalne.

## <a name="running-the-emulator-from-a-bootable-vhd-is-not-supported"></a>Uruchamianie emulatora z rozruchowego dysku VHD nie jest obsługiwane
 Jeśli spróbujesz uruchomić aplikację na emulatorze programu Visual Studio dla systemu Android podczas uruchamiania systemu Windows z rozruchowego dysku VHD, emulator zwykle trwa kilka minut, aby uruchomić lub nie można uruchomić. Gdy emulator nie może się uruchomić, zostanie wyświetlony następujący komunikat: Wdrożenie aplikacji nie powiodło się. Spróbuj ponownie.

 Ta konfiguracja nie jest obsługiwana. Aby uzyskać informacje na temat powiązanych problemów, zobacz [Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).

## <a name="hyper-v-requires-uncompressed-and-unencrypted-files"></a>Funkcja Hyper-V wymaga nieskompresowanych i niezaszyfrowanych plików
 Na dysku twardym skonfigurowanym z systemem plików NTFS wirtualne pliki dysków twardych używane przez program Hyper-V muszą być nieskompresowane i niezaszyfrowane. Upewnij się, że następujące katalogi nie są skompresowane lub zaszyfrowane:

- %localappdata%\Microsoft\XDE

- C:\Program Files (x86)\Microsoft Emulator Manager

- C:\Program Files (x86)\Microsoft Visual Studio Emulator dla systemu Android

- %localappdata%\Microsoft\VisualStudioEmulator

W systemie plików ReFS pliki wirtualnego dysku twardego nie mogą mieć ustawionego bitu integralności.

## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>Wymagania dotyczące przekazywania grafiki sprzętowej (obsługa OpenGL ES)

Aby emulator emulował wywołania do procesora GPU, takie jak te używane przez OpenGL ES, urządzenie musi mieć procesor graficzny zgodny z DirectX z zainstalowanymi odpowiednimi sterownikami DirectX.

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z narzędziem Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
