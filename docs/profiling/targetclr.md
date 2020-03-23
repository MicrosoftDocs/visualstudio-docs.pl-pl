---
title: TargetCLR | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771609"
---
# <a name="targetclr"></a>TargetCLR
**Opcja TargetCLR** określa wersję wspólnego języka wykonywania (CLR) do profilu, gdy więcej niż jedna wersja CLR jest ładowany w aplikacji.

 Domyślnie narzędzia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilowania są przeznaczone dla pierwszej wersji programu CLR ładowanej przez aplikację.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>Parametry
 `ClrVersion`Numer wersji programu CLR. Użyj formatu wersji **vN.N.NNNNN**.

## <a name="required-options"></a>Wymagane opcje
 Opcji **TargetCLR** można używać tylko z opcjami **Uruchom** lub **Dołącz.**

 **Uruchamianie:** `AppName` Uruchamia określoną aplikację i rozpoczyna profil.

 **Dołącz:** `PID` Rozpoczyna profil określony proces.

## <a name="example"></a>Przykład
 W tym przykładzie targetCLR opcja jest używana, aby upewnić się, że CLR w wersji 4.0.11003 jest profilowane.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```
