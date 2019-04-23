---
title: 'Instrukcje: Konfigurowanie projektów pod kątem wielu platform docelowych | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7457b5be3a6c1cbf2c2b6a1c6f66f9fb89e8d225
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60100303"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Instrukcje: Konfigurowanie projektów pod kątem wielu platform docelowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zapewnia sposób rozwiązania pod kątem kilku innej architektury procesora CPU lub platformami, jednocześnie. Właściwości, aby ustawić te są dostępne za pośrednictwem **programu Configuration Manager** okno dialogowe.  
  
## <a name="targeting-a-platform"></a>Obsługiwane platformy  
 **Programu Configuration Manager** okno dialogowe pozwala utworzyć i ustawić konfiguracje rozwiązania i na poziomie projektu i platformy. Każdej kombinacji konfiguracji na poziomie rozwiązania i elementy docelowe może mieć unikatowe zbiory właściwości skojarzonych z nią, dzięki czemu można łatwo przełączać się między, na przykład konfiguracja wydania przeznaczonego [!INCLUDE[vcprx64](../includes/vcprx64-md.md)] platforma, konfiguracja wydania który jest przeznaczony dla x86 platformy i konfiguracji debugowania, który jest przeznaczony dla x86 platformy.  
  
#### <a name="to-set-your-configuration-to-target-a-different-platform"></a>Aby ustawić konfigurację pod kątem różnych platform  
  
1. Na **kompilacji** menu, kliknij przycisk **programu Configuration Manager**.  
  
2. W **pole platforma rozwiązania aktywnego**, wybierz platformę rozwiązania do obiektu docelowego, lub wybierz  **\<nowy >** do utworzenia nowej platformie. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] będzie kompilować aplikację pod kątem platformy, który jest ustawiony jako aktywnej platformy w **programu Configuration Manager** okno dialogowe.  
  
## <a name="removing-a-platform"></a>Usuwanie platformy  
 Jeśli okazuje się, że użytkownik nie ma potrzeby dla platformy, możesz usunąć ją za pomocą okna dialogowego programu Configuration Manager. Spowoduje to usunięcie wszystkich ustawień rozwiązania i projektu, skonfigurowane dla tej kombinacji konfiguracji i docelowej.  
  
#### <a name="to-remove-a-platform"></a>Aby usunąć to platforma  
  
1. Na **kompilacji** menu, kliknij przycisk **programu Configuration Manager**.  
  
2. W **pole platforma rozwiązania aktywnego**, wybierz opcję  **\<Edytuj >**. **Edytuj platformy rozwiązań** zostanie otwarte okno dialogowe.  
  
3. Kliknij platformy, aby usunąć, a następnie kliknij przycisk **Usuń**.  
  
## <a name="targeting-multiple-platforms-with-one-solution"></a>Przeznaczone dla wielu platform za pomocą jednego rozwiązania  
 Ponieważ istnieje możliwość zmiany ustawień, oparte na kombinacji konfiguracji i ustawień platformy, można skonfigurować rozwiązanie, które mogą kierować więcej niż jedną platformę.  
  
#### <a name="to-target-multiple-platforms"></a>Do wielu platform docelowych  
  
1. Użyj **programu Configuration Manager** można dodać co najmniej dwóch platform dla rozwiązania.  
  
2. Wybierz platformę docelową z **aktywną platformą rozwiązania** listy.  
  
3. Skompiluj rozwiązanie.  
  
#### <a name="to-build-multiple-solution-configurations-at-once"></a>Aby od razu kompilowanie wielu konfiguracji rozwiązania  
  
1. Użyj **programu Configuration Manager** można dodać co najmniej dwóch platform dla rozwiązania.  
  
2. Użyj **tworzenie partii** okna, aby jednocześnie utworzyć kilka konfiguracji rozwiązania.  
  
   Można mieć platformę rozwiązanie na poziomie zestawu, na przykład [!INCLUDE[vcprx64](../includes/vcprx64-md.md)], i mieć żadnych projektów w ramach tego rozwiązania przeznaczone dla tej samej platformy. Istnieje również możliwość ma wiele projektów w rozwiązaniu, każdy przeznaczonych dla różnych platform. Zalecane jest, jeśli masz jedną z tych sytuacji, utworzenie nowej konfiguracji za pomocą opisową nazwę, aby uniknąć mylenia go.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)   
 [Ogólne informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md)   
 [Kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
