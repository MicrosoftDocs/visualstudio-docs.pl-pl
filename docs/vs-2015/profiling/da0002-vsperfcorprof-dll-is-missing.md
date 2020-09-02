---
title: 'DA0002: brak VSPerfCorProf.dll | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5723506415a0ddbf816b896e23e93eaa706bf7e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158724"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: Brak biblioteki VSPerfCorProf.dll
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0002 |  
| Kategoria | Użycie narzędzia profilowania |  
| Metody profilowania | Profilowanie przy użyciu narzędzi wiersza polecenia VSPerfCmd i VSPerfASPNETCmd |  
| Komunikat | Wydaje się, że plik został zebrany bez prawidłowego ustawienia zmiennych środowiskowych za pomocą VSPerfCLREnv. cmd. Symbole dla zarządzanych plików binarnych mogą nie być rozpoznawane. |  
| Typ reguły | Informacje |  
  
## <a name="cause"></a>Przyczyna  
 Profiler nie mógł znaleźć VSPerfCorProf.dll podczas przebiegu profilowania. To ostrzeżenie występuje, gdy narzędzia wiersza polecenia dla kolekcji danych profilera są używane bez użycia narzędzia VSPerfCLREnv. cmd w celu zainicjowania niezbędnych zmiennych środowiskowych. Ostrzeżenie może również być wyzwalane, jeśli inny Profiler jest uruchomiony po rozpoczęciu narzędzia profilowania.  
  
## <a name="rule-description"></a>Opis reguły  
 Określone zmienne środowiskowe muszą zostać ustawione przed uruchomieniem profilowania dla profilera w celu rozpoznania symboli w plikach binarnych .NET Framework. To ostrzeżenie sugeruje, że narzędzie VSPerfCLREnv. cmd nie zostało uruchomione przed zebraniem danych profilowania. Symbole dla zarządzanych plików binarnych mogą nie być rozpoznawane. Aby uzyskać więcej informacji na temat używania narzędzia profilowania z wiersza polecenia, zobacz [profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Podczas profilowania aplikacji zarządzanych przy użyciu narzędzi wiersza polecenia w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia profilowania należy uruchomić narzędzie wiersza polecenia [VSPerfCLREnv](../profiling/vsperfclrenv.md) przed rozpoczęciem zbierania danych.
