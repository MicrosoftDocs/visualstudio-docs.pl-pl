---
title: 'Obszar testowy 8: przełączanie wtyczek | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb815a773351c1bb6212962a639e2758114a0e2c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722429"
---
# <a name="test-area-8-plug-in-switching"></a>Obszar testowy 8: przełączanie wtyczki
@No__t_0 zintegrowanego środowiska programistycznego (IDE) ma interfejs użytkownika, aby zmienić bieżącą wtyczkę kontroli źródła. Ten obszar testowy zawiera przypadki testowe dla procesu wybierania wtyczki, która ma być używana na potrzeby kontroli źródła rozwiązania.

## <a name="command-menu-access"></a>Dostęp do menu poleceń
 W przypadku przypadków testowych używane są [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] następujące ścieżki menu zintegrowanego środowiska deweloperskiego.

- Bieżąca Wtyczka kontroli źródła: **narzędzia**  -> **Opcje**  -> **kontroli źródła**  -> **wyboru wtyczki**.

- Zmień powiązanie kontroli źródła: **plik**  -> **kontroli źródła**  -> **Zmień kontrolę źródła**...

## <a name="common-expected-behavior"></a>Typowe oczekiwane zachowanie
 Zmiana wtyczki kontroli źródła dla rozwiązania jest możliwa bez kończenia działania programu Visual Studio lub ponownego załadowania rozwiązania. Ponadto obecnie wtyczka do kontroli źródła jest automatycznie zmieniana na ten, który jest używany przez rozwiązanie po załadowaniu tego rozwiązania.

## <a name="test-cases"></a>Przypadki testowe
 Poniżej wymieniono określone przypadki testowe dla obszaru testowego przełączania wtyczki.

### <a name="case-8a-automatic-change"></a>Przypadek 8a: Automatyczna zmiana

#### <a name="expected-behavior"></a>Oczekiwane zachowanie
 Gdy użytkownik ładuje rozwiązanie, które jest pod kontrolą źródła, jest automatycznie ładowane, a odpowiednia wtyczka kontroli źródła jest wybierana jako bieżąca.

| Akcja | Kroki testu | Oczekiwane wyniki do zweryfikowania |
| - | - | - |
| Automatyczna zmiana wtyczki kontroli źródła | 1. Wybierz wtyczkę w obszarze Testuj jako bieżący (**narzędzia**  -> **Opcje**  -> **kontroli źródła**  -> **wyboru wtyczki**).<br />2. Utwórz nowy projekt.<br />3. Dodaj rozwiązanie do kontroli źródła.<br />4. Wybierz inną wtyczkę (na przykład [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />5. Zaakceptuj monit rozładowania rozwiązania.<br />6. Otwórz ponownie rozwiązanie z dysku. | Rozwiązanie jest otwarte.<br /><br /> Wtyczka poddawana testom jest bieżącą wtyczką kontroli źródła. |

### <a name="case-8b-solution-based-change"></a>Przypadek 8b: zmiana oparta na rozwiązaniu

#### <a name="expected-behavior"></a>Oczekiwane zachowanie
 Rozwiązanie może mieć zmienioną skojarzoną wtyczkę kontroli źródła.

| Akcja | Kroki testu | Oczekiwane wyniki do zweryfikowania |
|----------------------------------| - | - |
| Zmiana wtyczki dla rozwiązania | 1. Wybierz wtyczkę w obszarze Testuj jako bieżący (**narzędzia**  -> **Opcje**  -> **kontroli źródła**  -> **wyboru wtyczki**).<br />2. Utwórz nowy projekt i rozwiązanie.<br />3. Dodaj rozwiązanie do kontroli źródła.<br />4. Usuń powiązanie rozwiązania z kontroli źródła (przy użyciu okna dialogowego **Zmień kontrolę źródła** ).<br />5. Wybierz inną wtyczkę (na przykład [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />6. Załaduj ponownie rozwiązanie z dysku w przypadku jego niezaładowania.<br />7. Dodaj rozwiązanie do kontroli źródła.<br />8. Usuń powiązanie rozwiązania z kontroli źródła (przy użyciu okna dialogowego **Zmień kontrolę źródła** ).<br />9. Wybierz wtyczkę ponownie w obszarze Testuj.<br />10. Załaduj ponownie rozwiązanie z dysku, jeśli zostało zwolnione.<br />11. Powiąż rozwiązanie z oryginalną lokalizacją (przy użyciu okna dialogowego **Zmień kontrolę źródła** ). | Rozwiązanie jest dodawane do kontroli źródła przy użyciu wybranej wtyczki. |

## <a name="see-also"></a>Zobacz także
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)