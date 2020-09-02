---
title: WaitStart | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1737f13a5271b2c4012ff6ee957fa08b0b8b7799
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164556"
---
# <a name="waitstart"></a>WaitStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja WaitStart powoduje, że podpolecenie VSPerfCmd.exe Uruchom podpolecenia do zwrócenia tylko po zainicjowaniu profilera lub upływie określonej liczby sekund. Domyślnie polecenie Uruchom zwraca natychmiast. Jeśli polecenie Start sub zwróci wartość bez inicjowania profilera, zwracany jest błąd. Jeśli liczba sekund nie zostanie określona, polecenie uruchamiania czeka na czas nieokreślony.  
  
 Opcja WaitStart jest przydatna w plikach wsadowych, aby upewnić się, że profiler został zainicjowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Seconds`  
 Liczba sekund oczekiwania przed powrocie z polecenia Start sub.  
  
## <a name="required-options"></a>Wymagane opcje  
 Opcji WaitStart można użyć tylko z poleceniem Start sub.  
  
 **Dane wyjściowe:**`filename`  
 Określa nazwę pliku wyjściowego.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pliku wsadowego polecenie uruchamiania czeka 5 sekund na zainicjowanie profilera.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5  
if not %errorlevel% 0 goto :error_tag  
VSPerfCmd.exe /Launch:TestApp.exe  
goto :end  
:error_tag  
@echo Could not start Profiler!  
@echo Error %errorlevel%  
:end  
```
