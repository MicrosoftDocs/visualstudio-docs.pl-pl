---
title: Decyzje projektowe typu projektu | Microsoft Docs
description: Przed rozszerzeniem programu Visual Studio, należy zapoznać się z informacjami o elementach, trwałości plików projektu i decyzjach projektowych dla mechaników.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2f1a90082b0ba9d18336463b26cf72acea39851b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064312"
---
# <a name="project-type-design-decisions"></a>Decyzje projektowe dotyczące typów projektów
Przed utworzeniem nowego typu projektu należy podjąć kilka decyzji projektowych dotyczących typu projektu. Należy zdecydować, jakie typy elementów zawiera projekt, jak zostaną utrwalone pliki projektu i jakiego modelu zobowiązań będziesz używać.

## <a name="project-items"></a>Elementy projektu
 Czy projekt będzie używać plików lub obiektów abstrakcyjnych? Jeśli używasz plików, czy będą one plikami referencyjnymi lub opartymi na katalogu? Czy pliki lub obiekty abstrakcyjne mają być lokalne lub zdalne?

 Elementy projektu mogą być plikami lub mogą być bardziej abstrakcyjnymi obiektami, takimi jak obiekty w repozytorium bazy danych lub połączenia danych przez Internet. Jeśli elementy są plikami, projekt może być projektem opartym na odwołania lub w katalogu.

 W projektach opartych na odwołaniach elementy mogą znajdować się w więcej niż jednym projekcie. Jednak rzeczywisty plik reprezentowany przez element znajduje się tylko w jednym katalogu. W projektach opartych na katalogu wszystkie elementy projektu istnieją w strukturze katalogów.

 Elementy lokalne są przechowywane na tym samym komputerze, na którym zainstalowano aplikację. Elementy zdalne mogą być przechowywane na osobnym serwerze w sieci lokalnej lub w innym miejscu w Internecie.

## <a name="project-file-persistence"></a>Trwałość pliku projektu
 Czy dane będą przechowywane w popularnych zwykłych systemach plików, czy w magazynie strukturalnym? Czy pliki będą otwierane przy użyciu standardowego edytora czy edytora specyficznego dla projektu?

 Aby zachować swoje dane, większość aplikacji zapisuje swoje dane w pliku, a następnie odczytuje je ponownie, gdy użytkownik musi przejrzeć lub zmienić informacje.

 Magazyn strukturalny, nazywany również plikami złożonymi, jest zwykle używany, gdy kilka obiektów Component Object Model (COM) musi przechowywać utrwalone dane w jednym pliku. W przypadku magazynu strukturalnego niektóre różne składniki oprogramowania mogą współużytkować jeden plik na dysku.

 Istnieje kilka opcji, które należy wziąć pod uwagę w odniesieniu do elementów w projekcie. Można wykonać jedną z następujących czynności:

- Zapisz każdy plik indywidualnie, gdy został zmieniony.

- Przechwyć wiele transakcji w ramach jednej operacji **zapisywania** .

- Zapisz lokalnie pliki, a następnie opublikuj je na serwerze lub użyj innego podejścia do zapisywania elementów projektu, gdy element reprezentuje połączenie danych z obiektem zdalnym.

  Aby uzyskać więcej informacji na temat trwałości, zobacz temat [trwałość projektu](../../extensibility/internals/project-persistence.md) i [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="project-commitment-model"></a>Model zobowiązania projektu
 Czy utrwalane obiekty danych będą otwierane w trybie bezpośrednim czy w trybie transakcyjnym?

 Gdy obiekty danych są otwierane w trybie bezpośrednim, zmiany wprowadzone do danych są włączane natychmiast lub po ręcznym zapisaniu pliku przez użytkownika.

 Gdy obiekty danych są otwierane przy użyciu trybu transakcyjnego, zmiany są zapisywane w tymczasowej lokalizacji w pamięci i nie są zatwierdzane, dopóki użytkownik nie zdecyduje się ręcznie zapisać pliku. W tym czasie wszystkie zmiany muszą następować razem lub nie będą wprowadzane żadne zmiany.

## <a name="see-also"></a>Zobacz też
- [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)
- [Trwałość projektu](../../extensibility/internals/project-persistence.md)
- [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)
- [Podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md)
- [Tworzenie typów projektów](../../extensibility/internals/creating-project-types.md)
