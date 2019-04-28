---
title: TargetCLR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 479f7e1cbd85c0421497020ae1fc108154ca639a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968317"
---
# <a name="targetclr"></a>TargetCLR
**TargetCLR** opcji określa wersję wspólnego języka środowiska wykonawczego (języka wspólnego CLR) do profilowania, gdy więcej niż jedna wersja środowiska CLR jest załadowana w aplikacji.

 Domyślnie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools docelowe pierwszą wersję środowiska CLR, który jest ładowany przez aplikację.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>Parametry
 `ClrVersion` Numer wersji środowiska CLR. Użyj formatu wersji **vN.N.NNNNN**.

## <a name="required-options"></a>Wymagane opcje
 **TargetCLR** opcja może być używana tylko z **Uruchom** lub **Dołącz** opcje.

 **Uruchom:** `AppName` Uruchamia określoną aplikację i rozpoczyna się do profilu.

 **Dołącz:** `PID` Uruchamia profilowanie określonego procesu.

## <a name="example"></a>Przykład
 W tym przykładzie opcja TargetCLR służy do upewnij się, że środowisko CLR w wersji 4.0.11003 jest profilowane.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```