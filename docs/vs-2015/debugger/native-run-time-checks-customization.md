---
title: Dostosowanie natywnego sprawdzenia w czasie wykonywania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 434f2425b1eeefd82b954e47a8ced55491a7ec11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697820"
---
# <a name="native-run-time-checks-customization"></a>Dostosowanie macierzystego sprawdzania w trakcie wykonywania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas kompilowania z **/RTC** (sprawdzenia w czasie wykonywania) lub stosowania `runtime_checks` dyrektywy pragma Biblioteka wykonawcza C zapewnia natywne testy w czasie wykonywania. W niektórych przypadkach możesz chcieć dostosować sprawdzenie w czasie wykonywania:  
  
- Aby przekierować komunikaty sprawdzania w czasie wykonywania do pliku lub miejsca docelowego innego niż domyślne.  
  
- Aby określić wyjściowe miejsce docelowe dla komunikatów sprawdzania w czasie wykonywania w ramach debugera innej firmy.  
  
- Aby zgłosić komunikaty sprawdzania czasu wykonywania z programu skompilowanego z wydaną wersją biblioteki wykonawczej C. Wersje wersji biblioteki nie służą `_CrtDbgReportW` do zgłaszania błędów w czasie wykonywania. Zamiast tego wyświetla okno dialogowe **potwierdzenia** dla każdego błędu czasu wykonywania.  
  
  Aby dostosować sprawdzanie błędów czasu wykonywania, można:  
  
- Napisz funkcję raportowania błędów czasu wykonywania. Aby uzyskać więcej informacji, zobacz [jak: napisać funkcję raportowania błędów w czasie wykonywania](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
- Dostosuj lokalizację docelową komunikatu o błędzie.  
  
- Zapytanie o informacje o błędach sprawdzania czasu wykonywania.  
  
## <a name="customize-the-error-message-destination"></a>Dostosuj lokalizację docelową komunikatu o błędzie  
 Jeśli używasz `_CrtDbgReportW` do zgłaszania błędów, możesz użyć, `_CrtSetReportMode` Aby określić miejsce docelowe komunikatów o błędach.  
  
 Jeśli używasz niestandardowej funkcji raportowania, użyj, `_RTC_SetErrorType` Aby skojarzyć błąd z typem raportu.  
  
## <a name="query-for-information-about-run-time-checks"></a>Zapytanie o informacje dotyczące kontroli w czasie wykonywania  
 `_RTC_NumErrors` Zwraca liczbę typów błędów wykrytych przez sprawdzanie błędów czasu wykonywania. Aby uzyskać krótki opis każdego błędu, można wykonać pętlę od 0 do wartości zwracanej przez `_RTC_NumErrors` , przekazując wartość iteracji do `_RTC_GetErrDesc` każdej pętli. Aby uzyskać więcej informacji, zobacz [_RTC_NumErrors](https://msdn.microsoft.com/library/7e82adae-38e2-4f8b-bc0b-37bda8109fd1) i [_RTC_GetErrDesc](https://msdn.microsoft.com/library/7994ec2b-5488-4fd4-806d-a166c9a9f927).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: korzystanie z natywnych testów w czasie wykonywania](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](https://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [_CrtDbgReport, _CrtDbgReportW](https://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)
