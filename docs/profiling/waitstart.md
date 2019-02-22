---
title: WaitStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6307dcad45b7e2c8164aa892c4598d577e4ea464
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614639"
---
# <a name="waitstart"></a>WaitStart
Przyczyny opcji WaitStart *VSPerfCmd.exe* podrzędne polecenia uruchomienia, aby zwrócić tylko wtedy, gdy program profilujący został zainicjowany lub po upływie określonej liczby sekund. Domyślnie polecenia uruchomienia zwraca natychmiast. Jeśli polecenie podrzędne uruchamiania jest zwracane bez Inicjowanie programu profilującego, zwracany jest błąd. Jeśli nie określono liczbę sekund, przez czas nieokreślony oczekuje polecenia uruchomienia.

 Opcja WaitStart przydaje się w plikach wsadowych, aby upewnić się, że ten program profilujący został zainicjowany.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]
```

#### <a name="parameters"></a>Parametry
 `Seconds` Liczba sekund oczekiwania przed powrotem z podpolecenie rozpoczęcia.

## <a name="required-options"></a>Wymagane opcje
 Opcja WaitStart należy używać tylko za pomocą polecenia Start podrzędnych.

 **Dane wyjściowe:** `filename` Określa nazwę pliku wyjściowego.

## <a name="remarks"></a>Uwagi

## <a name="example"></a>Przykład
 W tym przykładzie plik wsadowy polecenia uruchomienia będzie czekać na 5 sekund w celu na zainicjowanie programu profiler.

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