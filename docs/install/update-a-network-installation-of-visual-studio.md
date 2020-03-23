---
title: Aktualizowanie instalacji sieciowej
description: Dowiedz się, jak zaktualizować instalację programu Visual Studio opartą na sieci przy użyciu polecenia --layout
ms.date: 01/08/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 68acfcd4acc06ff2b370f3d77a30bd4ec21eb6d1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114980"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Aktualizowanie instalacji sieciowej programu Visual Studio

Istnieje możliwość zaktualizowania układu instalacji sieciowej programu Visual Studio za pomocą najnowszych aktualizacji produktu, dzięki czemu może być używany zarówno jako punkt instalacji dla najnowszej aktualizacji programu Visual Studio, jak i do obsługi instalacji, które są już wdrożone na kliencie Stacje robocze.

## <a name="how-to-update-a-network-layout"></a>Jak zaktualizować układ sieci

> [!IMPORTANT]
> W tych instrukcjach przyjęto założenie, że wcześniej utworzono układ instalacji sieciowej. Aby uzyskać więcej informacji na temat tego, zobacz [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md) strony.

Aby odświeżyć udział instalacji sieciowej, tak `--layout` aby zawiera on najnowsze aktualizacje, uruchom polecenie, aby stopniowo pobierać zaktualizowane pakiety.

::: moniker range="vs-2017"

**Nowość w 15.3**: Jeśli podczas [pierwszego utworzenia układu sieci](create-a-network-installation-of-visual-studio.md)wybrano układ częściowy, ustawienia te zostaną zapisane. Wszystkie przyszłe polecenia układu używają poprzednich opcji oraz wszystkich nowych opcji, które określisz. Jeśli jednak używasz układu starszej wersji, należy użyć tych samych parametrów wiersza polecenia, które zostały użyte podczas pierwszego utworzenia układu instalacji sieciowej (innymi słowy tych samych obciążeń i języków), aby zaktualizować jego zawartość.

::: moniker-end

::: moniker range="vs-2019"

Jeśli podczas pierwszego tworzenia [układu sieci](create-a-network-installation-of-visual-studio.md)wybrano układ częściowy, ustawienia te zostaną zapisane. Wszystkie przyszłe polecenia układu używają poprzednich opcji oraz wszystkich nowych opcji, które określisz.

::: moniker-end

Jeśli układ jest hostowany w udziale plików, należy zaktualizować kopię prywatną układu (na przykład c:\VSLayout), a następnie po pobraniu całej \\zaktualizowanej zawartości skopiuj ją do udziału plików (na przykład server\products\VS). Jeśli tego nie zrobisz, istnieje większa szansa, że wszyscy użytkownicy, którzy uruchamiają Instalatora podczas aktualizowania układu, mogą nie być w stanie uzyskać całej zawartości z układu, ponieważ nie jest jeszcze całkowicie zaktualizowany.

Przejmijmy kilka przykładów tworzenia, a następnie aktualizacji układu:

* Po pierwsze, oto przykład tworzenia układu z jednym obciążeniem tylko w języku angielskim:

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Oto jak zaktualizować ten sam układ do nowszej wersji. Nie trzeba określać żadnych dodatkowych parametrów wiersza polecenia. Poprzednie ustawienia zostały zapisane i będą używane przez wszystkie kolejne polecenia układu w tym folderze układu.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout
  ```

* Poniżej opisano, jak zaktualizować układ do nowszej wersji w sposób nienadzorowany. Operacja układu uruchamia proces instalacji w nowym oknie konsoli. Okno pozostaje otwarte, aby użytkownicy mogli zobaczyć wynik końcowy i podsumowanie wszelkich błędów, które mogły wystąpić. Jeśli wykonujesz operację układu w sposób nienadzorowany (na przykład masz skrypt, który jest regularnie uruchamiany w `--passive` celu zaktualizowania układu do najnowszej wersji), a następnie użyj parametru, a proces automatycznie zamknie okno.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --passive
  ```

* Poniżej opisano, jak dodać dodatkowe obciążenie i zlokalizowany język.  (To polecenie dodaje obciążenie *deweloperów platformy Azure.*  Teraz zarówno zarządzanych pulpitu i platformy Azure są zawarte w tym układzie.  Zasoby językowe dla języka angielskiego i niemieckiego są również uwzględniane dla wszystkich tych obciążeń.  Układ jest aktualizowany do najnowszej dostępnej wersji.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Operacja aktualizacji nie instaluje nowo dodanych składników opcjonalnych, nawet jeśli te składniki zostaną uwzględnione w sekcji "dodaj" [pliku odpowiedzi](automated-installation-with-response-file.md). Dzieje się tak, ponieważ operacja dodawania nie jest używana podczas aktualizacji.
    >
    > **Obejście:** Uruchom oddzielną operację modyfikowania po uaktualnieniu, aby zainstalować brakujące składniki.

* Na koniec oto jak dodać dodatkowe obciążenie i zlokalizowany język bez aktualizowania wersji. (To polecenie dodaje ASP.NET i obciążenia *tworzenia sieci Web.)*  Teraz w tym układzie uwzględniono zarządzane obciążenia pulpitu, platformy Azure i ASP.NET & web development. Zasoby językowe dla języka angielskiego, niemieckiego i francuskiego są również uwzględniane dla wszystkich tych obciążeń.  Jednak układ nie został zaktualizowany do najnowszej dostępnej wersji po uruchomieniu tego polecenia. Pozostaje w istniejącej wersji.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="deploy-an-update-to-client-machines"></a>Wdrażanie aktualizacji na komputerach klienckich

W zależności od konfiguracji środowiska sieciowego aktualizacja może zostać wdrożona przez administratora przedsiębiorstwa lub zainicjowana z komputera klienckiego.

* Użytkownicy mogą zaktualizować wystąpienie programu Visual Studio zainstalowane z folderu instalacyjnego w trybie offline:
  * Uruchom Instalatora programu Visual Studio.
  * Następnie kliknij przycisk **Aktualizuj**.

::: moniker range="vs-2017"

* Administratorzy mogą aktualizować wdrożenia klienta programu Visual Studio bez żadnej interakcji użytkownika z dwoma oddzielnymi poleceniami:
  * Najpierw zaktualizuj instalator programu Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Następnie zaktualizuj samą aplikację programu Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range="vs-2019"

* Administratorzy mogą aktualizować wdrożenia klienta programu Visual Studio bez żadnej interakcji użytkownika z dwoma oddzielnymi poleceniami:
  * Najpierw zaktualizuj instalator programu Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Następnie zaktualizuj samą aplikację programu Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart```

::: moniker-end

> [!NOTE]
> Polecenie [vswhere.exe służy](tools-for-managing-visual-studio-instances.md) do identyfikowania ścieżki instalacji istniejącego wystąpienia programu Visual Studio na komputerze klienckim.
>
> [!TIP]
> Aby uzyskać szczegółowe informacje na temat kontrolowania, kiedy powiadomienia o aktualizacjach są prezentowane użytkownikom, zobacz [Aktualizacje sterowania wdrożeniami programu Visual Studio opartymi na sieci.](controlling-updates-to-visual-studio-deployments.md)

## <a name="verify-a-layout"></a>Weryfikowanie układu

Służy `--verify` do przeprowadzania weryfikacji w dostarczonej pamięci podręcznej w trybie offline. Sprawdza, czy brakuje plików pakietów lub są nieprawidłowe. Po zakończeniu weryfikacji drukuje listę brakujących plików i nieprawidłowych plików.

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

Vs_enterprise.exe mogą być wywoływane wewnątrz layoutDir.

> [!NOTE]
> Niektóre ważne pliki metadanych, `--verify` które są potrzebne przez tę opcję, muszą znajdować się w pamięci podręcznej trybu offline układu. Jeśli brakuje tych plików metadanych, nie można uruchomić programu "--verify", a Instalator popełni błąd. Jeśli wystąpi ten błąd, ponownie utwórz nowy układ trybu offline do innego folderu (lub do tego samego folderu pamięci podręcznej trybu offline. Aby to zrobić, uruchom to samo polecenie układu, które zostało użyte do utworzenia początkowego układu w trybie offline. Na przykład `vs_enterprise.exe --layout <layoutDir>`.

Firma Microsoft okresowo wysyła aktualizacje do programu Visual Studio, więc nowy układ, który tworzysz, może nie być tą samą wersją co układ początkowy.

> [!NOTE]
> Weryfikacja działa tylko dla najnowszej wersji określonej wersji pomocniczej programu Visual Studio. Jak tylko nowa wersja zostanie wydana, weryfikacja nie będzie działać dla wcześniejszych wersji na poziomie poprawki tej samej wersji pomocniczej.

## <a name="fix-a-layout"></a>Naprawianie układu

Służy `--fix` do wykonywania tej `--verify` samej weryfikacji, a także spróbuj rozwiązać zidentyfikowane problemy. Proces `--fix` wymaga połączenia z Internetem, więc upewnij się, że `--fix`komputer jest podłączony do Internetu przed wywołaniem .

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

Vs_enterprise.exe mogą być wywoływane wewnątrz layoutDir.

## <a name="remove-older-versions-from-a-layout"></a>Usuwanie starszych wersji z układu

Po wykonaniu aktualizacji układu do pamięci podręcznej w trybie offline, folder pamięci podręcznej układu może mieć kilka przestarzałych pakietów, które nie są już potrzebne przez najnowszą instalację programu Visual Studio. Można użyć `--clean` tej opcji, aby usunąć przestarzałe pakiety z folderu pamięci podręcznej trybu offline.

Aby to zrobić, musisz ścieżki plików do katalogu manifestów, które zawierają te przestarzałe pakiety. Manifesty katalogu można znaleźć w folderze "Archiwum" w pamięci podręcznej układu trybu offline. Są one zapisywane tam podczas aktualizacji układu. W folderze "Archiwum" znajduje się jeden lub więcej folderów o nazwie "GUID", z których każdy zawiera przestarzały manifest katalogu. Liczba folderów "GUID" powinna być taka sama jak liczba aktualizacji wprowadzonych do pamięci podręcznej trybu offline.

Kilka plików są zapisywane wewnątrz każdego folderu "GUID". Dwa pliki najbardziej interesujące są "catalog.json" plik i "version.txt" plik. Plik "catalog.json" jest przestarzałym manifestem katalogu, `--clean` który musisz przekazać do opcji. Inny plik version.txt zawiera wersję tego przestarzałego manifestu katalogu. Na podstawie numeru wersji można zdecydować, czy chcesz usunąć przestarzałe pakiety z tego manifestu katalogu. Możesz zrobić to samo, co przejście przez inne foldery "GUID". Po wykonaniu decyzji dotyczącej katalogów, które chcesz wyczyścić, uruchom `--clean` polecenie, podając ścieżki plików do tych katalogów.

Oto kilka przykładów użycia opcji --clean:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Można również wywołać vs_enterprise.exe wewnątrz &lt;layoutDir&gt;. Oto przykład:

```cmd
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Podczas wykonywania tego polecenia Instalator analizuje folder pamięci podręcznej trybu offline, aby znaleźć listę plików, które usunie. Następnie będziesz miał okazję przejrzeć pliki, które zostaną usunięte i potwierdzić usunięcia.

## <a name="get-support-for-your-offline-installer"></a>Uzyskaj pomoc techniczną dla instalatora w trybie offline

Jeśli wystąpi problem z instalacją w trybie offline, chcemy o tym wiedzieć. Najlepszym sposobem, aby nam to powiedzieć, jest użycie narzędzia [Zgłoś problem.](../ide/how-to-report-a-problem-with-visual-studio.md) Korzystając z tego narzędzia, możesz wysłać nam dane telemetryczne i dzienniki, których potrzebujemy, aby pomóc nam zdiagnozować i rozwiązać problem.

Oferujemy również opcję pomocy technicznej [**na czacie na żywo**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim) w przypadku problemów związanych z instalacją.

Mamy również inne opcje wsparcia. Aby uzyskać listę, zobacz naszą stronę [opinie.](../ide/feedback-options.md)

## <a name="see-also"></a>Zobacz też

* [Instalacja programu Visual Studio](install-visual-studio.md)
* [Przewodnik dla administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Instalowanie programu Visual Studio za pomocą parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
* [Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md)
* [Cykl życia produktu i serwis programu Visual Studio](/visualstudio/releases/2019/servicing/)
