---
title: 'DA0002: Brak pliku VSPerfCorProf.dll | Dokumenty firmy Microsoft'
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f768a35e7c50ec55867ae49901718063ca39bd0b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777754"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: brakuje VSPerfCorProf.dll

|||
|-|-|
|Identyfikator reguły|DA0002|
|Kategoria|Użycie narzędzi profilowania|
|Metody profilowania|Profilowanie przy użyciu narzędzi wiersza polecenia VSPerfCmd i VSPerfASPNETCmd|
|Komunikat|Wydaje się, że plik został zebrany bez prawidłowego ustawienia zmiennych środowiskowych z *VSPerfCLREnv.cmd*. Symbole zarządzanych plików binarnych mogą nie zostać rozwiązane.|
|Typ reguły|Informacje|

## <a name="cause"></a>Przyczyna
 Profiler nie może odnaleźć *pliku VSPerfCorProf.dll* podczas przebiegu profilowania. To ostrzeżenie występuje, gdy narzędzia wiersza polecenia do zbierania danych profilera są używane bez użycia narzędzia *VSPerfCLREnv.cmd* do inicjowania niezbędnych zmiennych środowiskowych. Ostrzeżenie może również być uruchamiane, jeśli inny profiler jest uruchomiony po uruchomieniu narzędzi profilowania.

## <a name="rule-description"></a>Opis reguły
 Określone zmienne środowiskowe muszą być ustawione przed uruchomieniem profilowania dla profilera, aby rozpoznać symbole w plikach binarnych programu .NET Framework. To ostrzeżenie sugeruje, że narzędzie *VSPerfCLREnv.cmd* nie zostało uruchomione przed zebraniem danych profilowania. Symbole zarządzanych plików binarnych mogą nie zostać rozwiązane. Aby uzyskać więcej informacji na temat korzystania z narzędzi profilowania z wiersza polecenia, zobacz [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Podczas profilowania zarządzanych aplikacji przy użyciu narzędzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersza polecenia w narzędziach profilowania należy uruchomić narzędzie wiersza polecenia [VSPerfCLREnv](../profiling/vsperfclrenv.md) przed rozpoczęciem zbierania danych.
