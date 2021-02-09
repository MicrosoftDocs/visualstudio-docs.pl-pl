---
title: Istotne zmiany w rozszerzalności programu Visual Studio 2017
description: Zapoznaj się z informacjami technicznymi dotyczącymi istotnych zmian w modelu rozszerzalności w programie Visual Studio 2017 i co możesz zrobić, aby rozwiązać te problemy.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e8c6febd609695be49fe868041faea25af70fed5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927382"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Zmiany w rozszerzalności programu Visual Studio 2017

Program Visual Studio 2017 zapewnia [szybsze, jaśniejsze środowisko instalacji programu Visual Studio](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) , które zmniejsza wpływ programu Visual Studio w systemach użytkowników, zapewniając użytkownikom większy wybór w przypadku zainstalowanych obciążeń i funkcji. Aby zapewnić obsługę tych ulepszeń, wprowadziliśmy zmiany w modelu rozszerzalności, w tym niektóre istotne zmiany. W tym artykule opisano techniczne informacje o tych zmianach i możliwości ich rozwiązania.

> [!NOTE]
> Niektóre informacje to szczegóły implementacji do określonego momentu i można je później zmienić.

## <a name="changes-affecting-vsix-format-and-installation"></a>Zmiany wpływające na format i instalację VSIX

W programie Visual Studio 2017 wprowadzono format VSIX v3 (wersja 3) do obsługi uproszczonej instalacji.

Zmiany w formacie VSIX obejmują:

* Deklaracja wymagań wstępnych Instalatora. Aby dostarczać w ramach obietnicy lekkiej i szybkiej instalacji programu Visual Studio, Instalator udostępnia teraz więcej opcji konfiguracji użytkownikom. W związku z tym, aby upewnić się, że funkcje i składniki wymagane przez rozszerzenie są zainstalowane, rozszerzenia muszą zadeklarować ich zależności.

  * Instalator programu Visual Studio 2017 automatycznie oferuje możliwość pobrania i zainstalowania niezbędnych składników dla użytkownika w ramach instalacji rozszerzenia.
  * Użytkownicy są również ostrzegani przy próbie zainstalowania rozszerzenia, które nie zostało skompilowane przy użyciu nowego formatu VSIX v3, nawet jeśli zostały oznaczone jako element docelowy w wersji 15,0.

* Ulepszone możliwości formatu VSIX. Aby zapewnić instalację programu Visual Studio z [niską wpływem](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) , która obsługuje także instalacje równoległe, nie zapisujemy w rejestrze systemu większości danych dotyczących programu Visual Studio i zostały one przeniesione z pamięci GAC. Zwiększono również możliwości formatu VSIX i aparatu instalacji VSIX, umożliwiając używanie go zamiast MSI lub EXE do instalowania rozszerzeń dla niektórych typów instalacji.

Nowe możliwości obejmują:

* Rejestracja w określonym wystąpieniu programu Visual Studio.
* Instalacja poza [folderem rozszerzeń](set-install-root.md).
* Wykrywanie architektury procesora.
* Zależność od pakietów językowych oddzielonych od języka.
* Instalacja z [obsługą NGen](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Kompiluj rozszerzenie dla programu Visual Studio 2017

Narzędzia projektanta do tworzenia nowego formatu manifestu VSIX V3 są dostępne w programie Visual Studio 2017. Zapoznaj się z towarzyszącym dokumentem [instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) w celu uzyskania szczegółowych informacji na temat korzystania z narzędzi projektanta lub ręcznego aktualizowania projektu i manifestu w celu opracowania rozszerzeń VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Zmiana: ścieżka danych użytkownika programu Visual Studio

Wcześniej na każdej maszynie może istnieć tylko jedna instalacja poszczególnych głównych wersji programu Visual Studio. Do obsługi równoległych instalacji programu Visual Studio 2017 na komputerze użytkownika może istnieć wiele ścieżek danych użytkownika dla programu Visual Studio.

Kod uruchomiony w ramach procesu programu Visual Studio należy zaktualizować, aby można było korzystać z Menedżera ustawień programu Visual Studio. Kod uruchomiony poza procesem programu Visual Studio może znaleźć ścieżkę użytkownika określonej instalacji programu Visual Studio [, postępując zgodnie ze wskazówkami tutaj](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Zmiana: globalna pamięć podręczna zestawów (GAC)

Większość zestawów podstawowych programu Visual Studio nie jest już zainstalowana w pamięci podręcznej GAC. Wprowadzono następujące zmiany, dzięki czemu kod uruchomiony w procesie programu Visual Studio nadal może znaleźć wymagane zestawy w czasie wykonywania.

> [!NOTE]
> [INSTALLDIR] poniżej odnosi się do katalogu głównego instalacji programu Visual Studio. *VSIXInstaller.exe* automatycznie wypełni to, ale aby napisać niestandardowy kod wdrożenia, przeczytaj artykuł [lokalizowanie programu Visual Studio](locating-visual-studio.md).

* Zestawy, które zostały zainstalowane tylko w pamięci podręcznej GAC:

  Te zestawy są teraz zainstalowane w obszarze <em>[INSTALLDIR] \Common7\IDE \* , * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> lub *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*. Te foldery są częścią ścieżek do sondowania procesu programu Visual Studio.

* Zestawy, które zostały zainstalowane w niezgodnej ścieżce i w pamięci GAC:

  * Kopia w pamięci podręcznej GAC została usunięta z Instalatora.
  * Dodano plik *. pkgdef* , aby określić podstawowy wpis kodu dla zestawu.

    Na przykład:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    W czasie wykonywania podsystem programu Visual Studio pkgdef scala te wpisy w pliku konfiguracji środowiska uruchomieniowego procesu programu Visual Studio (w obszarze *[VSAPPDATA] \devenv.exe.config*) jako [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) elementy. Jest to zalecany sposób, aby umożliwić programowi Visual Studio znalezienie Twojego zestawu, ponieważ pozwala to uniknąć wyszukiwania przez ścieżki sondowania.

### <a name="reacting-to-this-breaking-change"></a>Trwa przerywanie tej zmiany

* Jeśli rozszerzenie jest uruchomione w ramach procesu programu Visual Studio:

  * Twój kod będzie mógł znaleźć podstawowe zestawy programu Visual Studio.
  * Rozważ użycie pliku *. pkgdef* w celu określenia ścieżki do zestawów, jeśli jest to konieczne.

* Jeśli rozszerzenie jest uruchomione poza procesem programu Visual Studio:

  Rozważ wyszukiwanie zestawów podstawowych programu Visual Studio w obszarze <em>[INSTALLDIR] \Common7\IDE \* , * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> lub *[INSTALLDIR] \Common7\IDE\PrivateAssemblies* przy użyciu pliku konfiguracyjnego lub mechanizmu rozwiązywania problemów z zestawem.

## <a name="change-reduce-registry-impact"></a>Zmiana: Zmniejsz wpływ na rejestr

### <a name="global-com-registration"></a>Globalna Rejestracja modelu COM

* Wcześniej program Visual Studio zainstalował wiele kluczy rejestru w HKEY_CLASSES_ROOT i HKEY_LOCAL_MACHINE Hive w celu obsługi rejestracji natywnego modelu COM. Aby wyeliminować ten wpływ, program Visual Studio używa teraz [aktywacji bezpłatnej do rejestracji składników modelu COM](/previous-versions/dotnet/articles/ms973913(v=msdn.10)).
* W związku z tym większość plików TLB/OLB/DLL w folderze% ProgramFiles (x86)% \ Common Files\Microsoft Shared\MSEnv nie jest już instalowana domyślnie przez program Visual Studio. Te pliki są teraz zainstalowane w obszarze [INSTALLDIR] z odpowiednimi manifestami COM Registration-Free używanymi przez proces hosta programu Visual Studio.
* W rezultacie kod zewnętrzny, który opiera się na globalnej rejestracji modelu COM dla interfejsów COM programu Visual Studio, nie będzie już znajdować tych rejestracji. Kod uruchomiony w procesie programu Visual Studio nie będzie widział różnic.

### <a name="visual-studio-registry"></a>Rejestr programu Visual Studio

* Wcześniej program Visual Studio zainstalował wiele kluczy rejestru do **HKEY_LOCAL_MACHINE** systemu i **HKEY_CURRENT_USER** gałęzie w ramach klucza specyficznego dla programu Visual Studio:

  * **HKLM\Software\Microsoft\VisualStudio \{ Wersja}**: klucze rejestru utworzone przez Instalatora MSI i rozszerzenia dla poszczególnych maszyn.
  * **HKCU\Software\Microsoft\VisualStudio \{ Wersja}**: klucze rejestru utworzone przez program Visual Studio do przechowywania ustawień specyficznych dla użytkownika.
  * **HKCU\Software\Microsoft\VisualStudio \{ Wersja} _Config**: kopia programu Visual Studio HKLM Key powyżej oraz klucze rejestru scalone z plikami *. pkgdef* według rozszerzeń.

* Aby zmniejszyć wpływ na rejestr, program Visual Studio używa teraz funkcji [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) do przechowywania kluczy rejestru w prywatnym pliku binarnym w obszarze *[VSAPPDATA] \privateregistry.bin*. W rejestrze systemowym pozostaje tylko bardzo mała liczba kluczy specyficznych dla programu Visual Studio.
* Nie ma to wpływu na istniejący kod działający w ramach procesu programu Visual Studio. Program Visual Studio przekierowuje wszystkie operacje rejestru w kluczu specyficznym dla programu Visual Studio do rejestru prywatnego. Odczytywanie i zapisywanie w innych lokalizacjach rejestru będzie nadal korzystać z rejestru systemowego.
* Kod zewnętrzny będzie musiał załadować i odczytać z tego pliku dla wpisów rejestru programu Visual Studio.

### <a name="react-to-this-breaking-change"></a>Reagowanie na tę nieprzerwaną zmianę

* Kod zewnętrzny należy przekonwertować, aby używać również aktywacji Registration-Free dla składników COM.
* Składniki zewnętrzne mogą znaleźć lokalizację programu Visual Studio [, postępując zgodnie ze wskazówkami tutaj](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup).
* Firma Microsoft zaleca, aby składniki zewnętrzne używały [Menedżera ustawień zewnętrznych](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) zamiast odczytywania/zapisywania bezpośrednio w kluczach rejestru programu Visual Studio.
* Sprawdź, czy składniki używane przez rozszerzenie mogły zaimplementować inną technikę do rejestracji. Na przykład rozszerzenia debugera mogą być w stanie skorzystać z nowej [rejestracji modelu COM msvsmon JSON](migrate-debugger-COM-registration.md).