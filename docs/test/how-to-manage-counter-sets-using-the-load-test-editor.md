---
title: Zestawy liczników testu obciążeniowego
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 995cf0653886745d44ede4553e03f81ed45d37d7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049084"
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>Porady: Zarządzanie zbiorami liczników za pomocą edytora testu obciążenia

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**, jest dodawany początkowy zestaw liczników. Oferują one zestawy wstępnie zdefiniowanych zbiorów liczników dla testu obciążeniowego.

> [!NOTE]
> Jeśli testy obciążeniowe są rozmieszczone na komputerach zdalnych, liczniki kontrolera i agenta są mapowane na zbiory liczników kontrolera i agenta. Aby uzyskać więcej informacji o sposobie używania komputerów zdalnych w teście obciążenia, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

Zarządzanie zbiorami liczników obejmuje, wybierając zestaw komputerów, które chcesz zebrać dane o wydajności i przypisywanie zbiór zestawów liczników, które mają być zbierane z każdego komputera. Zarządzasz licznikami w **edytora testu obciążenia**.

![Zarządzanie zbiorami liczników](../test/media/loadtestmanagecountersets.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-manage-counter-sets"></a>Aby zarządzanie zbiorami liczników

1.  Otwórz test obciążenia.

2.  Wybierz **Zarządzaj zbiorem liczników** przycisku.

     — lub —

     Kliknij prawym przyciskiem myszy **zbiorów liczników** folderu obciążenia testów drzewa i wybierz przycisk **Zarządzaj zbiorem liczników**.

     **Zarządzaj zbiorem liczników** zostanie wyświetlone okno dialogowe.

3.  (Opcjonalnie) W **wybrane komputery i zbiory liczników zostaną dodane następujące parametry uruchomieniowe** pola listy, wybierz inne ustawienie uruchamiania.

    > [!NOTE]
    > Dotyczy to tylko, jeśli masz więcej niż jedno ustawienie uruchamiania w teście obciążenia.

4.  (Opcjonalnie) Wybierz **Dodaj komputer** należy dodać nowy komputer do monitorowania. Użytkownik jest monitowany o podanie nazwy. Wpisz nazwę komputera, a zobaczysz węzłów poniżej nowy wpis. Na przykład **ASP.NET**, **IIS**, **SQL**i innym osobom. Zaznacz pola wyboru przed węzły, które mają zostać zaznaczone. Nowe liczniki są wyświetlane w **podgląd zaznaczenia** okienka.

5.  (Opcjonalnie) W **tagów** pole tekstowe, wpisz znacznik do skojarzenia z komputera. Na przykład "TestMachine12 w lab3".

     Tagi komputera pozwalają zidentyfikować komputer o nazwie łatwy do rozpoznania.

     Znaczniki są wyświetlane w **mapowaniach zbioru liczników** węzeł w drzewie w edytorze testu obciążenia. Co ważniejsze, znaczniki są wyświetlane w raportach programu Excel, które pomagają identyfikować zainteresowane strony jaką rolę na komputerze nie ma w teście obciążeniowym. Na przykład "Web serwer1 w lab2" lub "SQL Server2 w pakiecie office Phoenix". Aby uzyskać więcej informacji, zobacz [testy obciążenia raport wyników dla potrzeb porównań testów lub analizy trendów](../test/compare-load-test-results.md).

6.  Wybierz **OK**.

## <a name="see-also"></a>Zobacz także

- [Kontrolerzy testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md)
- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)