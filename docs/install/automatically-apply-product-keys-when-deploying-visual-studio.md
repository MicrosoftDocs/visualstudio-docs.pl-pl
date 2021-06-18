---
title: Automatyczne stosowanie kluczy produktów
description: Dowiedz się, jak programowo stosować klucze produktów podczas wdrażania Visual Studio.
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a78da89d8e8ce4251bc9288270628bfe784eca7a
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307722"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio

Klucz produktu można zastosować programowo w ramach skryptu używanego do automatyzacji wdrażania Visual Studio. Klucz produktu można ustawić na urządzeniu programowo podczas instalacji Visual Studio lub po zakończeniu instalacji.

::: moniker range=">=vs-2022"

> [!IMPORTANT]
> Visual Studio 2022 r. jest obecnie w wersji zapoznawczej, a w okresie zapoznawczym program Visual Studio 2022 jest dostępny w ramach licencji ewaluacyjną, która nie wymaga stosowania klucza produktu.

::: moniker-end

::: moniker range="vs-2017"

## <a name="apply-the-license-after-installation"></a>Stosowanie licencji po zakończeniu instalacji

Zainstalowaną wersję pakietu można aktywować Visual Studio kluczem produktu przy użyciu narzędzia na maszynach docelowych `StorePID.exe` w trybie dyskretnym. `StorePID.exe` to program narzędziowy instalowany z programem Visual Studio 2017 w następującej lokalizacji domyślnej:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE
```

 Uruchom `StorePID.exe` polecenie z podwyższonym poziomem uprawnień, używając agenta System Center lub wiersza polecenia z podwyższonym poziomem uprawnień. Postępuj zgodnie z nim przy użyciu klucza produktu i kodu produktu firmy Microsoft (MPC).

>[!IMPORTANT]
> Pamiętaj, aby w kluczu produktu uwzględnić łączniki.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2019"

## <a name="apply-the-license-after-installation"></a>Stosowanie licencji po zakończeniu instalacji

Zainstalowaną wersję pakietu można aktywować Visual Studio kluczem produktu przy użyciu narzędzia na maszynach docelowych `StorePID.exe` w trybie dyskretnym. `StorePID.exe` to program narzędziowy instalowany z programem Visual Studio 2019 w następującej lokalizacji domyślnej:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE
```

 Uruchom `StorePID.exe` polecenie z podwyższonym poziomem uprawnień, używając agenta System Center lub wiersza polecenia z podwyższonym poziomem uprawnień. Postępuj zgodnie z nim przy użyciu klucza produktu i kodu produktu firmy Microsoft (MPC).

>[!IMPORTANT]
> Pamiętaj, aby w kluczu produktu uwzględnić łączniki.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2017"

W poniższym przykładzie pokazano wiersz polecenia do stosowania licencji dla programu Visual Studio 2017 Enterprise, który ma mpc 08860, klucz produktu i zakłada domyślną lokalizację `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` instalacji:

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

W poniższym przykładzie pokazano wiersz polecenia do stosowania licencji dla programu Visual Studio 2019 Enterprise, który ma klucz MPC 09260, klucz produktu i zakłada domyślną lokalizację `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` instalacji:

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 W poniższej tabeli wymieniono kody MPC dla każdej wersji Visual Studio:

| Visual Studio Edition                | Mpc   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2019"

| Visual Studio Edition                | Mpc   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

::: moniker range="vs-2017"

Jeśli `StorePID.exe` klucz produktu zostanie pomyślnie zastosowanie, zwraca wartość `%ERRORLEVEL%` 0. Jeśli wystąpią błędy, zwraca jeden z następujących kodów, w zależności od warunku błędu:

| Błąd                     | Kod |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> Po uruchomieniu wirtualnego wystąpienia Visual Studio upewnij się, że zwirtualizowany jest również lokalny folder AppData i rejestr. Aby rozwiązać problemy z wystąpieniami wirtualnymi, `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe` uruchom .  

::: moniker-end

::: moniker range="vs-2019"

Jeśli `StorePID.exe` klucz produktu zostanie pomyślnie zastosowanie, zwraca wartość `%ERRORLEVEL%` 0. Jeśli wystąpią błędy, zwraca jeden z następujących kodów, w zależności od warunku błędu:

| Błąd                     | Kod |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> Po uruchomieniu wirtualnego wystąpienia Visual Studio upewnij się, że zwirtualizowany jest również lokalny folder AppData i rejestr. Aby rozwiązać problemy z wystąpieniami wirtualnymi, `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe` uruchom .  

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](../install/install-visual-studio.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)