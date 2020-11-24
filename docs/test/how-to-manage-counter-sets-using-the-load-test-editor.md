---
title: Zestawy liczników testów obciążenia
description: Dowiedz się, jak za pomocą Edytor testu obciążeniowego zarządzać zbiorami liczników, wybierając komputery i przypisując zestawy liczników, które mają być zbierane z poszczególnych komputerów.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
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
ms.openlocfilehash: 15d04d105264d07a1f883c5b67ce57c8590375a8
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440016"
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>Instrukcje: zarządzanie zbiorami liczników przy użyciu Edytor testu obciążeniowego

Podczas tworzenia testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego** należy dodać początkowy zestaw liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego.

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji na temat korzystania z maszyn zdalnych w teście obciążenia, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

Zarządzanie zbiorami liczników obejmuje wybranie zestawu komputerów, z których mają być zbierane dane dotyczące wydajności, oraz przypisanie zestawu liczników zbieranych z poszczególnych komputerów. Zarządzasz licznikami w **Edytor testu obciążeniowego**.

![Zarządzanie zbiorami liczników](../test/media/loadtestmanagecountersets.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-manage-counter-sets"></a>Aby zarządzać zbiorami liczników

1. Otwórz test obciążenia.

2. Wybierz przycisk **Zarządzaj zbiorami liczników** .

     oraz

     Kliknij prawym przyciskiem myszy folder **zestawy liczników** w drzewie testu obciążenia i wybierz polecenie **Zarządzaj zbiorami liczników**.

     Zostanie wyświetlone okno dialogowe **Zarządzanie zbiorami liczników** .

3. Obowiązkowe W **obszarze wybrane komputery i zbiory liczników zostaną dodane do pola listy następujące parametry uruchomieniowe** wybierz inne ustawienie uruchomieniowe.

    > [!NOTE]
    > Ma to zastosowanie tylko wtedy, gdy masz więcej niż jedno ustawienie uruchomieniowe w teście obciążenia.

4. Obowiązkowe Wybierz pozycję **Dodaj komputer** , aby dodać nowy komputer do monitorowania. Zostanie wyświetlony monit o podanie nazwy. Wpisz nazwę komputera i zobaczysz węzły poniżej nowego wpisu. Na przykład **ASP.NET**, **IIS**, **SQL** i inne. Zaznacz pola wyboru przed węzłami, które chcesz wybrać. Nowe liczniki są wyświetlane w okienku **Opcje podglądu** .

5. Obowiązkowe W polu tekstowym **Tagi komputera** wpisz tag, który ma zostać skojarzony z komputerem. Na przykład "TestMachine12 in lab3".

     Znaczniki komputera pozwalają zidentyfikować komputer z łatwą do rozpoznania nazwą.

     Tagi są wyświetlane w węźle **mapowania zestawów liczników** w drzewie w Edytor testu obciążeniowego. Ważniejsze Tagi są wyświetlane w raportach programu Excel, które pomagają udziałowcom zidentyfikować rolę komputera w teście obciążenia. Na przykład "Web serwer1 in lab2" lub "SQL Serwer2 w biurze w Phoenix". Aby uzyskać więcej informacji, zobacz [raportowanie wyników testów obciążenia dla porównania testów lub analizy trendów](../test/compare-load-test-results.md).

6. Wybierz przycisk **OK**.

## <a name="see-also"></a>Zobacz także

- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Określ zestawy liczników i reguły progowe dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Skonfiguruj ustawienia przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
