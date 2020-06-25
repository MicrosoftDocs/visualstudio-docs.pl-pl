---
title: WaitStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b42936d9d87ad80b48b7fdc71cdf0fd3fa965af2
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329893"
---
# <a name="waitstart"></a>WaitStart
Opcja WaitStart powoduje, że podpolecenie *VSPerfCmd.exe* Uruchom podpolecenia do zwrócenia tylko po zainicjowaniu profilera lub upływie określonej liczby sekund. Domyślnie polecenie Uruchom zwraca natychmiast. Jeśli polecenie Start sub zwróci wartość bez inicjowania profilera, zwracany jest błąd. Jeśli liczba sekund nie zostanie określona, polecenie uruchamiania czeka na czas nieokreślony.

 Opcja WaitStart jest przydatna w plikach wsadowych, aby upewnić się, że profiler został zainicjowany.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Parametry
 `Seconds`Liczba sekund oczekiwania przed powrocie z polecenia Start sub.

## <a name="required-options"></a>Wymagane opcje
 Opcji WaitStart można użyć tylko z poleceniem Start sub.

 **Dane wyjściowe:** `filename` Określa nazwę pliku wyjściowego.

## <a name="remarks"></a>Uwagi

## <a name="example"></a>Przykład
 W tym przykładzie pliku wsadowego polecenie uruchamiania czeka 5 sekund na zainicjowanie profilera.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5
if not %errorlevel% 0 goto :error_tag
VSPerfCmd.exe /Launch:TestApp.exe
goto :end
:error_tag
@echo Could not start Profiler!
@echo Error %errorlevel%
:end
```
