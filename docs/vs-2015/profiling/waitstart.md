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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803517"
---
# <a name="waitstart"></a>WaitStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja WaitStart powoduje, że podpolecenie VSPerfCmd.exe Start zwrócić tylko wtedy, gdy program profilujący został zainicjowany lub po upływie określonej liczby sekund. Domyślnie polecenia uruchomienia zwraca natychmiast. Jeśli polecenie podrzędne uruchamiania jest zwracane bez Inicjowanie programu profilującego, zwracany jest błąd. Jeśli nie określono liczbę sekund, przez czas nieokreślony oczekuje polecenia uruchomienia.  
  
 Opcja WaitStart przydaje się w plikach wsadowych, aby upewnić się, że ten program profilujący został zainicjowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Seconds`  
 Liczba sekund oczekiwania przed powrotem z podpolecenie rozpoczęcia.  
  
## <a name="required-options"></a>Wymagane opcje  
 Opcja WaitStart należy używać tylko za pomocą polecenia Start podrzędnych.  
  
 **Dane wyjściowe:** `filename`  
 Określa nazwę pliku wyjściowego.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 W tym przykładzie plik wsadowy polecenia uruchomienia będzie czekać na 5 sekund w celu na zainicjowanie programu profiler.  
  
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
