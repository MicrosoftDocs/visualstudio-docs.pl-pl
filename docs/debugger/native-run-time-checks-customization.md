---
title: Natywne środowiska wykonawczego sprawdza dostosowywania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 7530f875b3eb14766e32b1237871e6ec48d4bb85
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836247"
---
# <a name="native-run-time-checks-customization"></a>Dostosowanie macierzystego sprawdzania w trakcie wykonywania
Podczas kompilacji z **usunęliśmy** (kontrole czasu wykonywania) lub użyj `runtime_checks` pragma, biblioteki wykonawczej C zapewnia macierzyste sprawdzanie w czasie wykonywania. W niektórych przypadkach możesz chcieć dostosować sprawdzanie w czasie wykonywania:  
  
- Można przekierować wiadomości Sprawdzanie w czasie wykonywania do pliku lub docelowy inny niż domyślny.  
  
- Aby określić dane wyjściowe miejsce docelowe dla środowiska wykonawczego, sprawdź komunikaty w debugerze innych firm.  
  
- Aby zgłosić wiadomości Sprawdzanie w czasie wykonania z poziomu programu skompilowany przy użyciu wersji biblioteki wykonawczej C. Nie należy używać wersji biblioteki `_CrtDbgReportW` do raportowania błędów czasu wykonywania. Zamiast tego są one wyświetlane **Asercja** okno dialogowe dla każdego błędu czasu wykonywania.  
  
  Aby dostosować, sprawdzanie błędów czasu wykonywania, możesz wykonywać następujące czynności:  
  
- Pisanie funkcji raportowania błędów czasu wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Pisanie funkcji raportowania błędów czasu wykonywania](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
- Dostosuj docelowego komunikat błędu.  
  
- Zapytanie dotyczące informacji o czasie wykonywania Sprawdź błędy.  
  
## <a name="customize-the-error-message-destination"></a>Dostosowywanie docelowy komunikatu błędu  
 Jeśli używasz `_CrtDbgReportW` do zgłaszania błędów, można użyć `_CrtSetReportMode` do określenia miejsca docelowego komunikaty o błędach.  
  
 Jeśli używasz niestandardowych funkcji raportowania, należy użyć `_RTC_SetErrorType` skojarzyć błąd z typu raportu.  
  
## <a name="query-for-information-about-run-time-checks"></a>Zapytanie o informacje dotyczące sprawdzania w trakcie wykonywania  
 `_RTC_NumErrors` Zwraca liczbę typów błędów, wykrytych przez sprawdzanie błędów czasu wykonywania. Aby uzyskać krótki opis każdego błędu, można pętli z zakresu od 0 do wartości zwracanej `_RTC_NumErrors`, przekazując wartość iteracji `_RTC_GetErrDesc` na każdej pętli. Aby uzyskać więcej informacji, zobacz [_rtc_numerrors —](/cpp/c-runtime-library/reference/rtc-numerrors) i [_RTC_GetErrDesc](/cpp/c-runtime-library/reference/rtc-geterrdesc).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Korzystanie z macierzystego sprawdzania w czasie wykonywania](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](/cpp/preprocessor/runtime-checks)   
 [_CrtDbgReport, _CrtDbgReportW](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)