---
title: Aktualizowanie programu Visual Studio przy użyciu minimalnego układu offline
description: Dowiedz się, jak zaktualizować program Visual Studio przy użyciu minimalnego układu offline.
ms.date: 07/21/2020
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: bd2e8c94bbfc24b731a40b2d4d4c298a528c622d
ms.sourcegitcommit: 55bc9df751a21656de8cc5b6dbd8a2a1915ec690
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2021
ms.locfileid: "99572957"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>Aktualizowanie programu Visual Studio przy użyciu minimalnego układu offline

W przypadku komputerów, które nie są połączone z Internetem, tworzenie minimalnego układu jest najłatwiejszym i najszybszym sposobem na aktualizację wystąpień programu Visual Studio w trybie offline.

Narzędzie minimalnej układu generuje układ dostosowany specjalnie do potrzeb zespołu. Administratorzy przedsiębiorstwa mogą używać tego narzędzia do tworzenia układów aktualizacji dla większości wersji dla programu Visual Studio 2017 i 2019. W przeciwieństwie do pełnego układu programu Visual Studio, minimalny układ zawiera tylko zaktualizowane pakiety, więc jest on zawsze krótszy i szybszy do generowania i wdrażania. Można bardziej zminimalizować rozmiar układu aktualizacji, określając tylko odpowiednie Języki, obciążenia i składniki.

## <a name="how-to-generate-a-minimal-layout"></a>Jak wygenerować minimalny układ

> [!IMPORTANT]
> W tych instrukcjach przyjęto założenie, że wcześniej zostały utworzone i używane układy. Więcej informacji o tym, jak to zrobić, można znaleźć na stronie [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md) .
>
> Aby lepiej zrozumieć cykl życia programu Visual Studio, zapoznaj się z informacjami na stronie [cykl życia i obsługa produktu Visual Studio](/visualstudio/releases/2019/servicing) .
>

To narzędzie tworzy układy aktualizacji dla programu Visual Studio 2017 (15,9) i do wewnątrz. Układ można wdrożyć na maszynach sieciowych/w trybie offline, aby zaktualizować wystąpienia programu Visual Studio. Podczas [normalnego tworzenia układu](update-a-network-installation-of-visual-studio.md)pobierane są wszystkie pakiety dla tej konkretnej wersji. Normalne tworzenie układu jest wymagane do naprawy, odinstalowania i innych operacji standardowych w wystąpieniach programu Visual Studio. Minimalny układ pobiera tylko zaktualizowane pakiety, więc jest mniejszy i łatwiejszy do kopiowania do maszyn w trybie offline.

### <a name="installing-the-minimal-layout-tool"></a>Instalowanie minimalnego narzędzia układu
 
 1. Najpierw pobierz narzędzie do układu minimalnego znajdujące się w [tym miejscu](https://aka.ms/vs/installer/minimallayout). Upewnij się, że po wyświetleniu monitu wybierz pozycję **Zapisz** , a następnie wybierz pozycję **Uruchom**.

     ![Zaoszczędź minimalne narzędzie układu](media/save-minimal-layout.png)

 2. Następnie zaakceptuj monit kontroli konta użytkownika, klikając **przycisk tak**.

     ![Zaakceptuj kontrolę konta użytkownika](media/accept-user-account-control.png)

 3. Zostanie zainstalowane narzędzie minimalnego układu `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout` .

### <a name="how-to-use-the-minimal-layout-tool"></a>Jak używać narzędzia do układu minimalnej

`MinimalLayout.exe` program używa następujących poleceń i opcji do wygenerowania układu. Do uruchomienia narzędzia wymagane jest co najmniej jedno polecenie. Poniżej przedstawiono sposób uruchamiania narzędzia:

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>Polecenia
* **Wersja zapoznawcza**: Użyj tego polecenia, aby wyświetlić informacje o liczbie pobieranych pakietów oraz o łącznym miejscu użytym do utworzenia tego układu. 
* **Generuj**: to polecenie służy do generowania minimalnego układu aktualizacji programu Visual Studio.
* **Wygeneruj ponownie**: to polecenie służy do ponownego generowania układu przy użyciu istniejącego pliku odpowiedzi o minimalnym układzie. Każdy minimalny układ tworzy `MinimalLayout.json` plik odpowiedzi, który zawiera oryginalne parametry wejściowe układu minimalnego. Możesz użyć polecenia **Regenerate** i `MinimalLayout.json` pliku odpowiedzi, aby ponownie wygenerować minimalny układ. Jest to przydatne, jeśli chcesz utworzyć minimalny układ nowej aktualizacji programu Visual Studio na podstawie pliku odpowiedzi poprzedniego układu minimalnego.

   Dla tego polecenia `MinimalLayout.json` wymagana jest ścieżka pliku z już wygenerowanego układu. 

    ```cmd
    MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
    ```

* **Weryfikuj**: Użyj tego polecenia, aby określić, czy folder układu jest uszkodzony.
* **Poprawka**: Użyj tego polecenia, aby naprawić uszkodzony folder układu, w tym zastępując wszystkie brakujące pakiety z folderu układu.

::: moniker range="vs-2019"

#### <a name="options"></a>Opcje 

|Opcje    |Opis    |Wymagane/Opcjonalne |Przykład |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt; dir&gt; |Określa katalog, w którym ma zostać utworzony minimalny układ w trybie offline.       |Wymagane        |--targetLocation c:\VSLayout\ |
|--baseVersion &lt; wersja&gt;|Minimalny układ offline zostanie wygenerowany, rozpoczynając od tej wersji.   |Wymagane|--baseVersion 16.4.0 |
|--targetVersion &lt; wersja&gt;|Minimalny układ w trybie offline zostanie wygenerowany do tej wersji i obejmuje tę wersję.|Wymagane|--targetVersion 16.4.4|
|--Języki    |Określa Języki, które mają zostać uwzględnione w układzie minimalnym w trybie offline. Można określić wiele wartości, rozdzielone spacjami.    |Wymagane    |— Języki en-US fr — FR |
|-- &lt; Identyfikator ProductID&gt;    |Identyfikator produktu, z którego zostanie wygenerowany minimalny układ trybu offline. <br> <ul><li>Microsoft. VisualStudio. Product. Enterprise</li><li>Microsoft. VisualStudio. Product. Professional</li><li>Microsoft. VisualStudio. Product. BuildTools</li><li>Microsoft. VisualStudio. Product. agenta testowego</li><li>Microsoft. VisualStudio. Product. TestController</li><li>Microsoft. VisualStudio. Product. TeamExplorer</li></ul>|Wymagane|--productId Microsoft. VisualStudio. Product. Enterprise |
|--filePath    |Ścieżka pliku MinimalLayout.jsna pliku z już utworzonego układu. Ta opcja jest używana tylko z poleceniem Regenerate.     |Wymagane do ponownego wygenerowania polecenia    |--filePath C:\VSLayout\minimalLayout.jswłączone <br><br> **Należy zauważyć, że polecenie Regenerate przyjmuje tylko--filePath jako opcję.** |
|--Dodaj &lt; co najmniej jeden identyfikator obciążenia lub składnika&gt;    |Określa co najmniej jeden identyfikator obciążenia lub składnika do dodania. Dodatkowe składniki można dodać globalnie za pomocą--includeRecommended i/lub <br> –-includeOptional. Można określić wiele obciążeń lub identyfikatorów składników, rozdzielonych spacją.    |Opcjonalne    |--Add Microsoft. VisualStudio. obciążeni. ManagedDesktop Microsoft. VisualStudio. obciążeni. NetWeb Component. GitHub. VisualStudio |
|--includeRecommended    |Zawiera zalecane składniki dla wszystkich obciążeń, które są zainstalowane, ale nie opcjonalne składniki.    |Opcjonalne    |Dla określonego obciążenia: <br> --Dodaj Microsoft. VisualStudio. obciążenia. ManagedDesktop;includeRecommended <br><br> Aby zastosować do wszystkich obciążeń:--includeRecommended |
|--includeOptional |Obejmuje opcjonalne składniki dla wszelkich zainstalowanych obciążeń, w tym zalecane składniki.    |Opcjonalne    |Dla określonego obciążenia: <br>--Dodaj Microsoft. VisualStudio. obciążenia. ManagedDesktop;includeOptional <br><br> Aby zastosować do wszystkich obciążeń:--includeOptional |

::: moniker-end

::: moniker range="vs-2017"

#### <a name="options"></a>Opcje 

|Opcje    |Opis    |Wymagane/Opcjonalne |Przykład |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt; dir&gt; |Określa katalog, w którym ma zostać utworzony minimalny układ w trybie offline.       |Wymagane        |--targetLocation c:\VSLayout\ |
|--baseVersion &lt; wersja&gt;|Minimalny układ offline zostanie wygenerowany, rozpoczynając od tej wersji.   |Wymagane|--baseVersion 15.0.0 |
|--targetVersion &lt; wersja&gt;|Minimalny układ w trybie offline zostanie wygenerowany do tej wersji i obejmuje tę wersję.|Wymagane|--targetVersion 15.9.31|
|--Języki    |Określa Języki, które mają zostać uwzględnione w układzie minimalnym w trybie offline. Można określić wiele wartości, rozdzielone spacjami.    |Wymagane    |— Języki en-US fr — FR |
|-- &lt; Identyfikator ProductID&gt;    |Identyfikator produktu, z którego zostanie wygenerowany minimalny układ trybu offline. <br> <ul><li>Microsoft. VisualStudio. Product. Enterprise</li><li>Microsoft. VisualStudio. Product. Professional</li><li>Microsoft. VisualStudio. Product. BuildTools</li><li>Microsoft. VisualStudio. Product. agenta testowego</li><li>Microsoft. VisualStudio. Product. TestController</li><li>Microsoft. VisualStudio. Product. TeamExplorer</li></ul>|Wymagane|--productId Microsoft. VisualStudio. Product. Enterprise |
|--filePath    |Ścieżka pliku MinimalLayout.jsna pliku z już utworzonego układu. Ta opcja jest używana tylko z poleceniem Regenerate.     |Wymagane do ponownego wygenerowania polecenia    |--filePath C:\VSLayout\minimalLayout.jswłączone <br><br> **Należy zauważyć, że polecenie Regenerate przyjmuje tylko--filePath jako opcję.** |
|--Dodaj &lt; co najmniej jeden identyfikator obciążenia lub składnika&gt;    |Określa co najmniej jeden identyfikator obciążenia lub składnika do dodania. Dodatkowe składniki można dodać globalnie za pomocą--includeRecommended i/lub <br> –-includeOptional. Można określić wiele obciążeń lub identyfikatorów składników, rozdzielonych spacją.    |Opcjonalne    |--Add Microsoft. VisualStudio. obciążeni. ManagedDesktop Microsoft. VisualStudio. obciążeni. NetWeb Component. GitHub. VisualStudio |
|--includeRecommended    |Zawiera zalecane składniki dla wszystkich obciążeń, które są zainstalowane, ale nie opcjonalne składniki.    |Opcjonalne    |Dla określonego obciążenia: <br> --Dodaj Microsoft. VisualStudio. obciążenia. ManagedDesktop;includeRecommended <br><br> Aby zastosować do wszystkich obciążeń:--includeRecommended |
|--includeOptional |Obejmuje opcjonalne składniki dla wszelkich zainstalowanych obciążeń, w tym zalecane składniki.    |Opcjonalne    |Dla określonego obciążenia: <br>--Dodaj Microsoft. VisualStudio. obciążenia. ManagedDesktop;includeOptional <br><br> Aby zastosować do wszystkich obciążeń:--includeOptional |

::: moniker-end

### <a name="generating-a-minimal-layout"></a>Generowanie minimalnego układu

> [!IMPORTANT]
>  W tych instrukcjach przyjęto założenie, że wcześniej utworzono układ instalacji sieciowej. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz stronę [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md) .

Utwórz minimalny układ za pomocą polecenia **Generuj** dla określonego zakresu wersji. Należy również znać wymagania dotyczące identyfikatorów productId, języków i określonych obciążeń. Ten minimalny układ spowoduje zaktualizowanie dowolnego wystąpienia programu Visual Studio z wersji podstawowej do i dołączenie wersji docelowej.

Przed utworzeniem układu można sprawdzić łączny rozmiar pobieranych plików i liczbę pakietów uwzględnionych za pomocą polecenia **Podgląd** . To polecenie pobiera te same opcje co polecenie **Generuj** , a szczegóły są zapisywane w konsoli programu.

Zapoznaj się z kilkoma przykładami podglądu, generowania i ponownego generowania minimalnego układu:

::: moniker range="vs-2019"

- Poniżej przedstawiono przykład sposobu wyświetlania podglądu układu dla Visual Studio Enterprise wersji 16.4.0 do 16.4.4 tylko w języku angielskim.

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
    ```

- Poniżej przedstawiono sposób generowania tego samego układu przy użyciu jednego obciążenia.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- A oto jak ponownie wygenerować minimalny układ offline przy użyciu istniejącego pliku odpowiedzi. 

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

Kilka innych przykładów przy użyciu polecenia **Generuj** :

- Poniżej przedstawiono sposób dodawania dodatkowego obciążenia i uwzględniania tylko zalecanych pakietów. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- Na koniec dowiesz się, jak uwzględnić wiele języków w minimalnym układzie. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

::: moniker range="vs-2017"

- Poniżej przedstawiono przykład sposobu wyświetlania podglądu układu dla Visual Studio Enterprise wersji 15.0.0 do 15.9.31 tylko w języku angielskim.

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
    ```

- Poniżej przedstawiono sposób generowania tego samego układu przy użyciu jednego obciążenia.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- A oto jak ponownie wygenerować minimalny układ offline przy użyciu istniejącego pliku odpowiedzi. 

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

Kilka innych przykładów przy użyciu polecenia **Generuj** :

- Poniżej przedstawiono sposób dodawania dodatkowego obciążenia i uwzględniania tylko zalecanych pakietów. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- Na koniec dowiesz się, jak uwzględnić wiele języków w minimalnym układzie. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

### <a name="how-to-maintain-a-minimal-layout"></a>Jak zachować minimalny układ

Użyj poleceń **Weryfikuj** i **napraw** , aby zachować minimalny układ po jego utworzeniu. Polecenie **verify** określa, czy w minimalnym układzie są uszkodzone lub brakujące pakiety. Jeśli napotkasz jakiekolwiek problemy po uruchomieniu polecenia **verify** , użyj polecenia **napraw** , aby skorygować te brakujące lub uszkodzone pakiety.

- Poniżej przedstawiono sposób sprawdzania, czy w układzie znajdują się uszkodzone lub brakujące pakiety: 

    ```cmd
    MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
    ```

- A oto jak naprawić ten układ:

    ```cmd
    MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
    ```

>[!NOTE] 
> Tego układu nie można użyć do naprawienia instalacji programu Visual Studio. Aby naprawić istniejące wystąpienie programu Visual Studio, zobacz temat [Naprawa programu Visual Studio](repair-visual-studio.md).
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Jak zaktualizować istniejącą instalację programu Visual Studio przy użyciu minimalnego układu offline

Po wygenerowaniu minimalnego układu można skopiować cały minimalny folder układu do komputera klienckiego. Jest to wymagane, jeśli komputer nie ma dostępu do folderu minimalny układ w jego pierwotnej lokalizacji.

Przejdź do folderu i zidentyfikuj nazwę aplikacji programu inicjującego. Nazwa aplikacji programu inicjującego zależy od wartości ProductId określonej podczas generowania minimalnego układu. Typowe przykłady znajdują się w poniższej tabeli.

|Wartość ProductId    |Nazwa aplikacji|
|:-----------|:------------|
|Microsoft. VisualStudio. Product. Enterprise    |vs_enterprise.exe|
|Microsoft. VisualStudio. Product. Professional    |vs_professional.exe|
|Microsoft. VisualStudio. Product. BuildTools    |vs_buildtools.exe|

Aktualizacja jest stosowana do wystąpienia programu Visual Studio w dwóch krokach. Zacznij od zaktualizowania Instalator programu Visual Studio, a następnie zaktualizuj program Visual Studio.

1. **Aktualizowanie Instalator programu Visual Studio** 

    Uruchom następujące polecenie, zastępując w `vs_enterprise.exe`  razie potrzeby poprawną nazwę aplikacji inicjującej. 

    ```cmd
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Aktualizowanie aplikacji Visual Studio**

    Aby zaktualizować program Visual Studio, należy określić installPath wystąpienia programu Visual Studio, które chcesz zaktualizować. Jeśli zainstalowano wiele wystąpień programu Visual Studio, każdy z nich musi zostać zaktualizowany osobno. Zdecydowanie zalecamy określenie `–noWeb` opcji za pomocą polecenia Update, aby zapobiec instalacji składników, które nie znajdują się w minimalnym układzie. Zapobiega to wychodzeniu programu Visual Studio w stanie niezdatnym do użytku.

    Uruchom następujące polecenie, zastępując odpowiednio parametr wiersza polecenia installPath. Upewnij się również, że została użyta poprawna nazwa aplikacji programu inicjującego.

    ```cmd
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi](tools-for-managing-visual-studio-instances.md)
* [Jak zdefiniować ustawienia w pliku odpowiedzi](automated-installation-with-response-file.md)
* [Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md)
* [Cykl życia produktu Visual Studio i obsługa](/visualstudio/releases/2019/servicing/)
