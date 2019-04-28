---
title: Dane wyjściowe | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78d5b39908bc0ffa39533c22ea4effcbe97397b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62794220"
---
# <a name="output"></a>Dane wyjściowe
**Dane wyjściowe** opcja określa nazwę pliku danych profilowania dla sesji wydajności. **Dane wyjściowe** musi być używany z **Start** opcji.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametry
 `FileName` Nazwa pliku danych. Akceptowane są pełne i częściowe ścieżki. Jeśli ścieżka nie zostanie określony, plik jest tworzony w bieżącym katalogu.

## <a name="required-options"></a>Wymagane opcje
 **Dane wyjściowe** opcja musi być używany z **Start** opcji.

 **Początek:** `Method` Określa nazwę pliku wyjściowego.

## <a name="example"></a>Przykład
 W poniższym przykładzie utworzono plik danych profilowania, w bieżącym katalogu.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)