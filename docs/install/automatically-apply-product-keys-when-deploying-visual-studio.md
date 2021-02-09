---
title: Automatycznie Zastosuj klucze produktu
description: Dowiedz się, jak programowo zastosować klucze produktu podczas wdrażania programu Visual Studio.
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 029c2829e1a31f3fc5329e38d1f369afafa17f6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868715"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio

Możesz programowo zastosować swój klucz produktu w ramach skryptu, który służy do automatyzowania wdrożenia programu Visual Studio. Klucz produktu można ustawić na urządzeniu programowo podczas instalacji programu Visual Studio lub po zakończeniu instalacji.

## <a name="apply-the-license-after-installation"></a>Zastosuj licencję po instalacji

::: moniker range="vs-2017"

Zainstalowaną wersję programu Visual Studio można aktywować za pomocą klucza produktu przy użyciu `StorePID.exe` Narzędzia na komputerach docelowych w trybie dyskretnym. `StorePID.exe` Program narzędziowy instalowany z programem Visual Studio 2017 w następującej lokalizacji domyślnej: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

::: moniker-end

::: moniker range="vs-2019"

Zainstalowaną wersję programu Visual Studio można aktywować za pomocą klucza produktu przy użyciu `StorePID.exe` Narzędzia na komputerach docelowych w trybie dyskretnym. `StorePID.exe` Program narzędziowy instalowany z programem Visual Studio 2019 w następującej lokalizacji domyślnej: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE`

::: moniker-end

 Uruchom `StorePID.exe` z podniesionymi uprawnieniami, korzystając z programu System Center Agent lub wiersza polecenia z podwyższonym poziomem uprawnień. Postępuj zgodnie z informacjami o kluczu produktu i kodzie produktu firmy Microsoft (MPC).

>[!IMPORTANT]
> Pamiętaj o uwzględnieniu kresek w kluczu produktu.

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker range="vs-2017"

Poniższy przykład przedstawia wiersz polecenia służący do zastosowania licencji programu Visual Studio 2017 Enterprise, która ma MPC 08860, klucz produktu `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` i przyjmuje domyślną lokalizację instalacji:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

Poniższy przykład przedstawia wiersz polecenia służący do zastosowania licencji programu Visual Studio 2019 Enterprise, która ma MPC 09260, klucz produktu `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` i przyjmuje domyślną lokalizację instalacji:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 Poniższa tabela zawiera listę kodów MPC dla każdej wersji programu Visual Studio:

| Wersja programu Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2019"

| Wersja programu Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

Jeśli `StorePID.exe` program pomyślnie zastosuje klucz produktu, zwraca wartość `%ERRORLEVEL%` 0. Jeśli wystąpią błędy, zwraca jeden z następujących kodów, w zależności od warunku błędu:

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
> Gdy uruchamiasz wirtualne wystąpienie programu Visual Studio, upewnij się, że jest również Wirtualizacja lokalnego folderu AppData i rejestru. Aby rozwiązać problemy z wystąpieniami wirtualnymi, uruchom polecenie `C:\Program Files (x86)\Microsoft Visual Studio\<version>\Common7\IDE\DDConfigCA.exe` .  

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](../install/install-visual-studio.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
