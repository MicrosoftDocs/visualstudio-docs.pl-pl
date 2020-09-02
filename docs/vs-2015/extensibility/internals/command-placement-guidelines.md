---
title: Wskazówki dotyczące umieszczania poleceń | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d88a477403c98ff11c5f7303b55f5eb713b668c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195102"
---
# <a name="command-placement-guidelines"></a>Wskazówki dotyczące umieszczania poleceń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najlepsze praktyki dotyczące pozycjonowania poleceń w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio różnią się w zależności od rozmiaru zestawu poleceń. Polecenia są definiowane i pozycjonowane zgodnie z informacjami w plikach. vsct.  
  
## <a name="best-practices-for-all-command-sets"></a>Najlepsze rozwiązania dotyczące wszystkich zestawów poleceń  
 Dla każdego zestawu poleceń postępuj zgodnie z następującymi wskazówkami:  
  
- Przygotuj wykres z zaawansowaną strukturą poleceń. Zidentyfikuj polecenia, pola kombi, grupy poleceń i menu skrótów, które będą używane w więcej niż jednej lokalizacji.  
  
- Polecenia, które pojawiają się w tej samej grupie, powinny być powiązane.  
  
- Grupy zawierające tylko jedno polecenie są dopuszczalne.  
  
- Pakiety nie powinny dodawać wielu poleceń do istniejących menu programu Visual Studio. Zamiast tego należy utworzyć menu lub podmenu, aby hostować nowe polecenia.  
  
- Gdy umieszczasz polecenie w istniejącym menu, nazwij to polecenie, tak aby jego przeznaczenie było jasne i nie będzie mylić z istniejącymi poleceniami.  
  
## <a name="best-practices-for-small-command-sets"></a>Najlepsze rozwiązania dotyczące małych zestawów poleceń  
 Jeśli opracowujesz pakietu VSPackage, który zawiera zaledwie kilka poleceń, postępuj zgodnie z następującymi wskazówkami:  
  
- Gdy to możliwe, użyj [elementu nadrzędnego](../../extensibility/parent-element.md) polecenia, pola kombi, grupy lub menu podrzędnego, aby umieścić je w odpowiedniej grupie.  
  
- Przypisz te grupy do menu wyświetlanych przez pakietu VSPackage.  
  
- Elementem nadrzędnym menu podrzędnego lub polecenia musi być [element grupy](../../extensibility/group-element.md). Przypisz polecenia i menu podrzędne do grup, a następnie przypisz grupy do menu nadrzędnego.  
  
- Możesz umieścić polecenie w dodatkowych grupach, dodając sekcję [elementu CommandPlacements](../../extensibility/commandplacements-element.md) po definicji polecenia, a następnie dodając do `CommandPlacements Element` [elementu CommandPlacement](../../extensibility/commandplacement-element.md) dla każdej dodatkowej grupy.  
  
## <a name="best-practices-for-large-command-sets"></a>Najlepsze rozwiązania dotyczące dużych zestawów poleceń  
 Jeśli pakietu VSPackage będzie zawierać wiele poleceń, które pojawią się w wielu kontekstach, należy również przestrzegać następujących wytycznych:  
  
- Utwórz własne menu, grupy i polecenia. Oznacza to, że nie należy przypisywać `Parent Element` w definicji elementu.  
  
- Użyj `CommandPlacement Element` wpisów w `CommandPlacements Element` sekcji, aby umieścić menu, grupy i polecenia w ich nadrzędnych menu i grupach.  
  
- W `CommandPlacements` sekcji wpisy, które wypełniają dany menu lub grupę, powinny należeć do siebie nawzajem. To ułatwia czytelność i ułatwia `Priority` określenie klasyfikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
