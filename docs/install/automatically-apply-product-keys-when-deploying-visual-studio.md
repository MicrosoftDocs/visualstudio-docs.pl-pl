---
title: Automatyczne stosowanie kluczy produktów
description: Dowiedz się, jak programowo stosowanie kluczy produktów podczas wdrażania programu Visual Studio.
ms.date: 08/14/2017
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa0ed93097c396808f8a4404243be925d1b03ca0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827946"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Automatyczne stosowanie kluczy produktów podczas wdrażania programu Visual Studio

Można zastosować klucz produktu programowego jako część skryptu, który służy do automatycznego wdrożenia programu Visual Studio. Możesz ustawić klucz produktu na urządzeniu programowo podczas instalacji programu Visual Studio lub po zakończeniu instalacji.

## <a name="apply-the-license-after-installation"></a>Po zainstalowaniu Zastosuj licencji

 Zainstalowana wersja programu Visual Studio za pomocą klucza produktu można aktywować za pomocą `StorePID.exe` narzędzia na komputerach docelowych, w trybie dyskretnym. `StorePID.exe` to narzędzie program, instaluje się za pomocą programu Visual Studio 2017 w następującej lokalizacji domyślnej: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 Uruchom `StorePID.exe` z podwyższonym poziomem uprawnień, za pomocą agenta programu System Center lub wiersz polecenia. Postępuj zgodnie z jej za pomocą klucza produktu i kod produktu firmy Microsoft (MPC).

>[!IMPORTANT]
> Upewnij się, które mają zostać objęte kresek klucza produktu.

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

 W poniższym przykładzie przedstawiono polecenie stosowania licencji dla programu Visual Studio 2017 Enterprise, która ma MPC 08860, klucz produktu `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, założono domyślna lokalizacja instalacji:

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 Poniższa tabela zawiera listę kodów MPC dla każdej wersji programu Visual Studio:

| Wersja programu Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

Jeśli `StorePID.exe` pomyślnie dotyczy klucz produktu, funkcja zwraca `%ERRORLEVEL%` 0. W przypadku wykrycia błędów, zwraca jedną z poniższych kodów, w zależności od warunku błędu:

| Błąd                     | Kod |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](../install/install-visual-studio.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
