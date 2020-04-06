---
title: 'Obszar badania 8: Przełączanie wtykowe | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 799fb04936a24004d73ce4c8aa3ec654490f3f62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704392"
---
# <a name="test-area-8-plug-in-switching"></a>Obszar testowy 8: przełączanie wtyczki
Zintegrowane [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowisko programistyczne (IDE) ma interfejs użytkownika (UI) do zmiany bieżącej wtyczki kontroli źródła. Ten obszar testowy zapewnia przypadki testowe dla procesu pobrania, które wtyczki do użycia do kontroli źródła rozwiązania.

## <a name="command-menu-access"></a>Dostęp do menu polecenia
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ścieżki menu zintegrowanego środowiska programistycznego są używane w przypadkach testowych.

- Wtyczka kontroli bieżącego źródła: Wybór**wtyczki wtyku****źródła** -> **opcje** ->  **narzędzi** -> .

- Zmień powiązanie kontroli źródła: Kontrola**źródła** ->  **pliku** -> Zmień źródło**kontroli ...**

## <a name="common-expected-behavior"></a>Typowe oczekiwane zachowanie
 Zmiana wtyczki kontroli źródła dla rozwiązania jest możliwe bez zamykania programu Visual Studio lub ponownego ładowania rozwiązania. Ponadto bieżąca wtyczka kontroli źródła automatycznie zmienia się na wtyczkę używaną przez rozwiązanie po załadowaniu tego rozwiązania.

## <a name="test-cases"></a>Przypadki testowe
 Poniżej przedstawiono konkretne przypadki testowe dla obszaru badania przełączania wtyczek.

### <a name="case-8a-automatic-change"></a>Przypadek 8a: Automatyczna zmiana

#### <a name="expected-behavior"></a>Oczekiwane zachowanie
 Gdy użytkownik ładuje rozwiązanie, które jest pod kontrolą źródła, rozwiązanie jest automatycznie ładowane i wtyczka kontroli odpowiedniego źródła jest wybierana jako bieżąca.

| Akcja | Etapy testu | Oczekiwane wyniki do zweryfikowania |
| - | - | - |
| Automatyczna zmiana wtyczki sterowania źródłem | 1. Wybierz wtyczkę w fazie testów jako bieżącą **(Wybór wtyczki wtyku****źródła** -> **opcji** -> **narzędzi).** -> <br />2. Utwórz nowy projekt.<br />3. Dodaj rozwiązanie do kontroli źródła.<br />4. Wybierz inną wtyczkę (na przykład [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />5. Zaakceptuj szybkie rozwiązanie rozładunkowe.<br />6. Otwórz ponownie rozwiązanie z dysku. | Rozwiązanie jest otwarte.<br /><br /> Testowa wtyczka jest wtyczką kontroli bieżącego źródła. |

### <a name="case-8b-solution-based-change"></a>Przypadek 8b: Zmiana oparta na rozwiązaniu

#### <a name="expected-behavior"></a>Oczekiwane zachowanie
 Rozwiązanie może mieć jego skojarzone wtyczki kontroli źródła zmienione.

| Akcja | Etapy testu | Oczekiwane wyniki do zweryfikowania |
|----------------------------------| - | - |
| Zmiana wtyczki dla rozwiązania | 1. Wybierz wtyczkę w fazie testów jako aktualną **(Wybór wtyczki wtyku****źródła** -> **opcji** -> **narzędzi).** -> <br />2. Utwórz nowy projekt i rozwiązanie.<br />3. Dodaj rozwiązanie do kontroli źródła.<br />4. Odłącz rozwiązanie od kontroli źródła (za pomocą okna dialogowego **Zmień formant źródła).**<br />5. Wybierz inną wtyczkę (na przykład [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />6. Ponownie załaduj rozwiązanie z dysku, jeśli jest rozładowane.<br />7. Dodaj rozwiązanie do kontroli źródła.<br />8. Odłącz rozwiązanie od kontroli źródła (za pomocą okna dialogowego **Zmień formant źródła).**<br />9. Ponownie wybierz test wtyczek.<br />10. Przeładuj rozwiązanie z dysku, jeśli jest rozładowane.<br />11. Powiąż rozwiązanie z oryginalną lokalizacją (za pomocą okna dialogowego **Zmień formant źródła).** | Rozwiązanie jest dodawane do kontroli źródła za pomocą wybranej wtyczki. |

## <a name="see-also"></a>Zobacz też
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
