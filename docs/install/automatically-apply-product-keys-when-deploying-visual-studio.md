---
title: Automatyczne stosowanie kluczy produktu
description: Dowiedz się, jak programowo stosować klucze produktu podczas wdrażania programu Visual Studio.
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e7f331536de264186bc2977cc4acaaab02147e13
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115222"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio

Klucz produktu można zastosować programowo jako część skryptu, który jest używany do automatyzacji wdrażania programu Visual Studio. Klucz produktu można ustawić na urządzeniu programowo podczas instalacji programu Visual Studio lub po zakończeniu instalacji.

## <a name="apply-the-license-after-installation"></a>Stosowanie licencji po instalacji

::: moniker range="vs-2017"

Zainstalowaną wersję programu Visual Studio można aktywować `StorePID.exe` przy użyciu klucza produktu przy użyciu narzędzia na komputerach docelowych w trybie cichym. `StorePID.exe`to program narzędziowy instaluje się w programie Visual Studio 2017 w następującej lokalizacji domyślnej: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

::: moniker-end

::: moniker range="vs-2019"

Zainstalowaną wersję programu Visual Studio można aktywować `StorePID.exe` przy użyciu klucza produktu przy użyciu narzędzia na komputerach docelowych w trybie cichym. `StorePID.exe`to program narzędziowy instaluje się w programie Visual Studio 2019 w następującej lokalizacji domyślnej: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE`

::: moniker-end

 Uruchom `StorePID.exe` z podwyższonymi uprawnieniami za pomocą agenta Centrum systemowego lub wiersza polecenia z podwyższonym poziomem uprawnień. Postępuj zgodnie z nim za pomocą klucza produktu i kodu produktu firmy Microsoft (MPC).

>[!IMPORTANT]
> Pamiętaj, aby uwzględnić myślniki w kluczu produktu.

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker range="vs-2017"

W poniższym przykładzie przedstawiono wiersz polecenia do zastosowania licencji dla programu Visual Studio 2017 Enterprise, który `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`ma MPC 08860, klucz produktu , i zakłada domyślną lokalizację instalacji:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

W poniższym przykładzie przedstawiono wiersz polecenia do zastosowania licencji dla programu Visual Studio 2019 Enterprise, który `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`ma MPC 09260, klucz produktu , i zakłada domyślną lokalizację instalacji:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 W poniższej tabeli wymieniono kody MPC dla każdej wersji programu Visual Studio:

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

Jeśli `StorePID.exe` klucz produktu zostanie pomyślnie zamówi, zwraca `%ERRORLEVEL%` wartość 0. Jeśli wystąpią błędy, zwraca jeden z następujących kodów, w zależności od warunku błędu:

| Błąd                     | Code |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> Po uruchomieniu wirtualnego wystąpienia programu Visual Studio upewnij się, że można również zwirtualizować lokalny folder AppData i rejestr. Aby rozwiązywać problemy `C:\Program Files (x86)\Microsoft Visual Studio\<version>\Common7\IDE\DDConfigCA.exe`z wystąpieniami wirtualnymi, uruchom plik .  

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalacja programu Visual Studio](../install/install-visual-studio.md)
* [Tworzenie instalacji programu Visual Studio w trybie offline](../install/create-an-offline-installation-of-visual-studio.md)
