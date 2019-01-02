---
title: Dane wyjściowe | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4bca95dea2ac381d28d2c2a4043f94dcfb6fd6e9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922269"
---
# <a name="output"></a>Dane wyjściowe
**Dane wyjściowe** opcja określa nazwę pliku danych profilowania dla sesji wydajności. **Dane wyjściowe** musi być używany z **Start** opcji.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `FileName`  
 Nazwa pliku danych. Akceptowane są pełne i częściowe ścieżki. Jeśli ścieżka nie zostanie określony, plik jest tworzony w bieżącym katalogu.  
  
## <a name="required-options"></a>Wymagane opcje  
 **Dane wyjściowe** opcja musi być używany z **Start** opcji.  
  
 **Początek:** `Method`  
 Określa nazwę pliku wyjściowego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie utworzono plik danych profilowania, w bieżącym katalogu.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)