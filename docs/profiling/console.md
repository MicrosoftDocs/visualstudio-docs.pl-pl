---
title: Konsola | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74a5cecbdf3bba942c888a5cde3d49236047f4ee
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607879"
---
# <a name="console"></a>Konsola
VSPerfCmd.exe **konsoli** opcji uruchomi aplikację określoną w nowym oknie wiersza polecenia. **Konsola** należy używać tylko przy użyciu narzędzia VSPerfCmd **Uruchom** opcji. Jeśli aplikacja nie jest aplikacją wiersza polecenia **konsoli** nie ma wpływu.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="required-options"></a>Wymagane opcje
 **Konsola** można określić tylko w wierszu polecenia, który zawiera także **Uruchom** opcji.

 **Uruchom:** `AppName` Uruchamia program profilujący i aplikacji, określonej przez `AppName`.

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)