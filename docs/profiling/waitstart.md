---
title: WaitStart | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1cbabcf86afa9770f1616c7e4e508af1c9afa1ba
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779860"
---
# <a name="waitstart"></a>WaitStart
Opcja WaitStart powoduje, że polecenie *podrzędne programu VSPerfCmd.exe* Start zwraca się tylko wtedy, gdy profiler zainicjował lub po upływie określonej liczby sekund. Domyślnie polecenie Start zwraca natychmiast. Jeśli polecenie Rozpocznij polecenie podrzędne zwraca bez inicjowania profilera, zwracany jest błąd. Jeśli liczba sekund nie jest określona, polecenie Start czeka przez czas nieokreślony.

 WaitStart Opcja jest przydatna w plikach wsadowych, aby zapewnić, że profiler został zainicjowany.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Parametry
 `Seconds`Liczba sekund oczekiwania przed zwróceniem z polecenia startowego.

## <a name="required-options"></a>Wymagane opcje
 Opcji WaitStart można używać tylko z poleceniem podrzędnym Start.

 **Dane wyjściowe:** `filename` Określa nazwę pliku wyjściowego.

## <a name="remarks"></a>Uwagi

## <a name="example"></a>Przykład
 W tym przykładzie pliku wsadowego polecenie Start będzie czekać przez 5 sekund na zainicjowanie profilera.

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
