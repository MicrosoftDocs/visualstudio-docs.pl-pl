---
title: Dane wyjściowe | Microsoft Docs
description: Dowiedz się, w jaki sposób opcja Output określa nazwę pliku danych profilowania dla sesji wydajności. Dane wyjściowe muszą być używane z opcją Start.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6067e13e33875be778ff59739f5511c4116937ed
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722805"
---
# <a name="output"></a>Dane wyjściowe
Opcja **wyjście** określa nazwę pliku danych profilowania dla sesji wydajności. **Dane wyjściowe** muszą być używane z opcją **Start** .

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametry
 `FileName` Nazwa pliku danych. Akceptowane są pełne i częściowe ścieżki. Jeśli ścieżka nie zostanie określona, plik zostanie utworzony w bieżącym katalogu.

## <a name="required-options"></a>Wymagane opcje
 Opcja **Output** musi być używana z opcją **Start** .

 **Rozpocznij:** `Method` Określa nazwę pliku wyjściowego.

## <a name="example"></a>Przykład
 W poniższym przykładzie plik danych profilowania jest tworzony w bieżącym katalogu.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
