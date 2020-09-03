---
title: DA0021 — wysoka liczba wyrzucania elementów bezużytecznych generacji 1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.21
- vs.performance.DA0021
- vs.performance.rules.DA0021
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b22341f1e4944b91f86a16af19494a85a2abd013
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544693"
---
# <a name="da0021-high-rate-of-gen-1-garbage-collections"></a>DA0021: Duża częstotliwość odzyskiwania pamięci 1. generacji

|Element|Wartość|
|-|-|
|Identyfikator reguły|DA0021|
|Kategoria|Użycie .NET Framework|
|Metody profilowania|Wszystko|
|Komunikat|Występuje dość duża liczba wyrzucania elementów bezużytecznych generacji 1. W przypadku, gdy konstrukcja większość struktur danych programu jest alokowana i utrwalana przez dłuższy czas, nie jest to problem. Jeśli jednak takie zachowanie jest niezamierzone, aplikacja może przypinać obiekty. Jeśli nie masz pewności, możesz zebrać dane alokacji pamięci .NET i informacje o okresie istnienia obiektu, aby zrozumieć wzorzec alokacji pamięci używanej przez aplikację.|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Dane wydajności systemu, które zostały zebrane podczas profilowania wskazują, że znacząca część obiektów struktury for.NET pamięci została odbrana w ramach generacji 1 wyrzucania elementów bezużytecznych w porównaniu z zbieraniem danych generacji 0.

## <a name="rule-description"></a>Opis reguły
 Microsoft .NET Common Language Time (CLR) zapewnia automatyczny mechanizm zarządzania pamięcią, który używa modułu wyrzucania elementów bezużytecznych do odzyskiwania pamięci z obiektów, które nie są już używane przez aplikację. Moduł wyrzucania elementów bezużytecznych jest oparty na generacji, w oparciu o założenie, że wiele alokacji jest krótkoterminowych. Zmienne lokalne, na przykład, powinny być krótkotrwałe. Nowo utworzone obiekty rozpoczynają się w generacji 0 (Gen 0), a następnie postępować w generacji 1, gdy zajmują się uruchomieniem odzyskiwania pamięci, a wreszcie przechodzą do generacji 2, jeśli aplikacja nadal używa tych danych.

 Obiekty w generacji 0 są zbierane często i zwykle bardzo wydajnie. Obiekty w generacji 1 są zbierane rzadziej i mniej wydajne. Na koniec obiekty długotrwałe w generacji 2 powinny być zbierane nawet rzadziej. Kolekcja 2 generacji, która jest pełnym przebiegiem odzyskiwania pamięci, jest również najtańszą operacją.

 Ta reguła jest wyzwalana, gdy wystąpiło zbyt wiele kolekcji elementów bezużytecznych generacji 1. Jeśli zbyt wiele dość krótkotrwałych obiektów przeżyje kolekcję 0, ale można je zebrać w kolekcji generacji 1, koszty zarządzania pamięcią mogą być nadmierne. Aby uzyskać więcej informacji, zapoznaj się z wpisem [kryzysowym](https://blogs.msdn.microsoft.com/ricom/2003/12/04/mid-life-crisis/) w systemie Mariani w witrynie MSDN w sieci Web.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) danych profilowania. Znajdź kolumny kolekcji ** \\ Gen 0 w programie .NET CLR** i w polu Liczba **danych programu .NET CLR \\ w obszarze kolekcje generacji 1** . Ustal, czy istnieją konkretne etapy wykonywania programu, w których wyrzucanie elementów bezużytecznych występuje częściej. Porównaj te wartości w kolumnie **% Time w usłudze GC** , aby sprawdzić, czy wzorzec alokacji pamięci zarządzanej powoduje nadmierne obciążenie zarządzania pamięcią.

 Aby zrozumieć wzorzec zastosowania pamięci zarządzanej, należy go ponownie uruchomić, a.NET profil alokacji pamięci i żądania okresu istnienia obiektu.

 Aby uzyskać informacje na temat zwiększania wydajności odzyskiwania pamięci, zobacz [podstawy modułu zbierającego elementy bezużyteczne i wskazówki dotyczące wydajności](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) w witrynie sieci Web firmy Microsoft. Aby uzyskać informacje o obciążeniu automatycznego odzyskiwania pamięci, zapoznaj się z [pokrytym stertą dużego obiektu](https://msdn.microsoft.com/magazine/cc534993.aspx).
