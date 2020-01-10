---
title: 'DA0005: częste kolekcje odzyskiwanie pamięci GC2 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0005
- vs.performance.rules.DAManyGC2Collections
- vs.performance.5
- vs.performance.rules.DA0005
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 74091a3fe2da42ce3a9d16fdfa581d7774492574
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852309"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005: Częste kolekcje GC2
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

RuleId|DA0005|  
|Category|.NET Framework Usage|  
| Metoda profilowania |. Pamięć sieciowa |  
| Komunikat | Wiele obiektów jest zbieranych w wyrzucaniu elementów bezużytecznych generacji 2. |  
| Typ komunikatu | Ostrzeżenie |  
  
## <a name="cause"></a>Przyczyna  
 W wyrzucaniu elementów bezużytecznych generacji 2 są odzyskiwane duże ilości obiektów pamięci platformy .NET.  
  
## <a name="rule-description"></a>Opis reguły  
 Microsoft .NET środowisko uruchomieniowe języka wspólnego (CLR) zapewnia automatyczny mechanizm zarządzania pamięcią, który używa modułu wyrzucania elementów bezużytecznych do odzyskiwania pamięci z obiektów, które nie są już używane przez aplikację. Moduł wyrzucania elementów bezużytecznych jest oparty na generacji, w oparciu o założenie, że wiele alokacji jest krótkoterminowych. Zmienne lokalne, na przykład, powinny być krótkotrwałe. Nowo utworzone obiekty rozpoczynają się w generacji 0 (Gen 0), a następnie postępować w generacji 1, gdy zajmują się uruchomieniem odzyskiwania pamięci, a wreszcie przechodzą do generacji 2, jeśli aplikacja nadal używa tych danych.  
  
 Obiekty w generacji 0 są zbierane często i zwykle bardzo wydajnie. Obiekty w generacji 1 są zbierane rzadziej i mniej wydajne. Na koniec obiekty długotrwałe w generacji 2 powinny być zbierane nawet rzadziej. Kolekcja 2 generacji, która jest pełnym przebiegiem odzyskiwania pamięci, jest również najtańszą operacją.  
  
 Ta reguła jest wyzwalana, gdy wystąpiło zbyt wiele kolekcji elementów bezużytecznych generacji 2. Jeśli zbyt wiele stosunkowo krótkotrwałych obiektów przeżyje kolekcję 1, ale można je zebrać w pełnej kolekcji generacji 2, koszty zarządzania pamięcią mogą być łatwo nadmierne. Aby uzyskać więcej informacji, zapoznaj się z wpisem [kryzysowym](https://blogs.msdn.com/ricom/archive/2003/12/04/41281.aspx) w systemie Mariani w witrynie MSDN w sieci Web.  
  
## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie  
 Przejrzyj raporty dotyczące [widoków danych pamięci .NET](../profiling/dotnet-memory-data-views.md) , aby zrozumieć wzorzec alokacji pamięci aplikacji. [Widok okres istnienia obiektu](../profiling/object-lifetime-view.md) służy do określania, które obiekty danych programu są przejmowane do generacji 2, a następnie odzyskiwane z tego miejsca. [Widok alokacje](../profiling/dotnet-memory-allocations-view.md) służy do określania ścieżki wykonywania, która spowodowała te przydziały.  
  
 Aby uzyskać informacje na temat zwiększania wydajności odzyskiwania pamięci, zobacz [podstawy modułu zbierającego elementy bezużyteczne i wskazówki dotyczące wydajności](https://msdn2.microsoft.com/library/ms973837.aspx) w witrynie sieci Web firmy Microsoft. Aby uzyskać informacje o obciążeniu automatycznego odzyskiwania pamięci, zapoznaj się z [pokrytym stertą dużego obiektu](https://msdn.microsoft.com/magazine/cc534993.aspx).
