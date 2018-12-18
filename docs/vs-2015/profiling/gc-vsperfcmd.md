---
title: GC (VSPerfCmd) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c9a57a8fa4b0610cc3cceb00e09749a2e5b077e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727871"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**GC** opcja umożliwia zbieranie danych pamięci .NET Framework alokacji i obiekt okresu istnienia. **GC** opcji należy używać tylko z metoda profilowania próbkowanie i tylko **Uruchom** opcji.  
  
 Kiedy używasz **GC** opcji polecenia VSPerfClrEnv **/sampleon** polecenia nie jest wymagana.  
  
 Jeśli nie określono żadnych parametrów lub **alokacji** parametr jest określony, są zbierane tylko .NET Framework dane alokacji pamięci. Jeśli **okres istnienia** parametr jest określony, alokacji pamięci .NET Framework i .NET Framework obiektu zbieranych danych o okresie istnienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 **Alokacja**  
 Domyślnie. Zbiera dane alokacji pamięci .NET Framework.  
  
 **Okres istnienia**  
 Zbiera dane alokacji pamięci .NET Framework i .NET Framework danych o okresie istnienia obiektu.  
  
## <a name="required-options"></a>Wymagane opcje  
 **GC** opcja może być używana tylko z **Uruchom** opcji.  
  
 **Uruchom:** `AppName`  
 Uruchamia określoną aplikację i rozpoczyna się profilowanie przy użyciu metody pobierania próbek.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład spowoduje uruchomienie aplikacji i zbiera dane alokacji pamięci .NET Framework.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)



