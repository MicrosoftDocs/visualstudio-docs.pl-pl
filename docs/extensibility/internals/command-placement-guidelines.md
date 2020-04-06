---
title: Wskazówki dotyczące umieszczania poleceń | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 021a5fd9f9931e3041a431d211c8ab49978bbbab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709572"
---
# <a name="command-placement-guidelines"></a>Wskazówki dotyczące umieszczania poleceń
Najważniejsze wskazówki dotyczące pozycjonowania poleceń w zintegrowanym środowisku programistycznym programu Visual Studio (IDE) różnią się w zależności od rozmiaru zestawu poleceń. Polecenia są definiowane i umieszczane zgodnie z informacjami w plikach *vsct.*

## <a name="best-practices-for-all-command-sets"></a>Najważniejsze wskazówki dotyczące wszystkich zestawów poleceń
 W przypadku każdego zestawu poleceń postępuj zgodnie z tymi wskazówkami:

- Przygotuj wykres struktury poleceń z wyprzedzeniem. Zidentyfikuj polecenia, pola kombi, grupy poleceń i menu skrótów, które będą używane w więcej niż jednej lokalizacji.

- Polecenia, które pojawiają się w tej samej grupie powinny być powiązane.

- Grupy, które zawierają tylko jedno polecenie są dopuszczalne.

- Pakiety nie należy dodawać wiele poleceń do istniejących menu programu Visual Studio. Zamiast tego należy utworzyć menu lub podmenu do hosta nowych poleceń.

- Po umieszczeniu polecenia w istniejącym menu, nazwij to polecenie, aby jego cel był jasny i nie będzie mylone z istniejącymi poleceniami.

## <a name="best-practices-for-small-command-sets"></a>Najważniejsze wskazówki dotyczące małych zestawów poleceń
 Jeśli tworzysz VSPackage, który ma tylko kilka poleceń, należy również wykonać następujące wskazówki:

- Jeśli to możliwe, użyj [elementu Nadrzędny](../../extensibility/parent-element.md) polecenia, pola kombi, grupy lub menu podrzędnego, aby umieścić go w odpowiedniej grupie.

- Przypisz te grupy do menu wyświetlanych przez VSPackage.

- Element nadrzędny menu podrzędnego lub polecenia musi być elementem [Group.](../../extensibility/group-element.md) Przypisz polecenia i menu podrzędne do grup, a następnie przypisz grupy do menu nadrzędnego.

- Można umieścić polecenie w dodatkowych grupach, dodając [CommandPlacements](../../extensibility/commandplacements-element.md) sekcji elementu po definicji `CommandPlacements` polecenia, a następnie dodanie do elementu [CommandPlacement](../../extensibility/commandplacement-element.md) element dla każdej dodatkowej grupy.

## <a name="best-practices-for-large-command-sets"></a>Najważniejsze wskazówki dotyczące dużych zestawów poleceń
 Jeśli vspackage będzie miał wiele poleceń, które pojawią się w wielu kontekstach, należy również wykonać następujące wskazówki:

- Tworzenie menu, grup i poleceń samo-parenting. Oznacza to, że `Parent` nie należy przypisywać elementu w definicji elementu.

- Wpisy elementów `CommandPlacements` w sekcji elementu umożliwia `CommandPlacement` umieszczanie menu, grup i poleceń w menu nadrzędnym i grupach.

- W `CommandPlacements` sekcji elementu wpisy, które wypełniają dane menu lub grupy powinny być obok siebie. Pomaga to w czytelności i ułatwia określenie `Priority` rankingów.

## <a name="see-also"></a>Zobacz też
- [Jak vspackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Pliki tabeli poleceń programu Visual Studio (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
