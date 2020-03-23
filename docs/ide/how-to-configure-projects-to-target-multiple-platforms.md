---
title: 'Jak: Konfigurowanie projektów do kierowania na wiele platform'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b86a5c95131a4dcb2e6af199b57e9c8302790b5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114450"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Jak: Konfigurowanie projektów do kierowania na wiele platform

Visual Studio zapewnia sposób rozwiązania do kierowania kilka różnych architektur procesora CPU lub platform naraz. Właściwości, które można je ustawić, są dostępne za pośrednictwem okna dialogowego **programu Menedżer konfiguracji.**

## <a name="target-a-platform"></a>Kierowanie na platformę

Okno dialogowe **Menedżer konfiguracji** umożliwia tworzenie i ustawianie konfiguracji i platform na poziomie rozwiązania i projektu. Każda kombinacja konfiguracji na poziomie rozwiązania i obiektów docelowych może mieć unikatowy zestaw właściwości skojarzonych z nim, [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] co pozwala łatwo przełączać się między, na przykład, konfiguracji wydania, która jest przeznaczona dla platformy, konfiguracji wydania, która jest przeznaczona dla platformy x86 i konfiguracji debugowania, która jest przeznaczona dla platformy x86.

1. W menu **Kompilacja** kliknij pozycję **Configuration Manager**.

2. W **polu Platforma rozwiązania Active**wybierz platformę, na którą ma być kierowane rozwiązanie, lub wybierz ** \<pozycję Nowy>,** aby utworzyć nową platformę. Visual Studio skompiluje aplikację do docelowej platformy, która jest ustawiona jako aktywna platforma w oknie dialogowym **programu Menedżer konfiguracji.**

## <a name="remove-a-platform"></a>Usuwanie platformy

Jeśli zdasz sobie sprawę, że nie potrzebujesz platformy, możesz ją usunąć za pomocą okna dialogowego **Menedżer konfiguracji.** Spowoduje to usunięcie wszystkich ustawień rozwiązania i projektu skonfigurowanych dla tej kombinacji konfiguracji i obiektu docelowego.

1. W menu **Kompilacja** kliknij pozycję **Configuration Manager**.

2. W **polu Platforma rozwiązania Active**wybierz pozycję ** \<Edytuj>**. Zostanie otwarte okno dialogowe **Edytowanie platform rozwiązań.**

3. Kliknij platformę, którą chcesz usunąć, a następnie kliknij przycisk **Usuń**.

## <a name="target-multiple-platforms-with-one-solution"></a>Kierowanie na wiele platform za pomocą jednego rozwiązania

Ponieważ można zmienić ustawienia na podstawie kombinacji konfiguracji i ustawień platformy, można skonfigurować rozwiązanie, które może kierować więcej niż jedną platformę.

### <a name="to-target-multiple-platforms"></a>Aby kierować reklamy na wiele platform

1. Użyj **menedżera konfiguracji,** aby dodać co najmniej dwie platformy docelowe dla rozwiązania.

2. Wybierz platformę, na którą chcesz kierować reklamy z listy **Platforma aktywnego rozwiązania.**

3. Skompiluj rozwiązanie.

### <a name="to-build-multiple-solution-configurations-at-once"></a>Aby utworzyć wiele konfiguracji rozwiązań jednocześnie

1. Użyj **menedżera konfiguracji,** aby dodać co najmniej dwie platformy docelowe dla rozwiązania.

2. Okno **kompilacji wsadowej** służy do tworzenia kilku konfiguracji rozwiązania jednocześnie.

   Istnieje możliwość, aby platforma na poziomie rozwiązania ustawiona na przykład [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)]i nie ma żadnych projektów w ramach tego rozwiązania kierowania tej samej platformy. Istnieje również możliwość wielu projektów w rozwiązaniu, z których każdy jest skierowany na różne platformy. Zaleca się, aby w przypadku jednej z tych sytuacji utworzyć nową konfigurację o opisowej nazwie, aby uniknąć nieporozumień.

## <a name="see-also"></a>Zobacz też

- [Jak: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)
- [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md)
- [Twórz i twórz projekty i rozwiązania w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
