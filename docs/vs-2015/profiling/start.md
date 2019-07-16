---
title: Start | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192819"
---
# <a name="start"></a>Uruchamianie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Start** opcja jest opcji VSPerfCmd.exe, która inicjuje profiler do określonej metody profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Method`  
 Musi mieć jedną z następujących słów kluczowych:  
  
- **ŚLEDZENIE** -określa metody instrumentacji.  
  
- **Przykładowe** -określa metody pobierania próbek.  
  
- **POKRYCIE** -określa pokrycie kodu.  
  
- **WSPÓŁBIEŻNOŚĆ** -określa metodę rywalizacji zasobów.  
  
## <a name="required-options"></a>Wymagane opcje  
 **Dane wyjściowe** opcja musi być określony, gdy **Start** jest określona w wierszu polecenia.  
  
 **Dane wyjściowe:** `filename`  
 Określa nazwę pliku wyjściowego.  
  
## <a name="exclusive-options"></a>Wykluczających się opcji  
 Następujące opcje można używać tylko z **Start** opcji w wierszu polecenia.  
  
 **CrossSession**&#124;**CS**  
 Włącza między procesami profilowania. Nazwy opcji **CrossSession** i **CS** są obsługiwane.  
  
 **Użytkownik:** [`domain\`]`username`  
 Umożliwia dostęp klienta do monitora z określonego konta.  
  
 **WinCounter:** `Path` [**Automark**:`n`]  
 **WinCounter** Określa licznik wydajności Windows, aby uwzględnić jako znacznik w pliku danych profilowania. **AutoMark** Określa interwał w milisekundach między operacjami pliku danych.  
  
## <a name="invalid-options"></a>Nieprawidłowe opcje  
 Nie można użyć następujących opcji z **Start** opcji w wierszu polecenia.  
  
 **Status**  
 **Stan** dotyczy procesy, które są profilowane. Wyświetla listę procesów i wątków oraz ich bieżącego stanu profilowania (wł. / wył.). Na przykład, jeśli proces zostanie zatrzymana **stan** nie wskaże, to w raporcie. **Stan** opisano proces albo jest profilowane czy nie.  
  
 **Zamknięcie**[ **:** `Timeout`]  
 Wyłącza profilera.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób użycia VSPerfCmd.exe **Start** możliwość zainicjowania programu profilującego.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
