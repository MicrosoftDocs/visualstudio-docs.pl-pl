---
title: 'Jak: Wybierz zdarzenia próbkowania | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 82462ae5052150da7761dfcd855e5339e1b7d821
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779054"
---
# <a name="how-to-choose-sampling-events"></a>Jak: Wybierz zdarzenia próbkowania
Domyślnie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania zbiera dane wydajności w odstępie, który jest określony jako liczba cykli procesora, które są używane przez profilowany proces. Domyślna liczba cykli w interwale wynosi 10 000 000, czyli około 0,01 sekundy na komputerze 1 GH. Można zmienić liczbę cykli w interwale i można zmienić zdarzenie próbki. Dostępne są następujące przykładowe zdarzenia:

- Cykle zegara - dla problemów związanych z procesorem.

- Błędy strony - w przypadku problemów związanych z pamięcią.

- Połączenia systemowe - w przypadku problemów związanych z we/wy.

- Licznik wydajności — liczniki procesora cpu dla problemów z wydajnością niskiego poziomu.

> [!IMPORTANT]
> Jeśli zbierasz dane pamięci .NET (alokacje lub okresy istnienia obiektów lub oba) przy użyciu metody próbkowania, wszystkie zdarzenia próbkowania określone przez użytkownika są ignorowane, a odpowiednie alokacje pamięci lub zdarzenia wyrzucania elementów bezużytecznych lub oba te zdarzenia są używane do zbierania danych.

### <a name="to-select-a-sample-event"></a>Aby wybrać przykładowe zdarzenie

1. W **Eksploratorze wydajności**kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.

2. Na **stronach właściwości**kliknij właściwości **próbkowania.**

3. Z listy rozwijanej **Przykładowe zdarzenie** wybierz przykładowe zdarzenie, którego chcesz użyć do profilowania aplikacji.

    > [!NOTE]
    > **Liczniki wydajności Dostępne** są włączone tylko wtedy, gdy wybierzesz **licznik wydajności** z listy rozwijanej **Przykładowe zdarzenie.**

4. Jeśli wybierzesz **licznik wydajności,** wybierz określony licznik procesora z **kontrolki Dostępne liczniki wydajności** widoku drzewa.

    - Liczniki w węźle **Zdarzenia przenośne** są dostępne dla wszystkich typów procesorów.

    - Liczniki w węźle **Zdarzenia platformy** są specyficzne dla procesora na bieżącym komputerze i mogą nie być dostępne dla innych typów procesorów.

5. Po wybraniu zdarzenia przykładowego domyślna wartość interwału próbkowania jest wyświetlana w polu tekstowym **interwał próbkowania.** W razie potrzeby można wprowadzić odpowiednią wartość w polu tekstowym.

## <a name="see-also"></a>Zobacz też
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
- [Jak: Wybierz metody zbierania](../profiling/how-to-choose-collection-methods.md)
- [Liczniki procesorów i systemu Windows](../profiling/cpu-and-windows-counters.md)
- [Zrozumienie wartości danych próbkowania](../profiling/understanding-sampling-data-values.md)
- [Profil z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
