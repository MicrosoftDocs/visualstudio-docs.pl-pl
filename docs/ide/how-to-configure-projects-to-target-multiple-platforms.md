---
title: Konfigurowanie projektów pod kątem wielu platform docelowych
description: Dowiedz się, w jaki sposób program Visual Studio umożliwia rozwiązanie ukierunkowane na kilka różnych architektur procesora CPU lub platform.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3255af161bd37d16eefeb6d41115cf0114059e81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875435"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Instrukcje: Konfigurowanie projektów pod kątem wielu platform docelowych

Program Visual Studio umożliwia rozwiązanie ukierunkowane na kilka różnych architektur procesora lub platform jednocześnie. Właściwości do ustawienia są dostępne za pomocą okna dialogowego **Configuration Manager** .

## <a name="target-a-platform"></a>Docelowa platforma

W oknie dialogowym **Configuration Manager** można tworzyć i ustawiać konfiguracje i platformy na poziomie projektu oraz. Każda kombinacja konfiguracji i elementów docelowych na poziomie rozwiązania może mieć unikatowy zestaw właściwości, co pozwala łatwo przełączać się między, na przykład konfiguracją wydania, która jest przeznaczona dla [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] platformy, konfiguracją wydania, która jest przeznaczona dla platformy x86, i konfiguracją debugowania, która jest przeznaczona dla platformy x86.

1. W menu **Kompilacja** kliknij pozycję **Configuration Manager**.

2. W **polu aktywna platforma rozwiązania** Wybierz platformę, dla której ma zostać utworzone rozwiązanie, lub wybierz opcję **\<New>** utworzenia nowej platformy. Program Visual Studio skompiluje aplikację jako docelową platformę ustawioną jako aktywną platformę w oknie dialogowym **Configuration Manager** .

## <a name="remove-a-platform"></a>Usuń platformę

Jeśli nie masz potrzeby dla platformy, możesz usunąć ją za pomocą okna dialogowego **Configuration Manager** . Spowoduje to usunięcie wszystkich ustawień rozwiązania i projektu skonfigurowanych dla danej kombinacji konfiguracji i celu.

1. W menu **Kompilacja** kliknij pozycję **Configuration Manager**.

2. W **polu aktywna Platforma rozwiązań** wybierz opcję **\<Edit>** . Zostanie otwarte okno dialogowe **Edytowanie platform rozwiązań** .

3. Kliknij platformę, którą chcesz usunąć, a następnie kliknij przycisk **Usuń**.

## <a name="target-multiple-platforms-with-one-solution"></a>Kierowanie wielu platform za pomocą jednego rozwiązania

Ponieważ można zmienić ustawienia na podstawie kombinacji ustawień konfiguracji i platformy, można skonfigurować rozwiązanie, które może być ukierunkowane na więcej niż jedną platformę.

### <a name="to-target-multiple-platforms"></a>Aby docelowa była wiele platform

1. Użyj **Configuration Manager** , aby dodać co najmniej dwie platformy docelowe dla rozwiązania.

2. Wybierz platformę, która ma być docelowa z listy **aktywnych platform rozwiązań** .

3. Skompiluj rozwiązanie.

### <a name="to-build-multiple-solution-configurations-at-once"></a>Aby jednocześnie skompilować wiele konfiguracji rozwiązań

1. Użyj **Configuration Manager** , aby dodać co najmniej dwie platformy docelowe dla rozwiązania.

2. Użyj okna **kompilacja wsadowa** , aby skompilować kilka konfiguracji rozwiązań jednocześnie.

   Istnieje możliwość, że platforma na poziomie rozwiązania ma ustawioną wartość, na przykład, [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] i nie ma żadnych projektów w ramach tego rozwiązania przeznaczonych dla tej samej platformy. Istnieje również możliwość, że w rozwiązaniu istnieje wiele projektów, z których każdy jest przeznaczony dla różnych platform. Zaleca się, aby w przypadku jednej z tych sytuacji utworzyć nową konfigurację z opisową nazwą, aby uniknąć nieporozumień.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)
- [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md)
- [Twórz i czyść projekty i rozwiązania w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
