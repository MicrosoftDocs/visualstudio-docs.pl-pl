---
title: Kontrolowanie aktualizacji wdrożeń
description: Dowiedz się, jak Visual Studio szuka aktualizacji podczas instalacji z sieci.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: f15281db55381dadbfd3370eb10a04feeab9c3a5
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307573"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Kontrolowanie aktualizacji wdrożeń Visual Studio sieciowych

Administratorzy przedsiębiorstwa często tworzą układ i hostują go w sieciowym udziałach plików w celu wdrożenia ich dla użytkowników końcowych. Na tej stronie opisano sposób prawidłowego konfigurowania opcji układu sieci.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Kontrolowanie, Visual Studio szuka aktualizacji

**Scenariusz 1. Klient pierwotnie zainstalowany z układu, ale jest skonfigurowany do odbierania aktualizacji z lokalizacji układu sieciowego lub sieci Web**

Domyślnie program Visual Studio wyszukiwania aktualizacji w trybie online, nawet jeśli instalacja została pierwotnie wdrożona z udziału sieciowego. Jeśli aktualizacja jest dostępna w Internecie, użytkownik może ją zainstalować. Mimo że pamięć podręczna układu sieciowego jest najpierw sprawdzana pod uwagę, czy nie znaleziono tam zaktualizowanych bitów produktu, Visual Studio będzie szukać zaktualizowanych bitów produktów z Internetu i pobierać je z Internetu.

**Scenariusz 2. Klient został pierwotnie zainstalowany i powinien otrzymywać aktualizacje tylko z układu sieci**

Jeśli chcesz kontrolować, gdzie klient programu Visual Studio szuka aktualizacji, na przykład jeśli komputer kliencki nie ma dostępu do Internetu i chcesz upewnić się, że jest on instalowany tylko i zawsze z układu, możesz skonfigurować lokalizację, w której instalator klienta szuka zaktualizowanych bitów produktów. Najlepiej jest upewnić się, że to ustawienie jest poprawnie skonfigurowane, zanim klient dokona początkowej instalacji z układu.

1. Tworzenie układu w trybie offline:

   ```shell
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Skopiuj go do udziału plików, w którym chcesz go hostować:

   ```shell
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Zmodyfikuj plik w układzie i zmień wartość tak, aby wskazać kopię channelManifest.js`response.json` `channelUri` na kontrolce administratora.

   Pamiętaj, aby przed ukośnikami odwrotnym w wartości, jak w poniższym przykładzie:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Teraz użytkownicy końcowi mogą uruchomić instalatora z tego udziału, aby zainstalować Visual Studio.

   ```shell
   \\server\share\VS\vs_enterprise.exe
   ```

Gdy administrator przedsiębiorstwa ustali, że na czas aktualizacji do nowszej wersji programu [](update-a-network-installation-of-visual-studio.md) Visual Studio, może zaktualizować lokalizację układu w celu uwzględnienia zaktualizowanych plików w następujący sposób.

1. Użyj polecenia podobnego do następującego polecenia:

   ```shell
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Upewnij się, że plik w zaktualizowanym układzie nadal zawiera dostosowania, w szczególności modyfikację `response.json` channelUri, w następujący sposób:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

Istniejące Visual Studio instalacji z tego układu poszukaj aktualizacji na stronie `\\server\share\VS\ChannelManifest.json` . Jeśli channelManifest.jsjest nowsze niż to, co użytkownik zainstalował, Visual Studio powiadamia użytkownika, że aktualizacja jest dostępna.

Każda aktualizacja instalacji zainicjowana przez klienta automatycznie zainstaluje zaktualizowaną wersję programu Visual Studio bezpośrednio z układu.

**Scenariusz 3. Klient pierwotnie zainstalowany z Sieci Web, ale teraz powinien odbierać aktualizacje tylko z układu sieci**

W niektórych przypadkach komputer kliencki może już Visual Studio z Sieci Web, ale teraz administrator chce, aby wszystkie przyszłe aktualizacje pochodziły z układu zarządzanego. Jedynym obsługiwanym sposobem jest utworzenie układu sieci z odpowiednią wersją produktu, a następnie na komputerze  klienckim uruchomienie programu inicjjącego z lokalizacji układu (np. `\\server\share\vs_enterprise.exe` ). W idealnym przypadku oryginalna instalacja klienta byłaby uruchamiana przy użyciu programu inicjjącego z układu sieciowego z poprawnie skonfigurowanym channelURI, ale będzie również działać zaktualizowany program inicjujący z lokalizacji układu sieciowego. Jedna z tych akcji osadza na komputerze klienckim połączenie z określoną lokalizacją układu. Jedynym zastrzeżeniam do poprawnego działania tego scenariusza jest to, że "ChannelURI" w pliku układu musi być taki sam jak wartość ChannelURI ustawioną na komputerze klienta podczas oryginalnej `response.json` instalacji. Najprawdopodobniej ta wartość została pierwotnie ustawiona na internetowy kanał [wydań](https://aka.ms/vs/16/release/channel).

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Kontrolowanie powiadomień w Visual Studio IDE

::: moniker range="vs-2017"

Jak opisano wcześniej, Visual Studio sprawdza lokalizację, z której została zainstalowana, na przykład udział sieciowy lub Internet, aby sprawdzić, czy są dostępne jakiekolwiek aktualizacje. Gdy aktualizacja jest dostępna, Visual Studio powiadomi użytkownika za pomocą flagi powiadomienia w prawym górnym rogu okna.

   ![Flaga powiadomienia dla aktualizacji](media/notification-flag.png)

::: moniker-end

::: moniker range=">=vs-2019&quot;

Jak opisano wcześniej, Visual Studio sprawdza lokalizację, z której została zainstalowana, na przykład udział sieciowy lub Internet, aby sprawdzić, czy są dostępne jakiekolwiek aktualizacje. Gdy aktualizacja jest dostępna, Visual Studio powiadomi użytkownika za pomocą ikony powiadomienia w prawym dolnym rogu okna.

   ![Ikona powiadomienia w Visual Studio IDE](media/vs-2019/notification-bar.png &quot;Ikona powiadomienia w Visual Studio IDE")

::: moniker-end

Powiadomienia można wyłączyć, jeśli nie chcesz, aby użytkownicy końcowi otrzymywać powiadomienia o aktualizacjach. (Na przykład można wyłączyć powiadomienia w przypadku dostarczania aktualizacji za pośrednictwem centralnego mechanizmu dystrybucji oprogramowania).

::: moniker range="vs-2017"

Ponieważ Visual Studio 2017 [](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)przechowuje wpisy rejestru w rejestrze prywatnym, nie można bezpośrednio edytować rejestru w typowy sposób. Jednak Visual Studio narzędzie, które umożliwia zmianę `vsregedit.exe` Visual Studio ustawień. Powiadomienia można wyłączyć za pomocą następującego polecenia:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Ponieważ Visual Studio 2019 [](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)przechowuje wpisy rejestru w rejestrze prywatnym, nie można bezpośrednio edytować rejestru w typowy sposób. Jednak Visual Studio narzędzie, które umożliwia zmianę `vsregedit.exe` Visual Studio ustawień. Powiadomienia można wyłączyć za pomocą następującego polecenia:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range=">=vs-2022"

Ponieważ Visual Studio 2022 [](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)przechowuje wpisy rejestru w rejestrze prywatnym, nie można bezpośrednio edytować rejestru w typowy sposób. Jednak Visual Studio narzędzie, które umożliwia zmianę `vsregedit.exe` Visual Studio ustawień. Powiadomienia można wyłączyć za pomocą następującego polecenia:

```shell
vsregedit.exe set "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Pamiętaj, aby zastąpić katalog tak, aby był taki, aby był taki, w którym zainstalowane wystąpienie ma być edytowane).

> [!TIP]
> Użyj [vswhere.exe, ](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) aby znaleźć określone wystąpienie Visual Studio na stacji roboczej klienta.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Włączanie aktualizacji administratora](enabling-administrator-updates.md)
* [Stosowanie aktualizacji administratora](applying-administrator-updates.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do zarządzania Visual Studio wystąpień](tools-for-managing-visual-studio-instances.md)
* [Visual Studio produktu i jego obsługa](/visualstudio/releases/2019/servicing/)
