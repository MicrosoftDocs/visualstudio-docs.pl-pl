---
title: Uruchom | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 83dc76e3e92a05f936d94c8cd0f6a2b9b69e4cc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192819"
---
# <a name="start"></a>Rozpocznij
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja **Start** jest opcją VSPerfCmd.exe, która inicjuje profiler do określonej metody profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Method`  
 Musi być jednym z następujących słów kluczowych:  
  
- **Trace** — określa metodę Instrumentacji.  
  
- **Przykład** — określa metodę próbkowania.  
  
- **Pokrycie** — określa pokrycie kodu.  
  
- **Współbieżność** — określa metodę rywalizacji o zasoby.  
  
## <a name="required-options"></a>Wymagane opcje  
 Opcja **Output** musi być określona, jeśli w wierszu polecenia określono wartość **Start** .  
  
 **Dane wyjściowe:**`filename`  
 Określa nazwę pliku wyjściowego.  
  
## <a name="exclusive-options"></a>Opcje wyłączności  
 Następujących opcji można używać tylko z opcją **Start** w wierszu polecenia.  
  
 **CrossSession**&#124;**CS**  
 Włącza profilowanie między procesami. Nazwy opcji **CrossSession** i **CS** są obsługiwane.  
  
 **Użytkownik:**[ `domain\` ]`username`  
 Umożliwia klientowi dostęp do monitora z określonego konta.  
  
 **WinCounter:** `Path` [**AutoMark**: `n` ]  
 **WinCounter** Określa licznik wydajności systemu Windows, który ma zostać uwzględniony jako znacznik w pliku danych profilowania. **Autoznacznik** określa interwał w milisekundach między kolekcjami pliku danych.  
  
## <a name="invalid-options"></a>Nieprawidłowe opcje  
 Następujących opcji nie można używać z opcją **Start** w wierszu polecenia.  
  
 **Stan**  
 **Stan** dotyczy tych procesów, które są profilowane. Wyświetla listę procesów i wątków oraz ich bieżący stan profilu (włączone/wyłączone). Na przykład jeśli proces został zatrzymany, **status** nie będzie wskazywać tego w raporcie. **Stan** będzie wskazywać, że proces jest profilowany lub nie.  
  
 **Zamknięcie**[**:** `Timeout` ]  
 Wyłącza Profiler.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak za pomocą opcji **Start** VSPerfCmd.exe zainicjować profiler.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
