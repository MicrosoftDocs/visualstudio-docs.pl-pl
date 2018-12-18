---
title: Natywne środowiska wykonawczego sprawdza dostosowywania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 216a96a6702bfabc57d235144bf4a6cc05df4224
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721145"
---
# <a name="native-run-time-checks-customization"></a>Dostosowanie macierzystego sprawdzania w trakcie wykonywania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas kompilacji z **usunęliśmy** (kontrole czasu wykonywania) lub użyj `runtime_checks` pragma, biblioteki wykonawczej C zapewnia macierzyste sprawdzanie w czasie wykonywania. W niektórych przypadkach możesz chcieć dostosować sprawdzanie w czasie wykonywania:  
  
- Można przekierować wiadomości Sprawdzanie w czasie wykonywania do pliku lub docelowy inny niż domyślny.  
  
- Aby określić dane wyjściowe miejsce docelowe dla środowiska wykonawczego, sprawdź komunikaty w debugerze innych firm.  
  
- Aby zgłosić wiadomości Sprawdzanie w czasie wykonania z poziomu programu skompilowany przy użyciu wersji biblioteki wykonawczej C. Nie należy używać wersji biblioteki `_CrtDbgReportW` do raportowania błędów czasu wykonywania. Zamiast tego są one wyświetlane **Asercja** okno dialogowe dla każdego błędu czasu wykonywania.  
  
  Aby dostosować, sprawdzanie błędów czasu wykonywania, możesz wykonywać następujące czynności:  
  
- Pisanie funkcji raportowania błędów czasu wykonywania. Aby uzyskać więcej informacji, zobacz [porady: pisanie funkcji raportowania błędów czasu wykonywania](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
- Dostosuj docelowego komunikat błędu.  
  
- Zapytanie dotyczące informacji o czasie wykonywania Sprawdź błędy.  
  
## <a name="customize-the-error-message-destination"></a>Dostosowywanie docelowy komunikatu błędu  
 Jeśli używasz `_CrtDbgReportW` do zgłaszania błędów, można użyć `_CrtSetReportMode` do określenia miejsca docelowego komunikaty o błędach.  
  
 Jeśli używasz niestandardowych funkcji raportowania, należy użyć `_RTC_SetErrorType` skojarzyć błąd z typu raportu.  
  
## <a name="query-for-information-about-run-time-checks"></a>Zapytanie o informacje dotyczące sprawdzania w trakcie wykonywania  
 `_RTC_NumErrors` Zwraca liczbę typów błędów, wykrytych przez sprawdzanie błędów czasu wykonywania. Aby uzyskać krótki opis każdego błędu, można pętli z zakresu od 0 do wartości zwracanej `_RTC_NumErrors`, przekazując wartość iteracji `_RTC_GetErrDesc` na każdej pętli. Aby uzyskać więcej informacji, zobacz [_rtc_numerrors —](http://msdn.microsoft.com/library/7e82adae-38e2-4f8b-bc0b-37bda8109fd1) i [_RTC_GetErrDesc](http://msdn.microsoft.com/library/7994ec2b-5488-4fd4-806d-a166c9a9f927).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Korzystanie z macierzystego sprawdzania w czasie wykonywania](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [_CrtDbgReport, _CrtDbgReportW](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)





