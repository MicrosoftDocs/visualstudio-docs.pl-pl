---
title: Aktualizowanie instalacji sieciowej
description: Informacje na temat aktualizowania instalacji programu Visual Studio opartej na sieci za pomocą polecenia--layout
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d5ad0231c2dc21acc4a8d954456921dbe2838e39
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547404"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Aktualizowanie instalacji sieciowej programu Visual Studio

Istnieje możliwość aktualizowania układu instalacji sieciowej programu Visual Studio przy użyciu najnowszych aktualizacji produktu, dzięki czemu można go użyć jako punktu instalacji najnowszej aktualizacji programu Visual Studio, a także w celu utrzymania instalacji, które są już wdrożone na stacjach roboczych klienta.

## <a name="how-to-update-a-network-layout"></a>Jak zaktualizować układ sieci

> [!IMPORTANT]
> W tych instrukcjach przyjęto założenie, że wcześniej utworzono układ instalacji sieciowej. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz stronę [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md) .

Aby odświeżyć udział instalacji sieci, aby zawierał najnowsze aktualizacje, uruchom `--layout` polecenie w celu przyrostowego pobrania zaktualizowanych pakietów.

W przypadku wybrania układu częściowego podczas [pierwszego tworzenia układu sieciowego](create-a-network-installation-of-visual-studio.md)te ustawienia są zapisywane. Wszystkie przyszłe polecenia układu używają poprzednich opcji oraz wszelkich nowych opcji, które określisz.

W przypadku hostowania układu w udziale plików należy zaktualizować prywatną kopię układu (na przykład c:\VSLayout), a następnie po pobraniu całej zaktualizowanej zawartości skopiować ją do udziału plików (na przykład \\ server\products\VS). Jeśli tego nie zrobisz, istnieje większa szansa, że każdy użytkownik, który uruchomił Instalatora, podczas aktualizowania układu może nie być w stanie pobrać całej zawartości z układu, ponieważ nie jest jeszcze w pełni aktualizowany.

Zapoznaj się z kilkoma przykładami tworzenia i aktualizowania układu:

* Najpierw poniżej przedstawiono przykład sposobu tworzenia układu z jednym obciążeniem tylko w języku angielskim:

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Oto jak zaktualizować ten sam układ do nowszej wersji. Nie trzeba określać żadnych dodatkowych parametrów wiersza polecenia. Poprzednie ustawienia zostały zapisane i będą używane przez kolejne polecenia układu w tym folderze układu.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout
  ```

* Poniżej przedstawiono sposób aktualizowania układu do nowszej wersji w sposób nienadzorowany. Operacja układu uruchamia proces instalacji w nowym oknie konsoli. Okno jest pozostawione otwarte, aby użytkownicy mogli zobaczyć końcowy wynik i podsumowanie wszystkich błędów, które mogły wystąpić. Jeśli wykonujesz operację układu w trybie nienadzorowanym (na przykład skrypt, który jest regularnie uruchamiany w celu zaktualizowania układu do najnowszej wersji), użyj `--passive` parametru, a proces spowoduje automatyczne zamknięcie okna.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --passive
  ```

* Poniżej przedstawiono sposób dodawania dodatkowego obciążenia i zlokalizowanego języka.  (To polecenie dodaje obciążenie *Programowanie na platformie Azure* ).  Teraz w tym układzie uwzględniono zarówno pulpit zarządzany, jak i platformę Azure.  Zasoby językowe w języku angielskim i niemieckim są również dołączone do wszystkich tych obciążeń.  Układ zostanie zaktualizowany do najnowszej dostępnej wersji.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Operacja aktualizacji nie instaluje nowo dodanych składników opcjonalnych. Jeśli potrzebujesz nowo dodanych składników opcjonalnych, usuń stare opcjonalne składniki w `Layout.JSON` [pliku odpowiedzi](automated-installation-with-response-file.md) i Uwzględnij składniki potrzebne w sekcji "Add" w temacie `Layout.JSON` . 
    >
    > **Obejście**: Uruchom oddzielną operację modyfikacji po uaktualnieniu, aby zainstalować brakujące składniki.

* Poniżej przedstawiono sposób dodawania dodatkowego obciążenia i zlokalizowanego języka bez aktualizowania wersji. (To polecenie dodaje obciążenie *ASP.NET i programowanie dla sieci Web* ).  Teraz w tym układzie są zawarte następujące obciążenia programu Managed Desktop, Azure i ASP.NET & Web Development. Wszystkie te obciążenia są również dołączone do zasobów języka dla języków angielskim, niemieckim i francuskim.  Jednak układ nie został zaktualizowany do najnowszej dostępnej wersji, gdy to polecenie zostało uruchomione. Pozostaje w istniejącej wersji.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="deploy-an-update-to-client-machines"></a>Wdrażanie aktualizacji na komputerach klienckich

W zależności od konfiguracji środowiska sieciowego aktualizacja może zostać wdrożona przez administratora przedsiębiorstwa lub zainicjowana z komputera klienckiego.

* Użytkownicy mogą aktualizować wystąpienie programu Visual Studio, które zostało zainstalowane z folderu instalacji w trybie offline:
  * Uruchom Instalator programu Visual Studio.
  * Następnie kliknij przycisk **Aktualizuj**.

::: moniker range="vs-2017"

* Administratorzy mogą aktualizować wdrożenia klienta programu Visual Studio bez żadnej interakcji użytkownika z dwoma osobnymi poleceniami:
  * Najpierw należy zaktualizować Instalatora programu Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Następnie zaktualizuj samą aplikację Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range="vs-2019"

* Administratorzy mogą aktualizować wdrożenia klienta programu Visual Studio bez żadnej interakcji użytkownika z dwoma osobnymi poleceniami:
  * Najpierw należy zaktualizować Instalatora programu Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Następnie zaktualizuj samą aplikację Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart```

::: moniker-end

> [!NOTE]
> Użyj [vswhere.exe polecenia](tools-for-managing-visual-studio-instances.md) , aby zidentyfikować ścieżkę instalacji istniejącego wystąpienia programu Visual Studio na komputerze klienckim.
>
> [!TIP]
> Aby uzyskać szczegółowe informacje na temat sposobu kontrolowania, kiedy powiadomienia o aktualizacjach są prezentowane użytkownikom, zobacz [Kontrola aktualizacji w ramach wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md).

## <a name="verify-a-layout"></a>Weryfikowanie układu

Użyj, `--verify` Aby przeprowadzić weryfikację w podanej pamięci podręcznej trybu offline. Sprawdza, czy brakuje plików pakietów lub są one nieprawidłowe. Na końcu weryfikacji drukuje listę brakujących plików i nieprawidłowych plików.

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

vs_enterprise.exe można wywołać wewnątrz layoutDir.

> [!NOTE]
> Niektóre ważne pliki metadanych, które są wymagane przez `--verify` opcję, muszą znajdować się w pamięci podręcznej w trybie offline. Jeśli brakuje tych plików metadanych, polecenie "--verify" nie może zostać uruchomione, a Instalator podaje błąd. W przypadku wystąpienia tego błędu należy ponownie utworzyć nowy układ w trybie offline do innego folderu (lub do tego samego folderu pamięci podręcznej offline. Aby to zrobić, uruchom polecenie układu, które zostało użyte do utworzenia początkowego układu w trybie offline. Na przykład `vs_enterprise.exe --layout <layoutDir>`.

Firma Microsoft dostarcza aktualizacje programu Visual Studio okresowo, więc nowy układ, który tworzysz, może nie być w tej samej wersji co początkowy układ.

> [!NOTE]
> Weryfikacja działa tylko dla najnowszej wersji programu Visual Studio. Gdy tylko zostanie wydana nowa wersja, weryfikacja nie będzie działała w przypadku wcześniejszych wersji na poziomie poprawek tej samej.

## <a name="fix-a-layout"></a>Naprawianie układu

Użyj, `--fix` Aby wykonać tę samą weryfikację co `--verify` i spróbuj naprawić zidentyfikowane problemy. `--fix`Proces wymaga połączenia internetowego, dlatego przed wywołaniem upewnij się, że komputer jest połączony z Internetem `--fix` .

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

vs_enterprise.exe można wywołać wewnątrz layoutDir.

## <a name="remove-older-versions-from-a-layout"></a>Usuń starsze wersje z układu

Po przeprowadzeniu aktualizacji układu do pamięci podręcznej w trybie offline folder pamięci podręcznej układu może mieć przestarzałe pakiety, które nie są już potrzebne w najnowszej instalacji programu Visual Studio. Możesz użyć opcji, `--clean` Aby usunąć Przestarzałe pakiety z folderu pamięci podręcznej offline.

W tym celu potrzebne są ścieżki plików do manifestów wykazu zawierających te przestarzałe pakiety. Manifesty katalogu można znaleźć w folderze "archiwum" w pamięci podręcznej układu offline. Są one zapisywane podczas aktualizowania układu. W folderze "archiwum" istnieje co najmniej jeden "GUID" o nazwie foldery, z których każdy zawiera przestarzały manifest katalogu. Liczba folderów "GUID" powinna być taka sama jak liczba aktualizacji wprowadzonych w pamięci podręcznej offline.

Kilka plików jest zapisywanych w każdym folderze "GUID". Dwa pliki najbardziej interesujące to plik "catalog.json" i plik "version.txt". Plik "catalog.json" jest przestarzałym manifestem katalogu, który należy przekazać do `--clean` opcji. Inny plik version.txt zawiera wersję tego przestarzałego manifestu katalogu. Na podstawie numeru wersji możesz zdecydować, czy chcesz usunąć Przestarzałe pakiety z tego manifestu katalogu. Można to zrobić tak samo jak w przypadku innych folderów "GUID". Po podjęciu decyzji dotyczącej wykazów, które mają być czyste, uruchom polecenie, podając `--clean` ścieżki plików do tych wykazów.

Poniżej przedstawiono kilka przykładów użycia opcji--Clean:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Możesz również wywołać vs_enterprise.exe wewnątrz &lt; layoutDir &gt; . Oto przykład:

```cmd
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Po wykonaniu tego polecenia Instalator analizuje folder pamięci podręcznej w trybie offline, aby znaleźć listę plików, które zostaną usunięte. Następnie będziesz mieć możliwość przejrzenia plików, które zostaną usunięte i potwierdzić usunięcie.

## <a name="get-support-for-your-offline-installer"></a>Uzyskaj pomoc techniczną dla Instalatora w trybie offline

Jeśli wystąpi problem z instalacją w trybie offline, chcemy wiedzieć o tym. Najlepszym sposobem na poinformowanie nas jest użycie narzędzia [Zgłoś problem](../ide/how-to-report-a-problem-with-visual-studio.md) . Korzystając z tego narzędzia, możesz wysłać nam dane telemetryczne i dzienniki, które muszą pomóc nam w zdiagnozowaniu i rozwiązaniu problemu.

Oferujemy również opcję obsługi [**rozmowy na żywo**](https://visualstudio.microsoft.com/vs/support/#talktous) (tylko w języku angielskim) dla problemów związanych z instalacją.

Dostępne są również inne opcje pomocy technicznej. Listę można znaleźć na naszej stronie [opinii](../ide/feedback-options.md) .

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
* [Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md)
* [Cykl życia produktu Visual Studio i obsługa](/visualstudio/releases/2019/servicing/)
