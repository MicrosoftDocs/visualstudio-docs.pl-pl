---
title: Decyzje projektowe dotyczące typów projektu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 706bbda01912c660982a84a385686d1418566971
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948339"
---
# <a name="project-type-design-decisions"></a>Decyzje projektowe dotyczące typów projektów
Przed przystąpieniem do tworzenia nowych typów projektów należy kilka decyzji projektowych dotyczących danego typu projektu. Należy zdecydować, jakie rodzaje elementów, który będzie zawarty w projekcie, jak pliki projektu zostaną utrwalone i jakie modelu zobowiązania będą używane.  
  
## <a name="project-items"></a>Elementy projektu  
 Projekt użyje plików lub abstrakcyjne obiekty? Jeśli używasz plików, ich będą oparte na odwołania lub na podstawie katalogu plików? Czy pliki lub abstrakcyjne obiekty przerywaj być lokalny lub zdalny?  
  
 Elementy w projekcie mogą być plikami lub mogą być bardziej abstrakcyjne obiekty, takie jak obiekty połączenia bazy danych repozytorium lub danych w Internecie. Jeśli elementy znajdują się pliki projektu można na podstawie odwołania lub na podstawie katalogu projektu.  
  
 W projektach odwołania elementów może się pojawić w więcej niż jeden projekt. Jednak sam plik, który reprezentuje element znajduje się w tylko jednym katalogu. W projektach na poziomie katalogu wszystkich elementów projektu istnieje w strukturze katalogów.  
  
 Elementy lokalne są przechowywane na tym samym komputerze, na którym zainstalowano aplikację. Elementy zdalne mogą być przechowywane na oddzielnym serwerze w sieci lokalnej lub gdzie indziej w Internecie.  
  
## <a name="project-file-persistence"></a>Trwałość pliku projektu  
 Będą przechowywane dane typowe systemy plików prostych lub strukturalny Magazyn? Zostaną otwarte pliki za pomocą edytora standardowego lub edytora specyficznych dla projektu?  
  
 Aby zachować swoje dane, większość aplikacji zapisać swoje dane w pliku, a następnie przeczytaj po użytkownik musi przejrzeć lub zmienić informacje.  
  
 Funkcji strukturalnego magazynu, nazywany również pliki złożone, zazwyczaj jest używane, gdy kilka obiektów Component Object Model (COM) należy do przechowywania ich danych w jednym pliku. Z funkcji strukturalnego magazynu kilka innych składników oprogramowania można udostępnić plik jednego dysku.  
  
 Istnieje kilka opcji do rozważenia dotyczące stanów trwałych dla elementów w projekcie. Możesz wykonać dowolne spośród następujących opcji:  
  
- Zapisz każdego pliku osobno, po zmianie.  
  
- Przechwytywanie wiele transakcji w ramach pojedynczej **Zapisz** operacji.  
  
- Zapisywanie plików lokalnie, a następnie opublikować na serwerze lub użyj innego podejścia do zapisywania elementów projektu, gdy element reprezentuje połączenie danych z obiektu zdalnego.  
  
  Aby uzyskać więcej informacji na temat stanu trwałego zobacz [trwałość projektu](../../extensibility/internals/project-persistence.md) i [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Model zobowiązania projektu  
 Zostanie otwarty obiekty utrwalone dane w trybie bezpośredniego lub transakcyjne?  
  
 Po otwarciu obiektów danych w trybie bezpośredniego, zmiany wprowadzone w danych są włączone bezpośrednio, lub gdy użytkownik ręcznie zapisuje plik.  
  
 Po otwarciu obiektów danych przy użyciu trybu transakcyjne, zmiany są zapisywane do tymczasowej lokalizacji w pamięci i nie są przekazywane, dopóki użytkownik chce ręcznie Zapisz plik. W tym czasie wszystkie zmiany muszą występować razem lub nie zostaną wprowadzone nie zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Trwałość projektu](../../extensibility/internals/project-persistence.md)   
 [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)   
 [Podstawowe składniki modelu projektu](../../extensibility/internals/project-model-core-components.md)   
 [Tworzenie typów projektów](../../extensibility/internals/creating-project-types.md)