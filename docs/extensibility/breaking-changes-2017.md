---
title: Przełomowe zmiany w rozszerzalności programu Visual Studio 2017
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b3a04c925ef897171de51c73c90973a12c3b17d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739972"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Zmiany w rozszerzalności programu Visual Studio 2017

Visual Studio 2017 zapewnia [szybsze, lżejsze środowisko instalacji programu Visual Studio,](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) które zmniejsza wpływ programu Visual Studio na systemy użytkowników, dając użytkownikom większy wybór w stosunku do zainstalowanych obciążeń i funkcji. Aby obsługiwać te ulepszenia, wnieśliśmy zmiany w modelu rozszerzalności, w tym niektóre zmiany podziału. W tym artykule opisano szczegóły techniczne tych zmian i co można zrobić, aby je rozwiązać.

> [!NOTE]
> Niektóre informacje są szczegółowe informacje o implementacji punktu w czasie i mogą zostać zmienione później.

## <a name="changes-affecting-vsix-format-and-installation"></a>Zmiany wpływające na format i instalację VSIX

W programie Visual Studio 2017 wprowadzono format VSIX w wersji 3 (wersja 3) w celu obsługi środowiska instalacji w wersji 1000.

Zmiany w formacie VSIX obejmują:

* Wymagania wstępne dotyczące deklaracji konfiguracji. Aby zrealizować obietnicę lekkiej, szybko instalującej się programu Visual Studio, instalator oferuje teraz użytkownikom więcej opcji konfiguracji. W rezultacie, aby upewnić się, że funkcje i składniki wymagane przez rozszerzenie są zainstalowane, rozszerzenia muszą zadeklarować swoje zależności.

  * Instalator programu Visual Studio 2017 automatycznie oferuje uzyskanie i zainstalowanie niezbędnych składników dla użytkownika w ramach instalowania rozszerzenia.
  * Użytkownicy są również ostrzegani podczas próby zainstalowania rozszerzenia, które nie zostało zbudowane przy użyciu nowego formatu VSIX v3, nawet jeśli zostały one oznaczone w manifeście jako kierowanie w wersji 15.0.

* Rozszerzone możliwości formatu VSIX. Aby dostarczyć na [instalacji o niskim wpływie](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) programu Visual Studio, który obsługuje również instalacje side-by-side, nie możemy już zapisać większość danych konfiguracyjnych w rejestrze systemu i przenieśli visual studio zestawy specyficzne z gac. Zwiększyliśmy również możliwości aparatu instalacyjnego formatu VSIX i VSIX, umożliwiając użycie go zamiast MSI lub EXE w celu zainstalowania rozszerzeń dla niektórych typów instalacji.

Nowe możliwości obejmują:

* Rejestracja w określonym wystąpieniu programu Visual Studio.
* Instalacja poza [folderem rozszerzeń](set-install-root.md).
* Wykrywanie architektury procesora.
* Zależność od pakietów językowych oddzielonych.
* Instalacja z [obsługą NGEN](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Tworzenie rozszerzenia dla programu Visual Studio 2017

Narzędzia projektanta do tworzenia nowego formatu manifestu VSIX v3 jest dostępny w programie Visual Studio 2017. Zobacz dokument towarzyszący [Jak: Migrowanie projektów rozszerzalności do programu Visual Studio 2017, aby](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) uzyskać szczegółowe informacje na temat korzystania z narzędzi projektanta lub ręcznego aktualizowania projektu i manifestu w celu opracowania rozszerzeń VSIX w wersji 3.

## <a name="change-visual-studio-user-data-path"></a>Zmiana: ścieżka danych użytkownika programu Visual Studio

Wcześniej tylko jedna instalacja każdej głównej wersji programu Visual Studio może istnieć na każdym komputerze. Aby obsługiwać instalacje side-by-side programu Visual Studio 2017, wiele ścieżek danych użytkownika dla programu Visual Studio może istnieć na komputerze użytkownika.

Kod uruchomiony wewnątrz procesu programu Visual Studio powinny zostać zaktualizowane do korzystania z Menedżera ustawień programu Visual Studio. Kod uruchomiony poza procesem programu Visual Studio można znaleźć ścieżkę użytkownika określonej instalacji programu Visual [Studio, postępujący w tym miejscu.](locating-visual-studio.md)

## <a name="change-global-assembly-cache-gac"></a>Zmiana: globalna pamięć podręczna zestawów (GAC)

Większość podstawowych zestawów programu Visual Studio nie są już instalowane w pliku GAC. Następujące zmiany zostały wprowadzone tak, że kod uruchomiony w procesie programu Visual Studio nadal można znaleźć wymagane zestawy w czasie wykonywania.

> [!NOTE]
> [INSTALLDIR] poniżej odnosi się do katalogu głównego instalacji programu Visual Studio. *Program VSIXInstaller.exe* automatycznie wypełni ten pakiet, ale aby napisać niestandardowy kod wdrożenia, przeczytaj [lokalizowanie programu Visual Studio](locating-visual-studio.md).

* Zestawy, które zostały zainstalowane tylko w gac:

  Zestawy te są teraz instalowane w obszarze <em>[INSTALLDIR]\Common7\IDE\*, *[INSTALLDIR]\Common7\IDE\PublicAssemblies</em> lub *[INSTALLDIR]\Common7\IDE\PrivateAssemblies*. Te foldery są częścią ścieżki sondowania procesu programu Visual Studio.

* Zestawy, które zostały zainstalowane w ścieżce niesądowania i do GAC:

  * Kopia w pliku GAC została usunięta z instalatora.
  * Plik *pkgdef* został dodany w celu określenia wpisu podstawowego kodu dla zestawu.

    Przykład:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    W czasie wykonywania podsystem pkgdef programu Visual Studio scala te wpisy z plikiem konfiguracji środowiska wykonawczego programu Visual Studio (w obszarze [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) *[VSAPPDATA]\devenv.exe.config)* jako elementy. Jest to zalecany sposób, aby umożliwić proces Visual Studio znaleźć zestaw, ponieważ unika przeszukiwania ścieżek sondowania.

### <a name="reacting-to-this-breaking-change"></a>Reagowanie na tę przełomową zmianę

* Jeśli rozszerzenie jest uruchomione w ramach procesu programu Visual Studio:

  * Kod będzie można znaleźć zestawy podstawowe programu Visual Studio.
  * Należy rozważyć użycie pliku *pkgdef,* aby określić ścieżkę do zestawów, jeśli to konieczne.

* Jeśli rozszerzenie jest uruchomione poza procesem programu Visual Studio:

  Rozważ wyszukania podstawowych zestawów programu Visual Studio w obszarze <em>[INSTALLDIR]\Common7\IDE\*, *[INSTALLDIR]\Common7\IDE\PublicAssemblies</em> lub *[INSTALLDIR]\Common7\IDE\PrivateAssemblies* przy użyciu pliku konfiguracyjnego lub programu rozpoznawania nazw zestawu.

## <a name="change-reduce-registry-impact"></a>Zmiana: Zmniejsz wpływ rejestru

### <a name="global-com-registration"></a>Globalna rejestracja COM

* Wcześniej program Visual Studio zainstalował wiele kluczy rejestru w HKEY_CLASSES_ROOT i HKEY_LOCAL_MACHINE gałęzi do obsługi natywnej rejestracji COM. Aby wyeliminować ten wpływ, program Visual Studio używa teraz [aktywacji bez rejestracji dla składników COM.](https://msdn.microsoft.com/library/ms973913.aspx)
* W rezultacie większość plików TLB / OLB / DLL w obszarze %ProgramFiles(x86)%\Common Files\Microsoft Shared\MSEnv nie jest już domyślnie instalowana w programie Visual Studio. Pliki te są teraz instalowane w obszarze [INSTALLDIR] z odpowiednimi manifestami COM bez rejestracji używanymi przez proces hosta programu Visual Studio.
* W rezultacie kod zewnętrzny, który opiera się na globalnej rejestracji COM dla interfejsów COM programu Visual Studio nie będzie już znaleźć te rejestracje. Kod uruchomiony wewnątrz procesu programu Visual Studio nie będzie widoczny różnicę.

### <a name="visual-studio-registry"></a>Rejestr programu Visual Studio

* Wcześniej program Visual Studio zainstalował wiele kluczy rejestru w **HKEY_LOCAL_MACHINE** i **HKEY_CURRENT_USER** gałęzi systemu w ramach klucza specyficznego dla programu Visual Studio:

  * **HKLM\Software\Microsoft\VisualStudio\{Version}**: Klucze rejestru utworzone przez instalatory MSI i rozszerzenia na komputer.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}**: Klucze rejestru utworzone przez program Visual Studio w celu przechowywania ustawień specyficznych dla użytkownika.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}_Config:** Kopia klucza HKLM programu Visual Studio powyżej oraz klucze rejestru scalone z plików *pkgdef* przez rozszerzenia.

* Aby zmniejszyć wpływ na rejestr, program Visual Studio używa teraz funkcji [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) do przechowywania kluczy rejestru w prywatnym pliku binarnym w obszarze *[VSAPPDATA]\privateregistry.bin*. Tylko bardzo mała liczba kluczy specyficznych dla programu Visual Studio pozostają w rejestrze systemu.
* Istniejący kod uruchomiony wewnątrz procesu programu Visual Studio nie ma wpływu. Visual Studio przekieruje wszystkie operacje rejestru w ramach klucza specyficznego dla programu HKCU Visual Studio do rejestru prywatnego. Odczytywanie i zapisywanie w innych lokalizacjach rejestru będzie nadal korzystać z rejestru systemowego.
* Kod zewnętrzny będzie musiał załadować i odczytać z tego pliku dla wpisów rejestru programu Visual Studio.

### <a name="react-to-this-breaking-change"></a>Reaguj na tę przełomową zmianę

* Kod zewnętrzny powinien zostać przekonwertowany na aktywację bez rejestracji dla składników COM.
* Składniki zewnętrzne można znaleźć lokalizację programu Visual [Studio, postępuje zgodnie ze wskazówkami tutaj](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup).
* Zaleca się, aby składniki zewnętrzne [używały Menedżera ustawień zewnętrznych](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) zamiast odczytywania/zapisywania bezpośrednio do kluczy rejestru programu Visual Studio.
* Sprawdź, czy składniki używane przez rozszerzenie mogły zaimplementować inną technikę rejestracji. Na przykład rozszerzenia debugera mogą być w stanie skorzystać z nowej [rejestracji COM pliku msvsmon JSON](migrate-debugger-COM-registration.md).
