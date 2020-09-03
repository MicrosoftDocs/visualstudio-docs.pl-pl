---
title: TargetCLR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fffcab1d841840c15957e8dae0ff0f87b20de28d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74771609"
---
# <a name="targetclr"></a>TargetCLR
Opcja **TargetCLR** określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska CLR jest załadowana w aplikacji.

 Domyślnie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania jest celem pierwszej wersji środowiska CLR, która jest ładowana przez aplikację.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>Parametry
 `ClrVersion` Numer wersji środowiska CLR. Użyj formatu wersji **vn. nnnnn**.

## <a name="required-options"></a>Wymagane opcje
 Opcji **TargetCLR** można użyć tylko z opcjami **uruchamiania** lub **dołączania** .

 **Uruchom:** `AppName` Uruchamia określoną aplikację i uruchamia profilowanie.

 **Dołącz:** `PID` Zaczyna profilować określony proces.

## <a name="example"></a>Przykład
 W tym przykładzie opcja TargetCLR jest używana w celu upewnienia się, że środowisko CLR w wersji 4.0.11003 jest profilowane.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```
