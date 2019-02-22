---
title: Aktualizowanie instalacji sieciowej
description: Dowiedz się, jak zaktualizować instalacji programu Visual Studio za pośrednictwem sieci przy użyciu polecenia — układ
ms.date: 08/14/2017
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28ba86dcfb1fb98d9ba88c06a8df2ea3a104ea4d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617291"
---
# <a name="update-a-network-based-installation-of-visual-studio-2017"></a>Aktualizowanie instalacji sieciowej programu Visual Studio 2017

Jego jest to możliwe, aby zaktualizować układu instalacji sieciowej programu Visual Studio przy użyciu najnowszych aktualizacji produktów, tak, aby można go jako punkt instalacji wykorzystywana do najnowszej aktualizacji programu Visual Studio, a także do obsługi instalacji, które są już wdrożone do klienta stacje robocze.

## <a name="how-to-update-a-network-layout"></a>Jak zaktualizować układ sieci

Aby odświeżyć instalacji udziale sieciowym, aby obejmowała najnowsze aktualizacje, należy uruchomić `--layout` polecenie, aby pobrać przyrostowo zaktualizowane pakiety.

**Nowość w 15.3**: Jeśli wybrano opcję częściowej układu podczas pierwszego utworzenia układu sieci, te ustawienia są zapisywane.  Dowolne polecenia przyszłych układu użyć poprzednie opcje, a także nowe opcje, które określisz. Ale jeśli używasz układu starszej wersji, należy użyć tego samego parametry wiersza polecenia, które były używane podczas pierwszego utworzenia instalacji układ sieci (innymi słowy, tego samego obciążenia i języków) aby zaktualizować swoją zawartość.

Jeśli hostujesz układu w udziale plików, należy zaktualizować prywatną kopię układu (na przykład c:\vs2017offline) i następnie, po pobraniu wszystkich zaktualizowanej zawartości, skopiuj go do udziału plików (na przykład \\server\products\VS2017). Jeśli nie możesz tego zrobić, istnieje duże prawdopodobieństwo, że użytkownicy, którzy uruchom Instalatora, podczas gdy aktualizujesz układ może nie można pobrać całą zawartość z układu, ponieważ to nie jest jeszcze całkowicie aktualizowany.

Przejdźmy przez kilka przykładów sposobu tworzenia, a następnie zaktualizuj układu:

* Po pierwsze poniżej przedstawiono przykład sposobu tworzenia układu z obciążeniem jeden dla angielskiego tylko:

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Oto jak można zaktualizować tego samego układu do nowszej wersji. Nie trzeba określać żadnych dodatkowych parametrów wiersza polecenia. Poprzednie ustawienia zostały zapisane i będą używane przez dowolne polecenia kolejnych układu, w tym folderze układu.

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout
  ```

* Poniżej przedstawiono sposób zaktualizować do nowszej wersji układu w trybie nienadzorowanym. Operacji układu uruchamia proces instalacji w nowym oknie konsoli. Okno jest pozostawione otwarte, dzięki czemu użytkownicy mogą zobaczyć wynik końcowy oraz podsumowania błędów, które mogły wystąpić. Jeśli przeprowadzasz operację układu w trybie nienadzorowanym (na przykład masz skrypt uruchamiany regularnie w celu aktualizacji układu do najnowszej wersji), następnie za pomocą `--passive` parametru i proces zostanie automatycznie zamknięte okna.

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --passive
  ```

* Poniżej przedstawiono sposób dodać dodatkowe obciążenie i język zlokalizowanego.  (To polecenie dodaje obciążenie platformy Azure).  Teraz zarządzane pulpitu i platformy Azure znajdują się w tym układzie.  Zasoby języka na język angielski i niemiecki dostępne są również dla tych obciążeń.  I układ zostanie zaktualizowany do najnowszej dostępnej wersji.

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

* A na koniec, Oto jak dodać dodatkowe obciążenie i język zlokalizowanego bez aktualizowania wersji. (To polecenie dodaje obciążenia ASP.NET i sieci Web).  Teraz obciążeń zarządzanego pulpitu, Azure, platformy ASP.NET i sieci Web znajdują się w tym układzie. Zasoby języka na język angielski, niemiecki i francuski dostępne są również dla tych obciążeń.  Układ nie został jednak zaktualizowany do najnowszej dostępnej wersji podczas uruchomienia tego polecenia. Pozostaje w istniejącą wersję.

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="how-to-deploy-an-update-to-client-machines"></a>Jak wdrożyć aktualizację na komputerach klienckich

W zależności od konfiguracji środowiska sieciowego aktualizacja może być wdrażane przez administratora przedsiębiorstwa lub inicjowane z komputera klienckiego.

* Użytkownicy mogą zaktualizować wystąpienia programu Visual Studio, która została zainstalowana z folderu instalacji w trybie offline:
  * Uruchom Instalatora programu Visual Studio.
  * Następnie kliknij przycisk **aktualizacji**.

* Administratorzy mogą zaktualizować wdrożeń klientów programu Visual Studio bez żadnej interakcji użytkownika z dwóch oddzielnych poleceń:
  * Po pierwsze Aktualizacja Instalatora programu Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Następnie zaktualizuj samej aplikacji programu Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

> [!NOTE]
> Użyj [polecenia vswhere.exe](tools-for-managing-visual-studio-instances.md) do identyfikowania ścieżki instalacji istniejącego wystąpienia programu Visual Studio na komputerze klienckim.
>
> [!TIP]
> Aby uzyskać szczegółowe informacje o sposobie kontroli, gdy aktualizacja powiadomienia są prezentowane dla użytkowników, zobacz [kontrolowania aktualizacji z wdrożeniami programu Visual Studio sieciowymi programami wykorzystującymi](controlling-updates-to-visual-studio-deployments.md).

## <a name="how-to-verify-a-layout"></a>Jak zweryfikować układu

Użyj `--verify` do przeprowadzenia weryfikacji w pamięci podręcznej offline dostarczony. Sprawdza, czy pliki pakietów brakujący lub nieprawidłowy. Po zakończeniu weryfikacji zostanie wydrukowany lista brakujących plików i plików nieprawidłowy.

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

Vs_enterprise.exe może być wywołana wewnątrz layoutDir.

> [!NOTE]
> Niektóre pliki ważne metadane, które są wymagane przez `--verify` opcja musi być w pamięci podręcznej offline układu. Jeśli brakuje te pliki metadanych "--Sprawdź" nie można uruchomić i konfiguracji zawiera błąd. Jeśli wystąpi ten błąd, ponownie utwórz nowy układ w trybie offline, inny folder (lub do tego samego folderu pamięci podręcznej offline. Aby to zrobić, uruchomić to samo polecenie Układ, który został użyty do utworzenia początkowego układu w trybie offline. Na przykład `Vs_enterprise.exe --layout <layoutDir>`.

Microsoft jest dostarczany aktualizacje programu Visual Studio okresowo, aby nowy układ, które tworzysz może nie być tej samej wersji, co wstępny układ.

## <a name="how-to-fix-a-layout"></a>Jak naprawić układu

Użyj `--fix` do wykonania tych samych weryfikacji jako `--verify` i również spróbować naprawić zidentyfikowanych problemów. `--fix` Proces wymaga połączenia internetowego, dlatego upewnij się, że maszyna jest połączona z Internetem, zanim wywołujesz `--fix`.

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

Vs_enterprise.exe może być wywołana wewnątrz layoutDir.

## <a name="how-to-remove-older-versions-from-a-layout"></a>Jak usunąć starsze wersje z układu

Po wykonaniu aktualizacji układ pamięci podręcznej trybu offline, układ folder pamięci podręcznej może mieć niektórych przestarzałych pakietów, które nie są już potrzebne najnowsze instalacją programu Visual Studio. Możesz użyć `--clean` opcji usuwania przestarzałych pakietów z folderu pamięci podręcznej offline.

Aby to zrobić, należy ścieżki pliku do katalogu manifest(s), zawierające te przestarzałych pakietów. Można znaleźć katalogu manifesty w folderze "Archiwalna" w pamięci podręcznej układu w trybie offline. Są zapisywane istnieje po zaktualizowaniu układu. W folderze "Archiwalna" ma co najmniej jeden "GUID" o nazwie folderów, z których każdy zawiera manifest przestarzałe katalogu. Liczba folderów "GUID" należy taka sama jak liczba aktualizacje wprowadzone w pamięci podręcznej w trybie offline.

Kilka pliki są zapisywane wewnątrz każdego folderu "GUID". Dwa pliki najbardziej przydatnych są oraz plik "catalog.json" "version.txt". Plik "catalog.json" jest manifest przestarzałe katalogu, należy przekazać do `--clean` opcji. Plik version.txt zawiera wersję tego manifestu przestarzałe katalogu. Oparte na numer wersji, możesz zdecydować, czy chcesz usunąć przestarzałych pakietów z manifestu tego katalogu. Można tak samo, jak przejść do innych folderów "GUID". Po podjęciu decyzji o katalogi, które chcesz wyczyścić, uruchom `--clean` polecenie, podając ścieżki plików do tych katalogów.

Poniżej przedstawiono kilka przykładów sposobu użycia — wyczyść opcję:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Można również wywołać vs_enterprise.exe wewnątrz &lt;layoutDir&gt;. Oto przykład:

```cmd
c:\VS2017Layout\vs_enterprise.exe --layout c:\VS2017Layout --clean c:\VS2017Layout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Po wykonaniu tego polecenia, Instalator analizuje folder pamięci podręcznej w trybie offline, aby uzyskać listę plików, które zostanie usunięta. Użytkownik będzie miał szansę, aby przejrzeć pliki, które są przesyłane do usunięcia, a potwierdzenie operacji usuwania.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Podręcznik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
* [Sterowanie aktualizacjami na potrzeby wdrożenia oparte na sieci programu Visual Studio](controlling-updates-to-visual-studio-deployments.md)
