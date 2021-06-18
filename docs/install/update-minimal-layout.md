---
title: Aktualizowanie programu Visual Studio przy użyciu minimalnego układu offline
description: Dowiedz się, jak zaktualizować Visual Studio przy użyciu minimalnego układu offline.
ms.date: 05/18/2021
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 1c3a6254c3205038be3d56c64de091e659d2bbd5
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306738"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>Aktualizowanie programu Visual Studio przy użyciu minimalnego układu offline

W przypadku komputerów, które nie są połączone z Internetem, utworzenie minimalnego układu jest najprostszym i najszybszym sposobem aktualizowania wystąpień Visual Studio offline.

Narzędzie do minimalnego układu generuje układ dostosowany specjalnie do potrzeb Twojego zespołu. Administratorzy przedsiębiorstwa mogą używać tego narzędzia do tworzenia układów aktualizacji dla większości wersji Visual Studio 2017 i 2019. W przeciwieństwie do pełnego Visual Studio układ minimalny układ zawiera tylko zaktualizowane pakiety, więc jego generowanie i wdrażanie jest zawsze mniejsze i szybsze. Możesz dodatkowo zminimalizować rozmiar układu aktualizacji, określając tylko żądane języki, obciążenia i składniki.

## <a name="how-to-generate-a-minimal-layout"></a>Jak wygenerować minimalny układ

> [!IMPORTANT]
> W tych instrukcjach założono, że wcześniej utworzono i użyliśmy układów. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz stronę Aktualizowanie instalacji sieciowej [Visual Studio](update-a-network-installation-of-visual-studio.md) sieciowej.
>
> Aby lepiej zrozumieć cykl życia Visual Studio, zobacz stronę Visual Studio Cykl życia produktu [i obsługa.](/visualstudio/releases/2019/servicing)
>

To narzędzie tworzy układy aktualizacji dla Visual Studio 2017 (15.9) i jego wersji. Układ można wdrożyć na maszynach sieciowych/offline w celu Visual Studio wystąpień. Podczas [normalnego tworzenia układu](update-a-network-installation-of-visual-studio.md)pobierane są wszystkie pakiety dla danego wydania. Normalne tworzenie układu jest wymagane do naprawy, odinstalowywania i innych standardowych operacji na Visual Studio wystąpień. Minimalny układ pobiera tylko zaktualizowane pakiety, dzięki czemu jest mniejszy i łatwiejszy do skopiowania na maszyny w trybie offline.

### <a name="installing-the-minimal-layout-tool"></a>Instalowanie minimalnego narzędzia układu

 1. Najpierw pobierz narzędzie do minimalnego układu znajdujące się [tutaj.](https://aka.ms/vs/installer/minimallayout) Upewnij się, że po **wyświetleniu monitu** wybierz pozycję Zapisz, a następnie wybierz **pozycję Uruchom**.

     ![Narzędzie do zapisywania minimalnej ilości układu](media/save-minimal-layout.png)

 2. Następnie zaakceptuj monit Kontrola konta użytkownika, klikając pozycję **Tak.**

     ![Akceptowanie kontroli konta użytkownika](media/accept-user-account-control.png)

 3. Narzędzie do minimalnego układu zostanie zainstalowane w programie `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout` .

### <a name="how-to-use-the-minimal-layout-tool"></a>Jak używać narzędzia do minimalnego układu

`MinimalLayout.exe` Używa następujących poleceń i opcji do generowania układu. Do uruchomienia narzędzia jest wymagane co najmniej jedno polecenie. Poniżej opisano sposób uruchamiania narzędzia:

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>Polecenia

* **Wersja** zapoznawcza: użyj tego polecenia, aby wyświetlić podgląd liczby pakietów do pobrania oraz całkowitej przestrzeni użytej do utworzenia tego układu.
* Wygeneruj: użyj tego polecenia, aby wygenerować minimalny układ na Visual Studio.
* **Wygeneruj** ponownie: to polecenie pozwala ponownie wygenerować układ przy użyciu istniejącego pliku odpowiedzi z minimalnym układem. Każdy minimalny układ tworzy `MinimalLayout.json` plik odpowiedzi, który zawiera oryginalne minimalne parametry wejściowe układu. Aby ponownie wygenerować minimalny **układ,** można użyć polecenia Wygeneruj ponownie i `MinimalLayout.json` pliku odpowiedzi. Jest to przydatne, jeśli chcesz utworzyć minimalny układ dla nowej Visual Studio aktualizacji na podstawie pliku odpowiedzi poprzedniego minimalnego układu.

   W przypadku tego polecenia wymagana jest ścieżka pliku z już `MinimalLayout.json` wygenerowanego układu.

   ```shell
   MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
   ```

* **Sprawdź:** użyj tego polecenia, aby określić, czy folder układu jest uszkodzony.
* **Poprawka:** użyj tego polecenia, aby naprawić uszkodzony folder układu, w tym zastąpić wszystkie brakujące pakiety z folderu układu.

#### <a name="options"></a>Opcje

::: moniker range=">=vs-2019"

| Opcje                                             | Opis                                                                                                                                                                                                                                                                                                                                                                                                                                 | Wymagane/Opcjonalne               | Przykład                                                                                                                                                          |
|-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --targetLocation &lt; dir&gt;                        | Określa katalog, w którym należy utworzyć minimalny układ offline.                                                                                                                                                                                                                                                                                                                                                                          | Wymagane                        | --targetLocation c:\VSLayout\                                                                                                                                    |
| --baseVersion, &lt; wersja&gt;                       | Od tej wersji zostanie wygenerowany minimalny układ w trybie offline.                                                                                                                                                                                                                                                                                                                                                                    | Wymagane                        | --baseVersion 16.4.0                                                                                                                                             |
| --targetVersion, &lt; wersja&gt;                     | Minimalny układ w trybie offline zostanie wygenerowany do tej wersji włącznie.                                                                                                                                                                                                                                                                                                                                                              | Wymagane                        | --targetVersion 16.4.4                                                                                                                                           |
| --languages                                         | Określa języki, które mają być dołączane w minimalnym układzie offline. Można określić wiele wartości rozdzielonych spacjami.                                                                                                                                                                                                                                                                                                                    | Wymagane                        | --languages en-US fr-FR                                                                                                                                          |
| --productIds &lt; co najmniej jeden identyfikator produktu&gt;        | Identyfikatory produktów, z których zostanie wygenerowany minimalny układ offline, rozdzielone przecinkami. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul> | Wymagane                        | --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional                                                               |
| --filePath                                          | Ścieżka pliku pliku MinimalLayout.jspliku z już utworzonego układu. Ta opcja jest używana tylko z poleceniem Wygeneruj ponownie.                                                                                                                                                                                                                                                                                                          | Wymagane do ponownego wygenerowania polecenia | --filePath C:\VSLayout\minimalLayout.jswł. <br><br> **Pamiętaj, że polecenie Regenerate przyjmuje tylko opcję --filePath.**                                      |
| — dodaj &lt; co najmniej jeden identyfikator obciążenia lub składnika&gt; | Określa co najmniej jeden identyfikator obciążenia lub składnika do dodania. Dodatkowe składniki można dodawać globalnie przy użyciu funkcji --includeRecommended i/lub <br> –-includeOptional. Można określić wiele obciążeń lub identyfikatorów składników, oddzielając je spacją.                                                                                                                                                                                                   | Opcjonalne                        | --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb Component.GitHub.VisualStudio                                        |
| --includeRecommended                                | Zawiera zalecane składniki dla wszystkich zainstalowanych obciążeń, ale nie składników opcjonalnych.                                                                                                                                                                                                                                                                                                                                  | Opcjonalne                        | Dla określonego obciążenia: <br> --add Microsoft.VisualStudio.Workload. ManagedDesktop;includeRecommended <br><br> Aby zastosować do wszystkich obciążeń: --includeRecommended |
| --includeOptional                                   | Zawiera opcjonalne składniki dla wszystkich zainstalowanych obciążeń, w tym zalecane składniki.                                                                                                                                                                                                                                                                                                                                | Opcjonalne                        | Dla określonego obciążenia: <br>--add Microsoft.VisualStudio.Workload. ManagedDesktop;includeOptional <br><br> Aby zastosować do wszystkich obciążeń: --includeOptional         |

::: moniker-end

::: moniker range="vs-2017"

| Opcje                                             | Opis                                                                                                                                                                                                                                                                                                                                                                                                                                 | Wymagane/Opcjonalne               | Przykład                                                                                                                                                          |
|-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --targetLocation &lt; dir&gt;                        | Określa katalog, w którym należy utworzyć minimalny układ offline.                                                                                                                                                                                                                                                                                                                                                                          | Wymagane                        | --targetLocation c:\VSLayout\                                                                                                                                    |
| --baseVersion, &lt; wersja&gt;                       | Minimalny układ w trybie offline zostanie wygenerowany, począwszy od tej wersji.                                                                                                                                                                                                                                                                                                                                                                    | Wymagane                        | --baseVersion 15.0.0                                                                                                                                             |
| --targetVersion, &lt; wersja&gt;                     | Minimalny układ w trybie offline będzie generowany do tej wersji włącznie.                                                                                                                                                                                                                                                                                                                                                              | Wymagane                        | --targetVersion 15.9.31                                                                                                                                          |
| --languages                                         | Określa języki, które mają być dołączane w minimalnym układzie offline. Można określić wiele wartości rozdzielonych spacjami.                                                                                                                                                                                                                                                                                                                    | Wymagane                        | --languages en-US fr-FR                                                                                                                                          |
| --productIds &lt; co najmniej jeden identyfikator produktu&gt;        | Identyfikatory produktów, z których zostanie wygenerowany minimalny układ w trybie offline, rozdzielone przecinkami. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul> | Wymagane                        | --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional                                                               |
| --filePath                                          | Ścieżka pliku pliku MinimalLayout.jspliku z już utworzonego układu. Ta opcja jest używana tylko z ponownie wygenerować polecenia.                                                                                                                                                                                                                                                                                                          | Wymagane do ponownego wygenerowania polecenia | --filePath C:\VSLayout\minimalLayout.jsna <br><br> **Pamiętaj, że polecenie Regenerate (Wygeneruj ponownie) przyjmuje tylko opcję --filePath.**                                      |
| — dodaj &lt; co najmniej jeden identyfikator obciążenia lub składnika&gt; | Określa co najmniej jeden identyfikator obciążenia lub składnika do dodania. Dodatkowe składniki można dodawać globalnie przy użyciu funkcji --includeRecommended i/lub <br> –-includeOptional. Można określić wiele obciążeń lub identyfikatorów składników, oddzielając je spacją.                                                                                                                                                                                                   | Opcjonalne                        | --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb Component.GitHub.VisualStudio                                        |
| --includeRecommended                                | Zawiera zalecane składniki dla wszystkich zainstalowanych obciążeń, ale nie składników opcjonalnych.                                                                                                                                                                                                                                                                                                                                  | Opcjonalne                        | Dla określonego obciążenia: <br> — dodaj pakiet Microsoft.VisualStudio.Workload. ManagedDesktop;includeRecommended <br><br> Aby zastosować do wszystkich obciążeń: --includeRecommended |
| --includeOptional                                   | Zawiera opcjonalne składniki dla wszystkich zainstalowanych obciążeń, w tym zalecane składniki.                                                                                                                                                                                                                                                                                                                                | Opcjonalne                        | Dla określonego obciążenia: <br>— dodaj pakiet Microsoft.VisualStudio.Workload. ManagedDesktop;includeOptional <br><br> Aby zastosować do wszystkich obciążeń: --includeOptional         |

::: moniker-end

### <a name="generating-a-minimal-layout"></a>Generowanie minimalnego układu

> [!IMPORTANT]
> W tych instrukcjach przyjęto założenie, że wcześniej utworzono układ instalacji sieciowej. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz stronę Tworzenie instalacji [sieciowej Visual Studio](create-a-network-installation-of-visual-studio.md) sieciowej.

Utwórz minimalny układ przy użyciu **polecenia generate** dla określonego zakresu wersji. Musisz również znać productId, języki i wszelkie wymagane określone obciążenia. Ten minimalny układ spowoduje zaktualizowanie dowolnego Visual Studio z wersji podstawowej do wersji docelowej włącznie.

Przed utworzeniem układu możesz sprawdzić całkowity rozmiar pobierania i liczbę pakietów dołączonych za pomocą **polecenia w wersji zapoznawczej.** To polecenie przyjmuje te same opcje co **polecenie generate,** a szczegóły są zapisywane w konsoli.

Przyjrzyjmy się kilku przykładom sposobu wyświetlania podglądu, generowania i ponownego generowania minimalnego układu:

::: moniker range=">=vs-2019"

* Najpierw przedstawiamy przykład wyświetlania podglądu układu dla wersji Visual Studio Enterprise od 16.4.0 do 16.4.4 tylko dla języka angielskiego.

  ```shell
  MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
  ```

* Poniżej opisano sposób generowania tego samego układu z jednym obciążeniem.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
  ```

* Poniżej opisano sposób ponownego generowania minimalnego układu offline przy użyciu istniejącego pliku odpowiedzi.

  ```shell
  MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
  ```

Kilka innych przykładów przy użyciu **polecenia generate:**

* Poniżej opisano sposób dodawania dodatkowego obciążenia i dołączania tylko zalecanych pakietów.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
  ```

* Można również wygenerować minimalny układ w trybie offline, który obsługuje wiele produktów.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
  ```

* Na koniec poniżej opisano sposób dołączania wielu języków w minimalnym układzie.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
  ```

::: moniker-end

::: moniker range="vs-2017"

* Najpierw przedstawiamy przykład wyświetlania podglądu układu dla wersji od Visual Studio Enterprise od 15.0.0 do 15.9.31 tylko dla języka angielskiego.

  ```shell
  MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
  ```

* Poniżej opisano sposób generowania tego samego układu z jednym obciążeniem.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
  ```

* Poniżej opisano sposób ponownego generowania minimalnego układu offline przy użyciu istniejącego pliku odpowiedzi.

  ```shell
  MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
  ```

Kilka innych przykładów przy użyciu **polecenia generate:**

* Poniżej opisano sposób dodawania dodatkowego obciążenia i dołączania tylko zalecanych pakietów.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
  ```

* Można również wygenerować minimalny układ w trybie offline, który obsługuje wiele produktów.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise,Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
  ```

* Na koniec poniżej opisano sposób dołączania wielu języków w minimalnym układzie.

  ```shell
  MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
  ```

::: moniker-end

### <a name="how-to-maintain-a-minimal-layout"></a>Jak zachować minimalny układ

Użyj poleceń **verify** i **fix,** aby zachować minimalny układ po jego utworzeniu. Polecenie **verify** określa, czy istnieją jakieś uszkodzone lub brakujące pakiety w minimalnym układzie. Jeśli po uruchomieniu polecenia **verify** wystąpią problemy, użyj polecenia **fix,** aby naprawić brakujące lub uszkodzone pakiety.

* Poniżej opisano sposób sprawdzania, czy układ ma uszkodzony lub nie ma brakujących pakietów:

  ```shell
  MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
  ```

* A oto jak naprawić ten układ:

  ```shell
  MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productIds Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
  ```

>[!NOTE]
> Tego układu nie można użyć do naprawy Visual Studio instalacji. Aby naprawić istniejące wystąpienie usługi Visual Studio, zobacz [Repair Visual Studio (Naprawianie Visual Studio](repair-visual-studio.md)).
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Jak używać minimalnego układu offline do aktualizowania istniejącej instalacji Visual Studio

Po wygenerowaniu minimalnego układu można skopiować cały minimalny folder układu na maszynę kliencową. Jest to wymagane, jeśli komputer nie ma dostępu do folderu minimalnego układu w swojej oryginalnej lokalizacji.

Przejdź do folderu i zidentyfikuj nazwę aplikacji programu inicjjącego. Nazwa aplikacji inicjujące zależy od wartości ProductId określonej podczas generowania minimalnego układu. Typowe przykłady można znaleźć w poniższej tabeli.

| Wartość ProductId                             | Nazwa aplikacji    |
|---------------------------------------------|---------------------|
| Microsoft.VisualStudio.Product.Enterprise   | vs_enterprise.exe   |
| Microsoft.VisualStudio.Product.Professional | vs_professional.exe |
| Microsoft.VisualStudio.Product.BuildTools   | vs_buildtools.exe   |

Aktualizacja jest stosowana do Visual Studio w dwóch krokach. Rozpocznij od zaktualizowania Instalator programu Visual Studio, a następnie zaktualizuj Visual Studio.

::: moniker range="vs-2017"

1. **Aktualizowanie Instalator programu Visual Studio**

    Uruchom następujące polecenie, zastępując w razie potrzeby poprawną nazwę aplikacji programu `vs_enterprise.exe`  inicjjącego.

    ```shell
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Aktualizowanie Visual Studio aplikacji**

    Aby zaktualizować Visual Studio, należy określić wartość installPath Visual Studio wystąpienia, które chcesz zaktualizować. Jeśli zainstalowano wiele wystąpień Visual Studio, każde z nich należy zaktualizować oddzielnie. Zdecydowanie zalecamy określenie opcji za pomocą polecenia update, aby zapobiec instalacji składników, które nie mają `–noWeb` minimalnego układu. Uniemożliwia to pozostawienie Visual Studio w stanie bezużytecznym.

    Uruchom następujące polecenie, odpowiednio zastępując parametr wiersza polecenia installPath. Upewnij się, że używasz również poprawnej nazwy aplikacji programu inicjującego.

    ```shell
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

::: moniker-end

::: moniker range="vs-2019"

1. **Aktualizowanie Instalator programu Visual Studio**

    Uruchom następujące polecenie, zastępując w razie potrzeby poprawną nazwę aplikacji programu `vs_enterprise.exe`  inicjjącego.

    ```shell
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Aktualizowanie Visual Studio aplikacji**

    Aby zaktualizować Visual Studio, należy określić wartość installPath Visual Studio wystąpienia, które chcesz zaktualizować. Jeśli zainstalowano wiele wystąpień Visual Studio, każde z nich należy zaktualizować oddzielnie. Zdecydowanie zalecamy określenie opcji za pomocą polecenia update, aby zapobiec instalacji składników, które nie mają `–noWeb` minimalnego układu. Uniemożliwia to pozostawienie Visual Studio w stanie bezużytecznym.

    Uruchom następujące polecenie, odpowiednio zastępując parametr wiersza polecenia installPath. Upewnij się, że używasz również poprawnej nazwy aplikacji programu inicjującego.

    ```shell
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise"
    ```

::: moniker-end

::: moniker range=">=vs-2022"

1. **Aktualizowanie Instalator programu Visual Studio**

    Uruchom następujące polecenie, zastępując w razie potrzeby poprawną nazwę aplikacji programu `vs_enterprise.exe`  inicjjącego.

    ```shell
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Aktualizowanie Visual Studio aplikacji**

    Aby zaktualizować Visual Studio, należy określić wartość installPath Visual Studio wystąpienia, które chcesz zaktualizować. Jeśli zainstalowano wiele wystąpień Visual Studio, każde z nich należy zaktualizować oddzielnie. Zdecydowanie zalecamy określenie opcji za pomocą polecenia update, aby zapobiec instalacji składników, które nie mają `–noWeb` minimalnego układu. Uniemożliwia to pozostawienie Visual Studio w stanie bezużytecznym.

    Uruchom następujące polecenie, odpowiednio zastępując parametr wiersza polecenia installPath. Upewnij się, że używasz również poprawnej nazwy aplikacji programu inicjującego.

    ```shell
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise"
    ```

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
* [Jak zdefiniować ustawienia w pliku odpowiedzi](automated-installation-with-response-file.md)
* [Kontrolowanie aktualizacji wdrożeń Visual Studio sieciowych](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio produktu i jego obsługa](/visualstudio/releases/2019/servicing/)
