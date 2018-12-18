---
title: Użytkownik (VSPerfCmd) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6c201253fe6952bed0657d54f8cc91eb60fbba6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760027"
---
# <a name="user-vsperfcmd"></a>Użytkownik (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Użytkownika** opcja określa nazwę domeny i użytkownika konta, które jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań Windows.  
  
 **Użytkownika** opcji można określić tylko w wierszu polecenia, który zawiera także **Start** opcji opcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Domain`  
 Nazwa domeny użytkownika.  
  
 `UserName`  
 Nazwa użytkownika.  
  
## <a name="required-options"></a>Wymagane opcje  
 **Użytkownika** opcja może być używana tylko z **Start** opcji.  
  
 **Początek:** `Method`  
 Inicjuje profiler do określonej metody profilowania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie **użytkownika** opcji.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)



