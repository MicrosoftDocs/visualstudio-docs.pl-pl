---
title: Aktualizowanie instalacji sieciowej
description: Dowiedz się, jak zaktualizować instalację sieciową Visual Studio za pomocą polecenia --layout
ms.date: 04/16/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0400f4be06afab2326ac738e1ac15f9d93a6ecee
ms.sourcegitcommit: 367a2d9df789aa617abaa09b0cd0a18db7357d0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107800775"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Aktualizowanie instalacji sieciowej programu Visual Studio

Istnieje możliwość zaktualizowania układu instalacji sieciowej programu Visual Studio przy użyciu najnowszych aktualizacji produktu, aby można było go używać zarówno jako punktu instalacji najnowszej aktualizacji programu Visual Studio, jak i do obsługi instalacji, które zostały już wdrożone na klienckich stacjach roboczych.

## <a name="how-to-update-a-network-layout"></a>Jak zaktualizować układ sieci

> [!IMPORTANT]
> W tych instrukcjach przyjęto założenie, że wcześniej utworzono układ instalacji sieci i decyzje dotyczące sposobu, w jaki klient ma pobrać aktualizacje. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz stronę Create [a network installation of Visual Studio](create-a-network-installation-of-visual-studio.md) and Control updates to Visual Studio deployments (Tworzenie instalacji sieciowej usługi Visual Studio i Kontrolowanie aktualizacji Visual Studio [wdrożeniach).](../install/controlling-updates-to-visual-studio-deployments.md)

Aby odświeżyć udział instalacji sieci w taki sposób, aby zawierał najnowsze aktualizacje, uruchom program inicjujący przy użyciu parametru `--layout` , aby pobrać zaktualizowane pakiety.

Jeśli podczas tworzenia układu [](create-a-network-installation-of-visual-studio.md)sieciowego wybrano układ częściowy, te ustawienia zostaną zapisane. Wszystkie przyszłe polecenia układu używają poprzednich opcji oraz wszystkich nowych opcji, które określisz.

Jeśli hostujesz układ w udziałach plików, zaktualizuj prywatną kopię układu (na przykład c:\VSLayout), a następnie po pobraniu całej zaktualizowanej zawartości skopiuj ją do udziału plików (na przykład \\ server\products\VS). Jeśli tego nie zrobisz, istnieje większe prawdopodobieństwo, że wszyscy użytkownicy, którzy uruchamiają Instalatora podczas aktualizowania układu, mogą nie być w stanie pobrać całej zawartości z układu, ponieważ nie została jeszcze całkowicie zaktualizowana.

Przyjrzyjmy się kilku przykładom tworzenia, a następnie aktualizowania układu:

* Najpierw oto przykład sposobu tworzenia układu z jednym obciążeniem tylko dla języka angielskiego:

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Poniżej opisano sposób aktualizowania tego samego układu do nowszej wersji. Nie trzeba określać żadnych dodatkowych parametrów wiersza polecenia. Poprzednie ustawienia zostały zapisane i będą używane przez wszystkie kolejne polecenia układu w tym folderze układu.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout
  ```

* Poniżej opisano sposób aktualizowania układu do nowszej wersji w sposób nienadzorowany. Operacja układu uruchamia proces instalacji w nowym oknie konsoli. Okno pozostaje otwarte, aby użytkownicy mogli zobaczyć wynik końcowy i podsumowanie wszelkich błędów, które mogły wystąpić. Jeśli wykonujesz operację układu w sposób nienadzorowany (na przykład masz skrypt, który jest regularnie uruchamiany w celu zaktualizowania układu do najnowszej wersji), użyj parametru , a proces automatycznie zamknie `--passive` okno.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --passive
  ```

* Poniżej opisano sposób dodawania dodatkowego obciążenia i zlokalizowanego języka.  (To polecenie dodaje obciążenie *Tworzenie aplikacji na platformie Azure).*  Teraz w tym układzie uwzględniono zarówno program Managed Desktop, jak i platformę Azure.  Zasoby językowe dla języka angielskiego i niemieckiego są również uwzględniane dla wszystkich tych obciążeń.  Układ został zaktualizowany do najnowszej dostępnej wersji.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Operacja aktualizacji nie instaluje nowo dodanych składników opcjonalnych. Jeśli potrzebujesz nowo dodanych składników opcjonalnych, usuń stare składniki opcjonalne z pliku odpowiedzi i uwzględnij potrzebne składniki w sekcji `Layout.JSON` [](automated-installation-with-response-file.md) "Dodaj" w pliku `Layout.JSON` . 
    >
    > **Obejście:** Uruchom oddzielną operację modyfikowania po uaktualnieniu, aby zainstalować brakujące składniki.

* Wreszcie poniżej opisano sposób dodawania dodatkowego obciążenia i zlokalizowanego języka bez aktualizowania wersji. (To polecenie dodaje obciążenie *tworzenie aplikacji ASP.NET sieci Web).*  Teraz w tym układzie znajdują się obciążenia Managed Desktop, Azure ASP.NET & Web Development. Zasoby językowe dla języka angielskiego, niemieckiego i francuskiego są również uwzględniane dla wszystkich tych obciążeń.  Jednak podczas uruchamiania tego polecenia układ nie został zaktualizowany do najnowszej dostępnej wersji. Pozostaje on w istniejącej wersji.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="deploy-an-update-to-client-machines"></a>Wdrażanie aktualizacji na maszynach klienckich

W zależności od konfiguracji środowiska sieciowego aktualizacja może zostać wdrożona przez administratora przedsiębiorstwa lub zainicjowana z komputera klienckiego.

* Użytkownicy mogą zaktualizować Visual Studio zainstalowane z folderu instalacji w trybie offline:
  * Uruchom Instalator programu Visual Studio.
  * Następnie kliknij pozycję **Aktualizuj**.

::: moniker range="vs-2017"

* Administratorzy mogą aktualizować wdrożenia klientów Visual Studio bez interakcji z użytkownikiem za pomocą dwóch oddzielnych poleceń:
  * Najpierw zaktualizuj instalatora Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Następnie zaktualizuj samą Visual Studio aplikację: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range="vs-2019"

* Administratorzy mogą aktualizować wdrożenia klientów Visual Studio bez interakcji z użytkownikiem za pomocą dwóch oddzielnych poleceń:
  * Najpierw zaktualizuj instalatora Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Następnie zaktualizuj samą Visual Studio aplikację: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart```

::: moniker-end

> [!NOTE]
> Użyjvswhere.exe [ polecenia ,](tools-for-managing-visual-studio-instances.md) aby zidentyfikować ścieżkę instalacji istniejącego wystąpienia Visual Studio na komputerze klienckim.
>
> [!TIP]
> Aby uzyskać szczegółowe informacje na temat kontrolowania, kiedy powiadomienia o aktualizacji są prezentowane użytkownikom, zobacz Kontrolowanie aktualizacji sieciowych [wdrożeń Visual Studio aktualizacji.](controlling-updates-to-visual-studio-deployments.md)

## <a name="verify-a-layout"></a>Weryfikowanie układu

Użyj `--verify` funkcji , aby przeprowadzić weryfikację dostarczonej pamięci podręcznej trybu offline. Sprawdza, czy brakuje plików pakietów lub czy są one nieprawidłowe. Po zakończeniu weryfikacji zostanie wyświetlona lista brakujących plików i nieprawidłowych plików.

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

vs_enterprise.exe wywoływane wewnątrz layoutDir.

> [!NOTE]
> Niektóre ważne pliki metadanych, które są wymagane przez tę opcję, muszą znajdować `--verify` się w pamięci podręcznej układu w trybie offline. Jeśli brakuje tych plików metadanych, nie można uruchomić elementu "--verify", a Instalator zwraca błąd. Jeśli wystąpi ten błąd, utwórz ponownie nowy układ trybu offline w innym folderze (lub w tym samym folderze pamięci podręcznej trybu offline). W tym celu uruchom to samo polecenie układu, które było używane do utworzenia początkowego układu w trybie offline. Na przykład `vs_enterprise.exe --layout <layoutDir>`.

Firma Microsoft okresowo Visual Studio aktualizacje, więc nowy układ, który utworzysz, może nie być w tej samej wersji co układ początkowy.

> [!NOTE]
> Weryfikacja działa tylko w przypadku najnowszej wersji określonej wersji pomocniczej Visual Studio. Po wydaniu nowej wersji weryfikacja nie będzie działać w przypadku wcześniejszych wersji poprawek na poziomie tej samej wersji pomocniczej.

## <a name="fix-a-layout"></a>Naprawianie układu

Użyj funkcji , aby przeprowadzić tę samą weryfikację co program , a także `--fix` `--verify` spróbuj rozwiązać zidentyfikowane problemy. Proces wymaga połączenia internetowego, dlatego przed wywołaniem metody upewnij się, że maszyna jest połączona `--fix` z `--fix` Internetem.

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

Ten vs_enterprise.exe można wywołać wewnątrz layoutDir.

## <a name="remove-older-versions-from-a-layout"></a>Usuwanie starszych wersji z układu

Po zakończeniu aktualizacji układu pamięci podręcznej w trybie offline folder pamięci podręcznej układu może zawierać przestarzałe pakiety, które nie są już potrzebne przez najnowszą Visual Studio pamięci podręcznej. Możesz użyć opcji , `--clean` aby usunąć przestarzałe pakiety z folderu pamięci podręcznej w trybie offline.

Aby to zrobić, musisz mieć ścieżki plików do wykazu manifestów, które zawierają przestarzałe pakiety. Manifesty wykazu można znaleźć w folderze "Archiwum" w pamięci podręcznej układu offline. Są one zapisywane w tym miejscu podczas aktualizowania układu. W folderze "Archive" znajduje się co najmniej jeden "identyfikator GUID" o nazwie foldery, z których każdy zawiera przestarzały manifest katalogu. Liczba folderów "GUID" powinna być taka sama jak liczba aktualizacji pamięci podręcznej trybu offline.

W każdym folderze "GUID" jest zapisywanych kilka plików. Dwa najbardziej interesujące pliki to plik "catalog.js" i plik "version.txt". Plik "catalog.jssię" to przestarzały manifest wykazu, który należy przekazać do `--clean` opcji . Drugi plik version.txt zawiera wersję tego przestarzałego manifestu wykazu. Na podstawie numeru wersji możesz zdecydować, czy chcesz usunąć przestarzałe pakiety z tego manifestu wykazu. Możesz to zrobić tak samo, jak w przypadku innych folderów "GUID". Po podjęciu decyzji dotyczącej katalogów, które chcesz oczyścić, uruchom polecenie, po podaniem ścieżek `--clean` plików do tych katalogów.

Oto kilka przykładów użycia opcji --clean:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Można również wywołać vs_enterprise.exe wewnątrz &lt; layoutDir &gt; . Oto przykład:

```cmd
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Po wykonaniu tego polecenia Instalator analizuje folder pamięci podręcznej w trybie offline, aby znaleźć listę plików, które zostaną usunięte. Następnie będzie można przejrzeć pliki, które mają zostać usunięte, i potwierdzić usunięcia.

## <a name="get-support-for-your-offline-installer"></a>Uzyskiwanie pomocy technicznej dla instalatora w trybie offline

Jeśli wystąpi problem z instalacją w trybie offline, chcemy się o tym dowiedzieć. Najlepszym sposobem, aby nam powiedzieć, jest użycie narzędzia Zgłoś [problem.](../ide/how-to-report-a-problem-with-visual-studio.md) Korzystając z tego narzędzia, możesz wysłać nam dane telemetryczne i dzienniki, których potrzebujemy, aby pomóc nam zdiagnozować i rozwiązać problem.

Oferujemy również opcję obsługi czatu [**na żywo**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim) w przypadku problemów związanych z instalacją.

Dostępne są również inne opcje pomocy technicznej. Aby uzyskać listę, zobacz naszą [stronę Opinii.](../ide/feedback-options.md)

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
* [Kontrolowanie aktualizacji wdrożeń Visual Studio sieciowych](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio produktu i jego obsługa](/visualstudio/releases/2019/servicing/)
