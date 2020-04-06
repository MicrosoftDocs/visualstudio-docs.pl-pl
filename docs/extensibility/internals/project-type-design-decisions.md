---
title: Decyzje dotyczące projektowania typu projektu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e33ac1c4168593b881f799dfdfb94005fb55fc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706372"
---
# <a name="project-type-design-decisions"></a>Decyzje projektowe dotyczące typów projektów
Przed utworzeniem nowego typu projektu należy podjąć kilka decyzji projektowych dotyczących typu projektu. Należy zdecydować, jakie typy elementów będą zawierać projekty, jak pliki projektu będą utrwalane i jaki model zaangażowania będzie używany.

## <a name="project-items"></a>Elementy projektu
 Czy projekt będzie używać plików lub abstrakcyjnych obiektów? Jeśli używasz plików, będą to pliki oparte na odwołaniach lub katalogach? Czy pliki lub abstrakcyjne obiekty będą lokalne lub zdalne?

 Elementy w projekcie mogą być plikami lub mogą być bardziej abstrakcyjnymi obiektami, takimi jak obiekty w repozytorium bazy danych lub połączenia danych w Internecie. Jeśli elementy są plikami, projekt może być projektem opartym na odwołań lub opartym na katalogu.

 W projektach opartych na odwołaniach elementy mogą być wyświetlane w więcej niż jednym projekcie. Jednak rzeczywisty plik, który reprezentuje element znajduje się tylko w jednym katalogu. W projektach opartych na katalogu wszystkie elementy projektu istnieją w strukturze katalogów.

 Elementy lokalne są przechowywane na tym samym komputerze, na którym jest zainstalowana aplikacja. Elementy zdalne mogą być przechowywane na oddzielnym serwerze w sieci lokalnej lub w innym miejscu w Internecie.

## <a name="project-file-persistence"></a>Trwałość pliku projektu
 Czy dane będą przechowywane we wspólnych płaskich systemach plików lub w ustrukturyzowanym magazynie? Czy pliki będą otwierane przy użyciu standardowego edytora lub edytora specyficznego dla projektu?

 Aby utrwalić swoje dane, większość aplikacji zapisać swoje dane w pliku, a następnie odczytać je z powrotem, gdy użytkownik musi przejrzeć lub zmienić informacje.

 Magazyn strukturalny, nazywany również plikami złożonymi, jest zwykle używany, gdy kilka obiektów com (Component Object Model) musi przechowywać swoje utrwalone dane w jednym pliku. Dzięki ustrukturyzowanej pamięci masowej kilka różnych składników oprogramowania może współużytkować pojedynczy plik dysku.

 Istnieje kilka opcji do rozważenia dotyczące trwałości dla elementów w projekcie. Można wykonać jedną z następujących opcji:

- Zapisz każdy plik indywidualnie po jego zmianie.

- Przechwytywanie wielu transakcji w jednej operacji **zapisywania.**

- Zapisz pliki lokalnie, a następnie opublikuj na serwerze lub użyj innego podejścia do zapisywania elementów projektu, gdy element reprezentuje połączenie danych z obiektem zdalnym.

  Aby uzyskać więcej informacji na temat trwałości, zobacz [Trwałość projektu](../../extensibility/internals/project-persistence.md) oraz [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="project-commitment-model"></a>Model zaangażowania projektu
 Czy utrwalone obiekty danych zostaną otwarte w trybie bezpośrednim lub w trybie transacted?

 Gdy obiekty danych są otwierane w trybie bezpośrednim, zmiany wprowadzone do danych są włączane natychmiast lub gdy użytkownik ręcznie zapisuje plik.

 Gdy obiekty danych są otwierane w trybie transakcji, zmiany są zapisywane w tymczasowej lokalizacji w pamięci i nie są zatwierdzane, dopóki użytkownik ręcznie nie zdecyduje się zapisać pliku. W tym czasie wszystkie zmiany muszą nastąpić razem lub żadne zmiany nie zostaną wprowadzone.

## <a name="see-also"></a>Zobacz też
- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)
- [Trwałość projektu](../../extensibility/internals/project-persistence.md)
- [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)
- [Podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md)
- [Tworzenie typów projektów](../../extensibility/internals/creating-project-types.md)
