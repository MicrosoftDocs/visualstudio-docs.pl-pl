---
title: Dane wyjściowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26a9532bcf0e641d9ad27522f207493b905dc471
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179564"
---
# <a name="output"></a>Dane wyjściowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja **wyjście** określa nazwę pliku danych profilowania dla sesji wydajności. **Dane wyjściowe** muszą być używane z opcją **Start** .  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `FileName`  
 Nazwa pliku danych. Akceptowane są pełne i częściowe ścieżki. Jeśli ścieżka nie zostanie określona, plik zostanie utworzony w bieżącym katalogu.  
  
## <a name="required-options"></a>Wymagane opcje  
 Opcja **Output** musi być używana z opcją **Start** .  
  
 **Rozpocznij:**`Method`  
 Określa nazwę pliku wyjściowego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie plik danych profilowania jest tworzony w bieżącym katalogu.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
