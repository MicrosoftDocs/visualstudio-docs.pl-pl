---
title: CrossSession | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 05e1f2360b3257e44fde1af8be3554dd7fd95115
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537186"
---
# <a name="crosssession"></a>CrossSession
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja VSPerfCmd.exe **CrossSession** umożliwia programowi Profiler zbieranie danych z dowolnych sesji konsoli. Opcja **CrossSession** musi być używana z opcją **Start** .  
  
 Można użyć skrótu **CS** zamiast **CrossSession**.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="valid-options"></a>Prawidłowe opcje  
 Aby włączyć profilowanie w innej sesji, należy określić opcję **CrossSession** z opcją **Start** . **CrossSession** należy również określić we wszystkich kolejnych poleceniach **dołączania** i **odłączania** VSPerfCmd.  
  
 **Rozpocznij:**`Method`  
 Opcja **Start** inicjuje profiler do określonej metody profilowania.  
  
 **Attach:** _PID_[**,**_PID_]  
 Rozpoczyna profilowanie określonych procesów.  
  
 **Odłącz**[**:**_PID_[,_PID_]]  
 Powoduje zatrzymanie profilowania określonych procesów.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie opcja **CrossSession** jest używana w celu dołączenia do aplikacji, która została uruchomiona w innej sesji konsoli.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
