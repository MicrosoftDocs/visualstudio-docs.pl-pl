---
description: Przykład Dia2dump — pokazuje, jak używać zestawu Microsoft Debug Interface Access Software Development Kit (DIA SDK) do wysyłania zapytań do pliku PDB w celu uzyskania informacji.
title: Przykład Dia2dump — | Microsoft Docs
ms.date: 07/24/2018
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a94a16d8e9fd60b042ea7113304b6d14c649b6fa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149187"
---
# <a name="dia2dump-sample"></a>Dia2dump — Przykład

Przykład Dia2dump — pokazuje, jak używać zestawu Microsoft Debug Interface Access Software Development Kit (DIA SDK) do wysyłania zapytań do pliku PDB w celu uzyskania informacji.

Przykład Dia2dump — jest instalowany z programem Visual Studio i zawiera rozwiązanie i pliki źródłowe. Skompilowany plik wykonywalny jest uruchamiany z wiersza polecenia. Może wyświetlać zawartość całego pliku bazy danych programu (. pdb) lub tylko interesujące Cię sekcje.

## <a name="install-the-sample"></a>Instalowanie przykładu

Przykład jest instalowany podczas wybierania **środowiska tworzenia aplikacji klasycznych w języku C++** w Instalator programu Visual Studio. Aby uzyskać informacje na temat sposobu instalowania programu Visual Studio i wybierania określonych obciążeń i poszczególnych składników, zobacz [Instalowanie programu Visual Studio](../../install/install-visual-studio.md).

Po zainstalowaniu przykład znajduje się w katalogu instalacyjnym programu Visual Studio, w podkatalogu o nazwie \DIA SDK\Samples\DIA2Dump.

## <a name="build-the-sample"></a>Kompiluj przykład

Domyślnie katalog instalacyjny jest katalogiem chronionym. Oznacza to, że należy użyć wiersza polecenia lub wystąpienia programu Visual Studio z podwyższonym poziomem uprawnień, aby skompilować i edytować przykładowe rozwiązanie w tej lokalizacji. Aby uprościć kompilację, zalecamy najpierw skopiować pliki z przykładowego katalogu do innego katalogu, takiego jak folder w folderze dokumenty, a następnie skompilować przykład.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Aby skompilować przykład Dia2dump — w programie Visual Studio

1. Otwórz plik Dia2dump —. sln w programie Visual Studio. Jeśli nie skopiowano rozwiązania do innego katalogu, może zostać wyświetlony monit o ponowne uruchomienie programu Visual Studio z podniesionymi uprawnieniami.

1. W **Eksplorator rozwiązań** wybierz projekt Dia2dump — (a nie rozwiązanie).

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Praca z właściwościami projektu](/cpp/build/working-with-project-properties).

1. Otwórz   >  stronę właściwości ogólne **C/C++** właściwości konfiguracji  >   .

1. W obszarze **Dodatkowe katalogi dołączania** Wybierz kontrolkę lista rozwijana, a następnie wybierz pozycję **Edytuj**.

1. W oknie dialogowym **Dodatkowe katalogi dołączane** w polu Edytuj wprowadź `$(VSInstallDir)DIA SDK\include` katalog. Dodaj ten katalog, aby zagwarantować, że kompilator może znaleźć plik dia2. h. Wybierz **przycisk OK** , aby zapisać zmiany.

1. Wybierz **przycisk OK** , aby zapisać zmiany właściwości projektu.

1. W menu **kompilacja** wybierz polecenie **Kompiluj ponownie rozwiązanie**. Domyślnie program Visual Studio kompiluje wersję przykładową do debugowania, znajdującą się w podkatalogu debugowania katalogu rozwiązania.

1. Zamknij program Visual Studio.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>Aby skompilować przykład Dia2dump — w wierszu polecenia

1. W oknie wiersza polecenia dla deweloperów Przejdź do katalogu, do którego skopiowano pliki przykładowe. Jeśli nie skopiowano przykładu do innego katalogu, należy użyć okna wiersza polecenia programisty z podwyższonym poziomem uprawnień (Uruchom jako administrator).

1. Wprowadź polecenie, `nmake makefile` Aby skompilować domyślną konfigurację debugowania dia2dump.exe.

## <a name="run-the-dia2dump-sample"></a>Uruchamianie przykładu Dia2dump —

Dia2Dump.exe opiera się na serwerze COM MSDIA *wersji*. dll w celu świadczenia usług. Począwszy od programu Visual Studio 2015, wersja jest msdia140.dll. Jeśli serwer COM MSDIA *wersja*. dll nie jest zainicjowany, należy go zarejestrować przed zadia2dump.exe może obejść. Katalog DIA SDK ma podkatalog bin, który zawiera wersję x86 biblioteki DLL. Wersja dla maszyn z architekturą x64 jest w bin\amd64, a wersja platformy ARM jest w bin\arm. Aby zarejestrować bibliotekę DLL, Otwórz okno wiersza polecenia dla deweloperów z podwyższonym poziomem uprawnień i przejdź do katalogu, który zawiera wersję architektury komputera. Wprowadź polecenie, `regsvr32 msdia140.dll` Aby zarejestrować serwer com.

### <a name="to-run-the-sample"></a>Aby uruchomić przykład

1. Otwórz wiersz polecenia i przejdź do katalogu, który zawiera skompilowaną dia2dump.exe.

1. Wprowadź polecenie, `dia2dump filename` gdzie *filename* to nazwa pliku PDB, który ma zostać sprawdzony. Jeśli plik PDB znajduje się w innym katalogu, użyj pełnej ścieżki do pliku jako *filename*. To polecenie wyświetla listę wszystkich danych w pliku PDB.

1. Dia2dump — ma inne opcje wyświetlania tylko wybranych informacji. Użyj `dia2dump -?` polecenia, aby wyświetlić listę wszystkich dostępnych opcji.

## <a name="see-also"></a>Zobacz też

- [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)
