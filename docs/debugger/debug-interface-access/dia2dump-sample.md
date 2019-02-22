---
title: Dia2dump — przykład | Dokumentacja firmy Microsoft
ms.date: 07/24/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb86929a050a61a50a7aa1dd41220f4e087ad767
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607047"
---
# <a name="dia2dump-sample"></a>Dia2dump — Przykład

Dia2dump — przykład pokazuje, jak tworzenie zapytania pliku PDB, aby uzyskać informacje przy użyciu Microsoft debugowanie interfejsu dostępu Software Development Kit (DIA SDK).

Dia2dump — przykład został zainstalowany przy użyciu programu Visual Studio i zawiera pliki rozwiązań i źródła. Skompilowany plik wykonywalny jest uruchamiany z wiersza polecenia. Umożliwia wyświetlanie zawartości pliku bazy danych (PDB) całego programu, lub po prostu sekcje interesuje Cię.

## <a name="install-the-sample"></a>Zainstaluj próbki

Próbka jest zainstalowany, po wybraniu **programowanie aplikacji klasycznych w języku C++** obciążenie w Instalatorze programu Visual Studio. Aby uzyskać informacje na temat sposobu instalowania programu Visual Studio i wybierz konkretnych obciążeń oraz poszczególnych składników, zobacz [Zainstaluj program Visual Studio](../../install/install-visual-studio.md).

Po zainstalowaniu przykładu jest w katalogu instalacji programu Visual Studio, w podkatalogu o nazwie \DIA SDK\Samples\DIA2Dump.

## <a name="build-the-sample"></a>Skompilować przykład

Domyślnie katalog instalacyjny jest chronionym katalogu. Oznacza to, że należy użyć wiersz polecenia dla deweloperów lub wystąpienia programu Visual Studio do tworzenia i edytowania przykładowe rozwiązanie w tej lokalizacji. Aby uprościć kompilacji, zalecamy najpierw skopiuj pliki z katalogu próbki do innego katalogu, takie jak folder w folderze dokumenty, a następnie skompilować przykład.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Aby zbudować dia2dump — przykład w programie Visual Studio

1. Otwórz plik DIA2Dump.sln w programie Visual Studio. Jeśli rozwiązanie nie został skopiowany do innego katalogu, monit może ponownie program Visual Studio z podniesionymi uprawnieniami.

1. W **Eksploratora rozwiązań**, wybierz projekt dia2dump — (nie rozwiązanie).

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](/cpp/ide/working-with-project-properties).

1. Otwórz **właściwości konfiguracji** > **C/C++** > **ogólne** stronę właściwości.

1. W **dodatkowe katalogi dołączenia** właściwości, wybierz formant listy rozwijanej, a następnie wybierz **Edytuj**.

1. W **dodatkowe katalogi dołączenia** wprowadź okna dialogowego, w polu edycji `$(VSInstallDir)DIA SDK\include` katalogu. Dodaj ten katalog w celu zagwarantowania, że kompilator może odnaleźć pliku dia2.h. Wybierz **OK** Aby zapisać zmiany.

1. Wybierz **OK** Aby zapisać zmiany we właściwościach projektu.

1. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**. Domyślnie program Visual Studio tworzy wersję debugowania przykładu znajduje się w podkatalogu katalogu rozwiązania debugowania.

1. Zamknij program Visual Studio.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>Aby zbudować dia2dump — przykład w wierszu polecenia

1. W oknie wiersza polecenia dla deweloperów przejdź do katalogu, gdzie kopiowane pliki przykładowe. Jeśli jeszcze nie został skopiowany plik do innego katalogu, należy użyć podwyższonym poziomem uprawnień (Uruchom jako administrator) okno wiersza polecenia dla deweloperów.

1. Wprowadź polecenie `nmake makefile` do tworzenia konfiguracji debugowania domyślne dia2dump.exe.

## <a name="run-the-dia2dump-sample"></a>Uruchom dia2dump — przykład

Dia2Dump.exe opiera się na msdia*wersji*DLL modelu COM serwera zapewnienie usług. W programie Visual Studio 2015 i Visual Studio 2017 wersja jest biblioteki msdia140.dll. Jeśli msdia*wersji*nie można zainicjować serwera COM DLL, należy zarejestrować go dia2dump.exe może pracować. Katalog DIA SDK ma podkatalogu pojemnika, który zawiera x86 wersję biblioteki DLL. Wersja x64 architektury maszyn w bin\amd64, a wersja dla ARM jest bin\arm. Aby zarejestrować bibliotekę dll, otworzyć podwyższone okno Wiersz polecenia dla deweloperów, a następnie przejdź do katalogu zawierającego wersję dla architektury maszyny. Wprowadź polecenie `regsvr32 msdia140.dll` do zarejestrowania serwera COM.

### <a name="to-run-the-sample"></a>Aby uruchomić przykład

1. Otwórz wiersz polecenia i przejdź do katalogu, który zawiera dia2dump.exe zbudowanego działka.

1. Wprowadź polecenie `dia2dump filename` gdzie *filename* to nazwa pliku PDB, aby sprawdzić. Jeśli plik PDB znajduje się w innym katalogu, należy użyć pełnej ścieżki do pliku jako *filename*. To polecenie wyświetla wszystkie dane w pliku PDB.

1. Dia2dump — ma inne opcje, aby wyświetlić tylko wybrane informacje. Użyj `dia2dump -?` polecenie, aby wyświetlić listę wszystkich dostępnych opcji.

## <a name="see-also"></a>Zobacz także

- [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)
