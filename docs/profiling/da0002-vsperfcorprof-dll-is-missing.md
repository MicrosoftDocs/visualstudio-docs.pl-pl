---
title: 'DA0002: Brakuje VSPerfCorProf.dll | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa263f6ceab515627fd33070517e3393aeec419d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936736"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: Brak biblioteki VSPerfCorProf.dll

|||
|-|-|
|Identyfikator reguły|DA0002|
|Kategoria|Użycie narzędzia profilowania|
|Metod profilowania|Profilowanie przy użyciu narzędzia wiersza polecenia narzędzia VSPerfCmd i VSPerfASPNETCmd|
|Komunikat|Wygląda na to, że plik został zebrany bez odpowiedniego ustawienia zmiennych środowiskowych poleceniem *VSPerfCLREnv.cmd*. Symbole dla zarządzanych danych binarnych mogą nie być rozpoznawane.|
|Typ reguły|Informacje|

## <a name="cause"></a>Przyczyna
 Program profilujący nie może odnaleźć *VSPerfCorProf.dll* podczas uruchomienia profilowania. To ostrzeżenie występuje, gdy są używane narzędzia wiersza polecenia do zbierania danych profilera, bez używania *VSPerfCLREnv.cmd* narzędzia, aby zainicjować zmienne środowiskowe wymagane. Ostrzeżenie można również uruchamiają się, jeśli inny profiler jest uruchomiona, gdy start Profiling Tools.

## <a name="rule-description"></a>Opis reguły
 Przed uruchomienie profilowania profiler można rozpoznać symboli w plikach binarnych w .NET Framework, należy ustawić określonych zmiennych środowiskowych. To ostrzeżenie wskazuje, żeby *VSPerfCLREnv.cmd* narzędzie nie zostało uruchomione, zanim został zebrany danych profilowania. Symbole dla zarządzanych danych binarnych nie może rozpoznać. Aby uzyskać więcej informacji o korzystaniu z narzędzi profilowania z wiersza polecenia, zobacz [profilowania z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Jeśli profilowany zarządzanych aplikacji za pomocą narzędzia wiersza polecenia w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools, uruchom [VSPerfCLREnv](../profiling/vsperfclrenv.md) narzędzie wiersza polecenia, przed rozpoczęciem zbierania danych.