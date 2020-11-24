---
title: Edytowanie testów obciążenia
description: Dowiedz się więcej o różnicach między scenariuszami, zestawami liczników i ustawieniami uruchomieniowymi, które definiują testy obciążenia.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 81825b2a9060d75a792e73519486275fd34569a4
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441472"
---
# <a name="edit-load-tests"></a>Edytuj testy obciążenia

Testy obciążenia umożliwiają uruchamianie testów wydajności sieci Web lub testów jednostkowych w celu symulowania wielu użytkowników uzyskujących dostęp do serwera w tym samym czasie. Test obciążeniowy umożliwia dostęp do danych obciążeniowych i wydajnościowych aplikacji. Test obciążeniowy można skonfigurować tak, aby emulował różne warunki obciążenia, np. obciążenie przez użytkowników i typy sieci.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Test obciążenia jest definiowany przez *scenariusze*, *zestawy liczników* i *Parametry uruchomieniowe*. Na poniższej ilustracji opisano różnice między [scenariuszami](../test/edit-load-test-scenarios.md), [zestawami liczników](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)i [ustawieniami uruchomieniowymi](../test/load-test-run-settings-properties.md):

![Architektura testu obciążenia](../test/media/load_test_editor.png)

## <a name="software-requirements"></a>Wymagania dotyczące oprogramowania

Projekty testów wydajności i obciążenia sieci Web są dostępne tylko w wersji Enterprise programu Visual Studio.

## <a name="edit-load-test-scenario-settings"></a>Edytuj ustawienia scenariusza testu obciążenia

Scenariusz jest używany do modelowania sposobu interakcji grupy użytkowników z aplikacją serwera. Scenariusz składa się z wzorca obciążenia, modelu testu mieszanego, testu mieszanego, mieszanej przeglądarki i mieszanego profilu sieciowego. Test obciążenia może mieć więcej niż jeden scenariusz, a jeden scenariusz może zawierać testy wydajności sieci Web i testy jednostkowe. Grupując podobne ustawienia, scenariusz umożliwia łączenie i wspólne wykonywanie testów o podobnym charakterze.

Aby uzyskać więcej informacji, zobacz [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md) i [właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md).

## <a name="configure-and-manage-performance-counter-sets"></a>Konfigurowanie zbiorów liczników wydajności i zarządzanie nimi

Testy obciążenia zapewniają nazwane zestawy liczników uporządkowane według technologii, które są przydatne podczas analizowania danych licznika wydajności. Zestawy liczników obejmują test obciążenia, IIS, ASP.NET i SQL. Podczas tworzenia testu obciążenia z **nowym Kreator testu obciążeniowego** początkowy zestaw wstępnie zdefiniowanych i ważnych liczników jest konfigurowany dla komputerów określonych do uwzględnienia w teście obciążenia. Zarządzasz licznikami w **Edytor testu obciążeniowego**.

Aby uzyskać więcej informacji, zobacz [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="configure-and-manage-load-test-run-settings"></a>Skonfiguruj ustawienia przebiegu testu obciążenia i zarządzaj nimi

Parametry uruchomieniowe są właściwościami wpływającymi na sposób uruchamiania testu obciążenia. Parametry uruchomieniowe są zorganizowane według kategorii w oknie **Właściwości** .

Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md) i [Ustawienia przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizowanie naruszeń reguł progu](../test/analyze-threshold-rule-violations-in-load-tests.md)
