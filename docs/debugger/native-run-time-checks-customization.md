---
title: Dostosowanie natywnego sprawdzenia Run-Time | Microsoft Docs
description: 'Dowiedz się, jak dostosować sprawdzanie w czasie wykonywania, w tym: Określanie miejsca docelowego komunikatu, pisanie funkcji raportowania błędów i wykonywanie zapytań dotyczących informacji o błędzie.'
ms.custom: SEO-VS-2020
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 3b5f5aa55ac9d8c13da605a09986569c534a30bf
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975202"
---
# <a name="native-run-time-checks-customization"></a>Dostosowanie macierzystego sprawdzania w trakcie wykonywania
Podczas kompilowania z **/RTC** (sprawdzenia w czasie wykonywania) lub stosowania `runtime_checks` dyrektywy pragma Biblioteka wykonawcza C zapewnia natywne testy w czasie wykonywania. W niektórych przypadkach możesz chcieć dostosować sprawdzenie w czasie wykonywania:

- Aby przekierować komunikaty sprawdzania w czasie wykonywania do pliku lub miejsca docelowego innego niż domyślne.

- Aby określić wyjściowe miejsce docelowe dla komunikatów sprawdzania w czasie wykonywania w ramach debugera innej firmy.

- Aby zgłosić komunikaty sprawdzania czasu wykonywania z programu skompilowanego z wydaną wersją biblioteki wykonawczej C. Wersje wersji biblioteki nie służą `_CrtDbgReportW` do zgłaszania błędów w czasie wykonywania. Zamiast tego wyświetla okno dialogowe **potwierdzenia** dla każdego błędu czasu wykonywania.

  Aby dostosować sprawdzanie błędów czasu wykonywania, można:

- Napisz funkcję raportowania błędów czasu wykonywania. Aby uzyskać więcej informacji, zobacz [jak: napisać Run-Time funkcję raportowania błędów](../debugger/how-to-write-a-run-time-error-reporting-function.md).

- Dostosuj lokalizację docelową komunikatu o błędzie.

- Zapytanie o informacje o błędach sprawdzania czasu wykonywania.

## <a name="customize-the-error-message-destination"></a>Dostosuj lokalizację docelową komunikatu o błędzie
 Jeśli używasz `_CrtDbgReportW` do zgłaszania błędów, możesz użyć, `_CrtSetReportMode` Aby określić miejsce docelowe komunikatów o błędach.

 Jeśli używasz niestandardowej funkcji raportowania, użyj, `_RTC_SetErrorType` Aby skojarzyć błąd z typem raportu.

## <a name="query-for-information-about-run-time-checks"></a>Zapytanie o informacje dotyczące sprawdzania Run-Time
 `_RTC_NumErrors` Zwraca liczbę typów błędów wykrytych przez sprawdzanie błędów czasu wykonywania. Aby uzyskać krótki opis każdego błędu, można wykonać pętlę od 0 do wartości zwracanej przez `_RTC_NumErrors` , przekazując wartość iteracji do `_RTC_GetErrDesc` każdej pętli. Aby uzyskać więcej informacji, zobacz [_RTC_NumErrors](/cpp/c-runtime-library/reference/rtc-numerrors) i [_RTC_GetErrDesc](/cpp/c-runtime-library/reference/rtc-geterrdesc).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: korzystanie z natywnych sprawdzeń Run-Time](../debugger/how-to-use-native-run-time-checks.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [_CrtDbgReport, _CrtDbgReportW](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)