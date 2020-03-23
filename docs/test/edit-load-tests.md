---
title: Edytowanie testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c61c13f6a9eca416a52221ba9da37be820dd4b89
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593229"
---
# <a name="edit-load-tests"></a>Edytowanie testów obciążenia

Testy obciążenia uruchamiają testy wydajności sieci web lub testy jednostkowe, aby symulować wielu użytkowników uzyskujących dostęp do serwera w tym samym czasie. Test obciążeniowy umożliwia dostęp do danych obciążeniowych i wydajnościowych aplikacji. Test obciążeniowy można skonfigurować tak, aby emulował różne warunki obciążenia, np. obciążenie przez użytkowników i typy sieci.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Test obciążenia jest definiowany przez *scenariusze,* *zestawy liczników*i *ustawienia uruchamiania*. Na poniższej ilustracji wyjaśniono różnice między [scenariuszami, zestawami](../test/edit-load-test-scenarios.md) [liczników](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)i [ustawieniami uruchamiania:](../test/load-test-run-settings-properties.md)

![Architektura testu obciążenia](../test/media/load_test_editor.png)

## <a name="software-requirements"></a>Wymagania dotyczące oprogramowania

Projekty testów wydajności sieci Web i obciążenia są dostępne tylko w wersji Enterprise programu Visual Studio.

## <a name="edit-load-test-scenario-settings"></a>Edytowanie ustawień scenariusza testu obciążenia

Scenariusz jest używany do modelowania, jak grupa użytkowników współdziała z aplikacją serwera. Scenariusz składa się z wzorca obciążenia, modelu testu mieszanego, testu mieszanego, mieszanej przeglądarki i mieszanego profilu sieciowego. Test obciążenia może mieć więcej niż jeden scenariusz i pojedynczy scenariusz może zawierać testy wydajności sieci web i testy jednostkowe. Grupując podobne ustawienia, scenariusz umożliwia łączenie i wspólne wykonywanie testów o podobnym charakterze.

Aby uzyskać więcej informacji, zobacz [Edytowanie scenariuszy testów obciążenia](../test/edit-load-test-scenarios.md) i [właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md).

## <a name="configure-and-manage-performance-counter-sets"></a>Konfigurowanie zestawów liczników wydajności i zarządzanie nimi

Testy obciążenia zapewniają nazwane zestawy liczników, uporządkowane według technologii, które są przydatne podczas analizowania danych licznika wydajności. Zestawy liczników obejmują test obciążenia, usługi IIS, ASP.NET i SQL. Podczas tworzenia testu obciążenia za pomocą **Kreatora nowego testu obciążenia**dla komputerów, które mają być uwzględnione w teście obciążenia, jest konfigurowany początkowy zestaw wstępnie zdefiniowanych i ważnych liczników. Liczniki można zarządzać w **Edytorze testów obciążenia**.

Aby uzyskać więcej informacji, zobacz [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="configure-and-manage-load-test-run-settings"></a>Konfigurowanie ustawień przebiegu testu obciążenia i zarządzanie nimi

Uruchom ustawienia są właściwości, które wpływają na sposób uruchamiania testu obciążenia. Ustawienia uruchamiania są uporządkowane według kategorii w oknie **Właściwości.**

Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md) i [Właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

## <a name="see-also"></a>Zobacz też

- [Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizowanie naruszeń reguł progowych](../test/analyze-threshold-rule-violations-in-load-tests.md)
