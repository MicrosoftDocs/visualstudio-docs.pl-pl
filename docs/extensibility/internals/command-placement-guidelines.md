---
title: Wskazówki dotyczące umieszczania poleceń | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4cc3dfa8aaeba01709ae74ca9a1d9d54f3c1743
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342119"
---
# <a name="command-placement-guidelines"></a>Wskazówki dotyczące umieszczania poleceń
Najlepsze rozwiązania dotyczące pozycjonowania poleceń w programie Visual Studio zintegrowane środowisko programistyczne (IDE) różnią się w zależności od rozmiaru zestawu poleceń. Polecenia są zdefiniowane i pozycjonować względem informacji w *vsct* plików.

## <a name="best-practices-for-all-command-sets"></a>Najlepsze rozwiązania dotyczące wszystkie zestawy poleceń
 Dla każdego zestawu poleceń należy przestrzegać następujących wytycznych:

- Przygotuj wcześniej wykres strukturę polecenia. Zidentyfikuj poleceń, pola kombi, grup poleceń i menu skrótów, które będą używane w więcej niż jednej lokalizacji.

- Polecenia, które pojawiają się w tej samej grupy, musi być powiązany.

- Grupy zawierające tylko jednego polecenia są akceptowane.

- Pakiety nie należy dodawać wiele poleceń do istniejącego menu programu Visual Studio. Zamiast tego należy ich utworzyć menu i podmenu do obsługi nowych poleceń.

- Po umieszczeniu polecenia w istniejącego menu, a nazwa polecenia tak, aby jej przeznaczenie było jasne, i nie należy mylić przy użyciu istniejących poleceń.

## <a name="best-practices-for-small-command-sets"></a>Najlepsze rozwiązania dotyczące polecenia małych zestawów
 Jeśli opracowujesz pakietu VSPackage, który ma kilka poleceń, należy również przestrzegać następujących wytycznych:

- Jeśli to możliwe, użyj [nadrzędnego](../../extensibility/parent-element.md) elementu polecenia, pola kombi, grupie lub menu podrzędne umieść go w odpowiedniej grupie.

- Przypisz te grupy do menu wyświetlane przez pakietu VSPackage.

- Element nadrzędny elementu menu podrzędne lub polecenia musi być [grupy](../../extensibility/group-element.md) elementu. Przypisać do grup poleceń i menu podrzędne, a następnie przypisać je do menu nadrzędnego.

- Polecenia można umieścić w dodatkowych grup, dodając [CommandPlacements](../../extensibility/commandplacements-element.md) element części po definicji polecenia, a następnie dodając do `CommandPlacements` elementu [CommandPlacement](../../extensibility/commandplacement-element.md) — element dla każdej grupy dodatkowych.

## <a name="best-practices-for-large-command-sets"></a>Najlepsze rozwiązania dotyczące polecenia dużych zestawów
 Jeśli Twojego pakietu VSPackage będzie miał wiele poleceń, które pojawią się w wielu sytuacjach, należy również przestrzegać następujących wytycznych:

- Upewnij się, menu, grupy i polecenia własnym elementy nadrzędne. Oznacza to, nie należy przypisywać `Parent` w definicji elementu.

- Użyj `CommandPlacement` wpisów element `CommandPlacements` elementu sekcji, aby umieścić w swojej grupy nadrzędnej menu i menu, grupy i polecenia.

- W `CommandPlacements` sekcji element wpisy, służące do wypełniania danego menu lub grupy powinny być przylegające do siebie nawzajem. To pomaga zwiększyć czytelność i sprawia, że `Priority` łatwiej określić klasyfikacji.

## <a name="see-also"></a>Zobacz także
- [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Pliki tabeli (vsct) polecenia programu Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)