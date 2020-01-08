---
title: Sterowanie aktualizacjami na potrzeby wdrożenia
description: Dowiedz się, jak zmienić, gdzie Visual Studio szuka aktualizacji podczas instalacji z sieci.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2cdf4d4e6fb90b18c8141d1d176629539a0a4f8b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75570586"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Sterowanie aktualizacjami na potrzeby wdrożenia oparte na sieci programu Visual Studio

Administratorzy przedsiębiorstwa często tworzenie układu a następnie Hostuj go w sieciowym udziale plików do wdrożenia dla swoich użytkowników końcowych.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Kontrolowanie, których program Visual Studio szuka aktualizacji

Domyślnie program Visual Studio w dalszym ciągu wyszukiwania w trybie online aktualizacje, nawet jeśli instalacja była wdrożona z udziału sieciowego. Jeśli jest dostępna aktualizacja, użytkownik może go zainstalować. Zaktualizowanej zawartości, która nie znajduje się w układzie w trybie offline jest pobierana z sieci web.

Jeśli ma bezpośrednią kontrolę nad którym szuka aktualizacji programu Visual Studio, można zmodyfikować lokalizacji, w którym wygląda na to. Można także kontrolować wersję, którą użytkownicy zaktualizowali system do. Aby to zrobić, wykonaj następujące kroki:

1. Tworzenie układu offline:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Skopiuj go do udziału plików, w którym chcesz udostępnić go:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Zmodyfikuj plik response.json w układ i zmiana `channelUri` wartość, aby wskazać kopię channelManifest.json, który kontroluje administrator.

   Pamiętaj anulować ukośników odwrotnych w wartości, jak w poniższym przykładzie:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Obecnie użytkownicy końcowi mogą uruchomić Instalatora z tego udziału, aby zainstalować program Visual Studio.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Gdy administrator przedsiębiorstwa ustali, nadszedł czas na swoich użytkowników zaktualizować do nowszej wersji programu Visual Studio, mogą oni [zaktualizować lokalizację układ](update-a-network-installation-of-visual-studio.md) zestawowi zaktualizowane pliki w następujący sposób.

1. Użyj polecenia, który jest podobny do następującego polecenia:

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Upewnij się, że response.json plik w układzie zaktualizowane nadal zawiera dostosowania, w szczególności modyfikacji identyfikator channelUri w następujący sposób:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Istniejący program Visual Studio instaluje z tego układu Wyszukaj aktualizacje `\\server\share\VS\ChannelManifest.json`. Jeśli channelManifest.json jest nowsza niż co użytkownik zainstalował, Visual Studio powiadamia użytkownika, że dostępna jest aktualizacja.

   Nowe instalacje automatycznie zainstalować zaktualizowaną wersję programu Visual Studio bezpośrednio z układu.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Kontrolowanie powiadomień w środowisku IDE programu Visual Studio

::: moniker range="vs-2017"

Visual Studio sprawdza lokalizacji, z którego został zainstalowany, takie jak udział sieciowy lub Internetu, aby zobaczyć, czy są dostępne aktualizacje, zgodnie z wcześniejszym opisem. Po udostępnieniu aktualizacji programu Visual Studio powiadamia użytkownika za pomocą flagi powiadomienia w prawym górnym rogu okna.

   ![Flaga powiadomienia dotyczące aktualizacji](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

Visual Studio sprawdza lokalizacji, z którego został zainstalowany, takie jak udział sieciowy lub Internetu, aby zobaczyć, czy są dostępne aktualizacje, zgodnie z wcześniejszym opisem. Po udostępnieniu aktualizacji program Visual Studio powiadamia użytkownika o ikonie powiadomienia w prawym dolnym rogu okna.

   ![Ikona powiadomienia w środowisku IDE programu Visual Studio](media/vs-2019/notification-bar.png "Ikona powiadomienia w środowisku IDE programu Visual Studio")

::: moniker-end

Możesz wyłączyć powiadomienia, jeśli nie chcesz, aby użytkownicy końcowi, aby otrzymywać powiadomienia o aktualizacji. (Na przykład możesz chcieć wyłączyć powiadomienia, jeśli dostarczania aktualizacji za pomocą mechanizmu dystrybucji oprogramowania w centralnej.)

::: moniker range="vs-2017"

Ponieważ program Visual Studio 2017 [wpisy rejestru są przechowywane w rejestrze prywatnym](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), nie można bezpośrednio edytować rejestru w typowy sposób. Jednak program Visual Studio obejmuje `vsregedit.exe` narzędzie, które można użyć, aby zmienić ustawienia programu Visual Studio. Można wyłączyć powiadomienia za pomocą następującego polecenia:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Ponieważ program Visual Studio 2019 [przechowuje wpisy rejestru w rejestrze prywatnym](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), nie można bezpośrednio edytować rejestru w typowy sposób. Jednak program Visual Studio obejmuje `vsregedit.exe` narzędzie, które można użyć, aby zmienić ustawienia programu Visual Studio. Można wyłączyć powiadomienia za pomocą następującego polecenia:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Pamiętaj zastąpić katalogu, aby dopasować zainstalowane wystąpienie, które chcesz edytować.)

> [!TIP]
> Użyj [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) można znaleźć określonego wystąpienia programu Visual Studio na stacji roboczej użytkownika.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Podręcznik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do zarządzania wystąpieniami programu Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Cykl życia produktu Visual Studio i obsługa](/visualstudio/releases/2019/servicing/)
