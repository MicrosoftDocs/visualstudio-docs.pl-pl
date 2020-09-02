---
title: 'Instrukcje: Konfigurowanie projektów pod kątem wielu platform docelowych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bb759faff99b641f24df87f73bc1d3d52b6635cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663558"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Porady: konfigurowanie projektów do wielu platform docelowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] umożliwia rozwiązanie ukierunkowane na kilka różnych architektur procesora lub platform jednocześnie. Właściwości do ustawienia są dostępne za pomocą okna dialogowego **Configuration Manager** .

## <a name="targeting-a-platform"></a>Kierowanie do platformy
 W oknie dialogowym **Configuration Manager** można tworzyć i ustawiać konfiguracje i platformy na poziomie projektu oraz. Każda kombinacja konfiguracji i elementów docelowych na poziomie rozwiązania może mieć unikatowy zestaw właściwości, co pozwala łatwo przełączać się między, na przykład konfiguracją wydania, która jest przeznaczona dla [!INCLUDE[vcprx64](../includes/vcprx64-md.md)] platformy, konfiguracją wydania, która jest przeznaczona dla platformy x86, i konfiguracją debugowania, która jest przeznaczona dla platformy x86.

#### <a name="to-set-your-configuration-to-target-a-different-platform"></a>Aby ustawić konfigurację jako docelową dla innej platformy

1. W menu **Kompilacja** kliknij pozycję **Configuration Manager**.

2. W **polu aktywna platforma rozwiązania**Wybierz platformę, dla której ma zostać utworzone rozwiązanie, lub wybierz opcję **\<New>** utworzenia nowej platformy. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spowoduje skompilowanie aplikacji jako docelowej platformy, która jest ustawiona jako aktywna platforma w oknie dialogowym **Configuration Manager** .

## <a name="removing-a-platform"></a>Usuwanie platformy
 Jeśli nie masz potrzeby dla platformy, możesz usunąć ją za pomocą okna dialogowego Configuration Manager. Spowoduje to usunięcie wszystkich ustawień rozwiązania i projektu skonfigurowanych dla danej kombinacji konfiguracji i celu.

#### <a name="to-remove-a-platform"></a>Aby usunąć platformę

1. W menu **Kompilacja** kliknij pozycję **Configuration Manager**.

2. W **polu aktywna Platforma rozwiązań**wybierz opcję **\<Edit>** . Zostanie otwarte okno dialogowe **Edytowanie platform rozwiązań** .

3. Kliknij platformę, którą chcesz usunąć, a następnie kliknij przycisk **Usuń**.

## <a name="targeting-multiple-platforms-with-one-solution"></a>Kierowanie wielu platform przy użyciu jednego rozwiązania
 Ponieważ można zmienić ustawienia na podstawie kombinacji ustawień konfiguracji i platformy, można skonfigurować rozwiązanie, które może być ukierunkowane na więcej niż jedną platformę.

#### <a name="to-target-multiple-platforms"></a>Aby docelowa była wiele platform

1. Użyj **Configuration Manager** , aby dodać co najmniej dwie platformy docelowe dla rozwiązania.

2. Wybierz platformę, która ma być docelowa z listy **aktywnych platform rozwiązań** .

3. Skompiluj rozwiązanie.

#### <a name="to-build-multiple-solution-configurations-at-once"></a>Aby jednocześnie skompilować wiele konfiguracji rozwiązań

1. Użyj **Configuration Manager** , aby dodać co najmniej dwie platformy docelowe dla rozwiązania.

2. Użyj okna **kompilacja wsadowa** , aby skompilować kilka konfiguracji rozwiązań jednocześnie.

   Istnieje możliwość, że platforma na poziomie rozwiązania ma ustawioną wartość, na przykład, [!INCLUDE[vcprx64](../includes/vcprx64-md.md)] i nie ma żadnych projektów w ramach tego rozwiązania przeznaczonych dla tej samej platformy. Istnieje również możliwość, że w rozwiązaniu istnieje wiele projektów, z których każdy jest przeznaczony dla różnych platform. Zaleca się, aby w przypadku jednej z tych sytuacji utworzyć nową konfigurację z opisową nazwą, aby uniknąć nieporozumień.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md) [Omówienie konfiguracji kompilacji](../ide/understanding-build-configurations.md) [Kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
