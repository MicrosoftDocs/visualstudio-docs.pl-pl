---
title: Wskazówki dotyczące umieszczania poleceń | Microsoft Docs
description: Poznaj wskazówki i najlepsze rozwiązania dotyczące poleceń pozycjonowania w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11a1619eaa625e086ac93bfa0f9e208239f8c844
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305248"
---
# <a name="command-placement-guidelines"></a>Wskazówki dotyczące umieszczania poleceń
Najlepsze praktyki dotyczące pozycjonowania poleceń w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio różnią się w zależności od rozmiaru zestawu poleceń. Polecenia są definiowane i pozycjonowane zgodnie z informacjami w plikach *. vsct* .

## <a name="best-practices-for-all-command-sets"></a>Najlepsze rozwiązania dotyczące wszystkich zestawów poleceń
 Dla każdego zestawu poleceń postępuj zgodnie z następującymi wskazówkami:

- Przygotuj wykres z zaawansowaną strukturą poleceń. Zidentyfikuj polecenia, pola kombi, grupy poleceń i menu skrótów, które będą używane w więcej niż jednej lokalizacji.

- Polecenia, które pojawiają się w tej samej grupie, powinny być powiązane.

- Grupy zawierające tylko jedno polecenie są dopuszczalne.

- Pakiety nie powinny dodawać wielu poleceń do istniejących menu programu Visual Studio. Zamiast tego należy utworzyć menu lub podmenu, aby hostować nowe polecenia.

- Gdy umieszczasz polecenie w istniejącym menu, nazwij to polecenie, tak aby jego przeznaczenie było jasne i nie będzie mylić z istniejącymi poleceniami.

## <a name="best-practices-for-small-command-sets"></a>Najlepsze rozwiązania dotyczące małych zestawów poleceń
 Jeśli opracowujesz pakietu VSPackage, który zawiera zaledwie kilka poleceń, postępuj zgodnie z następującymi wskazówkami:

- Gdy to możliwe, użyj elementu [nadrzędnego](../../extensibility/parent-element.md) polecenia, pola kombi, grupy lub menu podrzędnego, aby umieścić je w odpowiedniej grupie.

- Przypisz te grupy do menu wyświetlanych przez pakietu VSPackage.

- Elementem nadrzędnym menu podrzędnego lub polecenia musi być element [grupy](../../extensibility/group-element.md) . Przypisz polecenia i menu podrzędne do grup, a następnie przypisz grupy do menu nadrzędnego.

- Możesz umieścić polecenie w dodatkowych grupach, dodając sekcję elementu [CommandPlacements](../../extensibility/commandplacements-element.md) po definicji polecenia, a następnie dodając do `CommandPlacements` elementu element [CommandPlacement](../../extensibility/commandplacement-element.md) dla każdej dodatkowej grupy.

## <a name="best-practices-for-large-command-sets"></a>Najlepsze rozwiązania dotyczące dużych zestawów poleceń
 Jeśli pakietu VSPackage będzie zawierać wiele poleceń, które pojawią się w wielu kontekstach, należy również przestrzegać następujących wytycznych:

- Utwórz własne menu, grupy i polecenia. Oznacza to, że nie należy przypisywać `Parent` elementu w definicji elementu.

- Użyj `CommandPlacement` wpisów elementu w `CommandPlacements` sekcji element, aby umieścić menu, grupy i polecenia w ich nadrzędnych menu i grupach.

- W `CommandPlacements` sekcji element wpisy, które wypełniają danego menu lub grupę, powinny należeć do siebie nawzajem. To ułatwia czytelność i ułatwia `Priority` określenie klasyfikacji.

## <a name="see-also"></a>Zobacz też
- [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
