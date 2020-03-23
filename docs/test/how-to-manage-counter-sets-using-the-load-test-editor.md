---
title: Zestawy liczników testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.dialog.countersetmapping
helpviewer_keywords:
- counters, counter sets
- performance counters
- counter sets
- load tests, counter sets
ms.assetid: 64315c2f-a0b2-4378-be16-0774b99beef5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 224ac14a0d670648f8047a82a8abef0c2b7b2654
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113425"
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>Jak: Zarządzanie zestawami liczników za pomocą Edytora testów obciążenia

Podczas tworzenia testu obciążenia za pomocą **Kreatora nowego testu obciążenia**należy dodać początkowy zestaw liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego.

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji na temat korzystania z komputerów zdalnych w teście obciążenia, zobacz [Kontrolery testów i agenci testowi.](configure-test-agents-and-controllers-for-load-tests.md)

Zarządzanie zestawami liczników polega na wyborze zestawu komputerów, z których chcesz zbierać dane dotyczące wydajności, oraz na przypisywaniu zestawu zestawów liczników do zbierania z każdego komputera. Liczniki można zarządzać w **Edytorze testów obciążenia**.

![Zarządzanie zestawami liczników](../test/media/loadtestmanagecountersets.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-manage-counter-sets"></a>Aby zarządzać zestawami liczników

1. Otwórz test obciążenia.

2. Wybierz przycisk **Zarządzaj zestawami liczników.**

     – lub –

     Kliknij prawym przyciskiem myszy folder **Zestawy liczników** w drzewie testu obciążenia i wybierz polecenie **Zarządzaj zestawami liczników**.

     Zostanie wyświetlone okno dialogowe **Zarządzanie zestawami liczników.**

3. (Opcjonalnie) W polu listy **Wybrane komputery i zestawy liczników zostaną dodane w polu** listy Ustawienia uruchamiania wybierz inne ustawienie uruchamiania.

    > [!NOTE]
    > Dotyczy to tylko wtedy, gdy masz więcej niż jedno ustawienie uruchomienia w teście obciążenia.

4. (Opcjonalnie) Wybierz **pozycję Dodaj komputer,** aby dodać nowy komputer do monitorowania. Zostanie wyświetlony monit o podanie nazwy. Wpisz nazwę komputera, a zobaczysz węzły pod nowym wpisem. Na przykład **ASP.NET**, **IIS**, **SQL**i inne. Zaznacz pola wyboru przed węzłami, które chcesz zaznaczyć. Nowe liczniki pojawią się w okienku **Podgląd wyborów.**

5. (Opcjonalnie) W polu **tekstowym Znaczniki komputera** wpisz znacznik, który ma być skojarzony z komputerem. Na przykład "TestMachine12 w lab3".

     Znaczniki komputerowe umożliwiają identyfikację komputera o łatwej do rozpoznania nazwie.

     Znaczniki są wyświetlane w węźle **Mapowania zestawów liczników** w drzewie w Edytorze testów obciążenia. Co ważniejsze, tagi są wyświetlane w raportach programu Excel, które pomagają zainteresowanym stronom określić rolę komputera w teście obciążenia. Na przykład "Web Server1 w lab2" lub "SQL Server2 w biurze Phoenix". Aby uzyskać więcej informacji, zobacz [Raport wyników testów obciążenia dla porównań testów lub analizy trendów](../test/compare-load-test-results.md).

6. Wybierz pozycję **OK**.

## <a name="see-also"></a>Zobacz też

- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
