---
title: Wskazówki dotyczące umieszczania poleceń | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60046165"
---
# <a name="command-placement-guidelines"></a>Wskazówki dotyczące umieszczania poleceń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najlepsze rozwiązania dotyczące pozycjonowania poleceń w programie Visual Studio zintegrowane środowisko programistyczne (IDE) różnią się w zależności od rozmiaru zestawu poleceń. Polecenia są zdefiniowane i pozycjonować względem informacji w .vsct — pliki.  
  
## <a name="best-practices-for-all-command-sets"></a>Najlepsze rozwiązania dotyczące wszystkie zestawy poleceń  
 Dla każdego zestawu poleceń należy przestrzegać następujących wytycznych:  
  
- Przygotuj wcześniej wykres strukturę polecenia. Zidentyfikuj poleceń, pola kombi, grup poleceń i menu skrótów, które będą używane w więcej niż jednej lokalizacji.  
  
- Polecenia, które pojawiają się w tej samej grupy, musi być powiązany.  
  
- Grupy zawierające tylko jednego polecenia są akceptowane.  
  
- Pakiety nie należy dodawać wiele poleceń do istniejącego menu programu Visual Studio. Zamiast tego należy ich utworzyć menu i podmenu do obsługi nowych poleceń.  
  
- Po umieszczeniu polecenia w istniejącego menu, a nazwa polecenia tak, aby jej przeznaczenie było jasne, i nie należy mylić przy użyciu istniejących poleceń.  
  
## <a name="best-practices-for-small-command-sets"></a>Najlepsze rozwiązania dotyczące polecenia małych zestawów  
 Jeśli opracowujesz pakietu VSPackage, który ma kilka poleceń, należy również przestrzegać następujących wytycznych:  
  
- Jeśli to możliwe, użyj [elementu nadrzędnego](../../extensibility/parent-element.md) polecenia, pola kombi, grupy lub menu podrzędne umieść go w odpowiedniej grupie.  
  
- Przypisz te grupy do menu wyświetlane przez pakietu VSPackage.  
  
- Element nadrzędny elementu menu podrzędne lub polecenia musi być [Element grupy](../../extensibility/group-element.md). Przypisać do grup poleceń i menu podrzędne, a następnie przypisać je do menu nadrzędnego.  
  
- Polecenia można umieścić w dodatkowych grup, dodając [CommandPlacements, Element](../../extensibility/commandplacements-element.md) sekcji po definicji polecenia, a następnie dodając do `CommandPlacements Element` [CommandPlacement, Element](../../extensibility/commandplacement-element.md) dla każdego dodatkowe grupy.  
  
## <a name="best-practices-for-large-command-sets"></a>Najlepsze rozwiązania dotyczące polecenia dużych zestawów  
 Jeśli Twojego pakietu VSPackage będzie miał wiele poleceń, które pojawią się w wielu sytuacjach, należy również przestrzegać następujących wytycznych:  
  
- Upewnij się, menu, grupy i polecenia własnym elementy nadrzędne. Oznacza to, nie należy przypisywać `Parent Element` w definicji elementu.  
  
- Użyj `CommandPlacement Element` wpisów w `CommandPlacements Element` sekcji, aby umieścić w swojej grupy nadrzędnej menu i menu, grupy i polecenia.  
  
- W `CommandPlacements` sekcji wpisów, służące do wypełniania danego menu lub grupa powinna być przylegające do siebie nawzajem. To pomaga zwiększyć czytelność i sprawia, że `Priority` łatwiej określić klasyfikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
