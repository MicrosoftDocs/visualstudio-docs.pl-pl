---
title: Fundamentalne zmiany w rozszerzalności programu Visual Studio 2017 | Dokumentacja firmy Microsoft
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fac02f024813e3ca747f498025e113ba4e7a59bd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680479"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Zmiany w rozszerzalności programu Visual Studio 2017

Za pomocą programu Visual Studio 2017, oferujemy [szybszego i lżejszego środowisko instalacji programu Visual Studio](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) , zmniejsza wpływ programu Visual Studio w systemach użytkowników, zapewniając użytkownikom większy wybór za pośrednictwem obciążeń i funkcje są instalowane. Aby obsługiwać te ulepszenia, firma Microsoft wprowadzone zmiany modelu rozszerzalności i wprowadzono kilka zmian niepowodujących rozszerzalności programu Visual Studio. W tym dokumencie opisano szczegóły techniczne dotyczące tych zmian i co można zrobić pozwalających im sprostać. Należy pamiętać, że pewne informacje jest szczegółów implementacji w momencie i może być później zmienić.

## <a name="changes-affecting-vsix-format-and-installation"></a>Zmiany wpływające na VSIX format i instalacji

Wprowadzamy rozszerzeniu VSIX v3 (wersja 3) format obsługują środowisko uproszczonej instalacji.

Zmiany formatu VSIX obejmują:

* Deklaracja wymagań wstępnych Instalatora. Spełniającej obietnicy lekkie, szybkie — Instalowanie programu Visual Studio Instalator oferuje więcej opcji konfiguracji użytkowników. W rezultacie w zapewnienie zainstalowania funkcji i składniki wymagane przez rozszerzenie rozszerzenia należy zadeklarować ich zależności.
  * Instalator programu Visual Studio 2017 będzie automatycznie oferować uzyskanie i zainstalowanie wymaganych składników dla użytkownika w ramach instalacji rozszerzenia.
  * Użytkownicy będą również ostrzegani podczas próby instalacji rozszerzenia, które nie zostało utworzone przy użyciu nowego formatu VSIX v3, nawet wtedy, gdy zostały oznaczone w manifeście jako przeznaczone dla wersji 15.0.
* Poprawione możliwości w zakresie VSIX format. Spełniającej [instalacji o niskim wpływie na](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) programu Visual Studio, który również obsługuje instalacje side-by-side, firma Microsoft nie jest już Zapisz większość danych konfiguracji do rejestru systemowego i zostały przeniesione do programu Visual Studio specyficzne dla zestawów z globalnej pamięci podręcznej zestawów. Zwiększyliśmy także możliwości VSIX format i aparat instalacji VSIX, umożliwiając użyj go zamiast MSI lub EXE, aby zainstalować rozszerzenia dla niektórych typów instalacji.

  Nowe funkcje obejmują:

  * Rejestracja w określonym wystąpieniu programu Visual Studio.
  * Instalacja poza [folder rozszerzenia](set-install-root.md).
  * Wykrywanie architektury procesora.
  * Zależność od pakietów językowych oddzielone od języka.
  * Instalacja z [Obsługa NGEN](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Tworzenie rozszerzenia programu Visual Studio 2017

Projektanta, narzędzia do tworzenia nowej format manifestu VSIX v3 jest teraz dostępna w programie Visual Studio 2017. Zobacz dokument towarzyszący [jak: Migrowanie projektów rozszerzalności do programu Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) szczegółowe informacje na temat przy użyciu narzędzia projektanta lub dokonywania ręczne aktualizacje do projektu i manifest do tworzenia rozszerzenia v3 VSIX.

## <a name="change-visual-studio-user-data-path"></a>Zmiana: Visual Studio user data path

Wcześniej tylko jedna instalacja każdego wydania programu Visual Studio może znajdować się na każdym komputerze. Aby obsługiwać instalacje side-by-side programu Visual Studio 2017, wiele ścieżek danych użytkownika dla programu Visual Studio może istnieć na komputerze użytkownika.

Kodzie działającym wewnątrz procesu programu Visual Studio powinny zostać uaktualnione do użycia w Menedżerze ustawień usługi Visual Studio. Kod działający poza procesem programu Visual Studio można znaleźć ścieżki użytkownika z określoną instalacją programu Visual Studio [postępując zgodnie ze wskazówkami zawartymi w tym miejscu](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Zmiana: Globalna pamięć podręczna zestawów (GAC)

Większość zestawów podstawowych programu Visual Studio są już zainstalowane w GAC. Zostały wprowadzone następujące zmiany, tak że kod uruchomiony w procesie programu Visual Studio w dalszym ciągu można znaleźć wymaganych zestawów w czasie wykonywania.

> [!NOTE]
> [INSTALLDIR] poniżej odwołuje się do katalogu instalacyjnego programu Visual Studio. *VSIXInstaller.exe* automatycznie wypełnić to pole, ale aby pisać kod niestandardowy wdrożenia, należy przeczytać [lokalizowanie programu Visual Studio](locating-visual-studio.md).

* Zestawy, które tylko zostały zainstalowane w GAC:
  * Te zestawy są teraz instalowane w ramach <em>\Common7\IDE [INSTALLDIR]\*, * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> lub *\Common7\IDE\PrivateAssemblies [INSTALLDIR]*. Te foldery są częścią procesu programu Visual Studio ścieżkach sondowania.

* Zestawy, które zostały zainstalowane w ścieżce sondowanie i pamięci podręcznej GAC:
  * Kopiowanie w GAC został usunięty z instalacji.
  * A *.pkgdef* plik został dodany do określenia pozycji podstawowego kodu dla zestawu.

    Na przykład:

    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    W czasie wykonywania w podsystemie pkgdef programu Visual Studio spowoduje scalenie tych wpisów w pliku konfiguracji środowiska uruchomieniowego procesu programu Visual Studio (w obszarze *[VSAPPDATA]\devenv.exe.config*) jako [ `<codeBase>` ](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) elementy. Jest to zalecany sposób umożliwić procesu programu Visual Studio, Znajdź w swoim zestawie, ponieważ eliminuje przeszukiwania sondowania ścieżek.

### <a name="reacting-to-this-breaking-change"></a>Reagowanie na tej istotnej zmiany

* Jeśli rozszerzenie jest uruchomiona w ramach procesu programu Visual Studio:
  * Twój kod będzie szukać zestawów podstawowych programu Visual Studio.
  * Należy rozważyć użycie *.pkgdef* plik, aby określić ścieżkę do zestawów, jeśli to konieczne.
* Jeśli rozszerzenie działa poza procesem programu Visual Studio:
  * Należy wziąć pod uwagę wyszukiwanie zestawów podstawowych programu Visual Studio w obszarze <em>\Common7\IDE [INSTALLDIR]\*, * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> lub *\Common7\IDE\PrivateAssemblies [INSTALLDIR]* używanie mechanizmu rozpoznawania pliku lub zestawu konfiguracji.

## <a name="change-reduce-registry-impact"></a>Zmiana: Ograniczenia wpływu rejestru

### <a name="global-com-registration"></a>Globalne rejestracji modelu COM

* Wcześniej zainstalowany program Visual Studio wielu kluczy rejestru na HKEY_CLASSES_ROOT i HKEY_LOCAL_MACHINE gałęzie do obsługi rejestracji modelu COM macierzystego. Aby wyeliminować wpływ, używa teraz program Visual Studio [aktywacji bez rejestracji składników COM](https://msdn.microsoft.com/library/ms973913.aspx).
* W rezultacie, TLB większość / OLB / plików biblioteki DLL w % ProgramFiles (x86) %\Common Files\Microsoft Shared\MSEnv są już zainstalowane domyślnie w programie Visual Studio. Te pliki są teraz instalowane w ramach [INSTALLDIR] za pomocą odpowiedniego manifesty COM bez rejestrowania używane w procesie hosta programu Visual Studio.
* W rezultacie kod zewnętrzny, która zależy od globalnej rejestracji COM dla interfejsów COM usługi Visual Studio nie jest już znajduje się tyto registrace. Kodzie działającym wewnątrz procesu programu Visual Studio nie będzie widoczna różnica.

### <a name="visual-studio-registry"></a>Visual Studio registry

* Wcześniej zainstalowany program Visual Studio wielu kluczy rejestru w systemie **HKEY_LOCAL_MACHINE** i **HKEY_CURRENT_USER** gałęzie w kluczu dotyczące programu Visual Studio:
  * **HKLM\Software\Microsoft\VisualStudio\{Version}**: Klucze rejestru, tworzone przez instalatory MSI i rozszerzeń dla poszczególnych komputerów.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}**: Klucze rejestru, utworzone przez program Visual Studio, aby przechowywać ustawienia specyficzne dla użytkownika.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}_Config**: Kopię programu Visual Studio HKLM klucz powyżej, a także klucze rejestru są scalane z *.pkgdef* plików według rozszerzenia.
* Aby zmniejszyć wpływ na rejestrze, używa teraz program Visual Studio [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) funkcję, aby przechowywać klucze rejestru w prywatnej pliku binarnego w obszarze *[VSAPPDATA]\privateregistry.bin*. Bardzo niewielkiej liczby Visual Studio kluczy pozostają w rejestrze systemowym.

* Nie ma wpływu na istniejącym kodzie działającym wewnątrz procesu programu Visual Studio. Program Visual Studio będzie przekierowywać wszystkie operacje rejestru w kluczu HKCU Visual Studio specyficzne dla do prywatnego rejestru. Odczytywanie i zapisywanie do innych lokalizacji rejestru będzie nadal korzystać z rejestru systemowego.
* Kod zewnętrzny należy załadować i odczytać z pliku do wpisów rejestru programu Visual Studio.

### <a name="reacting-to-this-breaking-change"></a>Reagowanie na tej istotnej zmiany

* Kod zewnętrzny powinny być konwertowane na potrzeby aktywacji bez rejestracji składników COM, jak również.
* Składniki zewnętrzne, można znaleźć lokalizacji programu Visual Studio [postępując zgodnie ze wskazówkami zawartymi w tym miejscu](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup).
* Zalecane jest używanie składników zewnętrznych [zewnętrznego Menedżera ustawień](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) zamiast odczytu/zapisu bezpośrednio do kluczy rejestru programu Visual Studio.
* Sprawdź, czy składniki, które używa rozszerzenia mogą wdrażać inna technika rejestracji. Na przykład rozszerzenia debugera można korzystać z zalet nowego [msvsmon rejestracji COM plik JSON](migrate-debugger-COM-registration.md).
