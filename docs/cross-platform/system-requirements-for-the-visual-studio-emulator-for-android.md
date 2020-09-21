---
title: Wymagania systemowe dla emulatora VS dla systemu Android
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 327713a59b7c5c8da5c5b92cd16f3a20a76a7458
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808262"
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>Wymagania systemowe dla emulatora programu Visual Studio dla systemu Android

Program Visual Studio Emulator for Android działa jako maszyna wirtualna w funkcji Hyper-V, technologii wirtualizacji dla systemu Windows 8 i nowszych wersji. Aby uruchomić emulator, komputer musi spełniać wymagania dotyczące uruchamiania funkcji Hyper-V zgodnie z opisem w tym temacie.

Program instalacyjny próbuje skonfigurować te wymagania wstępne w trybie dyskretnym podczas instalacji emulatora. Gdy Instalator pomyślnie skonfiguruje wymagania wstępne, Emulator po prostu działa zgodnie z oczekiwaniami. W przeciwnym razie może być konieczne ręczne włączenie tych wymagań wstępnych. Aby ręcznie skonfigurować wymagania wstępne, kroki i narzędzia są takie same jak [w przypadku](/previous-versions/windows/apps/jj863509\(v=vs.105\)) emulatora Windows Phone.

> [!IMPORTANT]
> Program instalacyjny emulatora sprawdza wymagania wstępne dotyczące uruchamiania emulatora programu Visual Studio dla systemu Android. Wyświetla ostrzeżenia, jeśli wymagania wstępne nie są obecne, ale nie są wymagane.

## <a name="quick-checklist"></a><a name="Checklist"></a> Szybka lista kontrolna

Poniżej przedstawiono szybką listę kontrolną wymagań dotyczących uruchamiania emulatora programu Visual Studio dla systemu Android. Aby uzyskać bardziej szczegółowe informacje, zobacz kolejne sekcje w tym temacie.

Wymagania systemowe

- Obsługa funkcji Hyper-V (Zobacz wymagania dotyczące funkcji Hyper-V poniżej)

- 6 GB lub więcej pamięci RAM.

- 64 — bitowa wersja Pro z dodatkiem Windows 8, Windows 8.1, Windows10 lub nowsza

- Procesor obsługujący SSSE3 lub nowszy.

Wymagania dotyczące sieci

- DHCP

- Automatycznie skonfigurowane ustawienia DNS i bramy

Wymagania dotyczące funkcji Hyper-V

- W systemie BIOS muszą być obsługiwane następujące funkcje:

  - Wirtualizacja sprzętowa

  - Translacja adresów drugiego poziomu (SLAT)

  - Sprzętowe zapobieganie wykonywaniu danych (DEP)

- W systemie Windows funkcja Hyper-V musi być włączona i uruchomiona.

- Musisz być członkiem lokalnej grupy Administratorzy funkcji Hyper-V.

## <a name="system-requirements"></a>Wymagania systemowe
 Komputer musi spełniać następujące wymagania:

- Obsługa funkcji Hyper-V (zobacz [wymagania dotyczące funkcji Hyper-v](#hyper-v-requirements))

- 6 GB lub więcej pamięci RAM.

- 64 — bitowa wersja Pro z dodatkiem Windows 8, Windows 8.1, Windows10 lub nowsza.

Aby sprawdzić wymagania dotyczące pamięci RAM i systemu Windows, w panelu sterowania wybierz system i zabezpieczenia, a następnie wybierz system.

![Sprawdź wymagania systemowe](../cross-platform/media/android_emu_system_requirements.png "Android_Emu_System_Requirements")

## <a name="network-requirements"></a>Wymagania dotyczące sieci

Sieć musi spełniać następujące wymagania:

- DHCP

   Emulator wymaga protokołu DHCP, ponieważ konfiguruje go jako oddzielne urządzenie w sieci przy użyciu własnego adresu IP.

- Automatycznie skonfigurowane ustawienia DNS i bramy

   Nie można skonfigurować ustawień DNS i bramy ręcznie dla emulatora.

  Aby rozwiązać problemy z siecią w emulatorze, zapoznaj się z następującymi tematami:

- [Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

## <a name="hyper-v-requirements"></a>Wymagania dotyczące funkcji Hyper-V

Wymagania dotyczące funkcji Hyper-V w systemie BIOS

System BIOS komputera musi obsługiwać poniższe wymagania i musi być włączony:

- Wirtualizacja sprzętowa

- Translacja adresów drugiego poziomu (SLAT)

- Sprzętowe zapobieganie wykonywaniu danych (DEP)

Wymagania dotyczące funkcji Hyper-V w systemie Windows

Gdy ustawienia komputera i systemu BIOS są już skonfigurowane do obsługi funkcji Hyper-V, program instalacyjny włączy i uruchomi funkcję Hyper-V. W przeciwnym razie może być konieczne ręczne włączenie tych wymagań.

|Wymaganie|Jak sprawdzić i włączyć to wymaganie|
|-----------------|----------------------------------------------|
|Należy zainstalować funkcję Hyper-V|Postępuj zgodnie z tymi samymi instrukcjami, które są używane do [włączania funkcji Hyper-V dla emulatora Windows Phone](/previous-versions/windows/apps/jj863509(v=vs.105)).<br /><br /> Sprawdź stan usługi **zarządzania maszynami wirtualnymi funkcji Hyper-V** w przystawce usługi.|
|Funkcja Hyper-V musi być uruchomiona.|Aby uzyskać więcej informacji na temat zarządzania usługami, zobacz następujące tematy:<br /><br /> -   [Uruchamianie, zatrzymywanie, wstrzymywanie, wznawianie lub ponowne uruchamianie usługi](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [Konfigurowanie sposobu uruchamiania usługi](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|

 Musisz być członkiem lokalnej grupy Administratorzy funkcji Hyper-V.

 Aby uruchomić emulator programu Visual Studio dla systemu Android bez powtarzania monitu o podniesienie poziomu uprawnień, musisz być członkiem lokalnej grupy Administratorzy funkcji Hyper-V. Jeśli użytkownik jest już administratorem lokalnym na komputerze podczas instalowania zestawu SDK, program instalacyjny zestawu SDK dodaje użytkownika do grupy Administratorzy funkcji Hyper-V. W przeciwnym razie może być konieczne ręczne włączenie tego wymagania.

 Po uruchomieniu emulatora, jeśli nie jesteś jeszcze członkiem grupy Administratorzy funkcji Hyper-V, zostanie wyświetlony monit o dołączenie do grupy (okno dialogowe odwołuje się do emulatora Windows Phone). Dołączenie do grupy wymaga uprawnień administratora.

> [!IMPORTANT]
> Po dołączeniu do grupy Wyloguj się lub Uruchom ponownie, aby zmiany zaczęły obowiązywać.

 ![Przyłączanie do grupy zabezpieczeń Administratorzy funkcji Hyper&#45;V](../cross-platform/media/android_emu_hyperv_admin.png "Android_Emu_HyperV_Admin")

 Aby ręcznie dodać do grupy, Otwórz przystawkę Użytkownicy i grupy lokalne.

## <a name="running-the-emulator-from-a-bootable-vhd-is-not-supported"></a>Uruchamianie emulatora z rozruchowego dysku VHD nie jest obsługiwane
 Jeśli spróbujesz uruchomić aplikację w emulatorze programu Visual Studio dla systemu Android, gdy uruchamiasz system Windows z rozruchowego dysku VHD, Emulator zazwyczaj trwa kilka minut, aby uruchomić program lub go nie uruchomić. Po awarii emulatora zostanie wyświetlony następujący komunikat: wdrażanie aplikacji nie powiodło się. Spróbuj ponownie.

 Ta konfiguracja nie jest obsługiwana. Aby uzyskać informacje dotyczące problemów pokrewnych, zobacz [Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).

## <a name="hyper-v-requires-uncompressed-and-unencrypted-files"></a>Funkcja Hyper-V wymaga nieskompresowanych i nieszyfrowanych plików
 Na dysku twardym skonfigurowanym za pomocą systemu plików NTFS pliki wirtualnych dysków twardych używanych przez funkcję Hyper-V muszą być nieskompresowane i niezaszyfrowane. Upewnij się, że następujące katalogi nie są skompresowane ani zaszyfrowane:

- %localappdata%\Microsoft\XDE

- C:\Program Files (x86)\Microsoft Emulator Manager

- C:\Program Files (x86) \Microsoft Visual Studio Emulator for Android

- %localappdata%\Microsoft\VisualStudioEmulator

W systemie plików ReFS pliki wirtualnego dysku twardego nie mogą mieć ustawionego bitu integralności.

## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>Wymagania dotyczące sprzętowego przekazywania grafiki (Obsługa technologii OpenGL ES)

Aby emulator mógł emulować wywołania procesora GPU, na przykład te używane przez oprogramowanie OpenGL ES, maszyna musi mieć procesor GPU zgodny z odpowiednim sterownikiem DirectX.

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z narzędziem Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
