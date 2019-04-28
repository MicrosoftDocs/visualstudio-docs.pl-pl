---
title: 'Obszar testowy 8: Przełączanie wtyczki | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b308fb97a55f61645d038c9a81445f4561415e9b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908880"
---
# <a name="test-area-8-plug-in-switching"></a>Obszar testowy 8: przełączanie wtyczki
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zintegrowanego środowiska programistycznego (IDE) ma interfejs użytkownika (UI), aby zmienić bieżącą wtyczką kontroli źródła. Ten obszar testowy zawiera przypadki testowe dla procesu pobrania, który wtyczki do użycia rozwiązania kontroli źródła.

## <a name="command-menu-access"></a>Dostęp do Menu polecenia
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ścieżki menu środowiska zintegrowanego rozwoju są używane w przypadkach testowych.

- Bieżącą wtyczką kontroli źródła: **Narzędzia** -> **opcje** -> **kontroli źródła** -> **wybór wtyczki**.

- Zmień źródło powiązaniu kontroli: **Plik** -> **kontroli źródła** -> **Zmień kontrolę źródła**...

## <a name="common-expected-behavior"></a>Typowe oczekiwane zachowanie.
 Zmiana wtyczka do kontroli źródła dla rozwiązania jest możliwa bez zamykania programu Visual Studio lub ponowne załadowanie rozwiązania. Ponadto bieżącą wtyczką kontroli źródła automatycznie zmieni się używaną przez rozwiązanie po załadowaniu tego rozwiązania.

## <a name="test-cases"></a>Przypadki testowe
 Poniżej przedstawiono określonych przypadków testowych dla obszaru wtyczki testu przełączania.

### <a name="case-8a-automatic-change"></a>8a przypadków: Automatyczna zmiana

#### <a name="expected-behavior"></a>Oczekiwane zachowanie
 Gdy użytkownik wczytuje rozwiązanie, które jest pod kontrolą źródła, to rozwiązanie jest ładowane automatycznie i odpowiednie wtyczka do kontroli źródła jest wybrany jako bieżący.

| Akcja | Kroki testu | Oczekiwanych wyników, aby sprawdzić |
| - | - | - |
| Zmiana wtyczki kontroli źródła automatyczne | 1.  Wybierz wtyczkę w ramach testu jako bieżący (**narzędzia** -> **opcje** -> **kontroli źródła** -> **wtyczki Wybór**.)<br />2.  Utwórz nowy projekt.<br />3.  Dodaj rozwiązanie do kontroli źródła.<br />4.  Wybierz inne wtyczki (na przykład [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />5.  Zaakceptuj zwalnianie monit rozwiązania.<br />6.  Ponownie otwórz rozwiązanie z dysku. | Rozwiązanie jest otwierane.<br /><br /> Dodatek w ramach testu jest bieżącą wtyczką kontroli źródła. |

### <a name="case-8b-solution-based-change"></a>8b przypadków: Oparte na rozwiązaniach zmiany

#### <a name="expected-behavior"></a>Oczekiwane zachowanie
 Rozwiązanie może mieć jego skojarzony wtyczka do kontroli źródła zmienione.

| Akcja | Kroki testu | Oczekiwanych wyników, aby sprawdzić |
|----------------------------------| - | - |
| Zmiana wtyczki dla rozwiązania | 1.  Wybierz wtyczkę w ramach testu jako bieżący (**narzędzia** -> **opcje** -> **kontroli źródła** -> **wtyczki Wybór**).<br />2.  Utwórz nowy projekt i rozwiązanie.<br />3.  Dodaj rozwiązanie do kontroli źródła.<br />4.  Usuń powiązanie rozwiązanie z kontroli źródła (przy użyciu **Zmień kontrolę źródła** okno dialogowe).<br />5.  Wybierz inne wtyczki (na przykład [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />6.  Załaduj ponownie rozwiązanie z dysku, jeśli pozostaną niezaładowane.<br />7.  Dodaj rozwiązanie do kontroli źródła.<br />8.  Usuń powiązanie rozwiązanie z kontroli źródła (przy użyciu **Zmień kontrolę źródła** okno dialogowe).<br />9. Wybierz wtyczkę w ramach testu ponownie.<br />10. Załaduj ponownie rozwiązanie z dysku, jeśli pozostaną niezaładowane.<br />11. Powiązać rozwiązanie z oryginalnej lokalizacji (przy użyciu **Zmień kontrolę źródła** okno dialogowe). | Rozwiązanie zostanie dodany do kontroli źródła przy użyciu wybranej wtyczki. |

## <a name="see-also"></a>Zobacz też
- [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)